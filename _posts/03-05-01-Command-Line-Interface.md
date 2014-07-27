---
title: Komut Satırı Arayüzü
isChild: true
anchor: komut_satiri_arayuzu
---

## Komut Satırı Arayüzü {#komut_satiri_arayuzu_title}

PHP web uygulamaları geliştirmek için oluşturuldu, ama komut satırı (CLI) uygulamaları içinde yararlıdır. Komut Satırından çalışan PHP uygulamaları test etme, yayınlama ve uygulama yönetimi vs gibi uygulamaları otomatize etmenize yardımcı olabilir.

CLI PHP uygulamaları güvenli bir web arayüzü oluşturmadan direk olarak çalıştığı için güçlüdür. Sadece komut satırı uygulamanızı direk ana web anadizinine koymayınız!

Aşağıdaki komutları komut satırında çalıştırmayı deneyiniz :

{% highlight bash %}
> php -i
{% endhighlight %}

`-i` özelliği PHP'nin konfigürasyonlarını [`phpinfo`][phpinfo] fonksiyonu gibi ekrana bastıracaktır.

`-a` özelliği ise ruby'nin IRBsi veya python gibi interaktif bir kabuk sağlayacaktır. [command line options][cli-options]'dan daha fazla özelliğe ulaşabilirsiniz.

"Hello, $isim" yazan basit bir CLI uygulaması yazalım. `merhaba.php` adında bir dosya oluşturup bunu çalıştırmayı deneyin.

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php merhaba.php [isim].\n";
    exit(1);
}
$isim = $argv[1];
echo "Hello, $isim\n";
{% endhighlight %}

PHP kodunuz çalıştığında argümanlar için iki özel değişken oluşturmaktadır. [`$argc`][argc] argümanların *sayısını* içereren sayı(integer) tipinde bir değişkendir ve [`$argv`][argv] her bir argümanın *değerini* içeren değişken dizisidir. İlk argüman her zaman PHP kodunun çalıştırıldığı dosyanın adınıdır, bu örnekte `merhaba.php`dir. 

`exit()` kodu kabuğun komutun hata ile sonuçlandığını düşünmemesi için sıfır olmayan bir değişken ile kullanılmalıdır. Genelde kullanılan exit  komutları [buradadır][exit-codes].

Kodumuzu çalıştırmak için aşağıdaki satırları kullanabilirsiniz :

{% highlight bash %}
> php merhaba.php
Usage: php merhaba.php [isim]
> php merhaba.php dunya
Merhaba, dunya
{% endhighlight %}


 * [PHP komut satırı arayüzü hakkında][php-cli]
 * [Windows'da PHP komut satırı arayüzü][php-cli-windows]

[phpinfo]: http://php.net/manual/tr/function.phpinfo.php
[cli-options]: http://www.php.net/manual/tr/features.commandline.options.php
[argc]: http://php.net/manual/tr/reserved.variables.argc.php
[argv]: http://php.net/manual/tr/reserved.variables.argv.php
[php-cli]: http://php.net/manual/tr/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/tr/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
