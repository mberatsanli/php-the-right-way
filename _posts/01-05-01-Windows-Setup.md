---
title: Windows Kurulumu
isChild: true
anchor: windows_kurulumu
---

## Windows Kurulumu {#windows_kurulumu_title}

[windows.php.net/download][php-downloads] adresinden binary indirebilirsiniz. 
PHP'yi çıkardıktan sonra PHP'yi heryerden çalıştırabilmek için bir sizin PHP 
klasörünüze (php.exe nerede ise) [PATH][windows-path] belirlemenizi önerir.

Öğrenmek ve yerel geliştirme için hali hazırda gelen PHP 5.4+ sürümü 
kullanabilirsiniz ve konfigürasyonu düşünmeniz gerekmez. Eğer hepsi bir arada 
bir kurulum (MySQL ve bir çok ekstra araç içeren) istiyorsanız, 
[Web Platform Installer][wpi], [XAMPP][xampp], [EasyPHP][easyphp], 
[OpenServer][openserver] ve [WAMP][wamp] size Windows platformunda hızlıca bir 
kurulum için yardımcı olacaktır. Bu araçlar production ortamına göre biraz 
farklılıklar içerecektir. Eğer uygulamanızı Linux ortamında yayınlarken Windows 
ortamında geliştirme yapıyorsanız biraz dikkat etmeniz gerekebilir.

Eğer uygulamanızı Windows ortamında yayınlamak istiyorsanız IIS7 size daha stabil
ve en iyi performansı sunacaktır. [Phpmanager][phpmanager] (IIS7 için bir arayüz 
eklentisi) size PHP konfigürasyonları ve yönetimi için kolaylık sağlayacaktır.
IIS7 FastCGI ile gelmektedir sadece PHP'yi handler olarak ayarlamanız yeterlidir. 
Ekstra kaynaklar için [Dedicated area on iis.net][php-iis] adresine bakabilirsiniz. 

Genellikle uygulamalar farklı ortamlarda çalıştırıldığı için uygulama 
yayınlandığında farklı hatalar ile karşılaşılabilir. Eğer Windows ortamında 
geliştirirken projenizi Linux (ya da Windows olmayan herhangi bir yerde) 
ortamında yayınlıyorsanız, [Virtual Machine](/#virtualization_title) kullanmayı 
düşünmelisiniz. 

Chris Tankersley'in Windows ortamında kullanılacak araçlar ile ilgili çok yararlı 
blog yazılarıbulunmaktadır. [PHP development using Windows][windows-tools].


[easyphp]: http://www.easyphp.org/
[phpmanager]: http://phpmanager.codeplex.com/
[openserver]: http://open-server.ru/
[wamp]: http://www.wampserver.com/en/
[php-downloads]: http://windows.php.net/download/
[php-iis]: http://php.iis.net/
[windows-path]: http://www.windows-commandline.com/set-path-command-line/
[windows-tools]: http://ctankersley.com/2015/07/01/developing-on-windows/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[xampp]: http://www.apachefriends.org/en/xampp.html