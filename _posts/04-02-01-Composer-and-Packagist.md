---
title: Composer ve Packagist
isChild: true
anchor: composer_ve_packagist
---

## Composer ve Packagist {#composer_ve_packagist_title}

Composer PHP için **muhteşem** bir bağımlılık yönetimi aracıdır. Bağımlılık
yönetimini bir kaç basit komut ile `composer.json` dosyası içerisinde yazıyoruz,
Composer projenizin ihtiyaçlarını otomatik olarak indiriyor ve kurulumunu
gerçekleştiriyor.

Composer ile uyumlu şimdiden projenizde kullanmanız için bir çok PHP kütüphanesi
bulunmakta. Bu paketler Composer'ın resmi deposu olan [Packagist][1]'da
listelenmetedir.

### Composer Nasıl Kurulur

Yerel (önerilmemesine rağmen içinde bulunduğunuzu dizin için) ya da genel
(örneğin: /usr/local/bin) kullanım için Composer'ı kurabilirsiniz. Yerel olarak
kurmak için aşağıdaki örneğe bakınız:

    curl -s https://getcomposer.org/installer | php

Bu komut `composer.phar` (bir PHP ikili arşivi) dosyası indirecek. Bu dosyayı
`php` kullanarak çalıştırabilir ve projenizin ihtiyaçlarını yönetebilirsiniz.
<strong>Not:</strong> Kodu çevirici bir kaynağa indirdi iseniz öncelikle çevrim
içi kod okuyunuz.

#### Windows Kurulumu

Windows kullanıcıları için [ComposerSetup][6] adında bir kurulum dosyası
bulunmaktadır. Bu kurulum dosyası `$PATH` dizinine yani global dizine kurulum
yapmaktadır. Kullanırken `composer` komutu ile direk çalışabilirsiniz.


### Composer Nasıl Kurulur (elle)

Composer'i elle kurmak biraz üst seviye bir tekniktir. Ancak geliştiricinin
etkileşimli kurulum yerine bu yöntemi kullanması için bir kaç sebep vardır.
Etkilşimli kurulum aşağıdaki PHP kurulumlarını denetler:

 - PHP'nin yeterli bir sürümü kontrol edilir
 - `.phar` dosyası düzgün çalıştırılır.
 - Dizin izinleri kontrol edilir.
 - Sorunlu uzantılar yüklenmez.
 - Belirli `php.ini` ayarları ayarlanır. 

Bu kurulum adımlarının hiçbiri olmadan yapılan elle kurulumda, sizin için bir
değerinin olup olmadığına karar vermelisiniz. Aşağıdaki komutlar ile elle
kuruluma başlayalım :

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

`$HOME/local/bin` dizini (ya da sizin seçeceğiniz bir dizin) sizin `$PATH`
değişkeninizin içerisinde olmalı. Bu `composer` komutunu kullanılabilir
yapacaktır.

Dökümantasyonda karşılaştığımız `php composer.phar install` komutunu aşağıdaki
gibi kullanabilirsiniz :

    composer install

Bu bölüm compeser'ın global olarak nasıl kurulduğunu varsayar.

### Bağımlıklıkları Nasıl Tanımlar ve Kurarız

Composer proje bağımlılığını `composer.json` isimli bir dosya ile sağlar.
Bu dosyayı elle ya da Composer vasıtasıyla güncelleyebilirsiniz.
`composer.phar require` komutu projenize bağımlılığı ekler ve daha önce
oluşturmamış iseniz `composer.json` dosyanızı oluşturur. Aşağıda bir örnek
yapalım ve projemize [Twig][2]'i ekleyelim.

	composer require twig/twig:~1.8

`composer init` komutu sana tam bir `composer.json` dosyası oluşturmak için
rehber olabilir. Herhangi bir şekilde `composer.json` dosyanızı oluşturduktan
sonra aşağıdaki komutu kullanarak Composer ile bağımlılıklarınızı `vendor/`
dizini altına indirebilir ve yükleyebilirsiniz.

    composer install

Daha sonra aşağıdaki satırları uygulamanızın ana PHP dosyasına ekleyiniz;
bunları nasıl yapacağınız size zaten Composer'daki projelerde bildirilecek.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Şimdi projenize eklediğiniz kütüphaneleri kullanabilirsiniz ve bunlar projenizde
talep dahilinde otomatik yükleniyor (autoloaded) olacak.

### Bağımlılıkları Güncellemek

Composer, `php composer.phar install` komutunu ilk çalıştırdığınızda
`composer.lock` adında bir dosya oluşturur ve bu dosyada her paketin o anki
versiyonunu tutar. Projenizi başka geliştiricilerle paylaştığınızda,
`composer.lock` dosyanızı da paylaşırsanız, geliştiriciler
`php composer.phar install` komutunu uyguladıklarında sizinle aynı versiyondaki
paketlere sahip olurlar. Bağımlılıkları (Dependencies) güncellemek için,
`php composer.phar update` komutunu çalıştırabilirsiniz.

Esnek bir versiyon gereksinimlerini tanımlamak için çok kullanışlı. Örneğin ~1.8
versiyon gereksinimi "1.8.0'dan daha yeni ve 2.0.x-dev'den daha eski herşeyi"
anlamına gelmektedir. Ayrıca `1.8.*` şekilde `*` da kullanabilirsiniz. Şimdi
Composer'a `php composer.phar update` komutunu verdiğinizde kısıtlamalarda
belirlediğiniz tanımlamalara göre bağımlılıklarınızı güncelleyecektir.

### Güncelleme Bildirimleri

Yeni versiyon geldiğinde bildirim almak için [VersionEye][3]'a kayıt
olabilirsiniz, bu web servisi `composer.json` dosyasındaki dosyaların Github
veya BitBucket üzerindeki hesaplarını sizin için kontrol eder ve yeni bir
release çıktığında size e-posta gönderir.

### Güvenlik konusundaki bağımlılıklarınız kontrol etmek

[Security Advisories Checker][4] komut satırından ve web arayüzü olarak
çalışabilen bir servistir. Sizin `composer.lock` dosyanızı algılar ve bir
güncellemeye ihtiyacınız olup olmadığını tespit eder.

* [Composer Hakkında Daha Fazlası][5]


[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://www.versioneye.com/
[4]: https://security.sensiolabs.org/
[5]: http://getcomposer.org/doc/00-intro.md
[6]: https://getcomposer.org/Composer-Setup.exe
