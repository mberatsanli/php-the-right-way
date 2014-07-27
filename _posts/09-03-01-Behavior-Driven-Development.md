---
title: Davranış Odaklı Geliştirme
isChild: true
anchor: davranis_odakli_gelistirme
---

## Davranış Odaklı Geliştirme (Behaviour Driven Development) {#davranis_odakli_gelistirme_title}

İki tür Davranış Odaklı Geliştirme (Behavior-Driven Development - BDD) vardır: SpecBDD ve Story BDD. SpecBDD teknik
davranışa veya koda odaklanır. StoryBDD iş veya özellik davranışlarına ve etkileşimlerine odaklanır. PHP her iki
tür içinde çatıya sahiptir.

StoryBDD ile, uygulamanızın davranışlarını açıklamak için okunabilir hikayeler yazabilirsiniz. Bu hikayeler
uygulamanıza karşı test olarak kullanılabilir. PHP uygulamanızda StoryBDD için Behat adındaki çatı kullanabilirsiniz.
Bu çatı Ruby için yazılmış [Cucumber](http://cukes.info/) çatısından ilham alınarak oluşturulmuş.
Hikayeleri oluşturmak için Gherkin DSL dili kullanılır.

SpecBDD ile kodunuzun gerçekteki davranışlarınızı açıklayan açıklamalar yazabilirsiniz. Fonksiyon ya da metodu
test etmek yerine, bu fonksiyon ya da metodun nasıl davrandığını açıklayabilirsiniz. PHP PHPSpec çatısını
bu amaç için sunmaktadır. Bu çatı için Ruby için yazılmış [RSpec project](http://rspec.info/) projesinden
ilham alınmıştır.

### BDD Links

* [Behat](http://behat.org/), the StoryBDD framework for PHP, inspired by Ruby's [Cucumber](http://cukes.info/) project;
* [PHPSpec](http://www.phpspec.net/), the SpecBDD framework for PHP, inspired by Ruby's [RSpec](http://rspec.info/) project;
* [Codeception](http://www.codeception.com) is a full-stack testing framework that uses BDD principles.
