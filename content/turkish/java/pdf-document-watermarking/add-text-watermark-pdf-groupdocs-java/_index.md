---
date: '2026-01-21'
description: GroupDocs.Watermark for Java kullanarak PDF belgelerine nasıl filigran
  ekleyeceğinizi öğrenin. Fikri mülkiyetinizi kolay ve güvenle koruyun.
keywords:
- text watermark PDF
- GroupDocs Watermark Java
- PDF document watermarking
title: 'GroupDocs.Watermark for Java Kullanarak PDF''e Filigran Ekleme: Adım Adım
  Rehber'
type: docs
url: /tr/java/pdf-document-watermarking/add-text-watermark-pdf-groupdocs-java/
weight: 1
---

# Java için GroupDocs.Watermark Kullanarak PDF'ye Filigran Ekleme: Adım‑Adım Rehber

Günümüz dijital çağında, bir PDF'ye **how to add watermark** eklemek, gizli belgeleri korumak veya marka kimliğini güçlendirmek isteyen birçok geliştiricinin sorduğu bir sorudur. Filigran eklemek, yetkisiz kopyalamayı önlemekle kalmaz, aynı zamanda içeriğin sahipliğini net bir şekilde işaretler. Bu öğreticide, GroupDocs.Watermark for Java kullanarak bir PDF'nin belirli sayfalarına metin filigranı eklemeyi öğrenecek, ayrıca gizli filigran PDF uygulama, PDF'yi filigranla koruma ve daha fazlası için ipuçları bulacaksınız.

## Quick Answers
- **Java'da filigran eklemek için en iyi kütüphane hangisidir?** GroupDocs.Watermark for Java.
- **Sadece bir sayfaya filigran ekleyebilir miyim?** Yes – use `PdfArtifactWatermarkOptions.setPageIndex`.
- **Bir lisansa ihtiyacım var mı?** A trial license works for evaluation; a full license is required for production.
- **Hangi Java sürümü gereklidir?** Java 8 or higher with a compatible JDK.
- **Gizli bir filigran PDF eklemek mümkün mü?** Absolutely – just set the watermark text to “Confidential” and adjust styling.

## What Is Adding a Watermark to a PDF?
Filigran, sayfa içeriğinin arkasında veya önünde görünen yarı saydam bir kaplamadır—metin ya da görüntü. Genellikle **add confidential watermark PDF** bildirimleri, marka logoları veya taslak etiketleri eklemek için kullanılır.

## Why Use GroupDocs.Watermark for Java?
GroupDocs.Watermark, **apply watermark PDF Java** geliştiricileri için basit bir API sunar, karmaşık PDF yapısını dahili olarak yönetir. Toplu işleme, sayfa‑seviyesi kontrol ve geniş bir stil seçenekleri yelpazesi destekler, bu da hem küçük yardımcı programlar hem de büyük ölçekli belge akışları için idealdir.

## Prerequisites
Başlamadan önce, aşağıdakilere sahip olduğunuzdan emin olun:

1. **GroupDocs.Watermark for Java** version 24.11 or later.
2. Java geliştirme ortamı (JDK 8 or newer, IDE of your choice).
3. Java sözdizimi ve Maven hakkında temel bilgi.

## Setting Up GroupDocs.Watermark for Java

Kütüphaneyi entegre etmek için Maven kullanabilir veya JAR dosyasını doğrudan indirebilirsiniz.

**Maven Integration**

`pom.xml` dosyanıza depo ve bağımlılığı ekleyin:

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

**Direct Download**

Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirin.

### License Acquisition
Ücretsiz deneme ile başlayın veya tam bir lisans satın alın. Ürünü sadece değerlendirmek istiyorsanız bir [temporary license](https://purchase.groupdocs.com/temporary-license/) başvurusunda bulunun.

### Basic Initialization and Setup
Kütüphane kullanılabilir olduğunda, Java kodunuzda başlatın:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PdfLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Load PDF document
        PdfLoadOptions loadOptions = new PdfLoadOptions();
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/document.pdf";
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        
        System.out.println("Watermarker initialized successfully!");
    }
}
```

## Implementation Guide

Şimdi belirli bir sayfada **add text watermark pdf** eklemek için tam adımları inceleyeceğiz.

### Adding a Text Watermark to a Specific Page

**Genel Bakış:** Bu yöntem, PDF'nin herhangi bir sayfasına özel metin (ör. “Do not copy”, “Confidential”) yerleştirmenizi sağlar.

#### Step 1: Load the PDF Document
```java
// Step 1: Load the PDF document with PdfLoadOptions.
PdfLoadOptions loadOptions = new PdfLoadOptions();
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/document.pdf"; // Replace with your file path
Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
```

#### Step 2:```java
// Step 2: Create and configure the text watermark.
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.PdfArtifactWatermarkOptions;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

TextWatermark watermark = new TextWatermark("Do not copy");
watermark.setFont(new Font("Arial", 36));
watermark.setForegroundColor(Color.BLUE);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions);
watermark.setScaleFactor(1.0);
```

**Açıklama:**  
- `setFont` – yazı tipini ve boyutunu seçer.  
- `setForegroundColor` – filigran rengini tanımlar.  
- Hizalama özellikleri filigranı tam istediğiniz konuma yerleştirir.  
- `SizingType.ScaleToParentDimensions` filigranın sayfa boyutuna göre ölçeklen#### Step 3: Specify Page)
```java
// Step 3: Specify page options for adding the watermark.
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.setPageIndex(0); // Add watermark to the first page (index 0)
```

`setPageIndex` değerini sıfır‑tabanlı herhangi bir sayfa numarasına değiştirebilir veya birden fazla sayfayı hedeflemek için `options.setPageIndexes(new int[]{0,2,4})` çağırabilirsiniz.

#### Step 4: Add Watermark and Save
```java
// Step 4: Add the text watermark to the document.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_document.pdf");
watermarker.close();
```

**Açıklama:**  
- `add` tanımladığınız seçeneklerle filigranı uygular.  
- `save` yeni PDF'yi diske yazar.  
- `Watermarker`'ı kapatmak kaynakları serbest bırakır, bu büyük ölçekli işleme için önemlidir.

### Troubleshooting Tips
1. **File paths:** Giriş ve çıkış dizinlerinin mevcut olduğunu doğrulayın; aksi takdirde bir `FileNotFoundException` alırsınız.
2. **Font availability:** Belirttiğiniz font, ana makinede yüklü olmalıdır; aksi takdirde kütüphane varsayılan bir fonta geri döner.
3. **License errors:** “trial limit exceeded” hatası alırsanız, geçerli bir lisans dosyasının `License.setLicense("path/to/license.file")` ile yüklendiğinden emin olun.

## Practical Applications
- **Confidentiality Notices:** Filigran metni olarak “Confidential” veya “Internal Use Only” kullanın.
- **Branding:** Şirket adınızı veya sloganınızı ekleyerek marka kimliğini güçlendirin.
- **Draft Labels:** Erken sürümleri “DRAFT – NOT FOR DISTRIBUTION” ile iş:**## Performance Considerations
Büyük PDF'leri veya veya kullanılmayan nesneleri filigranlamadan önce kaldırın, böylece son dos## Conclusion
Artık GroupDocs.Watermark specific page**, **add confidential watermark pdf** ve **protect pdf with watermark** nasıl yapılır da biliyorsunuz. Projenizin ihtiyaçlarına göre farklı fontlar, renkler ve sayfa seçimleriyle deneyler yapın.

**Next Steps**
- `ImageWatermark` ile bir görüntü filigranı eklemeyi deneyin.
- Mevcut PDF'lerden filigranları kaldırmak keşfedin.
- Bu kodu daha büyük bir belge‑işleme hattına entegre edin.

## Frequently Asked Questions

**Q: GroupDocs?**  
A: Evet—`setPageIndex` çağrısını atresel olarak uygulamak için `options.setAllPages(true)` kullanın.

**Q: GroupDocs.Watermark kullanarak bir PDF'den filigranları nasılunu kullanın ve ardından sonucu kaydedin.

**Q: Şifre korumalı PDF'lere?**  
A: Evet—yüklemeden önce `PdfLoadOptions.setPassword("yourPassword")` ile şifreyi sağlayın.

**Q: GroupDocs.Watermark diğer belge formatlarını destekliyor mu?**  
A: Kesinlikle—Word, Excel, PowerPoint, görüntüler ve daha fazlası desteklenir.

---

**Last Updated:** 2026-01-21  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs