---
title: UTF-8 ile Çalışmak
isChild: true
anchor: php_and_utf8
---

## UTF-8 ile Çalışmak {#php_and_utf8_title}

Bu bölüm orjinalde [Alex Cabal](https://alexcabal.com/) tarafından
[PHP Best Practices](https://phpbestpractices.org/#utf-8) sayfasında yazılmıştır
ve kendi tavsiyelerimizin temelinde kullanılmıştır.

### Dikkatli, Ayrıntılı ve Tutarlı Olun.

Şu anki PHP alt seviyelerinde Unicode desteklemiyor. UTF-8 metinlerin işlenmesi
için çeşitli yolları var, ama bu çok kolay değil ve bu web uygulamanızın hemen
hemen her seviyesinde değişikliğe neden olacak. HTML'den SQL'e PHP'ye. Size
pratik bir özet sunmayı amaçlıyoruz.

### PHP Seviyesinde UTF-8

İki metni birleştirmek ve bir metni bir değişkene atama gibi basit metin
işlemlerinde, UTF-8 için özel bir şey yapmanız gerekmiyor. Ama `strpos()` ve
`strlen()` gibi çoğu metin fonksiyonlarında özel bir dikkat gerekmektedir. Bu
fonksiyonların sıksık `mb_*` benzerlerine sahiptir. Örneğin, `mb_strpos()` ve
`mb_strlen()` gibi. Bu `mb_*` fonskiyonları, metinleri, [Multibyte String Extension]'ı
ile Unicode metinler üzerinde işlem yapabilecek hale getirmektedir.

Ne zaman Unicode metinler üzerinde işlem yapacaksanız `mb_*` fonskiyonlarını
kullanmalısınız. Örneğin, `substr()` fonksiyonunu UTF-8 metinler üzerinde
kullanırsanız; sonuç olarak bazı bozuk karakterler ile karşılaşabilirsiniz.
Kullanmanız gereken doğru fonksiyon `mb_substr()`dir.

Zor kısmı `mb_*` fonksiyonlarını hatırlamak. Eğer unutursanız Unicode metinlerde
metinlerin bozuk çıkma ihtimalleri var.

Bütün metinler `mb_*` kullanmak zorunda değiller. Eğer yapmak istediğiniz şey
için birden fazla yol varsa, bozuk karakterlerden kurtulmak için şansınız
olabilir.

`mb_internal_encoding()` fonksiyonunu her PHP dosyanızın başında (ya da her yere
include ettiğiniz dosyanın başında) kullanabilirsiniz, ve `mb_http_output()`
fonksiyonunu browser'a çıktı vermek için kullanabilirsiniz. Açıkça her kodunuzda
encoding bilgisini tanımlamanız ileride karşınıza çıkacak bir sürü baş ağrısından
sizi kurtaracaktır.

Ek olarak, bir çok PHP fonksiyonu opsiyonel parametreler ile sizin metninizi
seçtiğiniz bir encoding ile işleme tabi tutar.

Her zaman UTF-8 olarak göstermelisiniz. Örneğin `htmlentities()` karakter
encoding için bir opsiyonu bulunmaktadır, ve eğer bir metin ile ilişkili iseniz
UTF-8 olarak belirtmelisiniz. Ayrıca, PHP 5.4.0'da `htmlentities()` ve
`htmlspecialchars()` için varsayılan karakter encoding'i UTF-8'dir.

Son olarak, eğer dağıtık bir uygulama kuruyorsanız ve `mbstring` eklentisinin
açık olup olmadığından emin olamazsanız, [patchwork/utf8] Composer paketini
kullanmayı deneyebilirsiniz. Bu paket eğer uygunsa `mbstring` kullanır.

[Multibyte String Extension]: http://php.net/manual/tr/book.mbstring.php
[patchwork/utf8]: https://packagist.org/packages/patchwork/utf8

### Veritabanı Seviyesinde UTF-8

Eğer MYSQL kullanıyorsanız, yukarıda belirtilen önlemleri alsanız bile
verilerinizin UTF-8 olamyan hallerini tutabilirsiniz. Verilerinizin veritabanına
UTF-8 olarak kaydedildiğinden emin olmak için, tüm tablo ve veritabanlarınızın
character set ve collation değerlerinin `utf8mb4` olduğundan emin olun ve
PDO bağlantı metninde `utf8mb4` character set'ini kullanın. Örneği gözden
geçirin. Bu _özellikle önemli_.

Not olarak, tamamen UTF-8 desteği için `utf8mb4` kullanmak zorundasınız,
`utf8` değil. Nedeni için okumaya devam edin.

### Browser Seviyesinde UTF-8

PHP kodunuzun çıktısının UTF-8 formatında browser'a gittiğinden emin olmak için
`mb_http_output()` fonksiyonu kullanın.

The browser will then need to be told by the HTTP response that this page should be considered as UTF-8. The historic approach to doing that was to include the [charset `<meta>` tag](http://htmlpurifier.org/docs/enduser-utf8.html) in your page's `<head>` tag. This approach is perfectly valid, but setting the charset in the `Content-Type` header is actually [much faster](https://developers.google.com/speed/docs/best-practices/rendering#SpecifyCharsetEarly).

{% highlight php %}
<?php
// PHP'ye script sonuna kadar UTF-8 kullanacağımızı söylüyoruz
mb_internal_encoding('UTF-8');

// PHP'ye browser'a gönderilecek çıktının UTF-8 olacağını söylüyoruz
mb_http_output('UTF-8');

// Bİzim UTF-8 test metnimiz
$string = 'Êl síla erin lû e-govaned vîn.';

// Metnimizi multibyte fonsksiyon ile değiştiriyoruz
$string = mb_substr($string, 0, 15);

// Veritabanı bağlantısı
// Daha fazla bilgi için PDO örneklerine bakabilirsiniz.
// Not: `set names utf8mb4`
$link = new \PDO(
    'mysql:host=your-hostname;dbname=your-db;charset=utf8mb4',
    'your-username',
    'your-password',
    array(
        \PDO::ATTR_ERRMODE => \PDO::ERRMODE_EXCEPTION,
        \PDO::ATTR_PERSISTENT => false
    )
);

// Değiştirdiğimiz metni UTF-8 olarak veritabanına kaydediyoruz
// Veritabanı ve tablolarınız utf8bm4 formatında değil mi?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();

// Düzgün kaydedildiğini görmek için metni tekrar alıyoruz.
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();

// Birazdan bilgiyi HTML olarak bastıracağız
$result = $handle->fetchAll(\PDO::FETCH_OBJ);

header('Content-Type: text/html; charset=utf-8');
?><!doctype html>
<html>
    <head>
        <title>UTF-8 test sayfası</title>
    </head>
    <body>
        <?php
        foreach($result as $row){
            print($row->Body);  // This should correctly output our transformed UTF-8 string to the browser
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Daha fazla bilgi

* [PHP Manual: String Operations](http://php.net/language.operators.string)
* [PHP Manual: String Functions](http://php.net/ref.strings)
    * [`strpos()`](http://php.net/function.strpos)
    * [`strlen()`](http://php.net/function.strlen)
    * [`substr()`](http://php.net/function.substr)
* [PHP Manual: Multibyte String Functions](http://php.net/ref.mbstring)
    * [`mb_strpos()`](http://php.net/function.mb-strpos)
    * [`mb_strlen()`](http://php.net/function.mb-strlen)
    * [`mb_substr()`](http://php.net/function.mb-substr)
    * [`mb_internal_encoding()`](http://php.net/function.mb-internal-encoding)
    * [`mb_http_output()`](http://php.net/function.mb-http-output)
    * [`htmlentities()`](http://php.net/function.htmlentities)
    * [`htmlspecialchars()`](http://php.net/function.htmlspecialchars)
* [PHP UTF-8 Cheatsheet](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Handling UTF-8 with PHP](http://www.phpwact.org/php/i18n/utf-8)
* [Stack Overflow: What factors make PHP Unicode-incompatible?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Best practices in PHP and MySQL with international strings](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [How to support full Unicode in MySQL databases](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Bringing Unicode to PHP with Portable UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
* [Stack Overflow: DOMDocument loadHTML does not encode UTF-8 correctly](http://stackoverflow.com/questions/8218230/php-domdocument-loadhtml-not-encoding-utf-8-correctly)