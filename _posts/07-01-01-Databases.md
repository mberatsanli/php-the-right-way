---
title: Veritabanları
anchor: veritabanlari
---

# Veritabanları {#veritabanlari_title}

Bilginin devamlılığı için bir çok zaman kodunuzda veritabanını kullanırsınız. 
Veritabanına bağlanmak için bir kaç yolunuz vardır. _PHP 5.1.0'e kadar_ PHP'de 
bulunan [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql] gibi veritabanı 
sürücülerini kullanabilirsiniz.

Eğer sadece bir veritabanı kullanıyorsanız yukarıda ki saydıklarımız çok iyi 
olacaktır. Ama MySQL yanında biraz da MSSQL kullanıyorsanız, ya da Oracle 
veritabanına bağlanmanız gerekiyorsa, aynı sürücüyü kullanma ihtimaliniz 
olmayacaktır. Her birisi için yeni bir API öğrenmeniz gerekecektir.

Diğer taraftan, mysql eklentisinin PHP'de aktif geliştirmesi duracaktır. 
PHP 5.4.0'dan bu yana resmi durumu "Uzun vadede önerilmemektedir" halindedir. 
Bunun anlamı bir kaç sürüm sonrasında silinecektir. PHP 5.6 ile gidebilir 
belki de. Eğer `mysql_connect()` ver `mysql_query()` kullanıyorsanız bu 
satırları tekrar yazmak durumunda kalacaksınız. Bu durumda en iyi seçenek 
mysql eklentisinin kullanımını belli bir geliştirme programı(takvimi) ile 
mysqli veya PDO ile değiştirmek olacaktır. _Eğer sıfırdan başlıyorsanız mysql 
eklentisi yerine [MySQLi extension][mysqli] veya PDO'yu kullanın._

* [PHP: MySQL için Bir API Seçmek](http://php.net/manual/tr/mysqlinfo.api.choosing.php)

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql