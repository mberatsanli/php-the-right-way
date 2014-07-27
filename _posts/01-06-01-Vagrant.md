---
title: Vagrant (Sanal Sunucu)
isChild: true
anchor: vagrant
---

## Vagrant (Sanal Sunucu) {#vagrant_sanal_sunucu_title}

Geliştirme ortamı ile yayınlama ortamınız farklı ise projenizi yayınladığınızda farklı hatalar ile 
karşılaşabilirsiniz. Bir ekip ile çalışırken, herkesin farklı geliştirme ortamlarında çalışması ve tüm uygulamaların aynı sürümde veya güncel olabilmesi çok zorlaşıyor.

Eğer Windows bir makinede geliştirme yapıp Linux bir makinede yayınlıyorsanız veya bir ekip ile yazılım geliştiriyorsanız sanal bir makine kurmayı düşünmelisiniz. Bu ilk etapta zor gelebilir, ama [Vagrant][vagrant] kullanarak basit birkaç adım 
ile sanal bir makine kurabilirsiniz. Vargant üzerindeki temel box'lar elle ayarlanabilir, veya daha önceden kurulu 
bir vargant box'ınız varsa bunu yapmak için [Puppet][puppet] veya [Chef][chef] gibi "provisioning" yazılımları 
kullanabilirsiniz. 

Provisioning, birbirleri ile özdeş birden fazla box kurulurken ve gerektiğinde silinirken, 
tekrarlanacak olan bir çok kurulum karmaşasından korunmak için güzel bir yöntemdir. Bir box'ı silebilir ve 
hiçbir manuel yöntem kullanmadan tekrar oluşturabilirsiniz. Bu güzel ve sorunsuz bir kurulumu size sağlar.

Vargant, projenizi local sunucunuz ve oluşturduğunuz sanal makine ile paylaşmanız için paylaşımlı bir klasör oluşturur. Bunun yararı, siz local sunucunuzda kodlarınızı yazarken, projenizin sanal sunucunuzda çalışmasına imkan tanımasıdır. 

Bunu ufak bir örnekle açıklayalım. Farzedelim ki siz Windows tabanlı sunucunuzda kendi IDE veya Text editörünüzü kullanarak bir proje geliştiriyorsunuz. PHP, MySQL gibi araçlar ise linux sanal sunucunuzda kurulu. Proje klasörünüzü Vagrant'ın paylaşım klasörü olarak ayarlarsanız, windows ortamında geliştirmeye devam edip, çalıştırma işlemini sanal sunucu üzerinde yapabilirsiniz. O klasör iki yönlü ve senkron olarak çalışacaktır.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
