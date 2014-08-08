---
title: Veritabanları
anchor: veritabanlari
---

# Veritabanları {#veritabanlari_title}

Bilginin devamlılığı için bir çok zaman kodunuzda veritabanını kullanırsınız. Veritabanına bağlanmak için bir kaç yolunuz vardır. _PHP 5.1.0'e kadar_ PHP'de bulunan [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql] gibi veritabanı sürücülerini kullanabilirsiniz.

Eğer sadece bir veritabanı kullanıyorsanız yukarıda ki saydıklarımız çok iyi olacaktır. Ama MySQL yanında biraz da MSSQL kullanıyorsanız, ya da Oracle veritabanına bağlanmanız gerekiyorsa, aynı sürücüyü kullanma ihtimaliniz olmayacaktır. Her birisi için yeni bir API öğrenmeniz gerekecektir.

Diğer taraftan, mysql eklentisinin PHP'de aktif geliştirmesi duracaktır. PHP 5.4.0'dan bu yana resmi durumu "Uzun vadede önerilmemektedir" halindedir. Bunun anlamı bir kaç sürüm sonrasında silinecektir. PHP 5.6 ile gidebilir belki de. Eğer `mysql_connect()` ver `mysql_query()` kullanıyorsanız bu satırları tekrar yazmak durumunda kalacaksınız. Bu durumda en iyi seçenek mysql eklentisinin kullanımını belli bir geliştirme programı(takvimi) ile mysqli veya PDO ile değiştirmek olacaktır. _Eğer sıfırdan başlıyorsanız mysql eklentisi yerine [MySQLi extension][mysqli] veya PDO'yu kullanın._

* [PHP: MySQL için Bir API Seçmek](http://php.net/manual/tr/mysqlinfo.api.choosing.php)

## PDO

PDO bir veritabanı soyutlama kütüphanesidir. &mdash; PHP 5.1.0'den beri &mdash; PDO farklı veritabanları ile bağlantı için genel bir arayüz sunar.
PDO SQL sorugularınızı çevirmez ya da eksik kısımlarını tamamlamamaz; Sadece farklı veritabanlarına bağlanmak için aynı API'yi kullanmanızı sağlar.

SQL injection atakları için `PDO` sorgunuzdaki yabancı girdileri kolaylıkla güvenli hale getirmenizi sağlar. Bu PDO deyimleri ve bağlı(bound) parametreler ile mümkündür.

Bir sorguya sayısal bir ID değeri ekleyelim ve veritabanından bir kullanıcının kayıtlarını çekmeye çalışalım. Bunu yapmak için aşağıdaki yanlış bir yöntemdir:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- Saldırıya açık bir sorgu!
{% endhighlight %}

Yukarıdaki kötü bir koddur. Kolaylıkla farkedilebilir ve kullanılabilir bir koddur. Kötü niyetli bir kişi `id` parametresinde sayı
yerine `http://domain.com/?id=1%3BDELETE+FROM+users` gibi bir sorgu gönderebilir. Bu `$_GET['id']` değişkenine `1;DELETE FROM users` değerini
atayacaktır ve bütün kullanıcılarınızı silecektir. Siz bunu PDO bağlı parameter ile girdiyi temizlemelisiniz.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); // <-- PDO tarafından sterilize edildi
$stmt->execute();
{% endhighlight %}

Bu doğru bir koddur. Bu bir PDO deyiminde bağlı parametreleri kullanıyor ve yabancı girdilerden gelecek zararları engelliyor.

* [PDO hakkında][1]

Veritabanı bağlantısı kapatılmadığında kaynaklarınız bir süre sonra tükenecektir. Bunu PDO kullanarak önleyebilirsiniz.
PDO sayesinde bağlantı nesnesi silinirken bağlantı kapatılır ve bütün referansları silinir veya NULL'a eşitlenir.
Bunu yapmazsanız kalıcı bir bağlantı kullanmadığınız sürece kodunuz bittiğinde PHP tabiki bağlantıları otomatik
olarak kapatacaktır.

* [PDO bağlantıları hakkında][5]

## Sayutlama Katmanı (Abstraction Layers)

Birçok çatı PDO üzerine kurulmuş kendi soyutlanmış katmanını barındırmaktadır. Bunlar genellikle bir veritabanı
sisteminin özelliklerini barındırmaktadır. Bazı durumlarda yetersiz kalsada uygulamanızın taşınabilir olması için
bu gibi katmanlar güzel olabilir. (!)

Aşağıda uygulamalarınızda kullanabileceğiniz [PSR-0][psd0] veya [PSR-4][psd4] standardında bir kaç örnek bulunmaktadır:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/tr/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/tr/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/Propel/

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md






---
title: Databases
anchor: databases
---

# Databases {#databases_title}

Many times your PHP code will use a database to persist information. You have a few options to connect and interact
with your database. The recommended option **until PHP 5.1.0** was to use native drivers such as [mysqli], [pgsql], [mssql], etc.

Native drivers are great if you are only using _one_ database in your application, but if, for example, you are using
MySQL and a little bit of MSSQL, or you need to connect to an Oracle database, then you will not be able to use the same
drivers. You'll need to learn a brand new API for each database &mdash; and that can get silly.

## MySQL Extension

The [mysql] extension for PHP is no longer in active development, and is [officially deprecated as of PHP 5.5.0],
meaning that it will be removed within the next few releases. If you are using any functions that start with `mysql_*`
such as `mysql_connect()` and `mysql_query()` in your applications then these will simply not be available in later
versions of PHP. This means you will be faced with a rewrite at some point down the line, so the best option is to
replace mysql usage with [mysqli] or [PDO] in your applications within your own development schedules so you won't be
rushed later on.

**If you are starting from scratch then absolutely do not use the [mysql] extension: use the [MySQLi extension][mysqli], or use PDO.**

* [PHP: Choosing an API for MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)
* [PDO Tutorial for MySQL Developers](http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers)

## PDO Extension

PDO is a database connection abstraction library &mdash; built into PHP since 5.1.0 &mdash; that provides a common interface to talk with
many different databases. For example, you can use basically identical code to interface with MySQL or SQLite:

{% highlight php %}
// PDO + MySQL
$pdo = new PDO('mysql:host=example.com;dbname=database', 'user', 'password');
$statement = $pdo->query("SELECT some\_field FROM some\_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);

// PDO + SQLite
$pdo = new PDO('sqlite:/path/db/foo.sqlite');
$statement = $pdo->query("SELECT some\_field FROM some\_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);
{% endhighlight %}

PDO will not translate your SQL queries or emulate missing features; it is purely for connecting to multiple types
of database with the same API.

More importantly, `PDO` allows you to safely inject foreign input (e.g. IDs) into your SQL queries without worrying about database SQL injection attacks.
This is possible using PDO statements and bound parameters.

Let's assume a PHP script receives a numeric ID as a query parameter. This ID should be used to fetch a user record from a database. This is the `wrong`
way to do this:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

This is terrible code. You are inserting a raw query parameter into a SQL query. This will get you hacked in a
heartbeat, using a practice called [SQL Injection](http://wiki.hashphp.org/Validation). Just imagine if a hacker passes in an inventive `id` parameter by calling a URL like
`http://domain.com/?id=1%3BDELETE+FROM+users`.  This will set the `$_GET['id']` variable to `1;DELETE FROM users`
which will delete all of your users! Instead, you should sanitize the ID input using PDO bound parameters.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); // <-- Automatically sanitized by PDO
$stmt->execute();
{% endhighlight %}

This is correct code. It uses a bound parameter on a PDO statement. This escapes the foreign input ID before it is introduced to the
database preventing potential SQL injection attacks.

* [Learn about PDO]

You should also be aware that database connections use up resources and it was not unheard-of to have resources
exhausted if connections were not implicitly closed, however this was more common in other languages. Using PDO you
can implicitly close the connection by destroying the object by ensuring all remaining references to it are deleted,
i.e. set to NULL.  If you don't do this explicitly, PHP will automatically close the connection when your script ends -
unless of course you are using persistent connections.

* [Learn about PDO connections]

[Learn about PDO]: http://www.php.net/manual/en/book.pdo.php
[Learn about PDO connections]: http://php.net/manual/en/pdo.connections.php
[officially deprecated as of PHP 5.5.0]: http://php.net/manual/en/migration55.deprecated.php
[SQL Injection]: http://wiki.hashphp.org/Validation

[pdo]: http://php.net/pdo
[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql