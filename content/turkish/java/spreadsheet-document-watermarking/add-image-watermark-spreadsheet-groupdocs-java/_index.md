---
date: '2026-03-20'
description: GroupDocs.Watermark Java SDK'sını kullanarak bir Excel elektronik tablosuna
  resim filigranı eklemeyi öğrenin; marka oluşturma ve belge güvenliği için mükemmeldir.
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'Su İşareti Ekleme: GroupDocs.Watermark Java SDK Kullanarak Excel Çalışma Sayfasına
  Görüntü Su İşareti Ekleme'
type: docs
url: /tr/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# GroupDocs.Watermark Java SDK Kullanarak Excel Çalışma Sayfasına Filigran Ekleme

Excel dosyalarınızı yetkisiz dağıtımdan korumak ya da sadece marka kimliğini güçlendirmek, dosya nasıl görüntülense de görünür kalan bir görsel işaret ekleyerek sağlanabilir. Bu öğreticide **filigran ekleme** — özellikle bir resim filigranı — Excel çalışma sayfasının üstbilgi veya altbilgiğine **GroupDocs.Watermark Java SDK** ile nasıl ekleyeceğinizi öğreneceksiniz. Rehberin sonunda, hücre verilerini değiştirmeden bir logo, gizlilik rozeti veya herhangi bir özel resmi doğrudan çalışma kitabınıza gömebileceksiniz.

## Hızlı Yanıtlar
- **“filigran ekleme” ne anlama geliyor?** Her yazdırılan sayfada veya üstbilgi/altbilgi gibi belirli bölümlerde görünen bir resim (veya metin) kaplaması eklemek.  
- **Java’da bunu hangi kütüphane destekliyor?** `GroupDocs.Watermark` Java SDK (en son sürüm).  
- **Lisans gerekiyor mu?** Geliştirme için ücretsiz deneme çalışır; üretim için ticari bir lisans gereklidir.  
- **Üstbilgiye bir logo ekleyebilir miyim?** Evet – görüntü filigranını kullanın ve üstbilgi seçeneğini ayarlayın (`add logo to header`).  
- **Birden fazla sayfayı aynı anda işlemek mümkün mü?** Çalışma sayfası indeksleri üzerinden döngü yaparak aynı filigranı her sayfaya uygulayın.

## Önkoşullar

İlerlemek için aşağıdakilere sahip olduğunuzdan emin olun:

- **GroupDocs.Watermark for Java SDK** (sürüm 24.11 veya daha yeni).  
- **Java Development Kit (JDK)** 8 veya üzeri.  
- Java ve Excel dosya yapıları hakkında temel bir aşinalık.

## GroupDocs.Watermark for Java SDK’yı Kurma

İlk olarak, SDK’nın sınıf yolunuzda bulunması için gerekli Maven bağımlılıklarını ekleyin.

### Maven Yapılandırması

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

Maven kullanmak istemiyorsanız, resmi sürüm sayfasından en son JAR dosyasını alın: [GroupDocs sürümleri](https://releases.groupdocs.com/watermark/java/).

**Lisans Alımı**  
- Tüm özellikleri değerlendirmek için ücretsiz bir deneme veya geçici bir lisans anahtarı alın.  
- Ticari dağıtımlar için tam bir lisans satın alın.

### Başlatma ve Kurulum

`Watermarker` örneği oluşturun; bu örnek Excel dosyasını yükleyecek ve tüm filigran işlemleri için giriş noktası olacaktır.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## Bir Çalışma Sayfasının Üstbilgi/Altbilgisine Filigran Ekleme

Aşağıda, **java add image watermark** işlevselliğini gösteren adım adım süreç ve ayrıca **add logo to header** nasıl yapılır gösterilmektedir.

### Adım 1: Yükleme Seçeneklerini Yapılandırma

`Watermarker`'ı yeniden örnekleyerek ve yükleme seçeneklerini tanımlayarak başlarız. Bu, SDK’nın çalışma kitabını doğru şekilde okumasını sağlar.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### Adım 2: Görüntü Filigranı Oluşturma ve Yapılandırma

Eklemek istediğiniz görüntüyü (ör. bir logo veya “CONFIDENTIAL” rozeti) işaret eden bir `ImageWatermark` nesnesi oluşturun. Üstbilgi/altbilgi alanına güzel oturması için hizalama ve ölçeklendirmesini ayarlayın.

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### Adım 3: Üstbilgi/Altbilgi Seçeneklerini Yapılandırma

SDK’ya hangi çalışma sayfasının ve hangi bölümün (üstbilgi veya altbilgi) filigranı alacağını söyleyin. Burada **add logo to header** yapabilir veya altbilgiyi seçebilirsiniz.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### Adım 4: Filigranı Ekleme

Şimdi hazırlanan görüntü filigranını seçilen üstbilgi/altbilgi konumuna ekleyin.

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### Adım 5: Kaydetme ve Kapatma

Orijinal çalışma kitabı dokunulmaz kalması için değişiklikleri yeni bir dosyaya kaydedin, ardından kaynakları serbest bırakın.

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### Sorun Giderme İpuçları
- Görüntü yolunu iki kez kontrol edin; yanlış bir yol `FileNotFoundException` hatası verir.  
- Çalışma sayfası indeksleri 0’dan başlar; ayarladığınız indeksin gerçekten var olduğundan emin olun.  
- Filigran bozuk görünüyorsa, `setScaleFactor` değerini ayarlayın veya `SizingType`'ı `StretchToParentDimensions` olarak değiştirin.

## Neden GroupDocs.Watermark Java SDK Kullanmalı?

- **Çapraz format desteği** – Excel, Word, PowerPoint, PDF'ler ve görüntülerle çalışır.  
- **Kayıpsız düzenleme** – orijinal hücre verileri dokunulmaz kalır.  
- **Performans‑optimize** – büyük çalışma kitapları ve toplu işleme için uygundur.  

## Pratik Kullanım Durumları

| Senaryo | Filigranın nasıl yardımcı olduğu |
|----------|---------------------------------|
| **Gizli raporlar** | Her yazdırılan sayfaya bir “CONFIDENTIAL” resmi ekleyin. |
| **Marka güçlendirme** | Faturaların üstbilgisine şirket logonuzu yerleştirin. |
| **Sürüm takibi** | Otomatik güncellenen bir sürüm‑numarası rozeti gömün. |
| **Yasal uyumluluk** | Düzenlenmiş elektronik tabloları bir uyumluluk mührüyle işaretleyin. |

## Performans Düşünceleri

- **Bellek kullanımı** – Çok büyük elektronik tabloları işlerken JVM yığınını izleyin.  
- **Toplu işleme** – Bellek ayak izini düşük tutmak için dosyaları gruplar halinde işleyin.  
- **Nesneleri yeniden kullanma** – Birden fazla dosya için tek bir `Watermarker` örneğini yeniden kullanmak, ek yükü azaltır.

## Sıkça Sorulan Sorular

**S: Tek bir belgeye birden fazla filigran ekleyebilir miyim?**  
C: Evet, ek `ImageWatermark` örnekleri oluşturarak ve her birini `watermarker.add()` çağırmadan önce yapılandırarak.

**S: Bir çalışma sayfasındaki mevcut bir filigranı nasıl kaldırırım?**  
C: Şu anda GroupDocs.Watermark filigran eklemeye odaklanmıştır. Birini kaldırmak için, filigran olmadan çalışma kitabını yeniden oluşturmanız veya filigran çıkarımını destekleyen bir araç kullanmanız gerekir.

**S: Filigranlar için hangi görüntü formatları destekleniyor?**  
C: PNG ve JPEG gibi yaygın formatlar desteklenir, ancak tam uyumlu format listesi için [GroupDocs dokümantasyonu](https://docs.groupdocs.com/watermark/java/) kontrol edin.

**S: Şifre korumalı çalışma sayfalarına filigran eklemek mümkün mü?**  
C: Evet, dosyayı açarken gerekli şifreyi sağladığınız sürece.

**S: Bir belgede tüm çalışma sayfalarına nasıl filigran uygularım?**  
C: Her bir çalışma sayfası indeksinde döngü yaparak filigran adımlarını tekrarlayın ve her yineleme için `headerFooterOptions.setWorksheetIndex(i)` ayarlayın.

## Sonuç

Artık **java add excel watermark**—özellikle bir görüntü filigranı—için **GroupDocs.Watermark Java SDK** kullanarak eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Bu yaklaşım, Excel dosyalarınızın üstbilgi veya altbilgisine doğrudan marka, gizlilik uyarısı veya herhangi bir görsel işaret eklerken alttaki verileri dokunulmaz tutar. Diğer filigran türlerini (metin, şekil) keşfetmekten ve daha zengin belge koruması için birleştirmekten çekinmeyin.

---

**Son Güncelleme:** 2026-03-20  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs