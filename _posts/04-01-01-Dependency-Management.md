---
title: Bağımlılık (Dependency) Yönetimi
anchor: bagimlilik_dependency_yonetimi
---

# Bağımlılık (Dependency) Yönetimi {#bagimlilik_dependency_yonetimi_title}

Kullanabilmeniz için tonlarca PHP kütüphanesi, yapısı(frameworks) ve
bileşeni(component) bulunmaktadır. Projeniz bunlardan birkaçını kullanacaktır -
bu başlıkta projenizde kullandığınız kütüphanelere bağımlılığınızdan ve bunların
yönetilmesinden bahsedeceğiz. Yakın zamana kadar PHP'de bu projeniz içerisinde
barındırdığınız diğer kütüphane, çatı ya da bileşeni yönetmek için uygun bir yol
yoktu. Elle yönetilse bile, `autoloader` endişesi mevcuttu. Ancak şu anda bu
endişeye girmenize bir neden yok.

Şu sıralarda PHP için iki büyük paket yönetim sistemi bulunmaktadır. [Composer] ve 
ve [PEAR]. Composer şu anda PHP için en popüler paket yöneticisi ama PEAR'da uzun
zaman ana paket yöneticisiydi. Hiç kullanmasanız bile PEAR hakkında bir kaç 
referans bulabilirsiniz. 

[Composer]: #composer_ve_packagist
[PEAR]: #pear