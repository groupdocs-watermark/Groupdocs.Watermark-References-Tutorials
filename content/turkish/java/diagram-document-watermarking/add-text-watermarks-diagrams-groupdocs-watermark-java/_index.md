---
date: '2026-04-04'
description: GroupDocs.Watermark for Java kullanarak Visio diyagramlarına metin filigranı
  nasıl oluşturulacağını öğrenin. Kurulum, kod ve gerçek dünya kullanım örneklerini
  içerir.
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: GroupDocs.Watermark Java ile Diyagramlara Metin Filigranı Oluşturma
type: docs
url: /tr/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java ile Diyagramlarda Metin Filigranı Oluşturma

Diyagramlarınızı yetkisiz yeniden kullanımdan korumak, günümüz işbirlikçi ortamlarında bir zorunluluktur. Bu öğreticide **GroupDocs.Watermark for Java** kullanarak Visio‑stil diyagramlarda **metin filigranı oluşturacaksınız**. Maven kurulumundan filigranlı dosyanın kaydedilmesine kadar her adımı adım adım göstereceğiz, böylece her diyagram sayfasına güvenle marka veya güvenlik işaretleri ekleyebilirsiniz.

## Hızlı Yanıtlar
- **Hangi kütüphane gerekiyor?** GroupDocs.Watermark for Java (Maven artefaktı `groupdocs-watermark`).
- **Hangi dosya türleri destekleniyor?** Visio (`.vsdx`, `.vsd`) ve ayrıca birçok diğer diyagram formatı.
- **Lisans gerekli mi?** Geliştirme için geçici bir deneme lisansı yeterlidir; üretim için tam lisans gereklidir.
- **Yazı tipi, renk ve dönüşü özelleştirebilir miyim?** Evet – `TextWatermark` sınıfı bu özelliklerin tümünü ayarlamanıza olanak tanır.
- **İşlem ne kadar sürer?** Tipik bir diyagrama metin filigranı eklemek, modern donanımda bir saniyeden az sürer.

## “Metin filigranı oluşturma” işlemi nedir?
Metin filigranı oluşturmak, bir belge sayfasının üzerine programlı olarak yarı şeffaf metin yerleştirmek anlamına gelir. Filigran ön planda ya da arka planda konumlandırılabilir, döndürülebilir, renklendirilebilir ve marka ya da güvenlik gereksinimlerine uygun şekilde biçimlendirilebilir.

## Neden GroupDocs.Watermark for Java kullanmalı?
- **Geniş format desteği** – Visio, PDF, Word, Excel ve daha fazlası ile çalışır.
- **İnce ayarlı kontrol** – konumlandırma, opaklık, dönüş ve arka plan/ön plan renderlamasını seçebilirsiniz.
- **Kolay entegrasyon** – Maven tabanlı kurulum ve basit API çağrıları kodunuzu temiz tutar.
- **Performans odaklı** – `Watermarker` nesnesini kapattığınızda kaynaklar otomatik olarak serbest bırakılır.

## Önkoşullar
- Java Development Kit (JDK) 8 ve üzeri.
- IntelliJ IDEA veya Eclipse gibi bir IDE.
- Bağımlılık yönetimi için Maven.

## GroupDocs.Watermark for Java Kurulumu
`pom.xml` dosyanıza depoyu ve bağımlılığı ekleyin:

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

Manuel indirmeyi tercih ederseniz, ikili dosyaları [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirin ve projenizin sınıf yoluna ekleyin.

### Lisans Alımı
Ücretsiz bir deneme lisansı için [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/) adresine gidin. Herhangi bir filigran işleminden önce lisans dosyasını yükleyin:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Adım Adım Uygulama

### Adım 1: Diyagram Dosyasını Yükle
`DiagramLoadOptions` kullanarak bir Visio dosyasını (veya desteklenen herhangi bir diyagram formatını) açın.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Adım 2: Metin Filigranı Oluştur
Filigran metnini, yazı tipini, rengi, arka plan bayrağını ve dönüş açısını yapılandırın.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### Adım 3: Diyagram İçin Konumlandırmayı Tanımla
Filigranın her diyagram sayfasının arka planında mı yoksa ön planında mı görüneceğini seçin.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Adım 4: Filigranlı Diyagramı Kaydet
Sonucu yeni bir dosyaya yazın ve kaynakları serbest bırakın.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Yaygın Sorunlar ve Çözümler
| Sorun | Çözüm |
|---------|----------|
| **Dosya bulunamadı** | Mutlak/göreli yolları doğrulayın ve dosyanın Java süreci tarafından okunabilir olduğundan emin olun. |
| **Lisans uygulanmadı** | Lisans dosyası yolunun doğru olduğunu ve dosyanın bozuk olmadığını doğrulayın. |
| **Filigran görünmüyor** | `setBackground(false)` ve dönüş açısını kontrol edin; farklı bir renk veya opaklık deneyin. |
| **Desteklenmeyen diyagram sürümü** | Yeni Visio formatlarını destekleyen en son GroupDocs.Watermark sürümünü (24.11) kullanın. |

## Pratik Kullanım Durumları
1. **Belge Güvenliği** – Rakiplerin özel akış şemalarını yeniden kullanmasını önleyin.
2. **Marka Tutarlılığı** – Tüm dışa aktarılan diyagramlara şirket adı veya logosunu otomatik olarak ekleyin.
3. **İşbirliği Takibi** – Her diyagramı kimlerin düzenlediğini belirlemek için kullanıcı baş harflerini filigran olarak ekleyin.

## Performans İpuçları
- İşiniz bittiğinde `Watermarker` nesnesini kapatın, böylece yerel kaynaklar serbest bırakılır.
- Toplu işleme için mümkün olduğunda tek bir `Watermarker` örneğini yeniden kullanın.
- Filigran metnini kısa tutun; büyük yazı tipleri render süresini artırır.

## Sonuç
Artık GroupDocs.Watermark for Java kullanarak Visio diyagramlarına **metin filigranı oluşturmayı** biliyorsunuz. Bu yöntem, görünüm, konumlandırma ve stil üzerinde tam kontrol sağlar ve görsel varlıklarınızı etkili bir şekilde korumanıza ve markalamanıza yardımcı olur.

### Sonraki Adımlar
- Logo markalama için görüntü filigranları (`ImageWatermark`) deneyin.
- `watermarker.getPages()` üzerinden döngü yaparak ve koşullu olarak seçenekler uygulayarak seçici sayfa filigranı keşfedin.
- Bu mantığı CI/CD boru hattınıza entegre ederek yayınlamadan önce diyagramları otomatik olarak güvence altına alın.

## SSS Bölümü
1. **GroupDocs.Watermark'ı diğer dosya formatları için kullanabilir miyim?**  
   Evet, PDF'ler, Word belgeleri, Excel sayfaları, PowerPoint sunumları ve daha birçok formatı destekler.
2. **Ekleyebileceğim filigran sayısında bir limit var mı?**  
   Katı bir limit yok, ancak çok sayıda karmaşık filigran eklemek performansı etkileyebilir.
3. **Bir diyagramdan filigranı nasıl kaldırırım?**  
   GroupDocs.Watermark, ekleme akışına benzer şekilde çağırabileceğiniz algılama ve kaldırma API'leri sunar.
4. **Metin filigranları tüm sayfalara mı yoksa sadece seçilen sayfalara mı eklenebilir?**  
   Her sayfa için `DiagramShapeWatermarkOptions` yapılandırabilir veya `add` çağırmadan önce filtre uygulayabilirsiniz.
5. **Filigran beklediğiniz gibi görünmüyorsa ne yapmalıyım?**  
   Konumlandırma ayarlarını, renk kontrastını iki kez kontrol edin ve diyagramın kaydedildikten sonra düzleştirildiğinden emin olun.

## Sık Sorulan Sorular

**S: Kütüphane Visio 2003 (`.vsd`) dosyalarıyla çalışıyor mu?**  
C: Evet – `DiagramLoadOptions` hem `.vsdx` hem de eski `.vsd` formatlarını destekler.

**S: Metin filigranının opaklığını değiştirebilir miyim?**  
C: Kesinlikle. `%50` şeffaflık ayarlamak için `textWatermark.setOpacity(0.5);` kullanın.

**S: Farklı diyagram sayfalarına farklı filigranlar eklemek mümkün mü?**  
C: Evet. `watermarker.getPages()` üzerinden döngü yaparak her sayfa için özel seçeneklerle ayrı `TextWatermark` örnekleri uygulayabilirsiniz.

**S: Ticari kullanım için lisans kısıtlamaları var mı?**  
C: Üretim dağıtımları için tam bir ticari lisans gereklidir; deneme lisansı sadece değerlendirme amaçlıdır.

**S: Tek bir çalıştırmada birden fazla diyagramı toplu işleme nasıl yapabilirim?**  
C: Yukarıdaki adımları bir döngü içinde sararak her dosyayı yükleyin, filigranı uygulayın, kaydedin ve bir sonraki dosyaya geçmeden önce `Watermarker` nesnesini kapatın.

---

**Son Güncelleme:** 2026-04-04  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/watermark/java/)
- [API Referansı](https://reference.groupdocs.com/watermark/java)
- [En Son Sürümü İndir](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)