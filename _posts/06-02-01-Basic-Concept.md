---
title: Temel Kavramlar
isChild: true
anchor: temel_kavramlar
---

## Temel Kavramlar {#temel_kavramlar_title}

Basit bir örnek ile kavramları size anlatmaya çalışalım.

Veritabanı ile iletişim kuran bir adapter gerektiren bir `Database` sınıfı olsun.
Bu `adapter`'in bir objesini constructor'da oluşturalım. Bu testi zorlaştırır.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

This code can be refactored to use Dependency Injection and therefore loosen the dependency.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Now we are giving the `Database` class its dependency rather than it creating it itself. We could even create a method
that would accept an argument of the dependency and set it that way, or if the `$adapter` property was `public` we could
set it directly.