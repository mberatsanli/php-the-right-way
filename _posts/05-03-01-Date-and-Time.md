---
title: Tarih ve Saat
isChild: true
anchor: tarih_ve_saat
---

## Tarih ve Saat {#tarih_ve_saat_title}

PHP'de `DateTime` isimli bir sınıf bulunmaktadır ve tarih zamanla ilgili okuma,
yazma, karşılaştırma veya hesaplama gibi işlerinizde yardımcı olmaktadır. PHP
içerisinde tarih ve saat ile ilgili bir çok fonksiyon bulunmaktadır, ama
`DateTime` sınıfı genel kullanım için nesne tabanlı güzel bir arayüz sunmaktadır.
DateTime sınıfı zaman dilimlerini(time zones) işleyebilir ancak bu durumda kısa
girişin dışına çıkmış oluruz.

İlk olarak `createFromFormat()` fonksiyonu ile işlenmemiş bir tarih saat
metnini(string) çevirelim ve onu ekranda gösterelim. `format()` fonksiyonu
DateTime nesnesini tekrar metne çevirmek için kullanılır.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Başlangıç Tarihi: ' . $start->format('Y-m-d') . "\n";
{% endhighlight %}

DateTime ile hesaplamalar DateInterval sınıfı ile mümkünüdür. DateTime sınıfının
`add()` ve `sub()` fonksiyonları DateInterval sınıfını parametre olarak alır.
DateInterval kullanmak yerine, tarih ve saat işlemleriyle kendinizi yormayın.
Gün ışığından yararlanma ve zaman dilimi değişiklikleri zaman hesaplamalarında
umduğumuzdan daha karışık sorunlar ortaya çıkarır. Zaman farkını hesaplamak için
`diff()` fonksiyonunu kullanabilirsiniz. Bu fonksiyon yeni bir DateInterval 
nesnesi döndürecektir.

{% highlight php %}
<?php
// $start'ın bir kopyasını oluşturuyoruz ce bir ay 6 gün ekliyoruz
$end = clone $start;
$end->add(new DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Fark: ' . $diff->format('%m ay, %d gün (toplam: %a days)') . "\n";
// Fark: 1 ay, 6 gün (toplam: 37 days)
{% endhighlight %}

DateTime nesnesi ile standart karşılaştırma yöntemlerini kullanabilirsiniz:

{% highlight php %}
<?php
if ($start < $end) {
    echo "Başlangıç bitişten önce!\n";
}
{% endhighlight %}

Son bir örnekte DatePeriod sınıfını gösterelim. Yenilenen zaman dilimleri için 
kullanılır. İki DateTime nesnesini, başlangıç(start) ve bitiş(end), ve zaman 
aralığını parametre olarak alır. Sonunda bu aralıktaki kriterlere uyan bütün 
tarihleri geri döner.

{% highlight php %}
<?php
// $start ve $end arasındaki bütün perşembeleri yazdırıyoruz
$periodInterval = DateInterval::createFromDateString('first thursday');
$periodIterator = new DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // her bir periyot için çıktı
    echo $date->format('Y-m-d') . ' ';
}
{% endhighlight %}

* [DateTime hakkında][datetime]
* [Tarih Formatlama hakkında][dateformat] (kabul edilen tarih formatı seçenekleri)

[datetime]: http://php.net/book.datetime
[dateformat]: http://php.net/function.date
