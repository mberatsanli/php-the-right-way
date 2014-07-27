---
title: Bağımlılık (Dependency) Yönetimi
anchor: bagimlilik_dependency_yonetimi
---

# Bağımlılık (Dependency) Yönetimi {#bagimlilik_dependency_yonetimi_title}

Kullanabilmeniz için tonlarca PHP kütüphanesi, yapısı(frameworks) ve bileşeni(component) bulunmaktadır. Projeniz bunlardan birkaçını kullanacaktır - bu başlıkta projenizde kullandığınız kütüphanelere bağımlılığınızdan ve bunların yönetilmesinden bahsedeceğiz. Yakın zamana kadar PHP'de bu projeniz içerisinde barındırdığınız diğer kütüphane, çatı ya da bileşeni yönetmek için uygun bir yol yoktu. Elle yönetilse bile, `autoloader` endişesi mevcuttu. Ancak şu anda bu endişeye girmenize bir neden yok.

Şu sıralarda PHP için iki büyük paket yönetim sistemi bulunmaktadır. `Composer` ve `PEAR`. Hanigis sizin için doğru? Cevap ikisi de.  

 * **Composer** bir proje için bağımlılıkları yönetmek için kullanılır.
 * **PEAR** PHP'nin bütün sisteminin bağımlılığı için kullanılır.

Genelde, `Composer` paketleri projeler içerisinde uygun iken, bir PEAR paketi bütün PHP projelerinizde kullanılabilir. PEAR
ilk bakışta kolay bir yaklaşım gibi gelebilir, project-By-Project yaklaşımın bağımlılıklarınız için avantajları vardır.
