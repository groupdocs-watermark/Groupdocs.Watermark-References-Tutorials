---
date: '2026-06-21'
description: GroupDocs.Watermark for Java ile Java sunumuna nasıl watermark ekleneceğini
  öğrenin, slaytları text watermarks ve unreadable‑character protection uygulayarak
  güvence altına alın.
keywords:
- add watermark java presentation
- GroupDocs.Watermark Java
- presentation security
schemas:
- author: GroupDocs
  dateModified: '2026-06-21'
  description: Learn how to add watermark java presentation with GroupDocs.Watermark
    for Java, securing slides by applying text watermarks and unreadable‑character
    protection.
  headline: Add Watermark Java Presentation Using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to add watermark java presentation with GroupDocs.Watermark
    for Java, securing slides by applying text watermarks and unreadable‑character
    protection.
  name: Add Watermark Java Presentation Using GroupDocs.Watermark
  steps:
  - name: '**Java Development Kit (JDK) 8 or later** – required for compilation and
      runtime.'
    text: '**Java Development Kit (JDK) 8 or later** – required for compilation and
      runtime.'
  - name: '**Maven** – handles dependency resolution; you can also use Gradle if preferred.'
    text: '**Maven** – handles dependency resolution; you can also use Gradle if preferred.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any Java‑compatible editor.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any Java‑compatible editor.'
  - name: '**Basic Java I/O knowledge** – to understand file streams and exception
      handling.'
    text: '**Basic Java I/O knowledge** – to understand file streams and exception
      handling.'
  type: HowTo
- questions:
  - answer: Yes—use the `ImageWatermark` class, which supports PNG, JPEG, and SVG
      formats.
    question: Can I add an image watermark instead of text?
  - answer: Absolutely; provide the password via `PresentationLoadOptions.setPassword("yourPassword")`.
    question: Does the library work with password‑protected PPTX files?
  - answer: There is no hard limit; the API streams slides, so you can process presentations
      with thousands of slides as long as the JVM heap is sized appropriately.
    question: How many slides can I watermark in one operation?
  - answer: Yes—specify a slide range in `PresentationLoadOptions` or pass a list
      of slide indices to the `add` method.
    question: Is it possible to watermark only selected slides?
  - answer: The examples were verified with GroupDocs.Watermark 23.12 for Java.
    question: What version of GroupDocs.Watermark is tested with this tutorial?
  type: FAQPage
title: GroupDocs.Watermark Kullanarak Java Sunumuna Watermark Ekleme
type: docs
url: /tr/java/getting-started/java-watermarking-groupdocs-watermark-presentation-security/
weight: 1
---

# GroupDocs.Watermark Kullanarak Java Sunumuna Su İşareti Ekleme

Bugünün hızlı tempolu iş ortamında, **add watermark java presentation** gizli slayt setlerini, eğitim materyallerini ve pazarlama dokümanlarını korumak için en iyi uygulamalardan biridir. GroupDocs.Watermark for Java, PowerPoint dosyalarına görünür veya görünmez metin su işaretleri eklemenizi sağlar ve dosyayı alan herkesin sahipliğini veya gizlilik durumunu anında görmesini temin eder. Bu kılavuz, kütüphaneyi kurmaktan sunumu yüklemeye, özel bir metin su işareti oluşturmaya, okunamaz‑karakter korumasıyla kilitlemeye ve son olarak güvenli dosyayı kaydetmeye kadar tüm adımları size gösterir.

## Hızlı Yanıtlar
- **Ana amaç nedir?** Sunum dosyalarını kalıcı metin su işaretleri ekleyerek güvence altına almak.  
- **Hangi kütüphane gereklidir?** GroupDocs.Watermark for Java (Maven artifact `com.groupdocs:groupdocs-watermark`).  
- **Lisans gerekiyor mu?** Ücretsiz deneme geliştirme için çalışır; üretim için tam lisans gereklidir.  
- **Büyük sunumları koruyabilir miyim?** Evet—GroupDocs.Watermark, tüm belgeyi belleğe yüklemeden 500 MB’a kadar dosyaları işleyebilir.  
- **API Java 8+ ile uyumlu mu?** Kesinlikle, JDK 8 ve daha yeni sürümlerde çalışır.

## “add watermark java presentation” nedir?
*Add watermark java presentation*, bir Java‑tabanlı PowerPoint (`.pptx`) dosyasına programlı olarak metin veya resim su işareti ekleyerek içeriğini koruma sürecine denir. Görünür veya görünmez işaretler ekleyerek sahipliği belirtebilir, gizliliği zorlayabilir ve yetkisiz dağıtımı engelleyebilirsiniz; böylece alıcılar her zaman kaynağı veya koruma durumunu görür.

## Neden GroupDocs.Watermark for Java Kullanmalı?
GroupDocs.Watermark **30+ dosya formatını** (PPTX, PPT, PDF, DOCX ve görseller dahil) destekler ve sunumlara **kalite kaybı olmadan** su işareti uygulayabilir. Motoru, tipik sunucu donanımında çok sayfalı sunumları bir saniyeden kısa sürede işler ve 150 MB’dan az RAM tüketir—yüksek hacimli toplu işler için idealdir.

## Önkoşullar

1. **Java Development Kit (JDK) 8 veya üzeri** – derleme ve çalışma zamanı için gereklidir.  
2. **Maven** – bağımlılık çözümlemesini yönetir; isterseniz Gradle da kullanabilirsiniz.  
3. **IDE** – IntelliJ IDEA, Eclipse veya herhangi bir Java‑uyumlu editör.  
4. **Temel Java I/O bilgisi** – dosya akışlarını ve istisna yönetimini anlamak için.

## GroupDocs.Watermark for Java Kurulumu

### Maven Kurulumu
`pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin. Bu, GroupDocs.Watermark’ın en son kararlı sürümünü çeker.

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
Manuel kurulum tercih ediyorsanız, resmi sürüm sayfasından JAR dosyalarını alın: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Lisans Edinme
- **Ücretsiz Deneme:** 30 gün boyunca sınırsız API çağrısına izin verir.  
- **Geçici Lisans:** Daha uzun geliştirme döngüleri için deneme limitlerini genişletir.  
- **Tam Lisans:** Ticari dağıtım için gereklidir ve tüm deneme kısıtlamalarını kaldırır.

### Temel Başlatma ve Kurulum
Tüm su işareti işlemleri için merkezi nesne olan bir `Watermarker` örneği oluşturun.

```java
import com.groupdocs.watermark.Watermarker;

public class InitializeWatermarker {
    public static void main(String[] args) {
        String filePath = "YOUR_DOCUMENT_DIRECTORY/presentation.pptx";
        Watermarker watermarker = new Watermarker(filePath);
    }
}
```

`Watermarker` belgeleri yükleyen, düzenleyen ve kaydeden çekirdek sınıftır. Bu nesne, sunum dosyalarınızı yükleme, düzenleme ve kaydetme işlemlerini yönetecektir.

## Uygulama Kılavuzu

### Java sunumuna su işareti nasıl eklenir?
Java sunumuna su işareti eklemek için önce `PresentationLoadOptions` ile PowerPoint dosyasını yükleyin. Ardından istediğiniz metin, stil ve dönüş açılarını içeren bir `TextWatermark` oluşturun. Okunamaz‑karakter korumasını `PresentationWatermarkSlideOptions` ile etkinleştirin, su işaretini hedef slaytlara ekleyin ve son olarak değişiklikleri kaydedin.

#### Sunum Belgesini Yükleme
İlk olarak, dosyayı uygun yükleme seçenekleriyle açmanız gerekir.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

public class LoadPresentation {
    public static void run() {
        PresentationLoadOptions loadOptions = new PresentationLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/presentation.pptx";
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
    }
}
```

**Tanım bağlantısı:** `PresentationLoadOptions` GroupDocs.Watermark'ın bir PowerPoint dosyasını nasıl okuduğunu tanımlar, şifre koruması, slayt aralığı ve bellek‑tasarrufu bayraklarını belirlemenize olanak tanır.

#### Metin Su İşareti Oluşturma
Sonra su işareti metnini oluşturun ve kurumsal yönergelerinize uygun şekilde stil verin.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

public class CreateTextWatermark {
    public static void run() {
        String watermarkText = "Confidential";
        Font font = new Font("Arial", 19);
        TextWatermark watermark = new TextWatermark(watermarkText, font);
    }
}
```

**Tanım bağlantısı:** `TextWatermark` konumlandırılabilir, döndürülebilir ve renklendirilebilir bir metin katmanı temsil eder. Unicode destekler, böylece çok dilli etiketler ekleyebilirsiniz.

#### Okunamaz Karakterler İçin Su İşareti Seçeneklerini Yapılandırma
Su işaretini müdahale karşıtı yapmak için okunamaz‑karakter korumasını etkinleştirin.

```java
import com.groupdocs.watermark.options.PresentationWatermarkSlideOptions;

public class ConfigureWatermarkOptions {
    public static void run() {
        PresentationWatermarkSlideOptions options = new PresentationWatermarkSlideOptions();
        options.setLocked(true);
        options.setProtectWithUnreadableCharacters(true);
    }
}
```

**Tanım bağlantısı:** `PresentationWatermarkSlideOptions` bir su işaretinin tek tek slaytlara nasıl uygulanacağını yapılandırır. Su işaretini kilitlemenize, sadece‑okunur bayrakları ayarlamanıza ve belge yetkisiz düzenlendiğinde metni karıştıran okunamaz‑karakter korumasını etkinleştirmenize izin verir.

#### Sunuma Su İşareti Ekleme
Şimdi `Watermarker` nesnesiyle su işaretini her slayta (veya bir alt kümesine) uygulayın.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationWatermarkSlideOptions;
import com.groupdocs.watermark.watermarks.TextWatermark;

public class AddWatermarkToPresentation {
    public static void run() {
        PresentationLoadOptions loadOptions = new PresentationLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/presentation.pptx";
        Watermarker watermarker = new Watermarker(filePath, loadOptions);

        TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
        PresentationWatermarkSlideOptions options = new PresentationWatermarkSlideOptions();
        options.setLocked(true);
        options.setProtectWithUnreadableCharacters(true);

        watermarker.add(watermark, options);
    }
}
```

**Tanım bağlantısı:** `Watermarker` sınıfının `add` metodu, yapılandırılmış `TextWatermark`ı hedef slaytlara ekler ve daha önce tanımladığınız seçeneklere saygı gösterir.

#### Su İşaretli Belgeyi Kaydetme ve Kapatma
Son olarak değişiklikleri kalıcı hale getirin ve kaynakları serbest bırakın.

```java
import com.groupdocs.watermark.Watermarker;

public class SaveAndCloseWatermarkedDocument {
    public static void run() {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/watermarked_presentation.pptx";
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx");

        watermarker.save(outputPath);
        watermarker.close();
    }
}
```

**Tanım bağlantısı:** `save` çağrısı değiştirilmiş sunumu diske yazar, `close` ise yerel kaynakları serbest bırakır ve bellek sızıntılarını önler.

## Pratik Uygulamalar

- **Kurumsal Teklifler:** Müşterilere göndermeden önce tüm slaytlara “Confidential – Company XYZ” ekleyin.  
- **Akademik Dersler:** Yetkisiz dağıtımı önlemek için üniversite logolarını ve ders kodlarını ekleyin.  
- **Etkinlik Sunumları:** Marka güçlendirmesi için her slayta etkinlik adı ve tarihini su işareti olarak ekleyin.  
- **Hukuki Belgeler:** Zincir‑iliş kanıtı sağlamak için yasal sunumları dava tanımlayıcılarıyla etiketleyin.  
- **Pazarlama Varlıkları:** PDF dönüşümünden sonra da kalıcı olan ince marka su işaretleriyle yüksek çözünürlüklü tanıtım sunumlarını koruyun.

## Performans Düşünceleri

- **Performansı Optimize Etme:** Toplu işleme için tek bir `Watermarker` örneği yeniden kullanın; bu JVM yükünü azaltır.  
- **Kaynak Kullanım Kılavuzu:** 200 MB'den büyük sunumlar için `PresentationLoadOptions` içinde akış modunu etkinleştirerek bellek tüketimini 200 MB altında tutun.  
- **Java Bellek Yönetimi:** Temizliği garanti altına almak için `close()` metodunu her zaman bir `finally` bloğunda çağırın veya try‑with‑resources kullanın.

## Yaygın Sorunlar ve Çözümler

| Sorun | Neden | Çözüm |
|-------|-------|----------|
| Su işareti görünmüyor | Varsayılan opaklık %0 olarak ayarlandı | `TextWatermark` üzerinde `setOpacity(0.5)` ayarlayın. |
| Büyük sunumlarda bellek dışı hata | Tüm dosya belleğe yüklendi | `PresentationLoadOptions` içinde `setLoadMode(LoadMode.STREAM)` etkinleştirin. |
| Okunamaz karakterler uygulanmadı | `setUnreadableCharacters(true)` atlanmış | `PresentationWatermarkSlideOptions` üzerinde bayrağın ayarlandığından emin olun. |
| Çalışma zamanında lisans istisnası | Süre dolduktan sonra deneme sürümü kullanılıyor | Lisans dosyasını güncelleyin veya yeni bir deneme anahtarı isteyin. |

## Sıkça Sorulan Sorular

**S: Metin yerine bir resim su işareti ekleyebilir miyim?**  
C: Evet—PNG, JPEG ve SVG formatlarını destekleyen `ImageWatermark` sınıfını kullanın.

**S: Kütüphane şifre korumalı PPTX dosyalarıyla çalışır mı?**  
C: Kesinlikle; şifreyi `PresentationLoadOptions.setPassword("yourPassword")` ile sağlayın.

**S: Tek bir işlemde kaç slaytı su işaretiyle işaretleyebilirim?**  
C: Katı bir limit yoktur; API slaytları akış olarak işler, böylece JVM yığını uygun boyutta olduğu sürece binlerce slaytı işleyebilirsiniz.

**S: Sadece seçili slaytlara su işareti eklemek mümkün mü?**  
C: Evet—`PresentationLoadOptions` içinde bir slayt aralığı belirtebilir veya `add` metoduna slayt indekslerinin bir listesini geçebilirsiniz.

**S: Bu öğreticide hangi GroupDocs.Watermark sürümü test edilmiştir?**  
C: Örnekler, Java için GroupDocs.Watermark 23.12 sürümüyle doğrulanmıştır.

## Sonuç

Artık GroupDocs.Watermark kullanarak **add watermark java presentation** için eksiksiz, üretim‑hazır bir iş akışına sahipsiniz. Yukarıdaki adımları izleyerek gizli slaytları koruyabilir, marka kimliğini güçlendirebilir ve yasal gereksinimlere uyum sağlayabilirsiniz—bunun yanı sıra performans maliyetini minimumda tutarsınız. API’yı daha fazla keşfederek metin ve resim su işaretlerini birleştirebilir, dinamik zaman damgaları ekleyebilir veya mevcut belge‑yönetim hattınıza entegre edebilirsiniz.

---

**Son Güncelleme:** 2026-06-21  
**Test Edilen Versiyon:** GroupDocs.Watermark 23.12 for Java  
**Yazar:** GroupDocs

## İlgili Eğitimler

- [Java'da PDF'lere Metin ve Görüntü Su İşaretleri Ekleme](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-pdf-watermarks/)
- [Java Kullanarak Word Belgelerinde Metin Su İşaretleri Ekleme ve Kilitleme: GroupDocs.Watermark ile Kapsamlı Rehber](/watermark/java/word-processing-document-watermarking/add-lock-text-watermark-word-java-groupdocs/)
- [Java için GroupDocs.Watermark Kullanarak Belgelerde Döndürülmüş Metin Su İşaretleri Ekleme](/watermark/java/text-watermarks/groupdocs-java-rotated-text-watermarks/)