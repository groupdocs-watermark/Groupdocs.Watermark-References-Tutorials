---
date: '2025-12-29'
description: GroupDocs.Watermark for Java kullanarak e-posta eklerine nasıl filigran
  ekleyeceğinizi öğrenin. Bu kılavuz adım adım talimatlar ve en iyi uygulamaları sunar.
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: GroupDocs.Watermark for Java ile e-posta eklerine filigran ekleyin
type: docs
url: /tr/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# E-posta eklerine su işareti ekleme – GroupDocs.Watermark for Java ile

Günümüz dijital ortamında, hassas bilgileri korumak çok önemlidir—özellikle **e-posta eklerine su işareti eklediğinizde** ekler gelen kutunuzdan çıkmadan önce. İster belge güvenliğini artırmak isteyen bir geliştirici olun, ister her giden dosyayı markalamak isteyen bir işletme, bu öğretici GroupDocs.Watermark for Java'ı kullanarak bir e-posta mesajındaki tüm desteklenen eklerine metin su işareti uygulamanın yolunu gösterir.

## Hızlı Yanıtlar
- **“e-posta eklerine su işareti ekleme” ne işe yarar?** Desteklenen her ek içine görünür veya yarı saydam bir etiket (ör. “Gizli”) ekler, yetkisiz dağıtımı caydırır.  
- **Hangi kütüphane gereklidir?** GroupDocs.Watermark for Java (en son sürüm).  
- **Lisans gerekiyor mu?** Geliştirme için deneme lisansı çalışır; üretim için ticari lisans gerekir.  
- **Birden fazla e-postayı aynı anda işleyebilir miyim?** Evet—adımları *.msg* dosyaları içeren bir klasör üzerinde döngüye alın.  
- **Hangi dosya türleri destekleniyor?** PDF'ler, Word, Excel, PowerPoint, görüntüler ve daha birçokları (resmi belgelere bakın).

## “e-posta eklerine su işareti ekleme” nedir?
E-posta eklerine su işareti eklemek, bir e-posta dosyasını programlı olarak açmak, her eki çıkarmak ve e-posta gönderilmeden veya depolanmadan önce bu belgelere özel bir metin (veya görüntü) damgalamak anlamına gelir. Bu, su işaretinin dosyayla birlikte seyahat etmesini sağlar, gizliliği ve marka kimliğini pekiştirir.

## Neden GroupDocs.Watermark for Java kullanmalı?
- **Geniş format desteği** – PDF'ler, Office dosyaları, görüntüler ve daha fazlası ile çalışır.  
- **Basit API** – birkaç satır kodla su işareti oluşturabilir, uygulayabilir ve kaydedebilirsiniz.  
- **Performansa odaklı** – düşük bellek kullanımı, sunucu tarafı işleme için ideal.  
- **Kurumsal lisanslama** – değerlendirme için deneme, üretim için ücretli lisans.

## Önkoşullar
- Java Development Kit (JDK) yüklü.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Projenize GroupDocs.Watermark for Java eklenmiş (aşağıdaki kurulum adımlarına bakın).

## GroupDocs.Watermark for Java Kurulumu

### Maven Kurulumu
Maven kullanıyorsanız, depo ve bağımlılığı `pom.xml` dosyanıza ekleyin:

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

#### Lisans Alımı
- Ücretsiz deneme için, GroupDocs web sitesine kaydolun ve geçici bir lisans isteyin.  
- Ticari kullanım için tam bir lisans satın alın. Daha fazla bilgi için [satın alma sayfasını](https://purchase.groupdocs.com/temporary-license/) ziyaret edin.

### Temel Başlatma
İhtiyacınız olan temel sınıfları içe aktarın:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## E-posta eklerine su işareti ekleme – Adım Adım Kılavuz

### Adım 1: Metin Su İşareti Oluşturma
İlk olarak, su işareti metnini ve görünümünü tanımlayın.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Adım 2: E-posta Yükleme Seçeneklerini Ayarlama
Yükleyiciyi, GroupDocs'un *.msg* dosyasını okuyabilmesi için yapılandırın.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Adım 3: E-posta Dosyanız için Watermarker'ı Başlatma
`Watermarker`'ı işlemek istediğiniz e-postaya yönlendirin.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Adım 4: E-posta İçeriğini Alın
E-postanın iç yapısını alın, böylece ekleriyle çalışabilirsiniz.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Adım 5: Ekler Üzerinde Döngü
Her eki döngüye alın ve su işareti eklenebilirliğini doğrulayın.

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

### Adım 6‑9: Desteklenen Eklerine Su İşareti Ekleme
Her uygun dosya için, yeni bir `Watermarker` ile açın, su işaretini uygulayın ve değişiklikleri e-postaya geri yazın.

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

### Adım 10: Su İşaretli E-postayı Kaydet
Değiştirilen e-postayı yeni bir dosyaya yazın, böylece orijinali dokunulmaz kalır.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Adım 11: Temizleme
Ana `Watermarker`'ı kapatarak kaynakları serbest bırakın.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Pratik Uygulamalar
1. **Dahili Belge Paylaşımı** – İç dağıtımdan önce her eke şirket markasını veya gizlilik bildirimlerini ekleyin.  
2. **Müşteri İletişimleri** – Sözleşmeleri, teklifleri ve finansal beyanları net bir “Gizli” etiketiyle koruyun.  
3. **E-posta Pazarlama Kampanyaları** – Tanıtım e-postalarına eklenen PDF'lere veya görüntülere ince marka su işaretleri ekleyerek marka hatırlanmasını pekiştirin.

## Performans Hususları
- **Bellek Yönetimi** – Bir seferde bir ek işleyin ve her `Watermarker`'ı hemen kapatın.  
- **Ek Boyutu** – Büyük dosyalar işlem süresini artırır; su işareti eklemeden önce sıkıştırmayı veya boyutu sınırlamayı düşünün.  
- **Toplu İşleme** – Çok sayıda e-posta işlenirken yükü azaltmak için *.msg* dosyalarının bulunduğu bir dizin üzerinde döngü oluşturun.

## Sıkça Sorulan Sorular

**S: Şifreli dosyalara su işareti ekleyebilir miyim?**  
C: Hayır. GroupDocs.Watermark, güvenlik nedeniyle şifreli belgeler üzerinde su işareti eklemeyi desteklemez.

**S: Su işareti için hangi dosya türleri destekleniyor?**  
C: PDF'ler, Word, Excel, PowerPoint, görüntüler (PNG, JPEG, BMP) ve birçok diğer yaygın format. Tam liste için resmi belgeleri inceleyin.

**S: Su işareti görünümünü nasıl özelleştirebilirim?**  
C: `TextWatermark` yapıcı ve özelliklerini kullanarak yazı tipi ailesi, boyut, renk, opaklık, dönüş ve konumu değiştirebilirsiniz.

**S: Birden fazla e-postanın toplu işlenmesi mümkün mü?**  
C: Evet. Adımları *.msg* dosyalarının bulunduğu bir klasör üzerinde dönen bir `for` döngüsü içinde sarın ve aynı mantığı her birine uygulayın.

**S: Su işaretim görünmüyor—ne kontrol etmeliyim?**  
C: Ek dosya türünün desteklendiğini doğrulayın, su işareti boyutunun sayfa boyutlarına uyduğundan emin olun ve belgenin şifre korumalı olmadığını kontrol edin.

## Kaynaklar
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

---

**Son Güncelleme:** 2025-12-29  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  

---