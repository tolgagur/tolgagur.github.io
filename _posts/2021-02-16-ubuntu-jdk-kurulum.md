---
title: Ubuntu 20.04'e JDK Kurulumu
updated: 2021-02-16 23:37
---

Oracle java jdk sayfasından işletim sistemi için uygun olan sürümü indimemiz gerekli.[ Java jdk indirme sayfası.](https://www.oracle.com/tr/java/technologies/javase-jdk15-downloads.html)

İndirdiğimiz klasörün yerine gidiyoruz.
```linux
cd Download
```
Dosyamızın uzantısı .deb olduğu için dpkg paket yönetim sisteminden yararlanıcağız. Bununla birlikte indirilen dosyayı kuruyoruz.
```linux
sudo dpkg -i jdk-15.0.2_linux-x64_bin.deb
```

Kurduğumuz sürümü derleyicimizde kullanmamız için `sudo update-alternatives` 'den yararlanmamız gerekiyor.
Eğer istediğiniz sürümde değilseniz alttaki komut yardımıyla seçim yapabilirsiniz:

```linux
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-15.0.2/bin/java 1
```
Muhtemel ekran çıktısı
> update-alternatives: /usr/bin/java (java) alternatifini sağlaması için /usr/lib/jvm/jdk-15.0.2/bin/java otomatik kipte kullanılıyor

Aynı işlemi javac içinde gerçekleştiriyoruz.
```linux
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-15.0.2/bin/javac 1
```

Muhtemel ekran çıktısı
>update-alternatives: /usr/bin/javac (javac) alternatifini sağlaması için /usr/lib/jvm/jdk-15.0.2/bin/javac otomatik kipte kullanılıyor

Java versiyon öğrenmek için:
```linux
java --verison
javac --version
```
Java bağ grubuna ekleme yapmamız gerekiyor.
```linux
sudo gedit /etc/environment
```
Gedit ile açılan dosyaya `JAVA_HOME="/usr/lib/jvm/jdk-15.0.2/bin/java"` yolunu ekliyoruz.

Değişikliklerin mevcut kabukta da uygulanması için source komutu kullanılabilir.
```linux
source /etc/environment
```
Son olarak yolumuzu ekrana yazdıralım.
```linux
echo $JAVA_HOME
```
Muhtemel ekran çıktısı
>/usr/lib/jvm/jdk-15.0.2/bin/java
