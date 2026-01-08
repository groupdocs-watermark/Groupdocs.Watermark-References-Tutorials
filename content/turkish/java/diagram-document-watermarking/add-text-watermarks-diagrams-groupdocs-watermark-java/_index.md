---
date: '2025-12-19'
description: GroupDocs.Watermark for Java ile diyagramlara metin filigranı eklemeyi
  öğrenin. Bu adım adım rehber, kurulum, filigran yazı tipi ayarları ve pratik kullanım
  senaryolarını kapsar.
keywords:
- text watermarks in Java
- add text watermark to diagram
- GroupDocs Watermark for Java setup
title: GroupDocs.Watermark for Java kullanarak diyagramlara metin filigranı ekleme
type: docs
url: /tr/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark for Java kullanarak diyagramlara metin filigranı ekleme

Diyagramlarınızı yetkisiz yeniden kullanımından korumak, birçok geliştirici ve tasarımcı için en önemli önceliktir. Bu öğreticide, güçlü **GroupDocs.Watermark for Java** kütüphanesini kullanarak diyagram dosyalarına **metin filigranı ekleme** yöntemini öğreneceksiniz. Maven kurulumundan özel filigran yazı tipi ayarlarının uygulanmasına kadar her adımı adım adım göstereceğiz, böylece görsel varlıklarınızı hızlı ve güvenilir bir şekilde koruyabilirsiniz.

## Quick Answers
- **Kütüphane ne yapar?** Metin (veya görüntü) filigranlarını 100'den fazla belge ve diyagram formatına gömer.  
- **Hangi anahtar kelimeyi hedeflemeliyim?** *add text watermark* – bu rehber boyunca kullanılmıştır.  
- **Lisans gerekir mi?** Geliştirme için geçici bir deneme lisansı yeterlidir; üretim için tam lisans gereklidir.  
- **Yazı tipini özelleştirebilir miyim?** Evet, filigran yazı tipi ayarlarıyla yazı tipi ailesi, boyutu, rengi ve dönüşünü kontrol edebilirsiniz.  
- **Java‑8 ile uyumlu mu?** Kesinlikle – kütüphane JDK 8 ve üzerini destekler.

## “add text watermark” nedir?
Metin filigranı eklemek, bir belgenin her sayfasına veya şekline yarı saydam bir metin yerleştirerek içeriğin tanımlanabilir kalmasını sağlamak anlamına gelir. Bu teknik, marka oluşturma, telif hakkı koruması ve ortak düzenleme için yaygın olarak kullanılır.

## Neden GroupDocs.Watermark for Java kullanmalı?
- **Geniş format desteği** – Visio, SVG, PDF, Word ve daha birçok formatla çalışır.  
- **İnce ayar kontrolü** – yazı tipi, renk, dönüş, opaklık ve konumlandırmayı ayarlayabilirsiniz.  
- **Basit API** – birkaç satır kod işi halleder, geliştirme süresini tasarruf eder.  
- **Performans‑optimizeli** – kaynakları hızlıca kapattığınızda büyük dosyaları verimli bir şekilde işler.

## Prerequisites
- Makinenizde JDK 8 veya daha yeni bir sürüm yüklü olmalı.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Temel Java bilgisi (sınıflar, nesneler ve Maven).

### Required Libraries and Dependencies
GroupDocs.Watermark kütüphanesini Maven ile çekeceğiz. Depoyu ve bağımlılığı `pom.xml` dosyanıza aşağıdaki gibi ekleyin:

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

Manuel indirmeyi tercih ederseniz, resmi sayfayı ziyaret edin: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) ve talimatları izleyin.

### License Acquisition
Deneme sürümüyle başlamak için geçici bir lisansı deneme portalından alın: [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Herhangi bir filigran işlemi öncesinde lisans dosyasını yükleyin:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Implementation Guide

### Step 1: Load Your Diagram
İlk olarak, `Watermarker`ı kaynak diyagram dosyanıza yönlendirin. `DiagramLoadOptions` nesnesi, kütüphaneye dosyayı bir diyagram formatı olarak işlemesini söyler.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Step 2: Initialize the Text Watermark (with custom **watermark font settings**)
İhtiyacınız olan metni, yazı tipi ailesini, boyutunu ve ek stil ayarlarını belirterek bir `TextWatermark` örneği oluşturun.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

> **Pro ipucu:** `setColor` ve `setRotationAngle` değerlerini marka yönergelerinize göre ayarlayın. `setBackground(false)` çağrısı, filigranın diyagram şekillerinin arkasına değil, üstüne yerleştirilmesini sağlar.

### Step 3: Choose Placement – Background vs. Foreground
GroupDocs, filigranın diyagram şekillerinin arkasında (arka plan) mı yoksa üstünde (ön plan) mı görüneceğine karar vermenizi sağlar. Çoğu marka senaryosu için arka plan konumu en iyisidir.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Step 4: Save the Watermarked Diagram
Son olarak, değiştirilmiş dosyayı diske yazın ve kaynakları serbest bırakın.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Common Issues and Solutions
| Belirti | Muhtemel Neden | Çözüm |
|---------|----------------|-------|
| **Dosya bulunamadı** hatası | `inputFilePath` hatalı veya okuma izinleri eksik | Yolu doğrulayın ve Java işleminin dosyayı okuyabildiğinden emin olun. |
| **Filigran görünmüyor** | Yerleşim `Foreground` olarak ayarlanmış ve renk şeffaf | `Background` yerleşimini kullanın veya zıt bir renk seçin. |
| **Büyük diyagramlarda Out‑of‑memory istisnası** | `Watermarker` kapatılmadığı veya döngüde çok sayıda dosya işlendiği | Her dosyadan sonra `watermarker.close()` çağırın ve toplu işlemeyi düşünün. |
| **Lisans tanınmadı** | Yanlış lisans dosyası yolu veya süresi dolmuş deneme | Yolu tekrar kontrol edin ve geçerli bir lisans dosyası kullanın. |

## Practical Applications
1. **Belge Güvenliği** – Rakiplerin özel akış şemalarını çalmasını önleyin.  
2. **Marka Oluşturma** – Kurumsal adı veya logoyu tüm diyagram sayfalarına gömün.  
3. **İşbirliği İzleme** – Diyagramı kimin düzenlediğini göstermek için kullanıcı baş harflerini filigran olarak ekleyin.  

## Performance Considerations
- Kaydetmeden hemen sonra `Watermarker`ı kapatın, böylece yerel kaynaklar serbest kalır.  
- Filigran metnini öz tutun; çok büyük yazı tipleri işlem süresini artırır.  
- Binlerce dosyayı toplu işleme almadan önce temsilci bir örnek üzerinde test edin.

## Conclusion
Artık **GroupDocs.Watermark for Java** kullanarak diyagram dosyalarına **metin filigranı ekleme** için eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Bu yaklaşım, fikri mülkiyetinizi korurken filigran yazı tipi ayarları ve konumlandırması üzerinde tam kontrol sağlar.

### Next Steps
- Görsel bir marka dokunuşu için görüntü filigranlarını keşfedin.  
- Katmanlı koruma için birden fazla filigranı (metin + görüntü) birleştirin.  
- Basit bir `for` döngüsü ve aynı API çağrılarıyla toplu işleme otomasyonu sağlayın.

## FAQ Section
1. **GroupDocs.Watermark'ı diğer dosya formatları için kullanabilir miyim?**  
   Evet, diyagramların yanı sıra PDF, DOCX, PPTX ve daha fazlasını içeren geniş bir belge türü yelpazesini destekler.  
2. **Ekleyebileceğim filigran sayısında bir sınırlama var mı?**  
   Katı bir sınırlama yok, ancak çok sayıda karmaşık filigran eklemek performansı etkileyebilir.  
3. **Bir diyagramdan filigranı nasıl kaldırırım?**  
   Kütüphane, tespit ve kaldırma API'leri sunar; ayrıntılar için resmi belgelere bakın.  
4. **Metin filigranları tüm sayfalara mı yoksa sadece seçilenlere mi eklenebilir?**  
   `DiagramShapeWatermarkOptions`'ı belirli sayfalara veya şekillere hedefleyecek şekilde yapılandırabilirsiniz.  
5. **Filigran beklediğiniz gibi görünmüyorsa ne yapmalıyım?**  
   Yerleşim ayarlarını, yazı tipi rengi kontrastını doğrulayın ve filigranı ekledikten sonra dosyayı kaydettiğinizden emin olun.

## Frequently Asked Questions

**S: GroupDocs.Watermark en son Java sürümleriyle çalışıyor mu?**  
C: Evet, Java 8'den Java 21'e kadar tam uyumludur.

**S: Metin filigranının opaklığını özelleştirebilir miyim?**  
C: Kesinlikle. `%50` opaklık için `textWatermark.setOpacity(0.5)` kullanın.

**S: Sadece seçili diyagram şekillerine filigran eklemenin bir yolu var mı?**  
C: Şekil ID'leri veya adları sağlayarak `DiagramShapeWatermarkOptions` ile şekilleri filtreleyebilirsiniz.

**S: Şifre korumalı diyagram dosyalarını nasıl yönetirim?**  
C: Şifreyi içeren `DiagramLoadOptions` ile dosyayı yükleyin, ardından filigranı normal şekilde uygulayın.

**S: Ticari kullanım için lisans kısıtlamaları var mı?**  
C: Üretim dağıtımları için ticari lisans gereklidir; deneme lisansları sadece değerlendirme amaçlıdır.

## Resources
- [Dokümantasyon](https://docs.groupdocs.com/watermark/java/)
- [API Referansı](https://reference.groupdocs.com/watermark/java)
- [En Son Sürümü İndir](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)

---

**Son Güncelleme:** 2025-12-19  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs