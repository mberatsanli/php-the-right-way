---
isChild: true
title: Soyutlama Katmanı
anchor: databases_abstraction_layers
---

## Soyutlama Katmanı {#databases_abstraction_layers_title}

Bir çok framework PDO üzerine kurulu kendine ait bir soyutlama katmanı içerir.
Bunlar genellikle PDO'nun bağlantı arayüzü için bir soyutlama oluşturmak yerine
tüm bir veritabanı için bir soyutlama getirirler, bu da farklı veritabanları
yerine bir veritabanı sistemini soyutlamalarına neden olur. Bu tabiki bu biraz 
yük katacaktır, ama eğer MySQL, PostgreSQL ve SQLite ile çalışabilecek taşınabilir 
bir uygulama insa etmek istiyorsak bu yük katlanılabilir bir yük olur.

Bazı soyutlama katmanları hali hazırda [PSR-0][psr0] veya [PSR-4][psr4] namespace 
standartlarına uygun inşa edilmiş ve siz uygulamanız için kullanabilirsiniz:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/Propel/

[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
