---
date: '2026-03-22'
description: GroupDocs.Watermark for Java kullanarak metin filigranı ekleyerek Excel
  dosyalarına filigran eklemeyi öğrenin. Elektronik tablolarınızı güvence altına alın
  ve markalaşmayı güçlendirin.
keywords:
- text watermark Excel
- GroupDocs.Watermark Java
- Excel document security
title: Java için GroupDocs.Watermark ile Excel Sayfalarına Metin Filigranı Ekleme
type: docs
url: /tr/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-watermark-java/
weight: 1
---

# Excel Sayfalarına Metin ile Su İşareti Eklemek – GroupDocs.Watermark for Java Kullanarak

When you need to **how to watermark Excel** workbooks—especially those that contain sensitive data—adding a clear, professional text watermark is one of the most effective ways to protect your content and reinforce brand identity. In this tutorial we’ll walk through the exact steps to **add text watermark Excel** files using the GroupDocs.Watermark library for Java, covering everything from project setup to saving the final, secured workbook.

## Hızlı Yanıtlar
- **Hangi kütüphaneyi kullanmalıyım?** GroupDocs.Watermark for Java.
- **Her sayfaya bir metin su işareti ekleyebilir miyim?** Yes – iterate over each worksheet and apply the same watermark.
- **Bir lisansa ihtiyacım var mı?** A free trial works for evaluation; a permanent license is required for production.
- **Hangi Java sürümü destekleniyor?** JDK 8 or later.
- **Su işareti hücre verilerini etkiler mi?** No, it only overlays images within the worksheet.

## Excel Su İşareti Nedir?
Watermarking Excel means embedding a visible marker—text or image—directly onto the worksheet’s visual elements (such as images) so that anyone opening the file can see the ownership or confidentiality notice. This technique helps deter unauthorized distribution and adds a professional look to your reports.

## Java Kullanarak Excel'e Metin Su İşareti Neden Eklenir?
- **Security** – Açıkça gizli veya mülkiyet bilgilerini gösterir.
- **Brand consistency** – Tüm paylaşılan elektronik tablolarda kurumsal markayı güçlendirir.
- **Automation** – Java, su işaretlerini programlı olarak eklemenizi sağlar, manuel düzenlemelerde zaman tasarrufu sağlar.
- **Cross‑format support** – Hem `.xlsx` hem de eski `.xls` dosyalarıyla çalışır.

## Önkoşullar
- **Java Development Kit (JDK)** 8 veya daha yenisi.
- **Maven** bağımlılık yönetimi için.
- Java sözdizimi ve nesne‑yönelimli kavramlara temel aşinalık.

## GroupDocs.Watermark for Java Kurulumu
To start, add the GroupDocs.Watermark dependency to your Maven project.

### Using Maven
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
Alternatively, download the latest JAR from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

**Lisans Alımı**
- **Free Trial** – Ücretsiz deneme, tüm özellikleri maliyetsiz keşfetmenizi sağlar.
- **Temporary License** – Kısa vadeli testler için kullanın.
- **Purchase** – Tam üretim yeteneklerini açın.

### Temel Başlatma
```java
import com.groupdocs.watermark.Watermarker;
// Initialize watermarker instance for your document
Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx");
```

## Uygulama Kılavuzu

### Özellik 1: Metin Su İşareti Oluşturma ve Özelliklerini Yapılandırma
Creating and customizing the watermark involves setting its text, font, alignment, rotation angle, and scaling.  

#### Adım‑Adım Genel Bakış
**Su İşaretinizi Tanımlayın**
```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a new TextWatermark object
text watermark = new TextWatermark("Protected image", new Font("Arial", 8));

// Configure the watermark properties
text watermark.setHorizontalAlignment(HorizontalAlignment.Center);
text watermark.setVerticalAlignment(VerticalAlignment.Center);
text watermark.setRotateAngle(45); // Set rotation angle
text watermark.setSizingType(SizingType.ScaleToParentDimensions);
text watermark.setScaleFactor(1); // Maintain original size scale factor
```
- **Text and Font** – Açık bir mesaj ve okunabilir bir yazı tipi seçin.
- **Alignment** – Çoğu görüntü için ortalama iyi çalışır.
- **Rotation & Scaling** – 45° eğim, su işaretini belirgin yapar ancak görüntüyü gizlemez.

### Özellik 2: Su İşareti İçin Elektronik Tablo Belgesi Yükleme
Load the workbook with appropriate options so GroupDocs can access its internal images.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
// Load your Excel spreadsheet
documentLoadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", documentLoadOptions);
```

### Özellik 3: Çalışma Sayfasındaki Görsellere Metin Su İşareti Ekleme
Iterate through the images on the first worksheet and apply the configured watermark.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.WatermarkableImageCollection;

// Access content from your loaded document
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
WatermarkableImageCollection images = content.getWorksheets().get_Item(0).findImages();

for (com.groupdocs.watermark.contents.WatermarkableImage image : images) {
    // Add the configured watermark to each image in the worksheet
    image.add(watermark);
}
```

### Özellik 4: Su İşaretli Elektronik Tablo Belgesini Kaydetme ve Kapatma
Persist the changes to a new file and clean up resources.

```java
// Save the changes to a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx");
// Close the watermarker instance to free resources
watermarker.close();
```

## Pratik Uygulamalar
- **Document Security** – Gizli finansal modelleri veya İK verilerini koruyun.
- **Branding** – Tüm paylaşılan raporlara şirket sloganları veya yasal uyarılar ekleyin.
- **Copyright Protection** – Her dışa aktarılan görüntüyü işaretleyerek intihalı önleyin.

## Performans Düşünceleri
- GroupDocs.Watermark'ı güncel tutarak en son performans iyileştirmelerinden yararlanın.
- `Watermarker` örneğini hemen serbest bırakın (`close()`) bellek boşaltmak için.
- Çok büyük çalışma kitapları için, yüksek bellek tüketimini önlemek amacıyla sayfaları toplu işleyin.

## Yaygın Sorunlar ve Çözümler
| Issue | Solution |
|-------|----------|
| Su işareti görünmüyor | Çalışma sayfasının gerçekten görüntü içerdiğini doğrulayın; API yalnızca görüntülere su işareti ekler, hücrelere değil. |
| Yanlış hizalanmış su işareti | `HorizontalAlignment` / `VerticalAlignment` ayarlarını değiştirin veya `RotateAngle` değerini değiştirin. |
| Büyük dosyalarda bellek yetersizliği hataları | JVM yığın boyutunu (`-Xmx`) artırın veya her çalışma sayfasını ayrı ayrı işleyin. |
| Lisans hataları | Deneme veya kalıcı lisans dosyasının projenizde doğru şekilde referans edildiğinden emin olun. |

## Sıkça Sorulan Sorular

**S: Bunu tüm Excel sürümlerinde kullanabilir miyim?**  
A: Evet, GroupDocs hem `.xlsx` hem de `.xls` formatlarını destekler.

**S: Su işaretim doğru görünmezse ne yapmalıyım?**  
A: Hizalama ayarlarını tekrar kontrol edin ve görüntü boyutlarının seçilen ölçek faktörüne uygun olduğundan emin olun.

**S: Yazı tipi stilini daha da özelleştirebilir miyim?**  
A: `Font` sınıfını kullanarak kalın, italik, renk veya diğer tipografik özellikleri ayarlayın.

**S: Bir çalışma kitabındaki tüm sayfalara su işareti eklemek mümkün mü?**  
A: Kesinlikle—`content.getWorksheets()` üzerinden döngü yapın ve her sayfaya aynı `image.add(watermark)` mantığını uygulayın.

**S: Büyük Excel dosyalarını verimli bir şekilde nasıl yönetebilirim?**  
A: Çalışma sayfalarını artımlı olarak işleyin, kaydettikten sonra her `Watermarker` örneğini kapatın ve JVM yığın boyutunu artırmayı düşünün.

## Kaynaklar
- [GroupDocs.Watermark Dokümantasyonu](https://docs.groupdocs.com/watermark/java/)
- [API Referansı](https://reference.groupdocs.com/watermark/java)
- [GroupDocs.Watermark for Java İndir](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)
- [Geçici Lisans Başvurusu](https://purchase.groupdocs.com/temporary-license/)

By integrating these steps into your Java projects, you can **java add watermark excel** files quickly, ensuring both security and brand consistency.

---

**Son Güncelleme:** 2026-03-22  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs