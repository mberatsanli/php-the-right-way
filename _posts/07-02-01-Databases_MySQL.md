---
title: Veritabanları MySQL
anchor: veritabanlari-mysql
isChild: true
---

## Veritabanları MySQL {#veritabanlari_mysql_title}

PHP için [mysql] eklentisi oldukça eski ve yerini 2 yeni eklentiye bırakmış 
haldedir:

- [mysqli]
- [pdo]

Sadece geliştirmesi durmuş değil ayrıca [PHP 5.5.0 ile eskimiş olarak][mysql_deprecated]
işaretlenmiş durumundadır, ve **[PHP 7.0 ile birlikte silinecektir.][mysql_removed]**

Hangi modulü kullandığınızı görmek için `php.ini` dosyanıza bakmanız 
gerekmektedir. Diğer bir opsiyon'da seçtiğiniz editörde `mysql_*` diye arama 
yapmanız olabilir. Eğer `mysql_connect()` ve `mysql_query()` diye fonksiyonlar
ile karşılaşırsanız `mysql` kullanımda demektir. 

PHP 7.0 kullanmıyor olsanız bile, PHP 7.0 güncellemesi geldiğinde bu güncellemeyi
yapmak sizin için çok zor olabilir. Halen geliştirmekte olduğunuz kendi 
uygulamanız için en iyi seçenek sizin mysql kullanımınızı [mysqli] veya [PDO] 
ile değiştirmek olacaktır. 

**Eğer [mysql]'den [mysqli]'ye güncellemek istiyorsanız, size basitçe şunu 
önerebiliriz. Uygulamanız içerisinde `mysql_*`ı arayıp `mysqli_*` ile değiştirin.
Bu basitleştirilmiş çözüm mysqli ve [PDO][pdo]'nun sunduğu, parameter binding
gibi imkanları kaçırmamıza neden olabilir.**

* [PHP: Choosing an API for MySQL][mysql_api]
* [PDO Tutorial for MySQL Developers][pdo4mysql_devs]

[mysql]: http://php.net/mysql
[mysql_deprecated]: http://php.net/migration55.deprecated
[mysql_removed]: http://php.net/manual/en/migration70.removed-exts-sapis.php
[mysqli]: http://php.net/mysqli
[pdo]: http://php.net/pdo
[mysql_api]: http://php.net/mysqlinfo.api.choosing
[pdo4mysql_devs]: http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers