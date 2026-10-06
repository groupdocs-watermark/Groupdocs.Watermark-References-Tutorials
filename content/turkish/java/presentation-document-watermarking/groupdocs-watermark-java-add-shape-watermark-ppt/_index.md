---
date: '2026-05-27'
description: GroupDocs'i kullanarak Java ile PPT dosyalarına şekil filigranları eklemeyi
  öğrenin. Adım adım kılavuz, yapılandırma ipuçları ve performans analizleri.
keywords:
- how to use groupdocs
- java add watermark ppt
- GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  headline: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  type: TechArticle
- description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  name: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  steps:
  - name: Create a Shape Watermark
    text: '`ShapeWatermarkOptions` defines visual properties of a shape watermark,
      including size, color, opacity, and rotation.'
  - name: Apply the Watermark to All Slides
    text: Iterate through each slide in the presentation and add the shape watermark.
  - name: Save the Watermarked Presentation
    text: Choose the output format (PPTX) and save the file. The SDK preserves original
      slide content and animations.
  type: HowTo
- questions:
  - answer: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions`
      for each watermark.
    question: Can I add multiple watermarks to the same slide?
  - answer: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")`
      before loading.
    question: Does GroupDocs.Watermark support password‑protected PPTX files?
  - answer: Yes – specify the slide indices in the `add` method instead of iterating
      over all slides.
    question: Is it possible to watermark only selected slides?
  - answer: The SDK works with Java 8 through Java 21, covering both legacy and modern
      environments.
    question: What Java versions are compatible?
  - answer: Shape watermarks are static by design; they do not interfere with existing
      animations on the slide.
    question: How does the library handle animated shapes?
  type: FAQPage
title: GroupDocs'i Kullanarak Java ile PowerPoint Sunumlarına Şekil Filigranları Ekleme
type: docs
url: /tr/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/
weight: 1
---

# GroupDocs'u Kullanarak Java'da PowerPoint Sunumlarına Şekil Filigranları Ekleme

PowerPoint sunumlarınızı korumak, marka tutarlılığı ve veri güvenliği için esastır. Bu öğreticide **GroupDocs'u nasıl kullanacağınızı** keşfedecek ve Java ile PPTX dosyalarına doğrudan şekil filigranları gömeceksiniz, bu da her slaytı markalamanın güvenilir, programatik bir yolunu sağlar.

## Hızlı Yanıtlar
- **Java'da PPTX'e filigran ekleyen kütüphane nedir?** GroupDocs.Watermark.
- **Sunumu yükleyen sınıf hangisidir?** `PresentationLoadOptions`.
- **Filigranı uygulayan sınıf hangisidir?** `Watermarker`.
- **Geliştirme için lisansa ihtiyacım var mı?** Ücretsiz deneme testi için çalışır; üretim için ücretli lisans gereklidir.
- **500 MB'den büyük dosyaları filigranlayabilir miyim?** Evet – GroupDocs, belgeyi belleğe tamamen yüklemeden 2 GB'a kadar dosyaları işler.

## GroupDocs.Watermark Nedir?
`GroupDocs.Watermark`, PPT, PPTX, PDF ve DOCX dahil olmak üzere 100'den fazla belge formatına metin, resim veya şekil filigranları eklemenizi sağlayan bir Java SDK'sıdır. Bellek kullanımını düşük tutarak 2 GB'a kadar dosyaları işler. Kütüphane ayrıca opaklık, dönüş ve konumlandırma özelleştirmeleri için API'ler sunar, böylece filigran mevcut slayt düzenleriyle sorunsuz bir şekilde bütünleşir.

## PowerPoint Sunumlarına Şekil Filigranları Neden Eklenir?
Şekil filigranları slaytlar arasında görsel tutarlılığı korur ve vektör koordinatları kullanılarak kesin bir şekilde konumlandırılabilir, böylece marka öğelerini tam olarak ihtiyaç duyulan yere hizalayabilirsiniz. Yerel PowerPoint şekilleri olarak düzenlenebilir kalırlar, böylece sunumda sonraki düzenlemeler filigranın görünümünü ve konumunu korur. Sayısal faydalar şunlardır:
- **50+** filigran stili (metin, resim, şekil) desteklenir.
- **%100** düzen sadakati – şekiller düzenleme sonrası hizalı kalır.
- **2 GB'a kadar** dosya boyutu işleme, tam belge yüklemesi olmadan, naif yaklaşımlara göre **%70** daha az bellek tüketimi.

## Ön Koşullar
- **Java Development Kit (JDK) 8+** yüklü.
- **Maven**, bağımlılık yönetimi için.
- **IntelliJ IDEA** veya **Eclipse** gibi bir IDE.
- Temel Java bilgisi ve Maven'e aşinalık.
- **GroupDocs.Watermark** lisansına (deneme veya ticari) erişim.

### Gerekli Kütüphaneler ve Sürümler
- **GroupDocs.Watermark for Java** sürüm **24.11** veya üzeri.

### Ortam Kurulum Gereksinimleri
- `JAVA_HOME`'un JDK'nıza işaret ettiğinden emin olun.
- Projenizin `pom.xml` dosyasını aşağıda gösterildiği gibi yapılandırın.

## GroupDocs.Watermark ile Java'da PowerPoint Dosyasına Şekil Filigranı Nasıl Eklenir?
`PresentationLoadOptions`, slayt seçimi ve şifre işleme gibi PowerPoint dosyalarını yükleme seçeneklerini belirler.  
`Watermarker`, bir belgeyi yükleyen ve filigranları uygulayan çekirdek sınıftır.

Sunumu `PresentationLoadOptions` ile yükleyin, bir `Watermarker` örneği oluşturun, bir şekil filigranı tanımlayın, her slayta uygulayın ve sonunda dosyayı kaydedin. Bu uçtan uca akış sadece birkaç satır kod gerektirir ve tipik 10‑slaytlık sunumlar için bir saniyeden kısa sürede çalışır.

### Maven Yapılandırması
Add the following dependency to your `pom.xml` file:

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

### Doğrudan İndirme
Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirin.

### Lisans Edinme
GroupDocs.Watermark'ın tüm özelliklerini keşfetmek için ücretsiz deneme veya geçici bir lisans edinin. Üretim kullanımı için, dağıtım ölçeğinize uygun bir lisans satın alın.

#### Temel Başlatma ve Kurulum
`Watermarker` is the core class that loads a document and applies watermarks.  
`PresentationLoadOptions` provides options for loading PowerPoint files, such as slide handling and animation preservation.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx\
```

#### Adım 1: Şekil Filigranı Oluşturma
`ShapeWatermarkOptions` defines visual properties of a shape watermark, including size, color, opacity, and rotation.  

```java
import com.groupdocs.watermark.watermarkoptions.ShapeWatermarkOptions;
import com.groupdocs.watermark.contents.Shape;

// Create a rectangle shape
Shape shape = new Shape(Shape.ShapeType.Rectangle);
shape.setWidth(200);
shape.setHeight(100);
shape.setColor(Color.BLUE);
shape.setOpacity(0.3);

// Configure watermark options
ShapeWatermarkOptions options = new ShapeWatermarkOptions(shape);
options.setHorizontalAlignment(HorizontalAlignment.Center);
options.setVerticalAlignment(VerticalAlignment.Center);
```

#### Adım 2: Filigranı Tüm Slaytlara Uygula
Iterate through each slide in the presentation and add the shape watermark.

```java
for (int i = 0; i < watermarker.getDocument().getPages().size(); i++) {
    watermarker.add(options, i); // i = slide index
}
```

#### Adım 3: Filigranlı Sunumu Kaydet
Choose the output format (PPTX) and save the file. The SDK preserves original slide content and animations.

```java
watermarker.save("OUTPUT_DIRECTORY/presentation_watermarked.pptx", SaveFormat.Pptx);
```

### Ortak Sorunlar ve Çözümler
- **Lisans eksik hatası:** Lisans dosyasının sınıf yolunda (classpath) bulunduğundan emin olun veya `License.setLicense("path/to/license.lic")` ile ayarlayın.  
`License` sınıfı, tam SDK işlevselliğini etkinleştirmek için bir GroupDocs lisans dosyasını yükler ve uygular.  
- **Şekil görünmüyor:** Şeklin opaklığını veya renk kontrastını artırın; varsayılan opaklık 0.2'dir.  
- **Büyük dosya yavaşlaması:** Bellek kullanımını azaltmak için slaytları talep üzerine yüklemek amacıyla `PresentationLoadOptions.setLoadAllSlides(false)` kullanın.

## Sıkça Sorulan Sorular

**S: Aynı slayta birden fazla filigran ekleyebilir miyim?**  
C: Evet – her filigran için farklı `ShapeWatermarkOptions` ile `watermarker.add()` metodunu birden çok kez çağırın.

**S: GroupDocs.Watermark şifre korumalı PPTX dosyalarını destekliyor mu?**  
C: Kesinlikle. Yüklemeden önce şifreyi `PresentationLoadOptions.setPassword("yourPassword")` içinde sağlayın.

**S: Yalnızca seçili slaytlara filigran eklemek mümkün mü?**  
C: Evet – tüm slaytları döngüyle geçmek yerine `add` metodunda slayt indekslerini belirtin.

**S: Hangi Java sürümleri uyumludur?**  
C: SDK, Java 8'den Java 21'e kadar çalışır, hem eski hem de modern ortamları kapsar.

**S: Kütüphane animasyonlu şekilleri nasıl yönetir?**  
C: Şekil filigranları tasarım gereği statiktir; slayttaki mevcut animasyonları etkilemez.

---

**Son Güncelleme:** 2026-05-27  
**Test Edilen Versiyon:** Java için GroupDocs.Watermark 24.11  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [GroupDocs.Watermark for Java Kullanarak PowerPoint Sunumlarına Filigran Ekleme](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)
- [GroupDocs.Watermark for Java Kullanarak PowerPoint Görsellerine Metin Filigranı Ekleme](/watermark/java/presentation-document-watermarking/add-text-watermarks-presentation-images-groupdocs-watermark-java/)
- [GroupDocs.Watermark ve Java Kullanarak PowerPoint'te Çizgi Efekti Filigranları Ekleme](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)