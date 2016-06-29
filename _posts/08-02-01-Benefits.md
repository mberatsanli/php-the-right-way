---
isChild: true
title: Templating (Şablon)
anchor: templating(Şablon)_yararlari
---

## Yararları {#templating_sablon_yararlari_title}

Sunum katmanındaki mantığı uygulamanın geri kalanından ayırmak template(şablon) mantığının kullanımındaki ana yarardır. 
Template yani şablonlar formatlanmış içeriği göstermekle görevlidirler. Verinin erişimi ya da verinin sürekliliği
ya da daha karmaşık görevler için değillerdir. Geliştiricilerin sunucu tarafındaki kodla (controller, model) 
ilgilendiği ve tasarımcıların kullanıcı tarafındaki kodla (markup) ilgilendiği bir takım çalışması içerisinde daha 
okunalı ve temiz kod yazmayı sağlar. 

Şablonlar sunum katmanındaki kodların organizasyonunuda geliştirir. Şablonlar genellikle "views" klasörü altında
olurlar ve her biri bir tekil dosya içerisinde bulunur. Bu taklaşım büyük kod parçalarının daha küçük hallere 
bölünmesiyle birlikte tekrar kullanılabilirliğini de artırır. Örneğin, sizin sitenizde bir başlık ve birde alt başlık 
kısmı varsa, bu şablonlar her bir sayfanın başına ve sonuna eklenebilir.

Sonuç olarak, kullandığınız kütüphanelere bağlı olarak, şablonlar kullanıcı tarafından oluşturulan içeriklerde 
bazı kısımlarda işlemler(escaping) yaparak daha güvenli olmasını sağlar. Bazı kütüphaneler daha kapalı kutu 
olur ve tasarımcılar sadece izin verilen değişkenlere ve methodlara erişebilirler. 
