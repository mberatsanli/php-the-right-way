---
title: Register Globals
isChild: true
anchor: register_globals
---

## Register Globals {#register_globals_title}

**NOT:** PHP 5.4.0 itibariyle `register_globals` özelliği kaldırıldı ve bundan sonrada kullanılmayacak. Bu sadece
uygulamanızı güncellemeniz için bir uyarı olarak eklendi.

Etkinleştirildiğinde, `$_POST`, `$_GET` ve `$_REQUEST` gibi değişkenler uygulamanızın her yerinden erişilebilir
olacaktır. Bu verinin nerden geldiğini bilinemeyeceği için kolayca güvenlik açığına sebep olabiliyor.

Örneğin: `$_GET['foo']` değişkeni `$foo` olarak kullanılabilecek, daha önceden tanımlanmamış bir değişkeni etkin
kılacaktır. Eğer 5.4.0'dan daha küçük versiyonlarda PHP kullanıyorsanız, `register_globals` ayarını __off__ durumuna
getirin.


* [PHP manual'de Register_globals](http://www.php.net/manual/tr/security.globals.php)