---
title: Veritabanları PDO
anchor: veritabanlari-pdo
isChild: true
---

# Veritabanları PDO {#veritabanlari_pdo_title}

PDO bir veritabanı soyutlama kütüphanesidir. &mdash; PHP 5.1.0'den beri &mdash; 
PDO farklı veritabanları ile bağlantı için genel bir arayüz sunar. PDO SQL 
sorgularınızı çevirmez ya da eksik kısımlarını tamamlamamaz; Sadece farklı 
veritabanlarına bağlanmak için aynı API'yi kullanmanızı sağlar.

SQL injection atakları için `PDO` sorgunuzdaki yabancı girdileri kolaylıkla 
güvenli hale getirmenizi sağlar. Bu PDO deyimleri ve bağlı(bound) parametreler 
ile mümkündür.

Bir sorguya sayısal bir ID değeri ekleyelim ve veritabanından bir kullanıcının 
kayıtlarını çekmeye çalışalım. Bunu yapmak için aşağıdaki yanlış bir yöntemdir:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- Saldırıya açık bir sorgu!
{% endhighlight %}

Yukarıdaki kötü bir koddur. Kolaylıkla farkedilebilir ve kullanılabilir bir 
koddur. Kötü niyetli bir kişi `id` parametresinde sayı yerine 
`http://domain.com/?id=1%3BDELETE+FROM+users` gibi bir sorgu gönderebilir. Bu 
`$_GET['id']` değişkenine `1;DELETE FROM users` değerini atayacaktır ve bütün 
kullanıcılarınızı silecektir. Siz bunu PDO bağlı parameter ile girdiyi 
temizlemelisiniz.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); // <-- PDO tarafından sterilize edildi
$stmt->execute();
{% endhighlight %}

Bu doğru bir koddur. Bu bir PDO deyiminde bağlı parametreleri kullanıyor ve 
yabancı girdilerden gelecek zararları engelliyor.

* [PDO hakkında][1]

Veritabanı bağlantısı kapatılmadığında kaynaklarınız bir süre sonra tükenecektir. 
Bunu PDO kullanarak önleyebilirsiniz. PDO sayesinde bağlantı nesnesi silinirken 
bağlantı kapatılır ve bütün referansları silinir veya NULL'a eşitlenir. Bunu 
yapmazsanız kalıcı bir bağlantı kullanmadığınız sürece kodunuz bittiğinde PHP 
tabiki bağlantıları otomatik olarak kapatacaktır.

* [PDO bağlantıları hakkında][5]

## Sayutlama Katmanı (Abstraction Layers)

Birçok çatı PDO üzerine kurulmuş kendi soyutlanmış katmanını barındırmaktadır. 
Bunlar genellikle bir veritabanı sisteminin özelliklerini barındırmaktadır. 
Bazı durumlarda yetersiz kalsada uygulamanızın taşınabilir olması için bu gibi 
katmanlar güzel olabilir. (!)

Aşağıda uygulamalarınızda kullanabileceğiniz [PSR-0][psr0] veya [PSR-4][psr4] 
standardında bir kaç örnek bulunmaktadır:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/tr/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/tr/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/Propel/

[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md