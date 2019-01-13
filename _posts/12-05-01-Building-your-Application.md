---
title: Uygulamanızı Build Etmek ve Deploy Etmek
isChild: true
anchor: uygulamanizi_build_etmek_ve_deploy_etmek
---

## Uygulamanızı Build Etmek ve Deploy Etmek {#uygulamanizi_build_etmek_ve_deploy_etmek_title}

Eğer dosyalarınızı güncellemeden önce kendinizi elle (manually) veritabanı şemasını güncellerken veya
testlerinizi elle (manually) çalıştırıyor buluyorsanız, iki kere düşünün!

Uygulamanızın yeni versiyonunu deploy etmek için elle (manually) yapmanız gerekecek her ekstra işlem ile büyük hatalar
yapma ihtimaliniz artacaktır. İster basit bir güncellemeyle uğraşırken, ister kapsamlı bir yapı kuruyorken ve hatta sürekli
entegrasyon stratejisiyle uğraşıyorken [build otomasyonu](http://en.wikipedia.org/wiki/Build_automation) arkadaşınızdır.

Otomatikleştirmek isteyeceğiniz bazı işlemler:

* Bağımlılık yönetimi
* Dosyalarınızın (assets) derleme, sıkıştırma (minification) işlemleri
* Test çalıştırma
* Dökümantasyon oluşturma
* Paketleme
* Deployment


### Otomasyon Araçlarını Hazırlamak {#otomasyon-aralarn-hazrlamak}

Otomasyon araçları, yazılım deployment'larının yaygın görevlerini idare eden betik koleksiyonu olarak tanımlanabilir.
Build araçları yazılımınızın bir parçası değildir, sadece yazılımınızla dışarıdan çalışır.

Bazıları PHP, bazıları farklı dillerde olmak üzere build otomasyonunda size yardımcı olabilecek bir çok açık kaynak
araç bulunmaktadır. Eğer belirli bir iş için daha uygunlarsa PHP ile yazılmış olmamaları sizi durdurmasın.
İşte bir kaç örnek:

[Phing](http://www.phing.info/) PHP dünyasında otomatik deployment a başlamak için en kolay yoldur. Phing ile basit
bir XML dosyasından paketleme, deployment veya test işlemlerini kontrol edebilirsiniz. Phing ([Apache Ant](http://ant.apache.org/)
tabanlıdır) bir web uygulamasını yüklemek ve ya güncellemek için genellikle ihtiyaç duyulabilecek geniş çaplı işlemleri
hizmetinize sunar ve PHP de yazılmış özel işlemler ile geliştirilebilir.

[Capistrano](https://github.com/capistrano/capistrano/wiki) her seviyede programcının kullanabileceği bir ya da birden fazla makinada uzaktan düzenli ve tekrar edebilecek şekilde konut çalıştırmasılmasını sağlayan bir sistemdir. Aslında Ruby on Rails uygulamaları için ayarlanmış olmasına rağmen **PHP uygulamaları** içinde başarıyla kullanılmaktadır. Etkili kullamıö için Ruby ve Rake bilgisi gereklidir.

Dave Gardner'ın yazısı [PHP Deployment with Capistrano](http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/) Capistrano kullanmak isteyen PHP programcıları için güzel bir başlangıç noktası olabilir.

[Chef](http://www.opscode.com/chef/) bir dağıtım çerçevesinden daha fazlasıdır. Yalnızca uygulamanızı dağıtmakla kalmayan, tüm sunucu ortamınızı veya sanal sunucu paaketlerinizi da oluşturabilen, çok güçlü bir Ruby tabanlı sistem entegrasyon çatısıdır.

PHP kullanlar için Chef hakkında bazı kaynaklar:

* [Three part blog series about deploying a LAMP application with Chef, Vagrant, and EC2](http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/)
* [Chef Cookbook which installs and configures PHP 5.3 and the PEAR package management system](https://github.com/opscode-cookbooks/php)

Daha fazla kaynak:

* [Automate your project with Apache Ant](http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/)
* [Maven](http://maven.apache.org/), a build framework based on Ant and [how to use it with PHP](http://www.php-maven.org/)

### Sürekli Entegrasyon (Continuous Integration)

> Sürekli Entegrasyon, bir ekibin üyelerinin sık sık işlerini entegre ettiği, genellikle her kişinin en az günlük olarak 
> bütünleştiği - günde birden fazla entegrasyona yol açan bir yazılım geliştirme pratiğidir. Birçok ekip bu yaklaşımın önemli > ölçüde entegrasyon sorunlarını azaltığını ve ekibin daha uyumlu bir yazılım geliştirmesini sağladığını tecrübe etti.

*-- Martin Fowler*

PHP için sürekli entegrasyon uygulamanın bir çok farklı yolu vardır. [Travis CI] (https://travis-ci.org/) küçük projeler için bile sürekli entegrasyonu uygulamayı kolaylaştırarar harika bir iş çıkardı. Travis CI  açık kaynak topluluğu için entegrasyon hizmeti sağlayan bir uygulamasıdır. GitHub ile entegredir ve birçok kişi için PHP dahil birinci sınıf destek sunar.

Daha fazla kaynak:

* [Continuous Integration with Jenkins](http://jenkins-ci.org/)
* [Continuous Integration with PHPCI](http://www.phptesting.org/)
* [Continuous Integration with Teamcity](http://www.jetbrains.com/teamcity/)
