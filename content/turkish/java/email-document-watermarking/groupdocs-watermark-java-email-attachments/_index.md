---
date: '2026-04-07'
description: GroupDocs.Watermark for Java kullanarak e-posta ekleri için metin filigranı
  oluşturmayı öğrenin, e-posta eklerini güvence altına alarak gizli verileri koruyun.
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: GroupDocs Java ile E-posta Eklerine Metin Filigranı Oluştur
type: docs
url: /tr/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# E-posta Eklerine GroupDocs.Watermark for Java Kullanarak Filigran Ekleme

Bu öğreticide **metin filigranı** nesneleri oluşturacak ve bunları bir e-posta mesajındaki her desteklenen eke uygulayacaksınız. Filigran eklemek, **e-posta eklerini güvence altına almanın**, gizliliği işaretlemenin ve marka kimliğini güçlendirmenin etkili bir yoludur — sadece birkaç satır Java kodu ile.

## Giriş

E-posta ile taşınan hassas bilgileri korumak her zamankinden daha önemli. İster dahili raporları etiketlemek, ister yasal sözleşmeleri işaretlemek, ya da sadece pazarlama varlıklarını markalamak isteyin, bir metin filigranı hafif, müdahale tespit edilebilir bir koruma katmanı sağlar. Bu kılavuz, **GroupDocs.Watermark for Java** kullanarak bir Outlook `.msg` dosyasındaki her eke özel bir filigran ekleme sürecini adım adım gösterir.

### Öğrenecekleriniz
- Özel yazı tipleri ve renklerle **metin filigranı** nesneleri **oluşturma**.  
- Java e-posta işleme iş akışına filigran eklemeyi adım adım **entegrasyon**.  
- Büyük eklerle çalışırken performansı **optimize etme** ipuçları.  
- Filigranlı e-posta eklerinin değer kattığı gerçek dünya senaryoları.

İlerlemeye başlamadan önce ihtiyacınız olan her şeyin mevcut olduğunu doğrulayalım.

## Hızlı Yanıtlar
- **“Metin filigranı oluşturma” ne anlama geliyor?** Görünür metni, yazı tipini, boyutunu ve stilini tanımlayan bir `TextWatermark` nesnesi örneklemesi demektir.  
- **Şifreli ekleri filigranlayabilir miyim?** Hayır – güvenlik nedenleriyle GroupDocs.Watermark şifreli dosyaları desteklemez.  
- **Hangi dosya türleri destekleniyor?** PDF, Word, Excel, PowerPoint, görüntüler ve daha fazlası – tam liste için resmi dokümantasyona bakın.  
- **Lisans gerekiyor mu?** Geliştirme için bir deneme lisansı yeterlidir; üretim kullanımı için ticari lisans gereklidir.  
- **İşlem ne kadar hızlı?** Tipik bir 2 MB ek, modern donanımda bir saniyeden az sürede filigranlanır.

## Önkoşullar

- **Java Development Kit (JDK)** – sürüm 8 veya üzeri.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **GroupDocs.Watermark for Java** projenize eklenmiş (aşağıdaki kurulum adımlarına bakın).  
- Koruma altına almak istediğiniz ekleri içeren bir e-posta dosyasına (`.msg`, `.eml` vb.) erişim.

## GroupDocs.Watermark for Java Kurulumu

### Maven Kurulumu

Bağımlılıkları Maven ile yönetiyorsanız, `pom.xml` dosyanıza aşağıdaki depo ve bağımlılığı ekleyin:

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

Alternatif olarak, resmi siteden en son JAR dosyasını indirin:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### Lisans Edinme
- **Deneme:** GroupDocs web sitesine kaydolun ve geçici bir lisans isteyin.  
- **Ticari:** Tam lisansı buradan satın alın: [purchase page](https://purchase.groupdocs.com/temporary-license/).

### Temel Başlatma

Java kaynak dosyanıza ihtiyacınız olan temel sınıfları içe aktarın:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Metin Filigranı Nedir?

Bir **metin filigranı**, bir belgenin her sayfasının üstüne yarı saydam bir metin parçası olarak işlenir. GroupDocs.Watermark ile yazı tipi, boyut, renk, dönüş ve opaklık gibi özellikleri kontrol edebilir, orijinal içeriğe doğal bir şekilde karışan bir marka veya gizlilik bildirimi oluşturabilirsiniz.

## E-posta Ekleri İçin GroupDocs.Watermark Neden Kullanılmalı?

- **E-posta eklerini güvence altına al** ve gizli olarak işaretle.  
- **Marka tutarlılığını** tüm giden belgelerde koru.  
- **Toplu işleme** sayesinde bir döngüyle birden çok e-postayı işleyerek zaman kazanın ve manuel hataları azaltın.  
- **Çapraz format desteği** – aynı kod PDF, Word dosyaları, görüntüler ve daha fazlası için çalışır.

## Uygulama Rehberi

Kodun arkasındaki *neden*i açıklayarak her adımı sizinle birlikte inceleyeceğiz, böylece kendi projelerinize kolayca uyarlayabilirsiniz.

### Adım 1: Metin Filigranı Oluşturma

İlk olarak, göstermek istediğiniz metin ve istediğiniz yazı tipi ayarlarıyla bir `TextWatermark` örneği oluşturun.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **Pro tip:** Kurumsal stil rehberinize uygun olması için yazı tipi boyutunu veya rengini ayarlayın. Daha hafif bir etki isterseniz `watermark.setOpacity(0.5)` ile opaklığı belirleyebilirsiniz.

### Adım 2: Email Yükleme Seçeneklerini Ayarlama

`EmailLoadOptions`, kütüphanenin gelen e-posta dosyasını nasıl yorumlayacağını belirler.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Adım 3: E-posta Dosyanız İçin Watermarker'ı Başlatma

`Watermarker` yapıcısını işlemek istediğiniz `.msg` (veya `.eml`) dosyasına yönlendirin.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Adım 4: E-posta İçeriğini Almak

E-postanın iç yapısını çıkarın, böylece ekleri üzerinde döngü kurabilirsiniz.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Adım 5: Ekler Üzerinde Döngü

Her ek için dosya tipinin desteklenip desteklenmediğini ve şifreli olup olmadığını doğrularız.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Adım 6‑9: Desteklenen Eklerine Filigran Ekleme

Koşullu blok içinde, ek için ayrı bir `Watermarker` oluşturur, filigranı uygular ve ardından değiştirilmiş içeriği e-postaya geri koyarız.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Adım 10: Filigranlı E-postayı Kaydetme

Orijinali bozulmasın diye güncellenmiş e-postayı yeni bir dosyaya yazın.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Adım 11: Temizleme

Bellek sızıntılarını önlemek için her zaman kaynakları serbest bırakın.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Yaygın Sorunlar ve Çözümler

| Sorun | Sebep | Çözüm |
|-------|--------|-----|
| **Filigran görünmüyor** | Opaklık çok düşük ayarlanmış veya yazı rengi arka planla aynı. | Opaklığı artırın (`watermark.setOpacity(0.7)`) veya kontrast bir renk seçin. |
| **Desteklenmeyen ek tipi** | Dosya formatı GroupDocs destek listesinde yok. | Dosyayı önce desteklenen bir formata (ör. PDF) dönüştürün veya bir log mesajı ile atlayın. |
| **Büyük PDF'lerde OutOfMemoryError** | Çok büyük eklerin yüklenmesi heap'i aşırı tüketiyor. | JVM heap'ini artırın (`-Xmx2g`) veya ekleri daha küçük partilerde işleyin. |

## Sıkça Sorulan Sorular

**S: Şifreli dosyalara filigran ekleyebilir miyim?**  
C: Hayır, GroupDocs.Watermark güvenlik kısıtlamaları nedeniyle şifreli dosyalara filigran eklemeyi desteklemez.

**S: Hangi dosya tipleri filigranlamayı destekliyor?**  
C: PDF, Word belgeleri, Excel elektronik tabloları, PowerPoint sunumları ve yaygın görüntü formatları desteklenir. Tam liste için resmi dokümantasyona bakın.

**S: Filigranımın görünümünü nasıl özelleştirebilirim?**  
C: `Font` sınıfını kullanarak boyut, stil ve rengi ayarlayın; `TextWatermark` örneğinde `setOpacity` ve `setRotationAngle` gibi metodları çağırın.

**S: Birden fazla e-postayı toplu işleme yapabilir miyim?**  
C: Evet. Aynı `TextWatermark` örneğini yeniden kullanarak bir dizindeki dosyalar üzerinde döngü kurabilirsiniz.

**S: Filigran son sayfada kesiliyor—neyin yanlış?**  
C: Filigranın sayfa kenar boşlukları içinde kaldığından emin olun. Konumunu `watermark.setHorizontalAlignment` ve `watermark.setVerticalAlignment` ile ayarlayabilirsiniz.

## Pratik Uygulamalar

1. **Dahili Doküman Paylaşımı:** Raporları organizasyon içinde dağıtmadan önce şirket markasını veya gizlilik uyarısını ekleyin.  
2. **Müşteri İletişimi:** Sözleşme ve teklifler üzerine “Gizli” etiketi ekleyerek alıcıları veri işleme politikalarına hatırlatın.  
3. **E-posta Pazarlama:** Bültenlere eklenen tanıtım PDF'lerine ince bir marka filigranı ekleyerek tasarımı bozmadan marka hatırlatmasını güçlendirin.

## Performans Düşünceleri

- **Bellek Yönetimi:** Her `attachedWatermarker`ı (Adım 9'da gösterildiği gibi) hemen kapatarak yerel kaynakları serbest bırakın.  
- **Dosya Boyutu Sınırları:** 10 MB'den büyük ekler için dosyayı akış olarak işleyin veya JVM heap boyutunu artırın.  
- **Paralel İşleme:** Java’nın `ExecutorService`'ini kullanarak birden çok e-postayı aynı anda filigranlayabilirsiniz; ancak CPU kullanımını izleyerek kaynak çatışmalarını önleyin.

## Sonuç

GroupDocs.Watermark for Java kullanarak bir e-posta dosyasındaki her desteklenen eke **metin filigranı** nesneleri oluşturma ve uygulama konusunda eksiksiz, üretim‑hazır bir tarif elde ettiniz. Bu iş akışını mevcut e-posta işleme hattınıza entegre ederek belge güvenliğini artırabilir, marka tutarlılığını sağlayabilir ve minimum ek yükle uyumluluğu sürdürebilirsiniz.

Bir sonraki adımı atmaya hazır mısınız? `.msg` dosyalarının bulunduğu bir klasörü işlemek için kodu genişletin ya da görüntü ve QR kodu gibi ek filigran türlerini keşfedin.

---

**Last Updated:** 2026-04-07  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Resources**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)