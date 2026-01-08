---
date: '2025-12-17'
description: GroupDocs.Watermark for Java kullanarak belirli bir diyagram sayfasına
  nasıl filigran ekleyeceğinizi öğrenin, diyagrama filigran ekleyin ve Java’da görüntü
  filigranı ekleyin. Fikri mülkiyetinizi korumak için adım adım rehber.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: GroupDocs.Watermark for Java ile Belirli Diyagram Sayfasına Filigran Ekleme
type: docs
url: /tr/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# GroupDocs.Watermark for Java Kullanarak Belirli Diyagram Sayfasına Filigran Ekleme

Diyagramlarınızı korumak çok önemlidir, özellikle fikri mülkiyeti korumak veya doğru atıfı sağlamak söz konusu olduğunda. Bu öğreticide GroupDocs.Watermark for Java ile **belirli diyagram sayfasına nasıl filigran eklenir** öğreneceksiniz; ister **diyagrama filigran ekle** metin olarak, ister **add image watermark java**‑stilindeki logolarla. Bu rehberin sonunda şunları yapabileceksiniz:

- Seçilen diyagram sayfalarına sorunsuz bir şekilde metin filigranları ekleyin.  
- Diyagramların belirlenmiş bölümlerine görüntü filigranları ekleyin.  
- GroupDocs.Watermark kullanırken performansı artırın.

Kodun içine girmeden önce ortamın hazır olduğundan emin olalım.

## Hızlı Yanıtlar
- **“watermark specific diagram page” ne anlama geliyor?** Bu, bir diyagram dosyasının yalnızca seçilen sayfalarına filigran uygulanması ve diğer sayfaların dokunulmaz bırakılması anlamına gelir.  
- **Hangi kütüphane sürümü gereklidir?** GroupDocs.Watermark 24.11 veya daha yeni bir sürüm.  
- **Aynı sayfada hem metin hem de görüntü filigranları kullanabilir miyim?** Evet – her filigran türü için `watermarker.add()` metodunu çağırın.  
- **Geliştirme için lisansa ihtiyacım var mı?** Test için geçici bir deneme lisansı yeterlidir; üretim için tam lisans gereklidir.  
- **Kütüphaneyi eklemenin tek yolu Maven mi?** Hayır – JAR dosyasını doğrudan da indirebilirsiniz (aşağıdaki “Direct Download” bölümüne bakın).

## “watermark specific diagram page” nedir?
Bir **watermark specific diagram page** işlemi, bir diyagram belgesi (ör. Visio *.vsdx*) içinde tek bir sayfayı (veya bir dizi sayfayı) hedef alır ve üzerine bir metin veya görüntü katmanı ekler. Bu, tüm dosyayı değiştirmeden gizli taslaklar, marka yerleştirme veya telif hakkı bildirimleri için faydalıdır.

## Neden GroupDocs.Watermark for Java Kullanmalı?
GroupDocs.Watermark, diyagram formatlarının karmaşıklığını soyutlayan yüksek seviyeli bir API sunar, toplu işleme destek verir ve opaklık, konumlandırma ve sayfa seçimi üzerinde ince ayar kontrolü sağlar. Ayrıca Maven ve standart Java yapı araçlarıyla sorunsuz entegrasyon sunar.

## Önkoşullar
- **GroupDocs.Watermark for Java** kütüphane sürümü 24.11 veya daha yeni bir sürüm yüklü olmalıdır.  
- Maven ile bir geliştirme ortamı (veya JAR'ı manuel olarak ekleme yeteneği).  
- Temel Java bilgisi ve dosya sistemi erişimi.  

## GroupDocs.Watermark for Java Kurulumu

### Maven Kullanarak
Projenize Maven üzerinden GroupDocs.Watermark eklemek için `pom.xml` dosyanıza aşağıdakini ekleyin:

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
Alternatif olarak, en son sürümü doğrudan [GroupDocs.Watermark for Java sürümleri](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

#### Lisans Edinme
Geçici bir lisans indirerek ücretsiz deneme ile başlayın. GroupDocs.Watermark kullanmaya devam etmeyi seçerseniz, resmi sitesinde satın alma seçenekleri mevcuttur.

### Temel Başlatma ve Kurulum
Kütüphane hazır olduğunda, korumak istediğiniz diyagrama işaret eden bir `Watermarker` örneği oluşturun:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## **add watermark to diagram** – Metin Filigranı Nasıl Eklenir

### Metin Filigranı Oluşturma
Uygulamak istediğiniz metin, yazı tipi, renk ve opaklığı tanımlayın:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

### Filigran İçin Sayfa İndeksini Ayarlama
Filigran eklemek istediğiniz tam sayfayı belirtin. Sayfa indeksleri sıfır‑tabanlıdır:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

### Metin Filigranını Ekleyin
Filigranı seçilen sayfaya uygulayın:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

## **add image watermark java** – Görüntü Filigranı Nasıl Eklenir

### Görüntü Filigranı Oluşturma
Üstüne bindirmek istediğiniz görüntüyü yükleyin (ör. şirket logosu):

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

### Görüntü Filigranı İçin Sayfa İndeksini Ayarlama
Görüntü filigranının gösterileceği sayfayı seçin:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

### Görüntü Filigranını Ekleyin
Seçilen sayfaya görüntü filigranını ekleyin:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

## Kaydet ve Kaynakları Kapat
İstenen tüm filigranları ekledikten sonra değişiklikleri kaydedin ve temizlik yapın:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Pratik Uygulamalar
- **Document Security** – Ortaklarla paylaşmadan önce taslak diyagramlara “Confidential” etiketi uygulayın.  
- **Branding** – Teknik şemaların belirli sayfalarına logonuzu damgalayın.  
- **Copyright Protection** – Yüksek değerli diyagramlara telif hakkı bildirimleri ekleyerek kötüye kullanımı önleyin.

## Performans Düşünceleri
- Büyük dosyalar için özellikle belleği verimli yönetin.  
- İşleme hızını artırmak için filigran olarak kullanmadan önce görüntü boyutlarını optimize edin.  
- Kaydettikten sonra tüm filigran nesnelerini kapatarak Java’nın çöp toplama özelliğinden yararlanın.

## Yaygın Sorunlar ve Çözümler
| Symptom | Likely Cause | Fix |
|---|---|---|
| Filigran görünmüyor | Yanlış sayfa indeksi | Sıfır‑tabanlı indeksin hedef sayfaya eşleştiğini doğrulayın. |
| Görüntü bozuk görünüyor | Yüksek çözünürlüklü kaynak görüntüsü | Görüntüyü makul bir boyuta (ör. 300 × 300 px) yeniden boyutlandırın. |
| Üretimde lisans hatası | Sadece deneme lisansı kullanmak | `License.setLicense("path/to/license.file")` yöntemiyle tam lisans dosyasını uygulayın. |
| Büyük diyagramlarda yavaş işleme | Büyük dosya boyutu ve kapatılmamış kaynaklar | `Watermarker` ve bireysel filigran nesnelerini hemen kapatın. |

## Sıkça Sorulan Sorular

**Q1: Tek bir diyagram sayfasına birden fazla filigran ekleyebilir miyim?**  
A: Evet, aynı `DiagramPageWatermarkOptions` için farklı filigran nesneleriyle `watermarker.add()` metodunu çağırın.

**Q2: GroupDocs.Watermark for Java hangi dosya formatlarını destekliyor?**  
A: Çeşitli diyagram ve görüntü formatlarını destekler. Tam liste için [API belgeleri](https://reference.groupdocs.com/watermark/java) sayfasına bakın.

**Q3: Deneme sürümünü kullanırken lisans sorunlarını nasıl yönetebilirim?**  
A: GroupDocs'tan ücretsiz geçici bir lisansla başlayın. Üretim için tüm özellikleri açmak amacıyla tam lisans satın alın.

**Q4: Filigranlar beklenildiği gibi görünmüyorsa yaygın sorun giderme ipuçları nelerdir?**  
A: Sayfa indeksinin doğru olduğundan emin olun, görüntü kaynakları için dosya yollarını kontrol edin ve opaklık ayarının 0 olmadığını doğrulayın.

**Q5: Filigran görünümünü daha da özelleştirebilir miyim?**  
A: `TextWatermark` veya `ImageWatermark` üzerindeki metodları kullanarak yazı tipi boyutunu, opaklığı, dönüşü ve konumlandırmayı ayarlayın.

**Q6: Tek bir çağrıyla birden fazla sayfaya filigran eklemek mümkün mü?**  
A: Evet – bir `DiagramPageWatermarkOptions` örneği oluşturup, sayfa indekslerinin bir listesini ayarlayarak `watermarker.add()` metoduna geçirebilirsiniz.

**Q7: GroupDocs.Watermark şifre korumalı diyagram dosyalarını destekliyor mu?**  
A: Evet, yüklemeden önce `DiagramLoadOptions.setPassword("yourPassword")` yöntemiyle şifreyi sağlayabilirsiniz.

## Kaynaklar
- [GroupDocs.Watermark Dokümantasyonu](https://docs.groupdocs.com/watermark/java/)  
- [API Referans Kılavuzu](https://reference.groupdocs.com/watermark/java)  
- [Kütüphaneyi İndir](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)  
- [Geçici Lisans Bilgileri](https://purchase.groupdocs.com/temporary-license/)

Bu kaynakları inceleyerek GroupDocs.Watermark for Java konusundaki bilginizi ve yeteneklerinizi derinleştirin. İyi filigranlamalar!

---

**Son Güncelleme:** 2025-12-17  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs