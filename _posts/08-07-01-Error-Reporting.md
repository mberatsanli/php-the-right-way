---
title: Hata Raporları
isChild: true
anchor: hata_raporlari
---

## Hata Raporları {#hata_raporlari_title}

Hata logları uygulamanızdaki sorunları bulmak için yararlı olabilir, ama aynı zamanda dış dünyaya uygulama yapısı
hakkında bilgi gösterebilir. Bu gibi sorunlarda uygulamanızı korumak için geliştirme ve canlı ortamın farklı
konfigüre edilmesi gerekebilir.

### Geliştirme

Geliştirme ortamında olası her hatayı görmek için aşağıdaki satırları `php.ini` dosyanıza ekleyebilirsiniz. 

    display_errors = On
    display_startup_errors = On
    error_reporting = -1
    log_errors = On

> `-1`, PHP'nin gelecekteki sürümlerinde yeni sabitler ve seviyeler eklense de olası her hatayı gösterecektir. `E_ALL` PHP 5.4'de aynı işi görecektir. - [php.net](http://php.net/manual/function.error-reporting.php)

`E_STRICT` hata seviyesi 5.3.0 sürümü ile başladı ve `E_ALL` ile aynı değildir, ama 5.4.0 sürümünde `E_ALL` ın bir parçası oldu. Bu yüzden `-1` ya da `E_ALL | E_STRICT` kullanmalısınız.

**PHP versionlarına göre olası tüm hata raporları**

* &lt; 5.3 `-1` or `E_ALL`
* &nbsp; 5.3 `-1` or `E_ALL | E_STRICT`
* &gt; 5.3 `-1` or `E_ALL`

### Canlı Ortam

Hataları canlı ortamda gizelemek için `php.ini` dosyasına aşağıdaki konfigürasyonları eklemelisiniz :

    display_errors = Off
    display_startup_errors = Off
    error_reporting = E_ALL
    log_errors = On

Canlı sistemde bu ayarlar ile, hatalar halen web server için saklanacaktır, ama kullanıcılara gösterilmeyecektir. Daha fazla bilgi
için aşağıdaki linkleri kullanabilirsiniz :

* [error_reporting](http://php.net/manual/errorfunc.configuration.php#ini.error-reporting)
* [display_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-errors)
* [display_startup_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-startup-errors)
* [log_errors](http://php.net/manual/errorfunc.configuration.php#ini.log-errors)
