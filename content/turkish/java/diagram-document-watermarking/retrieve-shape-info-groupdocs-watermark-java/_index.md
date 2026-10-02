---
date: '2026-02-13'
description: GroupDocs.Watermark for Java ile şekilleri nasıl çıkaracağınızı ve şekilden
  görüntü nasıl alacağınızı öğrenin, ayrıntılı diyagram bilgilerini verimli bir şekilde
  elde edin.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Java'da GroupDocs.Watermark Kullanarak Diyagramlardan Şekilleri Nasıl Çıkarabilirsiniz
type: docs
url: /tr/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Şekilleri Java'da GroupDocs.Watermark Kullanarak Diyagramlardan Nasıl Çıkarılır

Programlı olarak bir Visio‑benzeri diyagramdan **şekilleri nasıl çıkaracağınızı** öğrenmek istediğinizde, GroupDocs.Watermark kütüphanesi her ayrıntıyı—boyutları, konumları, gömülü görüntüler ve hatta her şeklin içindeki metni—temiz, Java‑odaklı bir şekilde almanızı sağlar. Bu öğreticide **şekilleri nasıl çıkaracağınızı**, neden önemli olduğunu ve projenize kopyalayabileceğiniz adım‑adım kodu göreceksiniz.

## Hızlı Cevaplar
- **Şekil çıkarımını hangi kütüphane yönetir?** Java için GroupDocs.Watermark  
- **Hangi Java sürümü gereklidir?** JDK 8 ve üzeri  
- **Bir şekilden görüntü verisi alabilir miyim?** Evet – `shape.getImage()` kullanın  
- **Şeklin içindeki metin erişilebilir mi?** Kesinlikle, `shape.getText()` ile  
- **Üretim için lisansa ihtiyacım var mı?** Geçerli bir GroupDocs.Watermark lisansı gereklidir  

## Giriş

Karmaşık diyagramları yönetmek, şekiller ve görüntüler gibi bileşenlerin ayrıntılı bilgilerine erişmeyi sıkça gerektirir. Java kullanarak diyagram şekillerinin boyutları, konumları veya metinleri gibi verileri programlı olarak almanız gerektiğinde bu öğretici tam size göre. GroupDocs.Watermark kütüphanesinin gücünden yararlanarak bu süreci bir Java uygulamasında kolaylaştırabilirsiniz. Bu rehberde **şekilleri nasıl çıkaracağınızı** bir diyagram dosyasından gösterecek ve ayrıca **şekilden görüntü çıkarma** ve **şekilden metin çıkarma** konularına da değineceğiz.

## “Şekilleri nasıl çıkarırız?” nedir?

Şekil çıkarma, diyagramın iç nesnelerini (sayfalar, şekiller, görüntüler, metin) okuyarak bunları analiz, dönüştürme veya başka uygulamalarda yeniden kullanma imkanı sağlar—otomasyon, raporlama veya CAD araçlarıyla entegrasyon için mükemmeldir.

## Şekil çıkarımı için neden GroupDocs.Watermark kullanmalı?

- **Tam format desteği** – VSDX, VDX ve birçok başka diyagram türüyle çalışır.  
- **Zengin nesne modeli** – şekil geometrisine, görüntülere ve metne doğrudan erişim sağlar.  
- **Harici bağımlılık yok** – saf Java, Maven projelerine kolayca eklenebilir.  

## Önkoşullar

- **GroupDocs.Watermark for Java** (sürüm 24.11 ve üzeri)  
- Java Development Kit (JDK) 8 ve üzeri  
- Bağımlılık yönetimi için Maven  
- IntelliJ IDEA veya Eclipse gibi bir IDE  

## GroupDocs.Watermark for Java Kurulumu

Kütüphaneyi Maven `pom.xml` dosyanıza ekleyin:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/watermark/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>24.11</version>
    </dependency>
</dependencies>
```

En yeni ikili dosyaları ayrıca [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

### Lisans Edinme Adımları
- **Ücretsiz Deneme:** API'yi değerlendirmek için bir deneme paketi indirin.  
- **Geçici Lisans:** Uzun süreli test için geçici bir anahtar isteyin.  
- **Satın Alma:** Üretim kullanımı için tam lisans alın.

### Temel Başlatma ve Kurulum

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Şekilleri Nasıl Çıkarılır – Uygulama Kılavuzu

### İçeriği Yükleme ve Alma

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Şekiller Üzerinde Döngü

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Şekilden görüntü nasıl çıkarılır

`shape.getImage()` çağrısı, ham bitmap'i, boyutlarını ve bayt dizisini içeren bir nesne döndürür. Yukarıda gösterilen özellikleri kullanarak görüntüyü diske kaydedebilir veya başka bir işleme hattına besleyebilirsiniz.

### Şekilden metin nasıl çıkarılır

`shape.getText()` yöntemi, şeklin içindeki düz metni döndürür. Şekil metin içermiyorsa yöntem `null` döner. Örnek döngü zaten metni yazdırır; ayrıca metni istediğiniz gibi işleyebilirsiniz—örneğin tüm şekil etiketlerinin bir dizinini oluşturmak gibi.

## Sorun Giderme İpuçları
- Dosya yolunu ve okuma izinlerini doğrulayın.  
- Desteklenen bir diyagram formatı (VSDX, VDX vb.) kullandığınızdan emin olun.  
- Bir şekil beklenen verileri göstermiyorsa, format‑özel sorunlar için kütüphanenin sürüm notlarını kontrol edin.

## Pratik Kullanım Alanları

1. **Diyagram Analizi:** Şekil boyutlarını veya eksik etiketleri kontrol ederek diyagramları otomatik olarak denetleyin.  
2. **Veri Görselleştirme:** Çıkarılan boyutları bir raporlama panosuna besleyerek yerleşim yoğunluğunu görselleştirin.  
3. **CAD Entegrasyonu:** Şekil verilerini CAD API'leriyle birleştirerek tasarım spesifikasyonlarını araçlar arasında senkronize edin.  

## Performans Düşünceleri

- **Kaynakları kapatın:** İşiniz bittiğinde `watermarker.close()` çağırarak yerel kaynakları serbest bırakın.  
- **Bellek yönetimi:** Büyük diyagramlar önemli heap tüketebilir; belleği izleyin ve gerekirse `-Xmx` değerini artırın.  
- **Toplu işleme:** Dosyaları toplu olarak işleyin ve mümkün olduğunda tek bir `Watermarker` örneğini yeniden kullanın.

## Sonuç

Bu kılavuzu izleyerek **şekilleri nasıl çıkaracağınızı**, **şekilden görüntü nasıl çıkaracağınızı** ve **şekilden metin nasıl çıkaracağınızı** GroupDocs.Watermark for Java ile öğrendiniz. Bu teknikler, otomatik diyagram analizi, raporlama ve diğer mühendislik sistemleriyle entegrasyon kapılarını açar. Bir sonraki adım olarak, tam API'yi incelemek için [belgelere](https://docs.groupdocs.com/watermark/java/) göz atın ve şekil çıkarımını özel iş mantığınızla birleştirmeyi deneyin.

## SSS Bölümü

1. **GroupDocs.Watermark nedir?**  
   - Çeşitli belge formatlarından, diyagramlar dahil, watermark ekleme ve bilgi çıkarma için tasarlanmış kapsamlı bir Java kütüphanesidir.  

2. **Bu kütüphaneyi tüm diyagram dosyası türlerini işlemek için kullanabilir miyim?**  
   - Evet, ancak dosya formatının desteklenip desteklenmediğini [API Referansı](https://reference.groupdocs.com/watermark/java/) üzerinden kontrol edin.  

3. **Java ve GroupDocs.Watermark kullanarak bir diyagramdan şekil boyutları ve konumlarını nasıl çıkarırım?**  
   - Diyagramı yükleyin, `DiagramContent`'e erişin, ardından şekiller üzerinde döngü yaparak genişlik, yükseklik, X ve Y gibi özellikleri alın.  

4. **GroupDocs.Watermark, Java ile diyagram şekillerindeki gömülü görüntüleri çıkarabilir mi?**  
   - Evet, şekiller içindeki görüntü verilerine, boyut ve piksel verilerine erişim sağlayan yöntemler sunar; bu veriler analiz veya değiştirme için kullanılabilir.  

5. **Java'da diyagram şekil bilgisi çıkarmak için önkoşullar nelerdir?**  
   - Java JDK 8+, Maven kurulumu, GroupDocs.Watermark kütüphanesi (24.11+), ve temel Java bilgisi uygulanabilir bir çözüm için gereklidir.  

---

**Son Güncelleme:** 2026-02-13  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs