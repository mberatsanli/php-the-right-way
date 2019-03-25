---
isChild: true
title: Yalın(Düz) PHP Şablonları
anchor: yalin_php_sablonlari
---

## Yalın PHP Şablonları {#yalin_php_sablonlari_title}

Yalın PHP şablonları düz PHP kodlarını kullanan basit şablonlardır. Bu doğal bir seçimdir çünkü PHP'nin kendisi 
aslında bir şablon dilidir. Bunun anlamı siz PHP dilini rahatça HTML gibi dillerin arasında kullanabilirsiniz.
Bu PHP geliştiricilerinin yararınadır çünkü başka yeni bir dil öğrenmelerine gerek yoktur, bildikleri fonksiyonları kullanabilirler ve hatta kullandıkları
editörlerinin renklendirme seçeneklerini bile değiştirmeden kullanabilirler. Dahası, düz 
PHP şablonları tekrar derlenen şablon yöntemlerine göre derlenme aşaması olmadığından daha da hızlı çalışacaktır.

Her modern PHP framework yapısı bir çeşit şablon sistemi kullanmaktadır, bir çoğuda varsayılan olarak düz PHP 
kullanır. Framework'ler dışında [Plates](http://platesphp.com/) veya [Aura.View](https://github.com/auraphp/Aura.View)
gibi kütüphaneler kalıtım, tasarım modeli(layout) ve eklenti gibi modern özellikleri sağlayan düz PHP şablonları 
ile çalışabilmeyi sağlarlar. 

Örnek bir düz PHP şablonu ([Plates](http://platesphp.com/) kütüphanesi ile):

{% highlight php %}
<?php $this->insert('header', ['title' => 'User Profile']) ?>

<h1>User Profile</h1>
<p>Hello, <?=$this->escape($name)?></p>

<?php $this->insert('footer') ?>
{% endhighlight %}
