---
date: '2026-02-18'
description: GroupDocs.Watermark for Java kullanarak diyagramlara nasıl filigran ekleyeceğinizi
  öğrenin. Görsel içeriğinizi etkili bir şekilde koruyun ve belge bütünlüğünü sağlayın.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: 'GroupDocs.Watermark for Java Kullanarak Diyagramlara Filigran Ekleme: Kapsamlı
  Bir Rehber'
type: docs
url: /tr/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Java için GroupDocs.Watermark Kullanarak Diyagramlara Filigran Ekleme: Kapsamlı Bir Rehber  

## Giriş  
Bu öğreticide, diyagram dosyalarınıza **filigran ekleme** yöntemini keşfedecek ve dosyalarınızın yetkisiz kullanımdan korunmasını sağlayacaksınız. Metin filigranları eklemek, sahipliği işaretlemenin, varlıklarınıza marka eklemenin veya yasal gerekliliklere uymanın basit ama güçlü bir yoludur. Bu kapsamlı rehber, **GroupDocs.Watermark for Java** kullanarak diyagramlara metin filigranları nasıl entegre edileceğini gösterir—çeşitli belge formatları için filigran eklemeye yönelik sağlam bir kütüphane.  

### Hızlı Yanıtlar  
- **Filigranın temel amacı nedir?** Sahipliği görsel olarak tanımlamak ve yetkisiz kopyalamayı önlemektir.  
- **Java'da diyagram filigranı desteği sağlayan kütüphane hangisidir?** GroupDocs.Watermark for Java.  
- **Kütüphaneyi kullanmak için Maven gerekli mi?** Evet, Maven aracılığıyla ekleyebilirsiniz (“groupdocs watermark maven” bölümüne bakın).  
- **Yazı tipi, boyut ve rengi özelleştirebilir miyim?** Kesinlikle—bu özellikleri yapılandırmak için `TextWatermark` API'sını kullanın.  
- **Üretim ortamı için lisans gerekli mi?** Üretim dağıtımları için geçerli bir GroupDocs.Watermark lisansı gereklidir.  

## “Filigran ekleme” diyagram bağlamında ne anlama geliyor?  
Filigran eklemek, bir diyagram dosyasının (ör. Visio, SVG) her sayfasına veya şekline yarı şeffaf bir metin katmanı gömmek anlamına gelir. Filigran dosyayla birlikte taşınır, belgeyi açan herkes tarafından görülebilir ve orijinal tasarıma müdahale etmez.  

## Neden GroupDocs.Watermark for Java Kullanmalı?  
- **Geniş format desteği** – Visio, SVG ve birçok diğer diyagram türünü işler.  
- **Kolay Maven entegrasyonu** – Hızlı başlamak için “groupdocs watermark maven” adımlarını izleyin.  
- **İnce ayarlı yerleştirme** – Filigranın nerede görüneceğini (arka plan, ön plan, belirli şekiller) tam olarak kontrol edin.  
- **Performans odaklı** – Büyük dosyalar için düşük bellek tüketimiyle tasarlanmıştır.  

## Önkoşullar  
- **GroupDocs.Watermark for Java** (sürüm 24.11 veya üzeri)  
- **Java Development Kit (JDK)** 8+  
- IntelliJ IDEA veya Eclipse gibi bir IDE  
- Bağımlılık yönetimi için Maven (isteğe bağlı ancak önerilir)  

## GroupDocs.Watermark for Java Kurulumu  

### Maven Yapılandırması (groupdocs watermark maven)  
Aşağıdaki depo ve bağımlılık girdilerini `pom.xml` dosyanıza ekleyin:  

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

**Doğrudan İndirme** – En son JAR dosyasını ayrıca [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden edinebilirsiniz.  

### Lisans Edinimi  
- **Ücretsiz Deneme** – Kütüphaneyi lisans anahtarı olmadan değerlendirin.  
- **Geçici Lisans** – Tüm özelliklerin kilidini açmak için geliştirme sırasında geçici bir anahtar kullanın.  
- **Satın Alma** – Sınırsız kullanım için üretim lisansı edinin.  

### Temel Başlatma ve Kurulum  
Java sınıfınıza gerekli içe aktarmaları ekleyin:  

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Diyagram Belgelerine Filigran Ekleme  

### Adım 1: Diyagram Belgesini Yükleme  
İlk olarak, kütüphaneyi korumak istediğiniz diyagram dosyasına yönlendirin ve bir `Watermarker` örneği oluşturun.  

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Açıklama*: `DiagramLoadOptions`, diyagramın nasıl ayrıştırılacağını (ör. gömülü yazı tiplerinin işlenmesi) ince ayarlamanızı sağlar.  

### Adım 2: Metin Filigranı Yapılandırma (configure text watermark)  
Bir `TextWatermark` nesnesi oluşturun ve yazı tipi, boyut ve renk gibi görsel özelliklerini ayarlayın.  

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Açıklama*: Bu satır, 19 punto Calibri yazı tipini kullanarak **“Test watermark 1”** metnini içeren bir filigran oluşturur. `setColor()`, `setOpacity()` vb. ile daha da özelleştirebilirsiniz.  

### Adım 3: Diyagram Şekilleri İçin Yerleştirme Seçeneklerini Tanımlama  
Filigranın diyagram içinde nerede görüneceğini (arka plan, ön plan veya belirli şekiller) belirtin.  

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Açıklama*: `DiagramShapeWatermarkOptions` sınıfı yerleştirmeyi kontrol eder. Burada `SeparateBackgrounds` seçiyoruz, böylece filigran her arka plan katmanında işlenir.  

### Adım 4: Filigranı Ekle ve Belgeyi Kaydet  
Son olarak, filigranı uygulayın ve korunan dosyayı diske yazın.  

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Açıklama*: `add()` tanımlı seçeneklerle yapılandırılmış filigranı ekler, `save()` sonucu yazar ve `close()` yerel kaynakları serbest bırakır.  

## Pratik Uygulamalar  
- **Fikri Mülkiyet Koruması** – Rakiplerin sahip olduğunuz diyagramları yeniden kullanmasını önleyin.  
- **Markalaşma** – Şirket adınızı veya logonuzu tüm dışa aktarılan varlıklarda tutarlı bir şekilde gösterin.  
- **Hukuki & Uyumluluk** – Gizli şemaları “Confidential” filigranı ile işaretleyin.  
- **Akademik Sunumlar** – Öğrenci çalışmalarını intihal takibi için benzersiz tanımlayıcılarla etiketleyin.  

## Performans Hususları  
- **Bellek Yönetimi** – Dosya topluluklarını işlerken `Watermarker` örneklerini yeniden kullanın.  
- **Kaynak Temizliği** – Her zaman bir `finally` bloğunda `watermarker.close()` çağırın veya destekleniyorsa try‑with‑resources kullanın.  
- **Büyük Dosyalar** – Çok megabaytlık diyagramlar için, en yüksek bellek kullanımını azaltmak amacıyla sayfaları tek tek işlemeyi düşünün.  

## Sonuç  
Artık GroupDocs.Watermark for Java kullanarak diyagram belgelerine **filigran ekleme** için eksiksiz, adım adım bir yönteme sahipsiniz. Diyagramınızı yükleyerek, bir `TextWatermark` yapılandırarak, yerleştirme seçeneklerini ayarlayarak ve sonucu kaydederek görsel varlıklarınızı minimum çaba ile koruyabilirsiniz.  

Sonraki adımda, farklı yazı tipleri, renkler ve opaklık seviyeleriyle deney yapın veya tüm diyagram kütüphanelerini otomatik olarak filigranlamak için toplu işleme keşfedin.  

## SSS Bölümü  
**1. Filigranlar için en iyi yazı tipi boyutu nedir?**  
En uygun yazı tipi boyutu, belge türüne ve görünürlük gereksinimlerine bağlıdır.  

**2. Filigran renklerini özelleştirebilir miyim?**  
Evet, `textWatermark.setColor()` yöntemiyle özel renkler ayarlayabilirsiniz.  

**3. Büyük belge topluluklarını nasıl yönetirim?**  
Verimliliği artırmak için toplu işleme tasarlanmış API yöntemlerini kullanın.  

**4. GroupDocs.Watermark ile ilgili sınırlamalar var mı?**  
Detaylı özellik desteği ve uyumluluk notları için [documentation](https://docs.groupdocs.com/watermark/java/) inceleyin.  

**5. Sorunlarla karşılaşırsam nasıl destek alabilirim?**  
Ücretsiz destek ve rehberlik için [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) adresini ziyaret edin.  

## Ek Sıkça Sorulan Sorular  

**S: Filigran opaklığını değiştirebilir miyim?**  
C: Evet, `textWatermark.setOpacity(0.5)` (0‑1 arasında bir değer) çağırın.  

**S: Sadece seçili sayfalara filigran eklemek mümkün mü?**  
C: Belirli sayfaları veya şekilleri hedeflemek için `DiagramPageWatermarkOptions` kullanın.  

**S: Kütüphane SVG diyagramlarını destekliyor mu?**  
C: Kesinlikle—GroupDocs.Watermark SVG, Visio ve birçok diğer diyagram formatını işler.  

**S: Şifre korumalı bir diyagrama nasıl filigran eklerim?**  
C: Yüklemeden önce `DiagramLoadOptions.setPassword("yourPassword")` ile şifreyi sağlayın.  

**S: Hangi Java sürümü gereklidir?**  
C: Java 8 veya daha yeni sürümler tam olarak desteklenir.  

## Kaynaklar  
- **Documentation**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API Reference**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub Repository**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free Support Forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary License**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---  

**Son Güncelleme:** 2026-02-18  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  

---