---
isChild: true
title: Derlenen Şablonlar (Compiled Template)
anchor: derlenmis_sablonlar_template
---

## Derlenmiş Şablonlar(Template) {#derlenmis_sablonlar_template}

PHP nesne odaklı bir dil olarak olgunlaşırken, bir şablon dili gibi [gelişmiş değil](http://fabien.potencier.org/article/34/templating-engines-in-php).
[Twig](http://twig.sensiolabs.org/) veya [Smarty](http://www.smarty.net/) gibi derlenmiş şablonlar, 
bu boşluğu yeni bir söz dizimi ile dolduruyorlar. Otomatik sızıntıları önleme, basit kontrol yapıları
ve kalıtım özelliği ile derlenebilen şablonlar kolay yazmak için, temiz okunabilir ve daha güvenli 
kullanım için tasarlanmıştır. Derlenen şablonlar hatta farklı diller arasında paylaşılabilirler bile. 
Buna [Mustache](http://mustache.github.io/) güzel bir örnektir. Şablonlar derlenirken performans
olarak biraz sıkıntı yaratabilir ancak bu derlenmiş şablon önbelleğe alındığında çok çok küçük 
bir performans kaybı yaratacaktır. 

Örnek bir derlenmiş şablon ([Twig](http://twig.sensiolabs.org/) kütüphanesi ile): 

{% highlight text %}
{% raw %}
{% include 'header.html' with {'title': 'User Profile'} %}

<h1>User Profile</h1>
<p>Hello, {{ name }}</p>

{% include 'footer.html' %}
{% endraw %}
{% endhighlight %}
