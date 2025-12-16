---
date: '2025-12-16'
description: GroupDocs.Watermark for Java kullanarak belgeleri önizlemeyi öğrenin
  ve Maven GroupDocs Watermark entegrasyonu ile kolayca küçük resimler oluşturun.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 'Java''da GroupDocs.Watermark ile Belgeleri Önizleme: İleri Düzey Kılavuz'
type: docs
url: /tr/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Java'da GroupDocs.Watermark ile Belgeleri Önizleme: İleri Düzey Kılavuz

## Giriş

Bu kılavuzda, GroupDocs.Watermark Java kütüphanesini kullanarak **belgeleri önizleme** yöntemini verimli bir şekilde öğreneceksiniz. Belge önizlemeleri oluşturmak, büyük miktarda dosya yöneten uygulamalar için kritik bir özelliktir; kullanıcıların tüm belgeyi açmadan içeriğe göz atmasını sağlar. Aşağıdaki adımları izleyerek **java generate thumbnail** görüntülerinin nasıl oluşturulacağını ve kütüphaneyi **maven groupdocs watermark** aracılığıyla entegre edeceğinizi de göreceksiniz. Geliştirme ortamınızı hazırlayarak başlayalım.

## Hızlı Yanıtlar
- **Birincil amaç nedir?** Desteklenen herhangi bir belgenin hafif sayfa‑sayfa önizlemelerini (küçük resimler) oluşturun.  
- **Hangi kütüphane gereklidir?** GroupDocs.Watermark for Java (version 24.11).  
- **Kütüphaneyi nasıl eklerim?** Kurulum bölümünde verilen Maven kod parçacığını kullanın.  
- **Tüm sayfalar için önizleme oluşturabilir miyim?** Evet – API her sayfayı bir görüntü dosyasına akıtıyor.  
- **Lisans gerekli mi?** Temel testler için bir deneme sürümü çalışır; üretim kullanımı için tam lisans gereklidir.  

## Belge Önizleme Oluşturma Nedir?

Belge önizleme oluşturma, bir kaynak dosyanın (PDF, DOCX, VDX vb.) her sayfasını PNG gibi bir görüntü formatına dönüştürür. Bu önizleme görüntüleri, dosya tarayıcılarında, web portallarında veya mobil uygulamalarda gösterilebilen küçük resimler olarak görev yapar ve kullanıcı deneyimini büyük ölçüde iyileştirir, yükleme sürelerini azaltır.

## Neden Java için GroupDocs.Watermark Kullanılmalı?

- **Speed & Scalability** – Optimize edilmiş yerel kod, büyük belgeleri hızlı bir şekilde işler.  
- **Broad Format Support** – Kutudan çıkar çıkmaz 100'den fazla dosya türüyle çalışır.  
- **Built‑in Watermarking** – Önizlemeler oluştururken filigran ekleyebilir, varlıklarınızı koruyabilirsiniz.  
- **Simple API** – Yüksek kaliteli küçük resimler üretmek için minimum kod gerekir.

## Önkoşullar

1. **Java Development Kit (JDK)** – JDK 8 veya daha yeni bir sürüm yüklü.  
2. **IDE** – IntelliJ IDEA, Eclipse veya tercih ettiğiniz herhangi bir editör.  
3. **Maven** – Bağımlılık yönetimi için (aşağıdaki Maven kurulumuna bakın).  
4. **Basic Java knowledge** – Dosya G/Ç ve nesne‑yönelimli programlamaya aşina olmak.  

## Java için GroupDocs.Watermark Kurulumu

Projenizde GroupDocs.Watermark kullanmaya başlamak için, onu bir Maven bağımlılığı olarak ekleyin:

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

Alternatif olarak, en son JAR dosyasını doğrudan resmi sürüm sayfasından indirebilirsiniz:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### Lisans Edinme

- **Free Trial** – Kütüphaneyi sınırlı işlevsellikle test edin.  
- **Temporary License** – Tam özellik değerlendirmesi için kısa vadeli bir anahtar edinin.  
- **Full License** – Sınırsız kullanım ve öncelikli destek için satın alın.  

## Uygulama Kılavuzu

### Watermarker Başlatma

#### Genel Bakış
İlk adım, kaynak belgeye işaret eden bir `Watermarker` örneği oluşturmaktır.

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

*Ana nokta:* `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` ifadesini önizlemek istediğiniz dosyanın gerçek yolu ile değiştirin.

### Önizleme Oluşturma için Sayfa Akışı Oluşturma

#### Genel Bakış
Özel bir akış oluşturucu, API'ye her sayfanın önizleme görüntüsünün nereye yazılacağını söyler.

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

`fileNameTemplate` bir yer tutucu (`%s`) kullanır; API bu yer tutucuyu mevcut sayfa numarasıyla değiştirerek `page1.png`, `page2.png` gibi dosyalar üretir.

### Sayfa Akışını Serbest Bırakma

#### Genel Bakış
Bir önizleme görüntüsü yazıldıktan sonra, akış sistem kaynaklarını serbest bırakmak için kapatılmalıdır.

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

Akışların doğru şekilde serbest bırakılması, özellikle büyük belge grupları işlenirken bellek sızıntılarını önler.

### Belge Önizlemesi Oluşturma

#### Genel Bakış
`Watermarker`, akış oluşturucu ve serbest bırakma işleyicisi hazır olduğunda, her sayfa için önizlemeler oluşturabilirsiniz.

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

*Ana nesnelerin açıklaması:*  
- `createPageStream` – her PNG dosyasının nereye kaydedileceğini belirler.  
- `releasePageStream` – yazma işleminden sonra dosya tutamacının kapatılmasını sağlar.  
- `previewOptions` – `generatePreview` çağrısı için iki işleyiciyi bir araya getirir.

## Pratik Uygulamalar

Belge önizlemeleri oluşturmak birçok gerçek dünya senaryosunda faydalıdır:

1. **PDF Viewer Apps** – Tam PDF'i yüklemeden küçük resim şeritleri gösterir.  
2. **Content Management Systems (CMS)** – Editörlerin belgeleri hızlıca göz atmasını sağlar.  
3. **Cloud Storage Services** – Depolanan dosyalar için görsel küçük resimler sunar, gezinmeyi iyileştirir.

## Performans Düşünceleri

- **Memory Management** – Yukarıda gösterilen akış‑serbest bırakma desenini kullanarak bellek ayak izini düşük tutun.  
- **I/O Optimization** – Yüzlerce sayfa işlenirken tamponlu akışlar disk gecikmesini daha da azaltabilir.  
- **Parallel Processing** – Toplu işlemler için, Java’nın `ExecutorService` kullanarak birden fazla belgeyi aynı anda işlemeyi düşünün.

## Yaygın Sorunlar ve Çözümler

| Sorun | Neden | Çözüm |
|-------|-------|-----|
| Önizleme dosyaları oluşturulmadı | Çıktı dizini yolu hatalı veya yazma izinleri eksik | `YOUR_OUTPUT_DIRECTORY` varlığını ve yazılabilirliğini doğrulayın |
| Büyük PDF'lerde bellek yetersizliği hatası | Akışlar zamanında serbest bırakılmadı | `FeatureReleasePageStream`'in doğru şekilde uygulandığından emin olun |
| Desteklenmeyen dosya formatı | Belge türü GroupDocs.Watermark tarafından desteklenmiyor | Kütüphanenin format destek listesini kontrol edin; gerekirse desteklenen bir türe dönüştürün |

## Sıkça Sorulan Sorular

**S: Parola korumalı belgeler için önizleme oluşturabilir miyim?**  
C: Evet. `Watermarker` yapıcısının şifre parametresini kabul eden sürümünü kullanarak belgeyi uygun şifreyle yükleyin, ardından gösterildiği gibi önizleme oluşturma işlemine devam edin.

**S: Kütüphane PNG dışındaki diğer görüntü formatlarını destekliyor mu?**  
C: Önizleme API'si varsayılan olarak PNG üretir, ancak gerekirse elde edilen akışları standart Java görüntü kütüphaneleriyle JPEG veya BMP'ye dönüştürebilirsiniz.

**S: Tek bir çalıştırmada kaç sayfa önizleyebilirim?**  
C: Katı bir sınır yoktur; ancak çok büyük belgeleri işlerken toplu işleme veya JVM yığın boyutunu artırma faydalı olabilir.

**S: Önizleme oluşturmak için lisans zorunlu mu?**  
C: Değerlendirme için bir deneme lisansı çalışır, ancak üretim dağıtımları için filigranları kaldırmak ve tüm özelliklerin kilidini açmak amacıyla tam lisans gereklidir.

**S: Önizlemelerin görüntü çözünürlüğünü özelleştirebilir miyim?**  
C: Evet. `PreviewOptions`, `generatePreview` çağrısı yapılmadan önce DPI ayarlarını belirtebileceğiniz `setResolution` gibi özellikler sunar.

## Sonuç

Artık Java'da GroupDocs.Watermark kullanarak **belgeleri nasıl önizleyeceğinize** dair eksiksiz, üretime hazır bir iş akışına sahipsiniz. `Watermarker`'ı başlatarak, sayfa akışlarını yöneterek ve kaynakları doğru şekilde serbest bırakarak ölçekli yüksek kaliteli küçük resimler oluşturabilirsiniz. Bu teknikleri, belge yoğun uygulamalarda kullanıcı deneyimini artırmak için uygulayın.

---

**Son Güncelleme:** 2025-12-16  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs