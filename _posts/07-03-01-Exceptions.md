---
title: İstisnalar (Exceptions)
isChild: true
anchor: istisnalar_exceptions
---

## İstisnalar (Exceptions) {#istisnalar_exceptions_title}

İstisnalar bir çok programlama dilinin en popüler kısmıdır, ama genellikle PHP geliştiriciler için gözden kaçmıştır.
Ruby gibi dillerde İstisnalar ağır derecede vardır, HTTP isteği hata vermesi, veya veritabanı sorgusu yanlış olduğunda, veya
resim bulunamadığında bile Ruby ekrana bir istisna tetikleyecektir.

PHP'nin kendisi bu konuda oldukça gevşektir, ve `file_get_contents()` çağrısı genellikle bir `FALSE` dönder ve bir uyarı gösterir.
Codeigniter gibi bir çok eski PHP çatılarında sadece `false` dönecektir, hata mesajlarına ekleyecektir ve hatayı
`$this->upload->get_error()` bu gibi yöntemleri kullanarak görebilirsiniz. Buradaki problem, hatanın son derece bariz olması yerine
hatanın yerine bakmak ve hangi metotta olduğunu bulmak için dökümanlarına bakmak zorunda olmaktadır.

Diğer bir problem, sınıflar otomatik olarak bir hata fırlattıklarında ve işlemden çıkıldığındadır.


When you do this you stop another developer from being able to dynamically handle that error. Exceptions should be thrown to make a developer aware
of an error, then they can choose how to handle this. E.g:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
finally
{
    // Use this to let user know email was sent
}

{% endhighlight %}

### SPL İstisnalar

Genel `Exception` sınıfı geliştiriciler için çok az ayıklama kaynağı sağlayabilir. Ancak, buna çare olarak, varsayılan `Exception`
sınıfını kapsayan özelliştirilmiş bir `Exception` sınıfı oluşturabilirsiniz:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Birden fazla `catch` bloğu ile farklı istisnalar yakalayabilirsiniz. Bu bir sürü özel istisna yaratılmasına sebep olabilir,
Bunlardan bazılarını [SPL extension][splext]'ın sunduğu SPL istisnalarını kullanarak önleyebilirsiniz.

Eğer `__call()` sihirli metodunu kullanıyorsanız ve geçersiz bir metot talep edildiğinde standart istisnalar yerine ki onlar
belirsizler, sadece bunun için özel bir istisna oluşturabilirsiniz, `throw new BadFunctionCallException;` bu şekilde hatayı
elle oluşturabilirsiniz.


* [Read about Exceptions][exceptions]
* [Read about SPL Exceptions][splexe]
* [Nesting Exceptions In PHP][nesting-exceptions-in-php]
* [Exception Best Practices in PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/en/language.exceptions.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
