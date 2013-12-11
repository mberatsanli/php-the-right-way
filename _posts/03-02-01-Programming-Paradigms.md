---
title: Programlama Yaklaşımları
isChild: true
---

## Programlama Yaklaşımları {#programlama_yaklasimlari_title}

PHP çeşitli programlama tekniklerini destekleyen esnek ve dinamik bir dildir. Özellikle PHP 5.0 ile katı bir nesne tabanlı model eklenmiş (2004), PHP 5.3 de "anonymous functions" ve "namespaces" (2009) desteği gelmiş ve PHP 5.4'de "traits" özelliği eklenerek yıllar içerisinde PHP, nesne tabanlı programlama konusunda kendisini önemli ölçüde geliştirmiştir.

### Nesne Tabanlı (Nesneye Dayalı) Programlama

PHP, nesne tabanlı programlamanın "class", "abstract class", "interfaces", "inheritance", "constructors", "cloning", 
"exception" özellikleri ve daha fazlasını içermektedir.

* [Nesne tabanlı programlama hakkında][oop]
* [Trait'ler hakkında][traits]

### Fonksiyonel Programlama

PHP, bir fonskiyonun bir değişkene atandığı "first-class" fonksiyonu desteklemektedir. Kullanıcı tanımlı ve dahili 
fonksiyonların ikiside bir değişkene referans edilebilir ve dinamik olarak çağırılabilir. Fonksiyon bir diğer fonksiyona parametre olarak gönderilebilir (bu özellik "High-order functions olarak bilinir.") veya bir fonksiyondan geri döndürülebilir.

Özyineleme (recursion), kendi kendini çağıran fonksiyon desteklenen bir özelliktir, ama bir çok PHP kodu iterasyona (iteration) odaklanmaktadır.

Yeni anonim fonksiyonlar (closures) PHP 5.3 ile gelmiştir. (2009)

PHP 5.4, closurelerin bir nesnenin scope'u içine bindlenmesi özelliğini getirmiş, ayrıca callable desteğini geliştirmiştir. Artık neredeyse callables ve closures neredeyse tüm durumlarda değişmeli olarak kullanılabilmektedir.

* [PHP'de Fonksiyonel Programlama hakkında](/php-the-right-way/pages/Functional-Programming.html) 
* ["Anonymous Functions" hakkında][anonymous-functions]
* ["Closure class" hakkında][closure-class]
* ["Closures RFC" hakkında][closures-rfc]
* ["Callables" hakkında][callables]
* [`call_user_func_array` ile dinamik olarak fonksiyon çağırmak hakkında][call-user-func-array]

### Meta Programlama

PHP, Reflection API ve Sihirli Yöntemler (Magic Methods) gibi bazı meta programlama mekanizmalarını destekler. PHP'de 
`__get()`, `__set()`, `__clone()`, `__toString()` ve `__invoke()` gibi Sihirli Yöntemler bulunmaktadır. Bunlar 
geliştiriciye sınıfların davranışlarını değiştirmelerine izin verirler. Ruby geliştiricileri genellikle 
PHP'de `method_missing`in (Çağırılan methodun olmaması durumu) eksik olduğunu söylerler. Ancak PHP bunu `__call()` ve `__callStatic()` Sihirli Yöntemlerini kullanarak desteklemektedir.

* [Sihirli yöntemler hakkında][magic-methods]
* [Reflection hakkında][reflection]

[namespaces]: http://php.net/manual/tr/language.namespaces.php
[overloading]: http://php.net/manual/tr/language.oop5.overloading.php
[oop]: http://www.php.net/manual/tr/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/tr/functions.anonymous.php
[closure-class]: http://php.net/manual/tr/class.closure.php
[callables]: http://php.net/manual/tr/language.types.callable.php
[magic-methods]: http://php.net/manual/tr/language.oop5.magic.php
[reflection]: http://www.php.net/manual/tr/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/tr/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
