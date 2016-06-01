---
title: Mac (OSX) Kurulumu
isChild: true
anchor: mac_osx_kurulumu
---

## Mac (OSX) Kurulumu  {#mac_osx_kurulumu_title}

OSX ile birlikte PHP zaten kurulu halde gelmektedir fakat kurulu PHP sürümü 
güncel ve kararlı sürümden biraz eski olabilir. Örneğin, Lion PHP 5.3.6 
versiyonu ile, Mountain Lion ise 5.3.10 versiyonu ile, Mavericks 5.4.17 ile, 
Yosemite 5.5.9 ile ve El Capitan 5.5.29 ile gelmektedir. Hali hazırda PHP 7.0
dahili olarak gelmemektedir. 

PHP'yi OS X'de kurmak için bir kaç yöntem bulunmaktadır. 


### Homebrew ile Kurulum

[Homebrew] OS X için güçlü bir paket yöneticisidir ve PHP ve eklentilerinin
kurulumunu kolayca yapabilmenizi sağlar. [Homebrew PHP] deposu, PHP kurulumuna 
izin verecek, PHP ile ilgili "formulae"leri barındıran bir depodur. 

Bu noktada, siz `php53`, `php54`, `php55`, `php56` veya `php70` sürümlerini 
`brew install` komutu ile rahatça kurablirsiniz ve bu sürümler arasında `PATH`
değişkenini değiştirerek dolaşabilirsiniz. Alternatif olarak [brew-php-switcher][brew-php-switcher]
sizin için bunu otomatik olarak yapacaktır. 

### Macports ile Kurulum

[MacPorts] projesi OS X üzerinde komut satırından çalışan, X11 üzerinde çalışan 
veya Aqua tabanlı açık kaynak yazılımları bile compile edip, kurup 
güncelleyebileceğiniz kolay kurulum için tasarlanmış bir açık kaynak projesidir. 

MacPorts pre-compiled binary dosyalar sunmaktadır. Bu yüzden kaynak kodundan 
bütün gereksinimlerle birlikte tekrar kurmanız gerekmez, Bu sizin hayatınızı 
kolaylaştırır ve ekstra kurulumlar ile uğraştırmaz. 

Bu noktada, `php54`, `php55`, `php56` veya `php70` sürümlerini `port install` 
komutu ile kolayca kurabilirsiniz. 

    sudo port install php56
    sudo port install php70

Ve kolayca `select` komutu ile kullanmak istediğiniz sürümü aktif edebilirsiniz.

    sudo port select --set php php70


### phpbrew ile Kurulum

[phpbrew] çoklu PHP sürümlerini yönetmek için bir araçtır. Farklı versiyonlara 
ihtiyaç duyduğunuz uygulama/projeler için gerçekten çok yararlı olabilir ve 
siz sanal makine kullanmazsınız. 

### Liip's binary installer ile Kurulum

[php-osx.liip.ch] 5.3 ile 7.0 sürümleri arasında her sürüm için bir satırlık 
kurulum scriptleri sunan popüler bir seçenektir. Apple tarafından kurulan PHP'nin 
üzerine yazmak ama her bir sürüm için farklı klasörler oluşturur (/usr/local/php5).

### Kaynaktan Kurmak

Diğer bir seçenek ise [kaynak kodunu compile][mac-compile] ederek kurmakdır. 
Bu durumda [Xcode][xcode-gcc-substitution]'un veya ["Command Line Tools for XCode"] 
kurulmuş olması gerekmektedir.

### Hepsi Bir Arada Kurulum

Yukarıdaki listelenenler PHP'nin kendisinin kurulumuyde ve Apache, Nginx veya 
SQL Server gibi şeyleri desteklemiyordu. [MAMP][mamp-downloads] ve [XAMPP][xampp]
gibi "Hepsi Bir Arada" çözümünde ekstra olarak bir kaç yazılım daha kurulmaktadır. 
Ancak kolay kurulum desteği ile gelmektedir. 


[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
