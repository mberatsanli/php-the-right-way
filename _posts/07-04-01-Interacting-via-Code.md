---
isChild: true
title: Interacting with Databases
anchor: veritabani_ile_etkilesim
---

## Veritabanı ile etkilesim {#veritabani_ile_etkilesim_title}

Geliştiriciler PHP öğrenmeye başladıkları zaman, genellikle kendi yöntemleri ile
bunu yapmaktadırlar ve kodları şu şekilde görünür:

{% highlight php %}
<ul>
<?php
foreach ($db->query('SELECT * FROM table') as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>";
}
</ul>
{% endhighlight %}

Bu kötü bir yöntemdir, ana olarak test edilmesi, debug edilmesi ve okunması 
zordur ve eğer bir limit konulmaz ise bütün alanları dışarıya çıktı olarak 
verebilirsiniz. 

[OOP](#object-oriented-programming) ya da [functional programming](#functional-programming)
seçimlerine göre bunu yapmanın bir çok farklı yolları vardır. 

En temel adımı düşünün:

{% highlight php %}
<?php
function getAllFoos($db) {
    return $db->query('SELECT * FROM table');
}

foreach (getAllFoos($db) as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>"; // BAD!!
}
{% endhighlight %}

Bu iyi bir başlangıçtır. İki farklı kalemi iki arklı dosyaya koyun ve bazı 
temizlikler yapın. 

Bir sınıf oluşturun ve içerisine bazı methodlarınızı koyun ve artık bir 
"Model"iniz var. Basit bir `.php` dosyası oluşturun ve sunum logic'inizi bu 
dosyanın içerisine koyun ve bir "View" katmanı oluşturun. Neredeyse bir [MVC]
oluşturdunuz ki bu OOP mimarisi neredeyse bir çok 
[framework](#frameworks_title)'de mevcut.


**foo.php**

{% highlight php %}
<?php

$db = new PDO('mysql:host=localhost;dbname=testdb;charset=utf8', 'username', 'password');

// Make your model available
include 'models/FooModel.php';

// Create an instance
$fooModel = new FooModel($db);
// Get the list of Foos
$fooList = $fooModel->getAllFoos();

// Show the view
include 'views/foo-list.php';
{% endhighlight %}


**models/FooModel.php**

{% highlight php %}
<?php
class FooModel()
{
    protected $db;

    public function __construct(PDO $db)
    {
        $this->db = $db;
    }

    public function getAllFoos() {
        return $this->db->query('SELECT * FROM table');
    }
}
{% endhighlight %}

**views/foo-list.php**

{% highlight php %}
<?php foreach ($fooList as $row): ?>
    <?php echo $row['field1'] ?> - <?= $row['field1'] ?>
<?php endforeach ?>
{% endhighlight %}

This is essentially the same as what most modern frameworks are doing, all be it a little more manual. You might
not need to do all of that every time, but mixing together too much presentation logic and database interaction can be a real problem if you ever want to [unit-test](/#unit-testing) your application.

[PHPBridge] have a great resource called [Creating a Data Class] which covers a very similar topic, and is great
for developers just getting used to the concept of interacting with databases.

[MVC]: http://code.tutsplus.com/tutorials/mvc-for-noobs--net-10488
[PHPBridge]: http://phpbridge.org/
[Creating a Data Class]: http://phpbridge.org/intro-to-php/creating_a_data_class