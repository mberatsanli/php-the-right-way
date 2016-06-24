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

[PSR-4][psr4] İsim Uzayları konusuna değinmiştir ve birbiri ile uyumlu
(tak-ve-kullan kod) standart dosyalar, sınıflar ve isim uzayları düzeni kurmayı
amaçlamaktadır.



Ekim 2014'de daha önceki autoloader standardı olan [PSR-0][psr0]'ı eski olarak 
işaretledi, ve [PSR-4][psr4] bunun yerine yayınlandı. Şu anda ikiside kullanılabilir
ve PSR-0 silinmiş değil. PSR-4 PHP 5.3 ve üstü sürümlerini gerektirdiği için daha
düşük sürümleri kullanan bir çok PHP projesi halen PSR-0'ı uygulamaktadır veya 
kullanmaktadır. _Luckily those PHP 5.2-only projects are starting to up their 
version requirements, meaning PSR-0 is being used less and less._

Eğer yeni bir proje ya da paket için autoloader standardını kullanmak 
istiyorsanız PSR-4'e bir gözatmak isteyebilirsiniz.

* [İsim Uzayları hakkında][namespaces]
* [PSR-0 hakkında][psr0]
* [Read about PSR-4][psr4]

[namespaces]: http://php.net/manual/tr/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md




