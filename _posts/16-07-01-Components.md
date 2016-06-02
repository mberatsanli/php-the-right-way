---
title: Bileşenler (Components)
isChild: true
anchor: bilesenler_components
---

## Bileşenler (Components) {#bilesenler_components_title}

Daha öncede değinildiği üzere "Bileşenler" paylaşımlı kod, yayınlama ve oluşturma aşamalarında genel bir amaç için diğer bir yaklaşımdır.
Bir çok bileşen deposu vardır. Bunlardan ana iki tanesi:

* [Packagist](/php-the-right-way/#composer_and_packagist)
* [PEAR](/php-the-right-way/#pear)

İki araçta yükleme ve yükseltme işlemlerinde yardımcı olmak için komut satırında çalışan bir arayüze sahiptir. Daha fazla bilgi için
[Bağımlılık Yönetimi] bölümüne bakabilirsiniz.

There are also component-based frameworks and component-vendors that offer no framework at all. These projects provide
another source of packages which ideally have little to no dependencies on other packages, or specific frameworks.

For example, you can use the [FuelPHP Validation package], without needing to use the FuelPHP framework
itself.

  [Bağımlılık Yönetimi]: /php-the-right-way/#bagimlilik_dependency_yonetimi
  [FuelPHP Validation package]: https://github.com/fuelphp/validation

* [Aura](http://auraphp.github.com/)
* [FuelPHP](https://github.com/fuelphp)
* [Hoa Project](https://github.com/hoaproject)
* [Orno](https://github.com/orno)
* [Symfony Components](http://symfony.com/doc/current/components/index.html)
* [The League of Extraordinary Packages](http://thephpleague.com/)
* Laravel's Illuminate Components
    * [Eloquent ORM](https://github.com/illuminate/database)
    * [Queue](https://github.com/illuminate/queue)

_Laravel's [Illuminate components](https://github.com/illuminate) will become better decoupled from the Laravel framework.
For now, only the components best decoupled from the Laravel framework are listed above._