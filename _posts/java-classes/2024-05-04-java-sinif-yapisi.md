---
title: "Java'da Sınıf (Class) Yapısı: A'dan Z'ye Kapsamlı Rehber"
date: 2024-05-04 09:00:00 +03:00
tags: [java, oop, programming]
description: Java'da sınıf yapısını, özelliklerini, metodlarını ve nesne yönelimli programlamanın temellerini detaylıca öğrenin.
image: "/java-classes/java-classes-banner.png"
---

# Java'da Sınıf (Class) Yapısı: Kapsamlı Rehber

## İçindekiler
1. [Giriş](#giriş)
2. [Sınıf Nedir?](#sınıf-nedir)
3. [Sınıf Yapısı ve Bileşenleri](#sınıf-yapısı-ve-bileşenleri)
4. [Erişim Belirleyicileri](#erişim-belirleyicileri)
5. [Constructor (Yapıcı Metod)](#constructor)
6. [Metodlar](#metodlar)
7. [Static Kavramı](#static-kavramı)
8. [Encapsulation (Kapsülleme)](#encapsulation)
9. [Best Practices ve Yaygın Hatalar](#best-practices)

## Giriş

Java'da sınıflar (class), nesne yönelimli programlamanın temel yapı taşlarıdır. Bir sınıf, nesnelerin şablonunu tanımlar ve bu nesnelerin sahip olacağı özellikleri (fields) ve davranışları (methods) belirler. Bu yazımızda, Java sınıflarını en temel seviyeden başlayarak ileri düzeye kadar detaylıca inceleyeceğiz.

## Sınıf Nedir?

Sınıf, gerçek dünyadaki nesnelerin programlama dilindeki temsilidir. Örneğin, bir Araba sınıfı düşünelim:

```java
public class Araba {
    // Özellikler (Fields)
    private String marka;
    private String model;
    private int yil;
    private double motorHacmi;
    
    // Constructor
    public Araba(String marka, String model, int yil) {
        this.marka = marka;
        this.model = model;
        this.yil = yil;
    }
    
    // Metodlar
    public void calistir() {
        System.out.println("Araba çalıştırıldı!");
    }
}
```

## Sınıf Yapısı ve Bileşenleri

Bir Java sınıfı temel olarak şu bileşenlerden oluşur:

1. **Fields (Alanlar)**: Sınıfın özellikleri
2. **Constructors (Yapıcılar)**: Nesne oluşturulurken çalışan özel metodlar
3. **Methods (Metodlar)**: Sınıfın davranışları
4. **Blocks (Bloklar)**: Static ve instance initialization blokları

Örnek bir sınıf yapısı:

```java
public class Ogrenci {
    // Fields
    private int ogrenciNo;
    private String ad;
    private String soyad;
    
    // Static field
    private static int ogrenciSayisi = 0;
    
    // Static initialization block
    static {
        System.out.println("Sınıf yüklendi!");
    }
    
    // Constructor
    public Ogrenci(String ad, String soyad) {
        this.ad = ad;
        this.soyad = soyad;
        ogrenciSayisi++;
        this.ogrenciNo = ogrenciSayisi;
    }
    
    // Method
    public void bilgileriGoster() {
        System.out.println("Öğrenci No: " + ogrenciNo);
        System.out.println("Ad Soyad: " + ad + " " + soyad);
    }
}
```

## Erişim Belirleyicileri

Java'da dört tür erişim belirleyici vardır:

1. **public**: Her yerden erişilebilir
2. **private**: Sadece sınıf içinden erişilebilir
3. **protected**: Aynı paket ve alt sınıflardan erişilebilir
4. **default (package-private)**: Sadece aynı paketten erişilebilir

```java
public class ErişimÖrneği {
    public String herkesErişebilir;
    private String sadeceSınıfİçi;
    protected String altSınıflarErişebilir;
    String ayniPaketErişebilir; // default
}
```

## Constructor

Constructor'lar, nesne oluşturulurken çalışan özel metodlardır:

```java
public class Kitap {
    private String ad;
    private String yazar;
    
    // Parametresiz constructor
    public Kitap() {
        this.ad = "Isimsiz";
        this.yazar = "Bilinmiyor";
    }
    
    // Parametreli constructor
    public Kitap(String ad, String yazar) {
        this.ad = ad;
        this.yazar = yazar;
    }
    
    // Copy constructor
    public Kitap(Kitap digerKitap) {
        this.ad = digerKitap.ad;
        this.yazar = digerKitap.yazar;
    }
}
```

## Metodlar

Metodlar, sınıfın davranışlarını tanımlar:

```java
public class HesapMakinesi {
    // Instance method
    public double topla(double a, double b) {
        return a + b;
    }
    
    // Static method
    public static double kareAl(double sayi) {
        return sayi * sayi;
    }
    
    // Overloaded method
    public int topla(int a, int b) {
        return a + b;
    }
}
```

## Static Kavramı

Static üyeler sınıfa aittir, nesneye değil:

```java
public class Sayac {
    private static int sayac = 0;
    private int id;
    
    public Sayac() {
        sayac++;
        id = sayac;
    }
    
    public static int getSayac() {
        return sayac;
    }
    
    public int getId() {
        return id;
    }
}
```

## Encapsulation

Encapsulation, veri gizleme ve güvenliği sağlar:

```java
public class BankaHesabi {
    private double bakiye;
    private String hesapNo;
    
    // Getter
    public double getBakiye() {
        return bakiye;
    }
    
    // Setter
    public void setBakiye(double bakiye) {
        if (bakiye >= 0) {
            this.bakiye = bakiye;
        } else {
            throw new IllegalArgumentException("Bakiye negatif olamaz!");
        }
    }
}
```

## Best Practices ve Yaygın Hatalar

### Best Practices:

1. Sınıf isimleri PascalCase ile yazılmalıdır
2. Field'lar private olmalı ve getter/setter kullanılmalıdır
3. Her sınıf tek bir sorumluluğa sahip olmalıdır
4. Constructor'larda validation yapılmalıdır
5. toString(), equals() ve hashCode() metodları override edilmelidir

### Yaygın Hatalar:

```java
public class KötüÖrnek {
    // HATALI: public field kullanımı
    public String data;
    
    // HATALI: validation eksikliği
    public void setYas(int yas) {
        this.yas = yas; // Negatif yaş kontrolü yok!
    }
    
    // HATALI: null kontrolü eksikliği
    public void islemYap(String veri) {
        veri.length(); // NullPointerException riski!
    }
}

// DOĞRU KULLANIM
public class İyiÖrnek {
    private String data;
    
    public void setYas(int yas) {
        if (yas < 0) {
            throw new IllegalArgumentException("Yaş negatif olamaz!");
        }
        this.yas = yas;
    }
    
    public void islemYap(String veri) {
        if (veri == null) {
            throw new IllegalArgumentException("Veri null olamaz!");
        }
        veri.length();
    }
}
```

## Sonuç

Java'da sınıflar, nesne yönelimli programlamanın temelini oluşturur. İyi tasarlanmış sınıflar, kodunuzun daha okunabilir, bakımı kolay ve yeniden kullanılabilir olmasını sağlar. Bu yazıda öğrendiğimiz kavramları uygulayarak, daha kaliteli ve profesyonel Java uygulamaları geliştirebilirsiniz.

### Kaynaklar
- Oracle Java Documentation
- Effective Java (Joshua Bloch)
- Clean Code (Robert C. Martin) 