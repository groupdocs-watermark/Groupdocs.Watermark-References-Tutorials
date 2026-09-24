---
date: '2026-03-27'
description: GroupDocs.Watermark for Java kullanarak Excel dosyalarına nasıl filigran
  ekleyeceğinizi öğrenin. Bu kılavuz, kurulum, kod ve elektronik tablo filigranlaması
  için en iyi uygulamaları adım adım anlatır.
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: GroupDocs.Watermark Java kullanarak Excel'e filigran ekleyin
type: docs
url: /tr/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java kullanarak Excel'e filigran ekleme

Excel dosyalarınıza filigran eklemek bir oyun değiştirici olabilir—hassas verileri korumanız, raporlarınıza marka eklemeniz veya sadece profesyonel bir dokunuş katmanız gerektiğinde. Bu öğreticide GroupDocs.Watermark for Java kullanarak **excel'e nasıl filigran eklenir** elektronik tablolarını öğrenecek, net açıklamalar, gerçek dünya kullanım örnekleri ve yaygın hatalardan kaçınma ipuçları bulacaksınız.

## Hızlı Yanıtlar
- **Hangi kütüphane gerekiyor?** GroupDocs.Watermark for Java (en son sürüm).  
- **Hangi Excel formatları destekleniyor?** .xlsx ve .xls dosyaları (şifrelenmemiş).  
- **Görüntü filigranları ekleyebilir miyim?** Evet – SDK hem metin hem de görüntü filigranlarını destekler.  
- **Üretim için lisansa ihtiyacım var mı?** Deneme dışı dağıtımlar için ticari lisans gereklidir.  
- **Uygulama ne kadar sürer?** Temel bir metin filigranı için yaklaşık 10‑15 dakika.

## **excel'e filigran ekleme** nedir?
Excel çalışma kitabına filigran eklemek, her çalışma sayfasına veya gömülü belgeye görünür (veya yarı şeffaf) bir metin veya görüntü damgası eklemek anlamına gelir. Bu, sahipliğinizi göstermenize, gizliliği belirtmenize veya tüm dosya boyunca markanızı güçlendirmenize yardımcı olur.

## Neden GroupDocs.Watermark for Java kullanmalı?
GroupDocs.Watermark, Office Open XML yapılarıyla uğraşmanın karmaşıklığını soyutlayan yüksek seviyeli bir API sunar. Şunları yapmanızı sağlar:

- Tek bir çağrıyla birden fazla çalışma sayfasına filigran uygulama.  
- Gömülü ekleri (ör. gömülü PDF'ler) otomatik olarak işleme.  
- Orijinal biçimlendirme ve formülleri koruma.  
- Hem metin hem de görüntü filigranlarıyla çalışma (ör. **java ile görüntü filigranı ekleme**).

## Önkoşullar

- **Java Geliştirme Ortamı** – Java 8 veya üzeri (JDK).  
- **GroupDocs.Watermark for Java SDK** – en son sürümü [buradan](https://releases.groupdocs.com/watermark/java/) indirin.  
- **IDE** – IntelliJ IDEA, Eclipse veya herhangi bir Java uyumlu editör.  
- **Örnek elektronik tablo** – korumak istediğiniz bir .xlsx dosyası.

SDK'yı projenize Maven, Gradle aracılığıyla veya JAR dosyalarını sınıf yoluna manuel olarak ekleyerek dahil edebilirsiniz.

## Paketleri İçe Aktar

Bu içe aktarmalar, temel filigran sınıflarına, elektronik tablo işleme ve yazı tipi yardımcı programlarına erişim sağlar.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## **elektronik tabloyu filigranlama** – Adım‑Adım Kılavuz

Aşağıda, Java ile **elektronik tabloyu nasıl filigranlayacağınızı** gösteren pratik, numaralı bir rehber bulacaksınız. Her adım kısa bir açıklama ve ardından orijinal kod bloğunu (değiştirilmemiş) içerir.

### Adım 1: Filigran Nesnenizi Oluşturun  
**Neden?** Bu nesne, uygulayacağınız damganın görsel görünümünü tanımlar.

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Adım 2: Elektronik Tabloyu Yükleyin  
**Neden?** Açma işlemi SDK'ya düzenleme için bir tutamaç sağlar.

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### Adım 3: Elektronik Tablo İçeriğine ve Çalışma Sayfalarına Erişin  
**Neden?** Excel dosyaları birçok sayfa içerebilir; her birini dolaşmanız gerekir.

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### Adım 4: Her Çalışma Sayfasındaki Ekleri Döngüyle İşleyin  
**Neden?** Bazı çalışma sayfaları diğer belgeleri (ör. PDF'ler) gömer. Bunları işlemek, dosyanın tamamında tutarlı bir filigran sağlar.

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### Adım 5: Her Eklenmiş Belgeye Filigran Ekleyin  
**Neden?** Her gömülü dosyada aynı “Gizli” damgasını istiyorsunuz.

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### Adım 6: Tüm Değişiklikleri Kaydedin  
**Neden?** Değişiklikleri yeni bir çalışma kitabına kalıcı olarak kaydetmek.

```java
watermarker.save("your-output-file.xlsx");
```

### Adım 7: Kaynakları Kapatın  
**Neden?** Kaynakları serbest bırakmak, özellikle büyük çalışma kitapları işlenirken bellek sızıntılarını önler.

```java
watermarker.close();
```

## Hepsini Bir Araya Getirme: Tam Örnek

Aşağıdaki sınıf, tüm adımları tek bir çalıştırılabilir programda birleştirir. **Kod bloğunu değiştirmeyin** – orijinal örnekle aynı kalır.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## Yaygın Sorunlar ve Çözümler

| Sorun | Neden Oluşur | Çözüm |
|-------|----------------|-----|
| **Şifreli çalışma kitabı atlanıyor** | SDK, şifreli dosyaları şifre olmadan okuyamaz. | Dosyayı önce şifre çözün veya şifreyi `SpreadsheetLoadOptions.setPassword("pwd")` ile sağlayın. |
| **Filigran bazı sayfalarda görünmüyor** | Sayfa, çizim nesnelerini gizleyen özel bir görünüm veya korumaya sahip olabilir. | Filigranı eklemeden önce sayfa korumasını devre dışı bırakın, ardından gerekirse yeniden uygulayın. |
| **Büyük dosyalarda performans yavaşlaması** | Tüm çalışma kitabını belleğe yüklemek yoğun olabilir. | Çalışma sayfalarını partiler halinde işleyin veya JVM yığın boyutunu (`-Xmx2g`) artırın. |
| **Görüntü filigranı bozulmuş görünüyor** | Yanlış ölçekleme ayarları. | En-boy oranını korumak için `ImageWatermark`'ı açık genişlik/yükseklik parametreleriyle kullanın. |

## Sıkça Sorulan Sorular

**S: Metin yerine bir görüntü filigranı ekleyebilir miyim?**  
C: Evet. SDK'dan `ImageWatermark` kullanın ve bir `java.awt.Image` örneği geçirin. Bu, **java ile görüntü filigranı ekleme** senaryosunu kapsar.

**S: Filigranın konumunu nasıl kontrol edebilirim?**  
C: `TextWatermark` (veya `ImageWatermark`) sınıfı, konumlandırmayı ve şeffaflığı ince ayarlamak için `setHorizontalAlignment`, `setVerticalAlignment` ve `setOpacity` gibi özellikler sunar.

**S: Tek bir çalıştırmada birden fazla Excel dosyasına filigran eklemek mümkün mü?**  
C: Kesinlikle. Tüm iş akışını, bir dizindeki dosyalar üzerinde yineleyen bir `for` döngüsü içinde sarın ve aynı `TextWatermark` örneğini yeniden kullanın.

**S: Elektronik tablo grafikler içeriyorsa ne olur?**  
C: Grafikler ayrı çizim nesneleri olarak ele alınır; filigran çalışma sayfası tuvaline uygulanır, bu yüzden grafikler etkilenmez ancak yarı şeffaf damga tarafından hâlâ örtülür.

**S: Daha önce eklenmiş bir filigranı kaldırabilir miyim?**  
C: SDK, `watermarker.remove(watermark)` yöntemlerini içerir, ancak orijinal filigran nesnesine bir referans tutmanız veya onu tanımlamak için metin/içerik üzerinden arama yapmanız gerekir.

**Son Güncelleme:** 2026-03-27  
**Test Edilen Sürüm:** GroupDocs.Watermark 23.12 (Java)  
**Yazar:** GroupDocs