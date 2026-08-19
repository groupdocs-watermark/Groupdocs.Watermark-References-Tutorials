---
date: '2026-08-19'
description: Java'da GroupDocs.Watermark kullanarak diyagram görüntülerini nasıl değiştireceğinizi
  ve diyagrama verimli bir şekilde filigran eklemeyi öğrenin. Adım adım kod ve en
  iyi uygulamalar.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Java'da GroupDocs.Watermark kullanarak diyagram görüntülerini nasıl
  değiştireceğinizi ve diyagrama verimli bir şekilde filigran eklemeyi öğrenin. Adım
  adım kod ve en iyi uygulamalar.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Java'da GroupDocs.Watermark kullanarak diyagram görüntülerini değiştirin
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Java'da GroupDocs.Watermark kullanarak diyagram görüntülerini değiştirin
type: docs
url: /tr/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Java'da GroupDocs.Watermark kullanarak diyagram görüntülerini değiştirin

Diyagram dosyalarındaki görüntüleri manuel olarak güncellemek zaman alıcı ve hataya açıktır. Bu öğreticide sadece birkaç satır kodla **Java'da diyagram görüntülerini değiştirmeyi** öğrenecek ve gerektiğinde **diyagrama filigran eklemeyi** de göreceksiniz. Sonunda Visio, Draw.io veya diğer desteklenen diyagram formatlarıyla çalışan herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Hızlı cevaplar
- **Diyagram görüntüsü değişimini hangi kütüphane yönetir?** GroupDocs.Watermark for Java.
- **Temel bir değişim için kaç satır kod gerekir?** Watermarker oluşturulduktan sonra sadece üç satır.
- **Aynı anda bir filigran ekleyebilir miyim?** Evet – aynı Watermarker örneğini bir filigran nesnesiyle kullanın.
- **Hangi Java sürümü gereklidir?** JDK 8 veya üzeri.
- **Üretim kullanımında lisansa ihtiyacım var mı?** Geçerli bir GroupDocs.Watermark lisansı gereklidir; ücretsiz deneme sürümü mevcuttur.

## Java'da diyagram görüntülerini değiştirme nedir?
Java'da diyagram görüntülerini değiştirmek, bir diyagram dosyası (.vsdx, .drawio veya .svg gibi) içinde bitmap grafik içeren şekilleri programlı olarak bulmak ve bu gömülü görüntüleri GroupDocs.Watermark API'si kullanarak yeni görüntülerle değiştirmek anlamına gelir. Bu, aksi takdirde bir diyagram düzenleyicisinde manuel olarak yapılması gereken güncellemeleri otomatikleştirir.

## Diyagram görüntüsü değişimi için neden GroupDocs.Watermark kullanılmalı?
GroupDocs.Watermark **50+ giriş ve çıkış formatını** destekler – Visio, Draw.io ve SVG dahil – ve belgeyi belleğe tamamen yüklemeden **500 MB'a kadar dosyaları** işleyebilir, bu da naif dosya akışı yaklaşımlarına göre **CPU kullanımında %30 azalma** sağlar.

## Önkoşullar
- JDK 8 veya daha yeni bir sürüm yüklü.
- Java geliştirme için bir IDE (IntelliJ IDEA, Eclipse veya VS Code).
- Maven (veya JAR'ları manuel ekleme yeteneği).
- Geçerli bir GroupDocs.Watermark lisansı (deneme veya kalıcı). Lisansı [GroupDocs](https://purchase.groupdocs.com/temporary-license/) adresinden edinebilirsiniz.

### Gerekli kütüphaneler, sürümler ve bağımlılıklar
GroupDocs.Watermark deposunu ve bağımlılığını `pom.xml` dosyanıza ekleyin:

```xml
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
```

Manuel JAR yönetimini tercih ediyorsanız, resmi siteden en son sürümü indirin: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Java'da diyagram görüntülerini adım adım nasıl değiştirilir

### Bir diyagram dosyası için Watermarker nasıl başlatılır?
Watermarker, bir belgeyi temsil eden ve içerik manipülasyonu için yöntemler sağlayan ana sınıftır. Başlamak için diyagram dosyasını belleğe yükleyen bir `Watermarker` nesnesi oluşturun. `Watermarker` sınıfı, GroupDocs.Watermark'ın temel giriş noktasıdır ve belgeleri okumanıza, değiştirmenize ve kaydetmenize olanak tanır. DPI veya sayfa aralığı gibi format‑özel ayarları belirtmek için `DiagramLoadOptions` kullanın. `DiagramLoadOptions`, bir diyagramın nasıl yükleneceğini yapılandırır; örneğin DPI veya yükleme modunu ayarlamak gibi.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Şekilleri bulmak için diyagram içeriğine nasıl erişilir?
Dosya yüklendikten sonra `Watermarker` üzerinden bir `DiagramContent` nesnesi alın. `DiagramContent`, diyagramın sayfalar ve şekiller içindeki iç hiyerarşisini temsil eder. Bu model, sayfa ve şekil koleksiyonlarını ortaya çıkarır; bu koleksiyonlar üzerinde döngü kurarak görüntü veya metin gibi belirli öğeleri kolayca bulabilirsiniz.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Diyagramda şekil görüntüleri nasıl değiştirilir?
İstenen sayfadaki her `DiagramShape` üzerinde döngü yapın, şeklin bir görüntü içerip içermediğini kontrol edin ve görüntü baytlarını yeni bir dosyanın baytlarıyla değiştirin. `DiagramShape`, diyagramdaki tek bir şeklin modelidir; `DiagramWatermarkableImage` ise bir şekle uygulanabilecek görüntü verilerini saklar.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Değişiklikleri nasıl kaydedip Watermarker'ı kapatırsınız?
Tüm değişiklikler tamamlandığında, güncellenen diyagramı bir dosyaya yazmak için `Watermarker` üzerinde `save` metodunu çağırın, ardından yerel kaynakları serbest bırakmak için `close` metodunu çalıştırın. Bu, dosya tanıtıcılarının serbest bırakılmasını sağlar ve özellikle toplu işte birçok diyagram işlenirken bellek sızıntılarını önler.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Aynı diyagrama filigran ekleme (isteğe bağlı)

Diyagramı markalamak da istiyorsanız, görüntü değişiminden önce ya da sonra bir filigran ekleyebilirsiniz:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Yaygın tuzaklar ve sorun giderme

| Semptom | Muhtemel neden | Çözüm |
|---------|----------------|-------|
| Kod çalıştırıldıktan sonra görüntü değişmedi | `DiagramShape.hasImage()` false döndürdü | Şekil tipini doğrulayın; bazı vektör şekilleri görüntüleri farklı şekilde depolar. |
| Büyük dosyalarda OutOfMemoryError | Diyagramın tamamını bir kerede yüklemek | `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` kullanarak sayfaları sıralı işleyin. |
| Filigran görünmüyor | Filigran mevcut içeriğin arkasına yerleştirildi | Kaydetmeden önce `watermarker.setWatermarkPosition(Position.Foreground)` metodunu çağırın. |

## Sıkça sorulan sorular

**S: Parola korumalı diyagramlardaki görüntüleri değiştirebilir miyim?**  
C: Evet. `Watermarker` oluştururken parolayı `DiagramLoadOptions`'a geçirin.

**S: Kütüphane .drawio (XML) dosyalarıyla çalışıyor mu?**  
C: Kesinlikle – GroupDocs.Watermark Draw.io XML formatını destekler ve her düğümü bir şekil olarak ele alır.

**S: Aynı anda kaç diyagram işleyebilirim?**  
C: Kütüphane sadece okuma işlemleri için iş parçacığı güvenlidir; yazma işlemleri için dosya tanıtıcı çakışmasını önlemek amacıyla eşzamanlılığı CPU çekirdek sayısıyla sınırlayın.

**S: Görüntü boyutu için bir limit var mı?**  
C: 100 MB'a kadar görüntüler desteklenir; daha büyük dosyalar bellek kullanımını düşük tutmak için önceden yeniden boyutlandırılmalıdır.

**S: Hangi lisans seçenekleri mevcuttur?**  
C: Ücretsiz 30‑günlük deneme ile başlayabilirsiniz; üretim kullanımı için ücretli bir lisans gerekir ve bu lisans GroupDocs mağazasından temin edilebilir.

---

**Son Güncelleme:** 2026-08-19  
**Test Edilen:** GroupDocs.Watermark 23.9 for Java  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [GroupDocs.Watermark Java için Diyagram Filigranlama Öğreticileri](/watermark/java/diagram-document-watermarking/)
- [Gelişmiş Belge Güvenliği için GroupDocs.Watermark Java kullanarak Diyagram Şekillerinden Hipermetin Bağlantılarını Kaldırma](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Java'da GroupDocs.Watermark kullanarak Görüntü Filigranı Ekleme: Adım Adım Kılavuz](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)