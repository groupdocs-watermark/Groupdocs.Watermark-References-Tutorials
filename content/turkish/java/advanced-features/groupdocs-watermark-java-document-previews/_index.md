---
date: '2026-09-26'
description: GroupDocs.Watermark kullanarak belgeyi görüntüye dönüştürmeyi ve Java
  ile thumbnail'lar oluşturmayı öğrenin. Adım adım rehber, kurulum, preview streams
  ve performance tips konularını kapsar.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: GroupDocs.Watermark kullanarak belgeyi görüntüye dönüştürmeyi ve Java
  ile thumbnail'lar oluşturmayı öğrenin. Bu rehber, installation, stream handling
  ve performance optimisation konularında hızlı preview creation için size yol gösterir.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: GroupDocs.Watermark Java ile belgeyi görüntüye dönüştür
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: GroupDocs.Watermark Java ile belgeyi görüntüye dönüştür
type: docs
url: /tr/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Belgeyi Görüntüye Dönüştürme - GroupDocs.Watermark Java

Çok sayfalı belgelerin hafif görüntü önizlemelerini oluşturmak, portal, içerik‑yönetim sistemleri ve bulut depolama hizmetleri için yaygın bir gereksinimdir. **convert document to image** işlemiyle son kullanıcılara tam dosyayı yükleme maliyeti olmadan hızlı bir görsel ipucu sunarsınız. GroupDocs.Watermark Java kütüphanesi yalnızca filigran eklemekle kalmaz, aynı zamanda tek bir geçişte her sayfa için **java generate thumbnails** yapabilen yüksek performanslı bir önizleme motoru sağlar.

Bu öğreticide kütüphaneyi nasıl kuracağınızı, özel sayfa akışları oluşturmayı, kaynakları güvenli bir şekilde serbest bırakmayı ve sonunda bir kaynak belgenin her sayfası için görüntü önizlemeleri üretmeyi öğreneceksiniz. Talimatlar Java ve nesne‑yönelimli kavramlara aşina geliştiriciler için yazılmıştır ve büyük dosya gruplarını işlemek için en iyi uygulama ipuçlarını içerir.

## Hızlı Yanıtlar
- **İlk adım nedir?** GroupDocs.Watermark Maven bağımlılığını ekleyin ve kaynak dosya yolu ile bir `Watermarker` başlatın.  
- **Önizleme görüntüleri nasıl oluşturulur?** Her sayfa için bir çıktı akışı açmak üzere `ICreatePageStream` uygulayın, ardından uygun seçeneklerle `generatePreview()` çağırın.  
- **Lisans gerekir mi?** Temel senaryolar için bir deneme sürümü yeterlidir, ancak tam lisans filigranları kaldırır ve toplu işleme özelliğini açar.  
- **200 sayfadan büyük PDF’leri işleyebilir miyim?** Evet – kütüphane sayfaları akış olarak işler, bu sayede 500 sayfalık dosyalarda bile bellek kullanımı düşük kalır.  
- **Hangi görüntü formatları destekleniyor?** PNG, JPEG, BMP ve TIFF kutudan çıkar çıkmaz kullanılabilir.

## convert document to image nedir?
**convert document to image** ifadesi, bir kaynak dosyanın (PDF, DOCX, PPTX vb.) her sayfasının PNG veya JPEG gibi bir raster görüntüsüne dönüştürülmesi sürecini tanımlar. Bu dönüşüm, küçük resim galerileri, önizleme bölmeleri ve mobil‑uyumlu belge görüntüleyicileri için faydalıdır.

## Önizleme oluşturma için neden GroupDocs.Watermark kullanmalı?
GroupDocs.Watermark **30+ giriş formatı** destekler ve **500 sayfaya** kadar belgeler için önizleme oluşturabilir; tüm dosyayı belleğe yüklemez. İçsel olarak sayfaları sıralı işler, bu da büyük PDF’lerde Java yığını kullanımını 50 MB’nin altında tutar. Kütüphane ayrıca yerleşik görüntü optimizasyonu sunar; DPI, renk derinliği ve sıkıştırma seviyesini belirleyebilirsiniz, bu da genellikle **%70 daha küçük** küçük resimler elde etmenizi sağlar.

## Önkoşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- **Java Development Kit (JDK) 11 veya daha yeni** – kütüphane Java 8+ için derlenmiştir, ancak JDK 11 uzun vadeli destek ve daha iyi performans sağlar.
- **Maven 3.6+** – bağımlılık yönetimi için.
- **GroupDocs.Watermark for Java sürüm 24.11** – yazım anındaki en son kararlı sürüm.
- **Java I/O akışları hakkında temel bilgi** – her önizleme sayfası için `FileOutputStream` nesneleri oluşturacaksınız.
- **Bir lisans anahtarı** (üretim için isteğe bağlı) – deneme sürümü önizleme boyutunu belge başına 5 MB ile sınırlar.

## GroupDocs.Watermark for Java Nasıl Kurulur

GroupDocs.Watermark’ı kurmak için önce Maven deposunu ekleyin, ardından kütüphaneyi projenizin `pom.xml` dosyasına bağımlılık olarak dahil edin. Bu, Maven’ın doğru artefaktları indirmesini ve sınıfların derleme ve çalışma zamanında sınıf yolunda bulunmasını sağlar.

### Maven Bağımlılığı Ekle
Kütüphane Maven Central üzerinden dağıtılır. Aşağıdaki kod parçacığını `<dependencies>` bloğu içinde `pom.xml` dosyanıza ekleyin:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Pro tip:** Versiyon numarasını bir özellik (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) içinde tutun; böylece yükseltme yapmak kolay olur.

### Doğrudan indirme (alternatif)
Manuel kurulum tercih ediyorsanız, resmi sürüm sayfasından JAR dosyasını indirebilirsiniz: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Lisans Nasıl Alınır ve Uygulanır

GroupDocs.Watermark’a bir lisans uygulamak, deneme sınırlamalarını kaldırır ve varsayılan filigran katmanını devre dışı bırakır. Lisans dosyasını bilinen bir konuma yerleştirin ve API’yı ona yönlendirin, ya da diğer tüm çağrılardan önce kod içinde lisans yolunu doğrudan belirtin. Yüklendikten sonra tüm sonraki işlemler tam özellikli modda çalışır.

Şunları yapabilirsiniz:

- **Ücretsiz deneme isteyin** GroupDocs portalından – 30‑günlük bir lisans dosyası sağlar.
- **Değerlendirme ortamları için geçici lisans oluşturun** çevrimiçi lisans üreteci aracılığıyla.
- **Ticari lisans satın alın** sınırsız üretim kullanımı ve öncelikli destek için.

Lisans dosyasını (`GroupDocs.Watermark.lic`) projenizin kök dizinine koyun veya `Watermarker.setLicense("path/to/license.file")` ile programatik olarak yolunu belirtin.

## Watermarker Nasıl Başlatılır

`Watermarker` sınıfını, kaynak belgenin yolunu sağlayarak başlatın; korumalı dosyalar için isteğe bağlı bir şifre de ekleyebilirsiniz. Yapıcı, formatı doğrular ve iç parser’ları hazırlar, böylece hemen önizleme veya filigran metodlarını çağırabilirsiniz. Oluşturduktan sonra, gerekirse aynı örneği birden fazla işlemde yeniden kullanmak için bir referans tutun.

`Watermarker` sınıfı, GroupDocs.Watermark’ın belge yükleyip filigran ekleme ve önizleme oluşturma gibi işlemleri gerçekleştiren çekirdek nesnesidir.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – kaynak dosyanın mutlak ya da göreli yolu.
- Yapıcı dosya formatını doğrular ve iç parser’ları hazırlar.

> **Definition anchor:** `Watermarker`, GroupDocs.Watermark for Java’da tüm belge‑işleme eylemlerinin giriş noktasıdır.

## Önizleme Oluşturma İçin Sayfa Akışları Nasıl Oluşturulur

Kütüphanenin her işlediği sayfa için çağırdığı `ICreatePageStream` arayüzünü uygulayarak özel sayfa akışları oluşturun. Uygulamanız, genellikle `FileOutputStream` olan yeni bir `OutputStream` üretmeli ve bu akış sayfa numarasına göre benzersiz bir dosya adına yönlendirilmelidir. Bu yaklaşım, her sayfanın çıktısını izole eder ve veri çakışmalarını önler.

**java generate thumbnails** yapmak için, işlenen her sayfa için bir akış sağlamalısınız. `ICreatePageStream` arayüzünü uygulayın; kütüphane her işlediği sayfa için sizin uygulamanızı çağırır.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** sayfa numarasını dosya adına doğrudan eklemenizi sağlar; bu da toplu işleme sürecini basitleştirir.
- Metot, her sayfa için yeni bir `OutputStream` döndürür, böylece önceki sayfalar sonraki yazmalara müdahale etmez.

> **Definition anchor:** `ICreatePageStream`, her önizleme sayfası için çıktı akışlarının nasıl oluşturulacağını tanımlamanıza olanak veren bir geri çağırma arayüzüdür.

## Önizleme Oluşturduktan Sonra Sayfa Akışları Nasıl Serbest Bırakılır

Bir sayfa görüntüsü yazıldıktan sonra, kütüphane `IReleasePageStream`’i çağırarak ilgili çıktı akışını kapatıp temizlemenizi sağlar. Bu geri çağırmayı uygulayarak dosya tanıtıcılarını kapatabilir, tamponları boşaltabilir ve ek loglama yapabilirsiniz. Doğru temizlik, tanıtıcı sızıntılarını önler ve sonraki sayfaların sorunsuz işlenmesini sağlar.

Doğru kaynak temizliği dosya‑tanıtıcı sızıntılarını önler ve JVM’in tanıtıcı sayısını tükenmekten korur. Kütüphane bir sayfa bittiğinde sinyal verdiğinde akışları kapatmak için `IReleasePageStream`’i uygulayın.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definition anchor:** `IReleasePageStream`, her sayfaya özgü çıktı kaynaklarını nasıl yok edeceğinizi tanımlamanıza izin veren bir geri çağırma arayüzüdür.

## Belge Önizlemeleri Nasıl Oluşturulur (convert document to image)

Önizlemeler, `Watermarker` örneği üzerinde `generatePreview()` metodunu çağırarak, çözünürlük, görüntü formatı ve sayfa aralığını tanımlayan bir `PreviewOptions` nesnesi ile oluşturulur. Metot her sayfayı döner, sizin akış oluşturucularınızı kullanarak raster görüntüyü yazar ve ardından akışları serbest bırakır. Bu süreç, belge sayfalarını temsil eden bir dizi görüntü dosyası üretir.

`Watermarker`, `FeatureCreatePageStream` ve `FeatureReleasePageStream` hazır olduğunda önizleme motorunu çalıştırabilirsiniz. `generatePreview()` metodu her sayfayı iteratif olarak işler, akış oluşturucularınızı çağırır, görüntüyü yazar ve sonunda akışları serbest bırakır.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** DPI’yı kontrol eder; web küçük resimleri için 150 DPI iyi bir dengedir.
- **`ImageFormat`** PNG, JPEG, BMP veya TIFF olabilir; ihtiyacınıza göre seçin.
- Metot sayfaları sıralı işler, bu sayede yüzlerce sayfalı belgelerde bile bellek tüketimi düşük kalır.

> **Definition anchor:** `generatePreview()` API çağrısı, sağladığınız akışları kullanarak yüklü belgenin her sayfasını bir görüntüye dönüştürür.

## convert document to image'ın Pratik Uygulamaları

Görüntü önizlemeleri oluşturmak birçok olasılık sunar:

1. **Belge tarayıcıları** – Kullanıcıların büyük PDF’leri açmadan göz atabilmesi için PNG küçük resim ızgarası gösterin.
2. **Arama sonuçları snippet’ları** – Arama indeks girişlerine önizleme resmi ekleyerek daha zengin bir UI sağlayın.
3. **E‑posta ekleri** – Ekli PDF’lerin gövdesine küçük bir önizleme gömün.
4. **Mobil uygulamalar** – Tam PDF yerine 200 KB PNG önizlemeler göndererek bant genişliğini azaltın.
5. **Uyum portalları** – Sözleşmelerin yasal olarak gerektirdiği filigranlı sürümlerini denetim izleri için görüntü olarak render edin.

## java generate thumbnails yaparken Performans Düşünceleri

Toplu işlem yaparken şu optimizasyon ipuçlarını aklınızda tutun:

- **Akış tamponlama** – Disk I/O’yu azaltmak için `FileOutputStream`’i `BufferedOutputStream` içinde sarın.
- **Paralel toplu yürütme** – Java’nın `ForkJoinPool`’unu kullanarak birden fazla belgeyi aynı anda işleyin; her görev kendi `Watermarker` örneğini oluşturmalı, böylece iş parçacığı güvenliği sağlanır.
- **Küçük resimler için DPI’yı sınırlayın** – Çoğu UI senaryosu için 72–150 DPI yeterlidir; daha yüksek DPI yalnızca baskı‑hazır önizlemeler için kullanılmalı.
- **Lisans nesnelerini yeniden kullanın** – Lisans dosyasını JVM başına bir kez yüklemek ek yükü azaltır.
- **Belleği izleyin** – Kütüphane yalnızca geçerli sayfayı bellekte tutar. Çok büyük dosyalar için ara sıra oluşabilecek artışları karşılamak üzere JVM yığınına (ör. `-Xmx512m`) hafif bir artış eklemeyi düşünün.

## Yaygın Tuzaklar ve Nasıl Önlenir

| Semptom | Muhtemel neden | Çözüm |
|---------|----------------|-------|
| `OutOfMemoryError` during preview generation | 1000‑sayfalık PDF’de 300 DPI ile `ImageFormat.Jpeg` kullanmak | DPI’yı düşürün veya daha düşük renk derinliğiyle PNG’ye geçin |
| Empty preview files | `FeatureCreatePageStream` her sayfa için aynı `FileOutputStream` döndürüyor | Her `pageNumber` için yeni bir akış oluşturulduğundan emin olun |
| Preview images are rotated | Kaynak PDF’nin döndürme meta verileri göz ardı ediliyor | `previewOptions.setRotatePages(true)` çağırın (varsa) |
| License warning appears | Lisans dosyası bulunamadı veya yol hatalı | `Watermarker.setLicense("path/to/license.file")` çağrısının diğer API çağrılarından önce çalıştığını doğrulayın |

## Sıkça Sorulan Sorular

**S: Şifre korumalı PDF’ler için önizleme oluşturabilir miyim?**  
C: Evet. Şifreyi `Watermarker` yapıcısına geçirin: `new Watermarker("file.pdf", "password")`.

**S: Önizleme çıktısı için hangi görüntü formatları destekleniyor?**  
C: PNG, JPEG, BMP ve TIFF mevcuttur. Kayıpsız küçük resimler için PNG önerilir.

**S: Tek bir çağrıda kaç sayfa işlenebilir?**  
C: Kütüphane katı bir sınır koymaz; depolama alanı ve I/O throughput’ı izin verdiği sürece binlerce sayfalı belgeler önizlenebilir.

**S: Her sunucu örneği için ayrı bir lisans gerekir mi?**  
C: Tek bir lisans dosyası birden çok örnek arasında kullanılabilir; toplam kullanım lisans koşullarına uygun olduğu sürece.

**S: Tek bir birleşik küçük resim (ör. sadece ilk sayfa) oluşturmanın bir yolu var mı?**  
C: Evet. `previewOptions.setPages(new int[]{1})` ayarlayarak yalnızca ilk sayfanın önizlemesini sınırlayabilirsiniz.

## Sonuç

GroupDocs.Watermark kullanarak **convert document to image** ve **java generate thumbnails** için eksiksiz, üretim‑hazır bir iş akışı elde ettiniz. Özel sayfa‑akış işleyicileriyle bellek kullanımını düşük tutar, `PreviewOptions` ayarlarıyla görüntü kalitesi ve dosya boyutunu kontrol edersiniz. Bu teknikler, Java tabanlı herhangi bir uygulamaya—web portalı, masaüstü istemcisi veya bulut‑yerel mikroservis—hızlı, yüksek‑kaliteli önizlemeler eklemenizi sağlar.

---

**Son Güncelleme:** 2026-09-26  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## İlgili Eğitimler

- [GroupDocs.Watermark for Java kullanarak Belge Bilgilerini Alma: Adım Adım Kılavuz](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [GroupDocs.Watermark Java için Gelişmiş Filigran Özellikleri Eğitimleri](/watermark/java/advanced-features/)
- [Java’da GroupDocs.Watermark ile Görüntü Filigranı Ekleme: Adım Adım Kılavuz](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)