---
date: '2026-01-16'
description: Java ve GroupDocs.Watermark kütüphanesini kullanarak Word belgelerine
  metin su işareti resimleri eklemeyi öğrenin. Java su işareti resmi ekleme örneklerini
  içerir.
keywords:
- GroupDocs Watermark Java
- add text watermarks to Word images
- Java watermarking in Word documents
title: Java ile Word belgelerine metin filigranı ekleyin
type: docs
url: /tr/java/image-watermarks/add-watermarks-word-images-groupdocs-java/
weight: 1
---

# Java ile Word belgelerine metin su izi resimleri ekleyin

## Giriş
Word belgelerine **metin su izi resimleri** eklemeniz gerekiyorsa — marka oluşturma, güvenlik veya sürüm kontrolü amaçları için — doğru yerdesiniz. Bu öğreticide, **GroupDocs.Watermark for Java** kullanarak bir Word dosyasının belirli bir bölümündeki her resme metin su izi yerleştirmek için gereken adımları ayrıntılı olarak göstereceğiz. Sonunda, herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

### Hızlı Yanıtlar
- **Bu hangi kütüphaneyi kullanıyor?** GroupDocs.Watermark for Java  
- **Hedeflenen anahtar kelime nedir?** add text watermark images  
- **Bir lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme çalışır; üretim için lisans gereklidir  
- **Tek bir bölümü hedefleyebilir miyim?** Evet – API, bölüm başına resimleri seçmenize izin verir  
- **Hangi Java sürümü destekleniyor?** Maven veya Gradle yapılandırmalarıyla Java 8+

## “add text watermark images” nedir?
Bir resme metin su izi eklemek, resmi üzerine yarı saydam metin bindirerek su izinin, resim nerede görüntülense veya basılsa o resimle birlikte gitmesini sağlar. Word belgelerinde bu, görsel içeriği yetkisiz yeniden kullanımdan korur.

## Neden GroupDocs.Watermark for Java kullanmalı?
- **Tam belge desteği** – DOCX, DOC ve diğer Office formatlarıyla çalışır.  
- **İnce ayarlı kontrol** – bireysel bölümleri, paragrafları veya resimleri seçebilirsiniz.  
- **Performans odaklı** – büyük dosyaları minimum bellek kullanımıyla işler.  

## Önkoşullar
- **GroupDocs.Watermark for Java** (sürüm 24.11 ve üzeri).  
- Bağımlılıkları yönetmek için Maven (veya başka bir yapı aracı).  
- Temel Java bilgisi ve korumak istediğiniz bir Word belgesi.

## GroupDocs.Watermark for Java Kurulumu
GroupDocs.Watermark for Java'ı kullanmak için, projenize aşağıdaki şekilde entegre edin:

**Maven Kurulumu:**  
`pom.xml` dosyanıza aşağıdaki yapılandırmayı ekleyin:

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

**Doğrudan İndirme:**  
Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

### Lisans Edinme
GroupDocs.Watermark'ı tam olarak kullanmak için bir lisans almayı düşünün. Ücretsiz deneme ile başlayabilir veya tüm özellikleri sınırsız olarak keşfetmek için geçici bir lisans **isteyebilirsiniz**. Satın alma seçenekleri için [GroupDocs satın alma sayfasını](https://purchase.groupdocs.com/temporary-license/) ziyaret edin.

## java add watermark picture – Adım Adım Kılavuz
Aşağıda, **java add watermark picture** işlevselliğini gösteren ve odak noktasını metin su izi resimleri eklemeye odaklayan eksiksiz bir yürütme bulunmaktadır.

### Adım 1: Word Belgesini Yükleyin
İlk olarak, değiştirmek istediğiniz Word dosyasını açın:

```java
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

### Adım 2: Metin Su İzini Oluşturun ve Özelleştirin
Su izi metnini, yazı tipini, hizalamayı, dönüşü ve boyutu tanımlayın:

```java
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.setHorizontalAlignment(HorizontalAlignment.Center); // Center horizontally
watermark.setVerticalAlignment(VerticalAlignment.Center);   // Center vertically
watermark.setRotateAngle(45);                          // Set rotation angle to 45 degrees
watermark.setSizingType(SizingType.ScaleToParentDimensions);// Scale size relative to parent dimensions
watermark.setScaleFactor(1);                           // Maintain original scale factor
```

### Adım 3: Belirli Bir Bölümdeki Resimlere Erişin
Yalnızca ilk bölümdeki resimleri hedefleyin (diğer bölümleri hedeflemek için indeksi değiştirebilirsiniz):

```java
WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);
var images = content.getSections().get_Item(0).findImages();
```

### Adım 4: Su İzini Her Resme Uygulayın
Alınan resimler üzerinde döngü oluşturun ve metin su izini gömün:

```java
for (var image : images) {
    image.add(watermark); // Add watermark to the current image
}
```

### Adım 5: Kaydedin ve Kapatın
Güncellenen belgeyi diske yazın ve kaynakları serbest bırakın:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```

## Yaygın Sorunlar ve Çözümler
- **Su izi görünmüyor:** Metin renginin resim arka planıyla kontrast oluşturduğunu doğrulayın. Ayrıca opaklığı `watermark.setOpacity(0.5);` ile ayarlayabilirsiniz.  
- **Büyük dosyalarda performans yavaşlaması:** Resimleri önceden sıkıştırın ve belgeyi tüm dosyayı bir kerede yüklemek yerine bölüm bölüm işleyin.  

## Pratik Uygulamalar
1. **Marka oluşturma:** Ortaklarla sunumları paylaşmadan önce tüm resimlere şirket çapında su izleri ekleyin.  
2. **Gizlilik:** İç kılavuzlardaki özel diyagramları koruyun.  
3. **Sürüm kontrolü:** Taslak resimleri “Confidential Draft” ile işaretleyerek yanlışlıkla yayınlanmasını önleyin.  

## Performans Hususları
- **Bellek Yönetimi:** Yerel kaynakları serbest bırakmak için her zaman `watermarker.close();` çağırın.  
- **Toplu İşleme:** Çok sayıda belgeyle çalışırken, bellek kullanımını düşük tutmak için küçük partiler halinde işleyin.  
- **Resim Optimizasyonu:** Su izi eklemeden önce uygun sıkıştırma ile JPEG veya PNG kullanın.  

## Sonuç
Artık Java kullanarak Word belgesi resimlerine **metin su izi resimleri** eklemek için eksiksiz, üretime hazır bir yönteme sahipsiniz. Bu teknik belge güvenliğini artırır, marka oluşturmayı güçlendirir ve hangi resimlerin su izi alacağını ince ayarlarla kontrol etmenizi sağlar.

**Sonraki Adımlar:** Ek su izi türlerini (görüntü‑tabanlı su izleri) keşfedin, farklı dönüş açılarıyla deney yapın veya bu kodu daha büyük bir belge‑işleme hattına entegre edin.

## Sıkça Sorulan Sorular
**S:** GroupDocs.Watermark'ı başka dosya formatlarıyla kullanabilir miyim?  
**C:** Evet, kütüphane Word dışında PDF, Excel, PowerPoint ve görüntü dosyalarını da destekler.

**S:** Su izinin opaklığını nasıl değiştiririm?  
**C:** Opaklığı `watermark.setOpacity(double opacity)` ile ayarlayın; `opacity` 0.0 (şeffaf) ile 1.0 (opak) arasında bir değer alır.

**S:** Belgemde birden fazla bölümde resimler varsa ne yapmalıyım?  
**C:** `content.getSections()` üzerinden döngü oluşturun ve ihtiyacınız olan her bölümde aynı mantığı uygulayın.

**S:** Özel yazı tipleri destekleniyor mu?  
**C:** Kesinlikle. `Font` nesnesini oluştururken `.ttf` dosyasının tam yolunu sağlayın.

**S:** Metin yerine görüntü‑tabanlı bir su izi ekleyebilir miyim?  
**C:** Evet—`TextWatermark` yerine `ImageWatermark` kullanın ve aynı `add` kalıbını izleyin.

**Last Updated:** 2026-01-16  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Kaynaklar**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/) GroupDocs.Watermark for Java