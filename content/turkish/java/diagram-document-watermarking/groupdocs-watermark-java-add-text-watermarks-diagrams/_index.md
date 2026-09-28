---
date: '2025-12-19'
description: GroupDocs.Watermark for Java ile diyagramlara metin filigranı eklemeyi
  öğrenin. Görsel içeriğinizi etkili bir şekilde koruyun ve belge bütünlüğünü sağlayın.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: GroupDocs.Watermark for Java Kullanarak Diyagramlara Metin Filigranı Ekleyin
  – Kapsamlı Bir Rehber
type: docs
url: /tr/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# GroupDocs.Watermark for Java Kullanarak Diyagramlara Metin Filigranı Ekleme: Kapsamlı Bir Rehber

## Giriş
Diyagram belgelerini yetkisiz kullanımdan korumak çok önemlidir ve **metin filigranı eklemek** basit ama etkili bir çözüm sunar. Bu öğreticide, diyagram dosyalarını nasıl yükleyeceğinizi, özelleştirilebilir bir metin filigranı oluşturacağınızı ve **GroupDocs.Watermark for Java** kullanarak arka plan sayfalarına veya belirli şekillere nasıl uygulayacağınızı keşfedeceksiniz. Rehberin sonunda, görsel varlıklarınızı orijinal görünüm ve hissiyatı koruyarak güvence altına alabileceksiniz.

### Hızlı Yanıtlar
- **“Metin filigranı eklemek” ne anlama gelir?**  
  Belgeye mülkiyet veya gizlilik göstermek amacıyla yarı saydam bir metin katmanı gömmek demektir.  
- **Hangi kütüphane diyagram filigranlamasını destekliyor?**  
  GroupDocs.Watermark for Java, diyagram formatları (ör. Visio, VSDX) için yerel destek sağlar.  
- **Lisans almam gerekiyor mu?**  
  Üretim kullanımı için geçici veya tam lisans gereklidir; değerlendirme için ücretsiz deneme sürümü mevcuttur.  
- **Filigranı arka plan sayfalarına yerleştirebilir miyim?**  
  Evet – **arka plan sayfa filigranı** için `DiagramWatermarkPlacementType.SeparateBackgrounds` seçeneğini kullanın.  
- **Kod Java 8+ ile uyumlu mu?**  
  Kesinlikle – kütüphane JDK 8 ve üzeri sürümlerle çalışır.

## Diyagramlar İçin Metin Filigranı Nedir?
Metin filigranı, diyagram öğelerinin üzerine ya da arkasına yerleştirilen (genellikle yarı saydam) okunabilir bir metin parçasıdır. Marka oluşturma, telif hakkı koruması veya gizli taslakları işaretleme gibi amaçlarla kullanılabilir.

## Neden GroupDocs.Watermark for Java Kullanmalısınız?
- **Geniş format desteği** – Visio, VSDX ve birçok diğer diyagram türüyle çalışır.  
- **İnce ayarlı yerleştirme** – ön plan, arka plan veya belirli şekil filigranı seçebilirsiniz.  
- **Basit API** – sadece birkaç satır Java kodu ile filigran oluşturup uygulayabilirsiniz.  

## Önkoşullar
- **GroupDocs.Watermark for Java** (v24.11 veya üzeri)  
- **Java Development Kit (JDK)** 8 veya daha yüksek  
- Maven (veya manuel JAR ekleme)  

## GroupDocs.Watermark for Java Kurulumu
### Maven Kurulumu
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

### Doğrudan İndirme
En son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirin.

### Lisans Edinme
- **Ücretsiz Deneme** – lisans anahtarı olmadan tüm özellikleri değerlendirin.  
- **Geçici Lisans** – geliştirme sırasında tam işlevselliği açmak için kullanın.  
- **Satın Alma** – ticari projeler için üretim lisansı alın.  

### Temel Başlatma ve Kurulum
Java sınıfınızda aşağıdaki içe aktarmaların bulunduğundan emin olun:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Adım‑Adım Uygulama

### Adım 1: Diyagram Belgesini Yükleme
Öncelikle kütüphaneyi diyagram dosyanıza yönlendirin ve yükleme seçeneklerini başlatın.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Explanation*: `DiagramLoadOptions`, filigranlamadan önce diyagramın nasıl ayrıştırılacağını kontrol etmenizi sağlar.

### Adım 2: Metin Filigranı Oluşturma
Şimdi filigran metnini oluşturun ve görsel stilini tanımlayın.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Explanation*: Bu kod, Calibri fontu ve 19 boyutunda **“Test watermark 1”** ifadesiyle bir `TextWatermark` oluşturur.

### Adım 3: Yerleşimi Yapılandırma – Arka Plan Sayfası Filigranı
Filigranın nerede görüneceğini seçin. **Arka plan sayfa filigranı** için aşağıdaki seçeneği kullanın:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Explanation*: `DiagramShapeWatermarkOptions`, tam konumu kontrol eder. Yerleştirme türünü `SeparateBackgrounds` olarak ayarlamak, diyagramın her arka plan sayfasına filigran ekler.

### Adım 4: Filigranı Uygulama ve Kaydetme
Son olarak, filigranı belgeye ekleyin, sonucu kaydedin ve kaynakları serbest bırakın.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Explanation*: `add` yöntemi, yapılandırılmış `textWatermark`ı yerleştirme seçenekleriyle uygular; ardından değiştirilmiş diyagram `outputPath` konumuna kaydedilir.

## Pratik Uygulamalar
- **Fikri Mülkiyet Koruması** – rakiplerin sahip olduğunuz diyagramları yeniden kullanmasını engelleyin.  
- **Marka Güçlendirme** – şirket adı veya logosunu tüm dışa aktarılan diyagramlarda metin filigranı olarak ekleyin.  
- **Hukuki Belgeler** – mühendislik şemalarının gizli taslaklarını işaretleyin.  
- **Akademik Sunumlar** – öğrenci kimlikleri veya ders kodlarını diyagramlara ekleyerek intihal takibi yapın.

## Performans Düşünceleri
- **Bellek Yönetimi** – büyük dosyalar işlenirken özellikle `Watermarker` örneğini (`watermarker.close()`) kapatarak yerel kaynakları serbest bırakın.  
- **Toplu İşleme** – mümkün olduğunda tek bir `Watermarker` örneğini yeniden kullanarak bir dizi diyagram yolu üzerinden döngü oluşturun; bu, ek yükü azaltır.  

## Yaygın Sorunlar ve Çözümler
| Issue | Solution |
|-------|----------|
| **Büyük diyagramlarda OutOfMemoryError** | JVM yığın boyutunu (`-Xmx2g`) artırın ve dosyaları tek tek işleyin. |
| **Filigran görünmüyor** | Filigran renginin yeterli kontrast sağladığından emin olun; opaklığı `textWatermark.setOpacity(0.5)` ile ayarlayın. |
| **Desteklenmeyen diyagram formatı** | Formatın GroupDocs.Watermark desteklenen formatlar belgelerinde listelendiğini doğrulayın. |

## Sıkça Sorulan Sorular

**S: Filigranlar için en iyi yazı tipi boyutu nedir?**  
C: Optimum boyut, diyagramın boyutlarına bağlıdır; çoğu durumda 12‑20 pt iyi çalışır.

**S: Filigran renklerini özelleştirebilir miyim?**  
C: Evet, `textWatermark.setColor(Color.GRAY)` (veya herhangi bir `java.awt.Color`) kullanabilirsiniz.

**S: Büyük belge topluluklarını nasıl yönetebilirim?**  
C: Kütüphanenin toplu API'sini kullanın veya `Watermarker` nesnelerini yeniden kullanan bir döngü yazarak ek yükü minimize edin.

**S: GroupDocs.Watermark ile ilgili sınırlamalar var mı?**  
C: Kütüphane çoğu yaygın diyagram formatını destekler, ancak bazı özel uzantılar tam olarak işlenemeyebilir. Ayrıntılar için [documentation](https://docs.groupdocs.com/watermark/java/) sayfasına bakın.

**S: Sorun yaşarsam nasıl destek alabilirim?**  
C: Topluluk yardımı için [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) adresini ziyaret edin veya doğrudan GroupDocs destek ekibiyle iletişime geçin.

## Ek Kaynaklar
- **Documentation**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API Reference**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub Repository**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free Support Forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary License**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs