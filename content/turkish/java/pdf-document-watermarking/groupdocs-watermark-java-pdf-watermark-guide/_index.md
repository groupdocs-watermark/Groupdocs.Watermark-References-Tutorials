---
date: '2026-01-31'
description: GroupDocs.Watermark for Java kullanarak PDF dosyalarına nasıl filigran
  ekleyeceğinizi öğrenin. Belgeleri koruyun, PDF'leri markalaştırın ve filigranları
  verimli bir şekilde yönetin.
keywords:
- GroupDocs Watermark for Java PDF
- PDF watermarking guide
- Java watermark application
title: GroupDocs.Watermark for Java ile PDF'ye Filigran Ekleme
type: docs
url: /tr/java/pdf-document-watermarking/groupdocs-watermark-java-pdf-watermark-guide/
weight: 1
---

.Watermark for Java ile

PDF dosyalarınıza su işareti eklemek, fikri mülkiyeti korumak, markanızı sergilemek veya belgeleri giz, GroupDocs.Watermark for Java kullanarak PDF'ye su işareti eklemeyi öğreneceksiniz**, süreci basit tutarken çıktının yüksek kalitede olmasını sağlayarak.

## Hızlı Yan nedir?** Sahipliği korumak, markayı iletmek veya gizliliği göstermek.  
- **Bu öğreticide hangi kütüphane kullanılıyor?** GroupDocs.Watermark for Java.  
- **Lisans gerekir mi?** Değerlendirme için ücretsiz deneme çalışır; üretim için ücretli lisans gereklidir.  
- **Yazı tipi, boyut ve konumu özelleştirebilir miyim?** Evet – API, yazı tipini, hizalamayı, boyutu ve kenar boşluğu ayarlarını belirlemenizi sağlar.  
- **Çözüm Maven projeleriyle uyumlu mu?** Kesinlikle; kütüphane Maven depoları aracılığıyla dağıtılır.

## PDF Su İşareti Nedir?
PDF su işareti, genellikle metin veya görüntü olan görsel bir üst katmandır ve bir PDF belgesinin her sayfasında görünür. Yarı şeffaf, döndürülmüş veya tam istediğiniz konumda olabilir; böylece içeriği değiştirmeden sahipliği göstermenize veya önemli bilgileri iletmenize yardımcı olur.

## Neden GroupDocsay entegrasyon** Maven veya Gradle ile.  
- **Tam kontrol** metin stilizasyonu, hizalama, ölans** büyük belgelerde verimli kaynak yönetimi sayesinde.  
- **Çapraz platform** desteği, aynı kod Windows, Linux ve macOS'ta çalışır.

## Önkoşullar
- Java Development Kit (JDK) yüklü.  
- Kütüphaneleri yönetmek için Maven (veya başka bir bağımlılık yöneticisiBeans gibi bir IDE.  
- Java ve PDF kavramları hakkında temel bilgi.

## GroupDocs.W kullanmaya başlamak için kütüphaneyi projenize ekleyin:

**Maven Yapılandırması**  
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

**Doğrudan İndirme**  
Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresindenın veya tam özellikleri keşfetmek için geçici bir lisans isteyin. Uzun vadeli üretim kullanımı için bir lisans satın alın.

### Temel Başlatma ve Kurulum
Kütüphane eklendikten sonra projenizi aşağıdaki gibi başlatın:

```java
import com.groupdocs.watermark.Watermarker;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize watermarker with input PDF path.
        Watermarker watermarker = new Watermarker("input.pdf");
        
        System.out.println("Watermarker initialized successfully!");
        
        // Close the resource once done
        watermarker.close();
    }
}
```

## Uygulama Kılavuzu

### Özellik: Su İşareti Oluşturma ve Yapılandırma
#### Genel Bakış
Metin su işareti oluşturun, hizalamasını ayarlayın ve PDF sayfalarınıza uygun boyutlandırmayı yapılandırın.

##### Belirli Yazı Tipi Ayarlarıyla Metin Su İşareti Oluşturma
`TextWatermark` nesnesi oluşturularak başlanır. kullanılmıştır:

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a text watermark with specific font settings.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
```

##### Yatay ve Dikey Hizalama Ayarla
Su işaretini istediğiniz konuma hizalayın:

```java
// Set the horizontal alignment of the watermark to the right.
watermark.setHorizontalAlignment(HorizontalAlignment.Right);

// Set the vertical alignment of the watermark to the top.
watermark.setVerticalAlignment(VerticalAlignment.Top);
```

##### Boyutlandırma Tipini Yapılandır
Belge boyutlarına uygun şekilde sığmasını sağlamak için boyutlandırmayı ayarlayın:

```java
// Configure the sizing type to scale to parent dimensions.
watermark.setSizingType(SizingType.ScaleToParentDimensions);

// Set the scaling factor for the watermark.
watermark.setScaleFactor(1);
```

### Özellik: Sayfa Kenar Boşluğu Tipiyle Su İşareti U kenar boşluklarını dikkate alarak su işareti uygulayın; böyleceleme Seçeneklerini Başlat ve PDF Belgesini Yükle
Yükleme seçeneklerini ayarlayın başlatın:

```java
import com.groupdocs.watermark.options.PdfLoadOptions;
import com.groupdocs.watermark.contents.PdfContent;

// Initialize load options for the PDF document.
PdfLoadOptions loadOptions = new PdfLoadOptions();

Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/in_document_pdf.pdf", loadOptions);
```

##### Sayfa Kenar Boşluğu Tipluklarının su işareti konumunu nasıl etkilediğini ayarlayın:

```java
import com.groupdocs.watermark.contents.PdfPageMarginType;

// Get the content of the loaded PDF and set the page margin type to BleedBox.
PdfContent pdfContent = watermarker.getContent(PdfContent.class);
pdfContent.setPageMarginType(PdfPageMarginType.BleedBox);

watermark.setConsiderParentMargins(true);
```

##### Su İşaretini Ekle ve Belgeyi Kaydet
Su işaretini uygulayın ve belgenizi kaydedin:

```java
// Add the configured watermark to the PDF document.
watermarker.add(watermark);

// Save the watermarked PDF to the specified output directory. Replace 'YOUR_OUTPUT_DIRECTORY' with your path.
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_document_pdf.pdf");

// Close the Watermarker resource to release any associated system resources.
watermarker.close();
```

## Sorun Giderme İpuçları
- Uygulamanızdan tüm dosya yollarının doğru ve erişilebilir olduğundan emin olun.  
- İstenen yazı tipinin (ör. Arial) sistemde yüklü olduğundan emin olun; aksi takdirde mevcut bir yazı tipi seçin.  
- Büyük PDF'lerde bellek sorunlarıyla karşılaşırsanız, belgeyi daha küçük partilerde işleyin veya JVM yığın boyutunu artırın.

## Pr Koruması** – Gizli dosyin.  
2. **Markalaşma** – Şirket adı veya logosunulere ekleyin.  
3. **Sürüm Kontrolü**aretleriyle son sürümlerden ayırın.  
4. **Hukuki Belgeler** – Sözleşme ve anlaşmaların özgünlüğünü pekiştirin.  
5. **Eğitim Materyalleri** – Kurs PDF'lerinin izinsiz dağıtımını önleyin.

## Performans Düşünceleri
- `Watermarker` örneklerini kaynakları serbest bırakmak için hemen kapatın.  
- Çok büyük PDF'lerde, tüm dosyayı bir kerede yük- Birden fazla su iş.

## Sonuç
**GroupDocs.Watermark for Java** ile **PDF'ye su işareti ekleme** uygulaması basittir ve belge yönetim iş akışınızı geliştirir. Bu kılavuzu izleyerek, sayfa kenar boşlukları ve stil tercihlerini göz önünde bulundurarak metin su işaretleri oluşturmayı, yapılandırmayı ve uygulamayı öğrendiniz.

**Sonraki Adımlar**
- Logolar veya mühürler belge işleme hattının parçası olarak otomatikleştirin.  

## Sıkça Sorulan Sorular

**S: Bu kütüphaneyi görüntülere de su işareti eklemek için kullanabilir miyim?**  
C: Evet, GroupDocs.Watermark, PNG ve JPEG gibi yaygın görüntü türleri de dahil olmak üzere geniş bir dosya formatıferde birden fazla su işaretiveya `ImageWatermark`) nesnesi oluşturup aynı `Watermarker` örneğine sırasıyla ekleyebilirsiniz.

**S: PDF'de farklı sayfa boyutlarıyla nasıl başa çıkabilirim?**  
C: GroupDocs.Watermark, su işaretini yerleştirilen sayfanın boyutlarına otomatik olarak uyar, bu yüzden boyut sunucuda mevcut değilse ne olur?**  
C: Yazı tipi dosyasının ana makinede kurulu olduğundan emin olun veya `Font` nesnesi oluştururken `.ttf` veya `.otf` dosyasının tam yolunu vererek özel bir yazı tipi gömün.

**S: Kütüphane şifre korum`'ı başlatırken belge şifresini `Pdf:** 2026-01-31  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs