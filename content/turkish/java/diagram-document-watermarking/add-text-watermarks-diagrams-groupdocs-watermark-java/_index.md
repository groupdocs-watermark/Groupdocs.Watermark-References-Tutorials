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

# GroupDocs.Watermark for Java diyagramlarına metin filigranı ekleme

Diyagramlarınızı yetkisiz olarak yeniden kullanmaktan koruyun, birçok geliştirici ve tasarımcı için en önemli parlaklıktır. Bu öğreticide, güçlü **GroupDocs.Watermark for Java** kütüphanesini kullanarak diyagram dosyalarına **metin filigranı ekleme** merkezi bölgeleri. Maven kurulumundan özel filigran yazı tipi çalışmasının performansınına kadar her adım adım adım gösterirz, böylece görsel varlıklarınızı hızlı ve güvenilir bir şekilde geliştirebilirsiniz.

## Hızlı Yanıtlar
- **Kütüphane ne yapar?** Metin (veya görüntü) filigranlarını 100'den fazla belge ve diyagram formatına gömer.
- **Hangi anahtar kelimeyi hedeflemeliyim?** *metin filigranı ekle* – bu rehber boyunca kullanıldı.
- **Lisans gerekir mi?** Geliştirme için geçici bir deneme lisansı yeterlidir; üretim için tam lisans gereklidir.
- **Yazı tipini özelleştirebilir miyim?** Evet, filigran yazı tipi ayarlarıyla yazı tipi ailesi, boyutu, rengi ve dönüşünü kontrol edebilirsiniz.
- **Java‑8 ile uyumlu mu?** kesinlikle – JDK8 ve üzerini bulundurmak.

## “metin filigranı ekle” nedir?
Metin filigranını seçer, bir belgenin her sayfası veya şekline yarı saydam bir metin yerleştirerek içeriğin saklanmasını sağlama anlamına gelir. Bu teknik, marka oluşturma, telif hakkının korunması ve ortak düzenleme için yaygın olarak kullanılır.

## Neden GroupDocs.Watermark for Java kullanılmıyor?
- **Geniş format desteği** – Visio, SVG, PDF, Word ve daha birçok formatla çalışır.
- **İnce ayar kontrolü** – yazı tipi, renk, dönüş, opaklık ve kimlikleri ayarlayabilirsiniz.
- **Basit API** – birkaç satır kod işini halleder, geliştirme tasarrufu sağlar.
- **Performans‑optimizeli** – kaynakları hızlı bir şekilde kapattığınızda büyük dosyaları verimli bir şekilde işler.

## Önkoşullar
- Makinenizde JDK8 veya daha yeni bir sürüm yüklü olmalı.
- IntelliJ IDEA veya Eclipse gibi bir IDE.
- Temel Java bilgisi (sınıflar, nesneler ve Maven).

### Gerekli Kitaplıklar ve Bağımlılıklar
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

### Lisans Edinimi
Deneme sürümüyle başlamak için geçici bir lisansı deneme portalından alın: [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Herhangi bir filigran işlemi öncesinde lisans dosyasını yükleyin:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Uygulama Kılavuzu

### Adım 1: Diyagramınızı Yükleyin
İlk olarak, `Watermarker`ı kaynak diyagramı dosyanıza yönlendirin. `DiagramLoadOptions`ın nesnesi, kütüphaneye ait bir diyagram formatı olarak işlenmesini söylüyor.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Adım 2: Metin Filigranını Başlatın (özel **filigran yazı tipi ayarları** ile)
İhtiyacınız olan metni, yazı tipi ailesini, boyutunu ve ek stil ayarlarını belirterek bir `TextWatermark` örneği oluşturun.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

> **Pro ipucu:** `setColor` ve `setRotationAngle` değerlerini marka yönergelerinize göre ayarlayın. `setBackground(false)` çağrısı, filigranın diyagram şekillerinin arkasına değil, üstüne yerleştirilmesini sağlar.

### Adım 3: Yerleşimi Seçin – Arka Plan mı Ön Plan mı?
GroupDocs, filigranın diyagram şekillerinin arkasında (arka plan) mı yoksa üstünde (ön plan) mı görüneceğine karar vermenizi sağlar. Çoğu marka senaryosu için arka plan konumu en iyisidir.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Adım 4: Filigranlı Diyagramı Kaydedin
Son olarak, değiştirilmiş dosyayı diske yazın ve kaynakları serbest bırakın.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Yaygın Sorunlar ve Çözümler
| Belirti | Muhtemel Neden | Çözüm |
|-----------|-----|------|
| **Dosya hatası** hatası | `inputFilePath` hatalı veya okumaya izinleri eksik | Yolu doğrulayın ve Java depolarının okunabildiğinden emin olun. |
| **Filigran görünmüyor** | Yerleşim `Ön Plan` olarak ayarlanmış ve renk şeffaf | Arka plan yerleşimini kullanın veya bir renk seçin. |
| **Büyük diyagramlarda bellek yetersizliği istisnası** | `Watermarker` kapatılmadığı veya döngüde çok sayıda dosya işlendiği | Onu dosyadan sonra `watermarker.close()` çağırın ve toplu işlemeyi düşünün. |
| **Lisans tanınmadı** | Yanlış lisans dosya yolu veya süresi dolmuş deneme | Yolu tekrar kontrol edin ve geçerli bir lisans dosyasını kullanın. |

## Pratik Uygulamalar
1. **Belge Güvenliği** – Rakiplerin özel akış şemasını çalmasını önleyin.
2. **Marka Oluşturma** – Kurumsal ad veya logoyu tüm diyagram sayfalarına gömün.
3. **İşbirliği İzleme** – Diyagramı kimin düzenlediğini göstermek için kullanıcı baş harflerini filigran olarak ekleyin.

## Performansla İlgili Hususlar
- Kaydetmeden hemen sonra `Watermarker`ı kapatın, böylece yerel kaynaklar serbest kalır.
- Filigran metnii öz tutun; Çok büyük yazı tipi işlem süresini artırır.
- Orantılı olarak görülen toplu işlem yapılmadan önce temsilcinin bir örneği üzerinde test edin.

## Çözüm
Artık **GroupDocs.Watermark for Java** kullanarak diyagram dosyalarına **metin filigranını ekleme** için eksiksiz, üretim‑hazır bir yönteme ilerleme. Bu seçenek, fikri mülkiyetinizi korurken filigran yazı tipi ayarlarını ve kimlikleri üzerinde tam kontrol sağlar.

### Sonraki Adımlar
- Görsel bir marka dokunuşu için görüntü filimlerini evler.
- Katmanlı koruma için birden fazla filigran (metin + görüntü) birleştirin.
- Basit bir konu için ve aynı API çağrılarıyla toplu otomasyonu sağlayın.

## Sıkça Sorulan Sorular

**S: GroupDocs.Watermark en son Java'da çalıştırılarak çalışıyor mu?**
C: Evet, Java8'den Java21'e kadar tam uyumludur.

**S: Metin filigranının opaklığını özelleştirebilir miyim?**
C: elbette. `%50` opaklık için `textWatermark.setOpacity(0.5)` kullanın.

**S: Sadece diyagram şekillerine filigran eklemenin bir yolu var mı?**
C: Şekil ID'leri veya reklamları sağlayarak `DiagramShapeWatermarkOptions` ile seçenekleri filtreleyebilirsiniz.

**S: Şifreli diyagram düzeni nasıl yönetilir?**
C: Şifreyi içeren `DiagramLoadOptions` ile tanışın, ardından filigranı normal şekilde etkinleştirin.

**S: Ticari kullanım için lisans kısıtlamaları var mı?**
C: Üretim sunumları için ticari lisans gereklidir; Deneme lisansları sadece değerlendirme amaçlıdır.

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/watermark/java/)
- [API Referansı](https://reference.groupdocs.com/watermark/java)
- [En Son Sürümü İndir](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)

---

**Son Güncelleme:** 2025-12-19
**Edilen Sürümünü Test Edin:** Java için GroupDocs.Watermark 24.11
**Yazar:** GroupDocs