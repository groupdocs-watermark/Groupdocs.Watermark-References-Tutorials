---
date: '2026-02-16'
description: GroupDocs.Watermark for Java kullanarak belirli bir diyagram sayfasına
  nasıl filigran ekleyeceğinizi, Java’da görüntü filigranı eklemeyi ve dosyalarınızı
  korumayı öğrenin.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: GroupDocs.Watermark for Java ile Belirli Diyagram Sayfasına Filigran Ekle
type: docs
url: /tr/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

 |
| License error on production | Using trial license beyond its expiration | Apply a full license file via `License.setLicense("path/to/license.json")`. |

We translate header row and content rows.

Make sure to keep backticks.

Now produce final answer.# GroupDocs.Watermark for Java ile Belirli Diyagram Sayfasına Filigran Ekleme

Diyagramlarınızı korumak çok önemlidir, özellikle fikri mülkiyet güvenliği veya marka atıfı için **belirli diyagram sayfasına filigran** eklemeniz gerektiğinde. Bu öğreticide, **GroupDocs.Watermark for Java** kullanarak bir diyagram dosyasının seçilen sayfalarına hem metin hem de görüntü filigranları eklemeyi adım adım öğreneceksiniz. Sonunda, diyagramlarınızı güvence altına almaya ve her filigranın tam olarak nerede görüneceğini kontrol etmeye hazır olacaksınız.

## Hızlı Yanıtlar
- **Birincil amaç nedir?** Seçili diyagram sayfalarına filigran eklemek.  
- **Hangi kütüphane gereklidir?** GroupDocs.Watermark for Java (Maven veya doğrudan indirme).  
- **Java'da bir görüntü filigranı ekleyebilir miyim?** Evet – sayfa‑özel seçeneklerle `ImageWatermark` kullanın.  
- **Lisans gerekir mi?** Test için geçici bir deneme lisansı yeterlidir; üretim için tam lisans gereklidir.  
- **Kaç satır kod?** Tam bir metin + görüntü filigranı iş akışı için 30 satırdan az.

## “watermark specific diagram page” nedir?

**belirli diyagram sayfasına filigran** birden çok sayfalı diyagram (ör. Visio . vsdx) içinde yalnızca seçtiğiniz sayfalara görsel bir işaret—metin veya görüntü—uygulamak anlamına gelir. Bu, tüm belgeyi etkilemeden marka, gizlilik uyarıları veya telif hakkı bildirimleri üzerinde ince ayarlı kontrol sağlar.

## Neden GroupDocs.Watermark for Java Kullanmalı?
- **Tam sayfa kontrolü** – ihtiyacınız olan herhangi bir sayfa indeksine hedefleyin.  
- **Zengin stil** – yazı tipleri, renkler, opaklık, dönüş ve görüntü ölçeklendirme tamamen yapılandırılabilir.  
- **Performans‑optimizeli** – büyük diyagramları verimli bir şekilde işler ve Maven derlemeleriyle sorunsuz entegrasyon sağlar.  
- **Çapraz‑format desteği** – Visio, SVG ve birçok diğer diyagram formatıyla çalışır.

## Önkoşullar
- **GroupDocs.Watermark for Java** kütüphane sürümü 24.11 ve üzeri.  
- Maven veya doğrudan JAR indirme.  
- Temel Java geliştirme ortamı (JDK 8+ önerilir).  

## GroupDocs.Watermark for Java Kurulumu
### Maven groupdocs watermark Kullanımı
Maven aracılığıyla projenize GroupDocs.Watermark eklemek için `pom.xml` dosyanıza aşağıdakini ekleyin:

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
Alternatif olarak, en son sürümü doğrudan [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

#### Lisans Edinimi
Geçici bir lisans indirerek ücretsiz deneme ile başlayın. GroupDocs.Watermark'ı kullanmaya devam etmeyi seçerseniz resmi sitesinde satın alma seçenekleri mevcuttur.

### Temel Başlatma ve Kurulum
Kurulum tamamlandıktan sonra, filigran işlemleri için `Watermarker` sınıfını başlatın:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Uygulama Kılavuzu
### Belirli Bir Sayfaya Metin Filigranı Ekleme
Metin filigranı eklemek için, hedef sayfayı belirtmeden önce onu oluşturup yapılandırın.

#### Metin Filigranı Oluşturma
İçeriği, yazı tipi stili, boyutu vb. özelleştirilebilir özelliklerle metin filigranınızı tanımlayın:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### Filigran İçin Sayfa İndeksini Ayarlama
`DiagramPageWatermarkOptions` kullanarak filigranın hangi diyagram sayfasında gösterileceğini belirleyin:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### Metin Filigranını Ekleme
Yapılandırılmış filigranı diyagrama ekleyin:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### Belirli Bir Sayfaya Görüntü Filigranı Ekleme
`ImageWatermark` nesnesi kullanarak görüntü filigranları için benzer adımları izleyin.

#### Görüntü Filigranı Oluşturma
İstenen filigran görüntüsü yolu ile bir `ImageWatermark` örneği oluşturun:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### Filigran İçin Sayfa İndeksini Ayarlama
Görüntü filigranının hangi sayfada gösterileceğini belirtin:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### Görüntü Filigranını Ekleme
Belirttiğiniz diyagram sayfasına görüntüyü ekleyin:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### Kaydetme ve Kaynakları Kapatma
Değişiklikleri kaydetmeyi ve sızıntıları önlemek için kaynakları kapatmayı unutmayın:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Pratik Uygulamalar
- **Document Security** – Hassas şemalar içeren sayfalara yalnızca gizli filigranlar uygulayın.  
- **Branding** – Kapak sayfasına şirket logonuzu yerleştirirken iç sayfaları temiz bırakın.  
- **Copyright Protection** – Teknik diyagram paketinin son sayfasına telif hakkı bildirimi ekleyin.

## Performans Düşünceleri
- **Memory Management** – Kaydetme sonrası her filigran nesnesini kapatarak yerel kaynakları serbest bırakın.  
- **Image Optimization** – İşlemi hızlı tutmak için uygun boyutta PNG/JPEG dosyaları kullanın.  
- **Batch Processing** – Çok sayıda diyagram işlenirken mümkün olduğunca tek bir `Watermarker` örneğini yeniden kullanın.

## Yaygın Sorunlar ve Çözümler
| Semptom | Muhtemel Neden | Çözüm |
|---------|----------------|-------|
| Filigran görünmüyor | Yanlış `pageIndex` (sıfır‑tabanlı) | İndeksin hedef sayfaya eşleştiğini doğrulayın. |
| Görüntü bozuk görünüyor | Yüksek çözünürlüklü kaynak görüntü | `ImageWatermark` oluşturmadan önce görüntüyü yeniden boyutlandırın. |
| Üretimde lisans hatası | Deneme lisansını süresi dolduktan sonra kullanmak | `License.setLicense("path/to/license.json")` ile tam lisans dosyasını uygulayın. |

## Sıkça Sorulan Sorular

**Q1: Tek bir diyagram sayfasına birden fazla filigran ekleyebilir miyim?**  
A1: Evet, aynı sayfa indeksi için farklı filigran nesneleriyle `watermarker.add()` metodunu çağırmanız yeterlidir.

**Q2: GroupDocs.Watermark for Java hangi dosya formatlarını destekliyor?**  
A2: Çeşitli diyagram ve görüntü formatlarını destekler. Tam liste için [API documentation](https://reference.groupdocs.com/watermark/java) adresine bakın.

**Q3: Deneme sürümünü kullanırken lisans sorunlarını nasıl yönetebilirim?**  
A3: GroupDocs'tan ücretsiz geçici bir lisansla başlayın. Üretim için tüm özellikleri açmak amacıyla tam lisans satın alın.

**Q4: Filigranlar beklenildiği gibi görünmüyorsa yaygın sorun giderme ipuçları nelerdir?**  
A4: Sayfa indeksinin doğru olduğundan emin olun ve görüntü kaynakları için dosya yollarını iki kez kontrol edin. Ayrıca filigran opaklığının 0 olarak ayarlanmadığını doğrulayın.

**Q5: Filigran görünümünü daha da özelleştirebilir miyim?**  
A5: `TextWatermark` veya `ImageWatermark` üzerindeki mevcut yöntemleri kullanarak yazı tipi boyutunu, opaklığı, dönüşü ve konumlandırmayı ayarlayabilirsiniz.

## Kaynaklar
- [GroupDocs.Watermark Belgeleri](https://docs.groupdocs.com/watermark/java/)
- [API Referans Kılavuzu](https://reference.groupdocs.com/watermark/java)
- [Kütüphane İndir](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)
- [Geçici Lisans Bilgileri](https://purchase.groupdocs.com/temporary-license/)

Bu kaynakları keşfederek GroupDocs.Watermark for Java konusundaki bilginizi ve yeteneklerinizi derinleştirin. Mutlu filigranlamalar!

---

**Son Güncelleme:** 2026-02-16  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs