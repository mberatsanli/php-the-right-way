---
title: Kodlama Stili Rehberi
anchor: kodlama_stili_rehberi
---

# Kodlama Stili Rehberi {#kodlama_stili_rehberi_title}

PHP topluluğu geniş ve çeşitlidir. Sayısız kütüphane, framework ve bileşenlerden
oluşmaktadır. Bunlardan birkaçını seçip herhangi bir projede kullanmak PHP
geliştiricilerinin sıklıkla kullandığı bir yöntemdir. PHP kodlarında genel bir
stile uymak, farklı ve çeşitli kütüphaneleri sorunsuz kullanmak açısından son
derece önemlidir. PHP kodunun genel kod stiline olabildiğince uyması,
geliştiricilerin kolaylıkla farklı kütüphaneleri kullanabilmesine olanak tanır.

[Framework Interop Group][fig] (daha önce 'PHP Standartları Grubu' olarak
bilinen) çeşitli kodlama standartları önerilerinde bulunmuş ve [PSR-0][psr0],
[PSR-1][psr1] ve [PSR-2][psr2] gibi standartları kabul etmiştir. Kabul edilmiş
olan bu standartlar Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP,
Laravel ve Lithium gibi birçok büyük projelerde kullanılmaya başlanmış ve
desteklenmiştir. Bu standartları dilerseniz kendi projelerinizde
kullanabilirsiniz veya kendi kodlama stiliniz ve standartlarınız ile devam
edebilirsiniz.

Diğer geliştiricilerin yazdığınız kodu daha kolay okuyup anlamaları ve üzerinden
çalışabilmeleri için bu standartlardan bir veya daha fazlasına uygun kod
yazmalısınız. Bunlar PSR'nin standartları ya da PEAR veya Zend'in standartları
olabilir. Üçüncü partiler tarafından hazırlanmış kodlarla çalışırken birçok
bileşenden oluşan uygulamalar birbiri ile daha uyumlu olabilir.

* [PSR-0 hakkında][psr0]
* [PSR-1 hakkında][psr1]
* [PSR-2 hakkında][psr2]
* [Read about PSR-4][psr4]
* ["PEAR Coding Standards" hakkında][pear-cs]
* ["Zend Coding Standards" hakkında][zend-cs]
* [Read about Symfony Coding Standards][symfony-cs]

[PHP_CodeSniffer][phpcs] eklentisini kullanarak yazdığınız kodların bu
standartlardan herhangi birine uyumlu olup olmadığını kontrol edebilirsiniz.
[Sublime Text 2][st-cs] gibi bir editörde ise bu konuda gerçek zamanlı
geribildirimler alabilirsiniz. 


[PHP_CodeSniffer][phpcs] aracını bu standartlara karşı uygun olup olmadığını
kotrol etmek için kullanabilirsiniz veya [Sublime Text 2-3][st-cs] gibi bir 
editör'e eklenti olarak kurabilir ve neredeyse gerçek zamanlı geribildirimler 
alabilirsiniz.

Kod düzeninizi aşağıdaki bir kaç aracı kullanarak kolayce düzeltebilirsiniz. 
Bunlardan birisi iyi test edilmiş bir kod bulunan 
[PHP Coding Standards Fixer][phpcsfixer]'dir. Diğer bir seçenek ise [sublime-phpfmt][sublime-phpfmt]
olarak bir Sublime Text ektentisi olan [php.tools][phptools]'dur. 

Ayrıca `phpcs`yi komut satırından da çalıştırabilirsiniz:

    phpcs -sw --standard=PSR2 file.php

Size hataları ve nasıl düzelteceğinize dair açıklamaları gösterecektir. Ayrıca 
bu komutu git hook olarak da kaydedebilirsiniz. Bu kod deponuza standart olmayan
hiç bir kodun girmemesinde yardımcı olacaktır. 

İngilizce, kod içinde bulunan değişken, sabit, fonksiyon, yordam gibi semboller
ve yapılara ait isimlendirmelerde tercih edilmektedir. Yorumlar için ise şu
anda ve gelecekte kodlar üzerinde uğraşacak kişilerin anlayabileceği bir dil
tercih edilmelidir. Örneğin, proje ekibinde Türkçe bilmeyen bir eleman varsa,
yorum satırlarını Türkçe yerine İngilizce yazmanız daha doğru olacaktır.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
[phptools]: https://github.com/phpfmt/php.tools
[sublime-phpfmt]: https://github.com/phpfmt/sublime-phpfmt