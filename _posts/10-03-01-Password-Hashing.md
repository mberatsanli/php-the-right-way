---
title: Şifre Karıştırma (hashing)
isChild: true
anchor: sifre_karistirma_hashing
---

## Şifre Karıştırma (hashing) {#sifre_karistirma_hashing_title}

Herkes bir şekilde, şifre ile korunan kullanıcı giriş ekranı bulunan bir uygulama yapar. Kullanıcı adı ve şifre veritabanında barındırılır ve giriş sırasında kimlik doğrulaması için kullanılır.

Bu aşamada en önemli şey şifre saklanmadan önce [_karıştırılmasıdır (hash)_][3]. Şifre karıştırıldıktan sonra geri döndürülemezdir ve tek yönlüdür. Sabit uzunluktadır ve geri döndürülemez. Bunun anlamı, özgün metine ulaşılamaz ancak karıştırılmış şifreler birbiri ile karşılaştırarak doğruluğu belirlenir. Eğer şifreler karıştırılmaz ise 3. kişilerçe bir şekilde veritabanına ulaşılırsa kişilerin bilgileri tehlikeye girer. Bazı kullanıcılar (maalesefki) diğer servisler ile aynı şifreleri kullanabilir. Bu yüzden, bu konuda ciddi güvenlik önlemi almak gerekir.


**`password_hash` ile Şifre Karıştırma**

PHP 5.5 ile `password_hash` fonksiyonu geldi. `password_hash` şu anda PHP'nin desteklediği güçlü bir algoritmaya sahip BCrypt kütüphanesini kullanıyor. Ama gerektiğinde daha fazla algoritmayı desteklemek için güncellenecektir. [`password_compat`][2], password_* fonksiyonlarının PHP 5.3.7'den üstünede destek verebilmek için oluşturulmuş bir kütüphanedir.

Aşağıda bir metni karıştıralım, sonra yeni bir metin ile karşılaştıralım. İki metin farklı olduğu için karşılaştırma sonucu yanlış olarak dönecektir.

{% highlight php %}
<?php
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    // Correct Password
} else {
    // Wrong password
}
{% endhighlight %}



* [`password_hash` hakkında] [1]
* [`password_compat` for PHP  >= 5.3.7 && < 5.5] [2]
* [Kriptografi açısından karıştırmayı öğrenin] [3]
* [PHP `password_hash` RFC] [4]

[1]: http://us2.php.net/manual/en/function.password-hash.php
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
