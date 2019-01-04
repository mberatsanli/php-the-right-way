---
title: Bağımlılık Değiştirme
anchor: dependency_injection
---

## Bağımlılık Değiştirme {#dependency_injection_title}

[Wikipedia](http://en.wikipedia.org/wiki/Dependency_injection)'da:

> Bağımlılık değiştirme kodlanmış bağımlılıkların çalışma veya derlenme anında kaldırılabilmesine ve değiştirilebilmesine izin veren 
> bir yazılım tasarım desenidir.

Bu açıklama konuyu olduğundan biraz daha karmaşık gösteriyor olabilir.
Bağımlılık değiştirme bir bileşenin bütün bağımlıklarının yaratılma anında (constructor aracılığıyla),
metod kullanarak ya da özelliklere atama yaparak verilebilmesini sağlıyor. Böylece istenen anda bu bağımlıklar değiştirilebiliyor.
Konu bu kadar basit aslında.
