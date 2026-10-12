# MBR Bootloader
> MBR disk yapısını temel alan, Assembly ve C ile geliştirilmiş bootloader projesi.

## Açıklama
İşlemci, sıfırlandığında `sıfırlama vektörü`nden komut yürütmeye başlar. Ancak bilgisayar kapatıldığında RAM'deki veriler kaybolur ve bilgisayar tekrar açıldığında RAM'in içeriği belirsizdir. Bu nedenle işlemcinin başlangıç komutları RAM'de bulunamaz; güç kesildiğinde de verilerini koruyan kalıcı bir başlangıç koduna ihtiyaç vardır.

`BIOS`, anakart üzerindeki kalıcı bellekte bulunan bu başlangıç yazılımıdır. İşlemcinin sıfırlama vektörü BIOS kodunun bulunduğu adresi işaret eder ve işlemci buradan komut yürütmeye başlar. BIOS, gerekli donanımları başlattıktan sonra önyükleme yapılacak aygıtı belirler.

Geleneksel `MBR` önyüklemesinde BIOS, seçilen diskin ilk 512 byte'lık sektörünü RAM'e yükler. Sektörün son iki byte'ı `0x55` ve `0xAA` imzasını taşıyorsa BIOS, işlemciye bu sektördeki kodu yürütmesi için kontrolü devreder. Böylece MBR kodu çalışmaya başlar.

Bu mekanizma sayesinde işletim sisteminden bağımsız çalışabilen bir yazılım geliştirip derleyerek diskin ilk 512 byte'lık sektörüne yazabiliriz. BIOS bu sektörü yükleyip kodumuzu çalıştırdığında, herhangi bir işletim sistemine ihtiyaç duymadan kendi yazılımımızı başlatabiliriz. Bu proje, söz konusu önyükleme sürecini anlamak ve uygulamak amacıyla geliştirilmiştir.
