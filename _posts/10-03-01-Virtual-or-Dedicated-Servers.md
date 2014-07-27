---
title: Sanal veya Özel Sunucular
isChild: true
anchor: sanal_veya_ozel_sunucular
---

## Sanal veya Özel Sunucular (Virtual or Dedicated Servers) {#sanal_veya_ozel_sunucular_title}

Sistem yönetimini seviyorsanız veya öğrenmek istiyorsanız, virtual veya dedicated sunucular uygulamanızın yayınlamanız için tam bir kontrol sağlarlar.

### nginx ve PHP-FPM

PHP, PHP'nin dahili FastCGI Process Manager (FPM)'ı üzerinden, [nginx](http://nginx.org) ile hafif ve yüksek performanslı web sunucusu olarak güzel eşleşiyor. Apache'ye göre daha az bellek kullnırken daha fazla isteği cevaplıyabiliyor. Bu özellikle sanal sunucular üzerinde, ki bellek her zaman bir ihtiyaç, çok önem kazanıyor.

* [nginx Hakkında](http://nginx.org)
* [PHP-FPM Hakkında](http://php.net/manual/en/install.fpm.php)
* [nginx ve PHP-FPM Güvenli Kurulumu Hakkında](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

### Apache ve PHP

PHP ve Apache'nin uzun bir geçmişi var. Apache çok geniş konfigürasyona ve işlevselliğini artırmak için çokça [modüle](http://httpd.apache.org/docs/2.4/mod/) sahip. PHP çatıları ve Wordpress gibi açık kaynak kodlu uygulamaların kolay kurulumu için en çok seçilen ortak sunucu uygulamasıdır. Ne yazık ki, nginx ile karşılaştırıldığında daha fazla kaynak kullanmaktadır ve aynı zamandaki kaldırabileceği ziyaretçi sayısı daha azdır.

Apache PHP'yi çalıştırmak için bir kaç konfigürasyona sahip. En yaygın ve en kolay kurulum, mod_php5 ile [prefork MPM](http://httpd.apache.org/docs/2.4/mod/prefork.html)'dir. Bellek kullanımı verimli olmasada kullanımı ve çalışması en kolay olandır. Sunucu tarafı ile çok fazla uğraşmak istemiyorsanız sizin için uygun bir seçimdir. _Eğer mod\_php5 kullanacaksanız, prefork MPM kullanmalısınız._

Alternatif olarak, Apache dışında daha fazla performans ve kararlılık istiyorsanız, nginx'le aynı FPM sisteminden yararlanabilirsiniz ve mod_fastcgi veya mod_fcgid ile [worker MPM](http://httpd.apache.org/docs/2.4/mod/worker.html) veya [event MPM](http://httpd.apache.org/docs/2.4/mod/event.html) modüllerini çalıştırabilirsiniz. Bu konfigürasyon belleği daha verimli kullanacak ve daha hızlı olacak ama kurulum aşaması daha zor olacaktır.

* [Apache Hakkında](http://httpd.apache.org/)
* [Multi-Processing Modulü Hakkında](http://httpd.apache.org/docs/2.4/mod/mpm_common.html)
* [mod_fastcgi Hakkında](http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html)
* [mod_fcgid Hakkında](http://httpd.apache.org/mod_fcgid/)
