---
title: İsim Uzayları (Namespaces)
isChild: true
anchor: isim_uzaylari_namespaces
---

## İsim Uzayları (Namespaces) {#isim_uzaylari_namespaces_title}

Daha öncede bahsedildiği üzere PHP topluluğu bir sürü geliştiriciden oluşmaktadır.
Bu nedenle bazı durumlarda bir kaç farklı kütüphane aynı isimde kullanılmış
olabilir. İki kütüphane aynı isim uzayında oldukları zaman çakışırlar ve bu da
fatal error gibi sorunlara veya exceptionlara neden olur.

_İsim uzayları_ bu sorunu çözmektedir. PHP referans kılavuzunda da açıklandığı
gibi, isim uzayları işletim sistemlerindeki klasörler ile karşılaştırılabilir.
Aynı isimdeki iki dosya nasıl farklı klasörlerde bulunabilirsa, aynı şekilde
aynı isimdeki iki sınıf farklı İsim Uzayları altında aynı isimde bulunabilmektedir.

Diğer geliştiricilerin geliştirdiği kütüphaneler ile çakışma korkusu yaşamadan
geliştirme yapabilmeniz için isim uzaylarını kullanmak sizin yararınıza olacaktır.

[PSR-0][psr0] İsim Uzayları konusuna değinmiştir ve birbiri ile uyumlu
(tak-ve-kullan kod) standart dosyalar, sınıflar ve isim uzayları düzeni kurmayı
amaçlamaktadır.

Aralık 2013'de PHP-FIG belkide ilerde [PSR-0][psr0] yerine geçecek olan yeni bir
autoloading standartı olan [PSR-4][psr4]'ü çıkardı. Şu anda ikiside
kullanılabilir durumda. PSR-4 PHP 5.3 gerektiriyor ve PHP 5.2 projeleri PSR-0
ile uygulanabiliyor. Eğer projenizde autoloader standartını kullanmak
istiyorsanız PSR-4'e bir gözatmanız gerekebilir.

* [İsim Uzayları hakkında][namespaces]
* [PSR-0 hakkında][psr0]
* [Read about PSR-4][psr4]

[namespaces]: http://php.net/manual/tr/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md