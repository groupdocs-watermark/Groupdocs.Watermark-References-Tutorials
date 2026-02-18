---
date: '2026-02-18'
description: GroupDocs.Watermark for Java ile .vsdx gibi diyagram dosyalarına filigran
  eklemeyi ve filigranı kaldırmayı öğrenin. GroupDocs Watermark Java ile belge bütünlüğünü
  koruyun.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: GroupDocs.Watermark for Java kullanarak Diyagramlara Filigran Ekleme
type: docs
url: /tr/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

. Keep them.

Make sure not to translate URLs.

All good.# Diagramlere Watermark Eklemek için GroupDocs.Watermark for Java Kullanımı

Diagram dosyalarında watermark yönetimi, fikri mülkiyeti korumanın ve belgeleri kamu dağıtımı için temiz tutmanın temel bir parçasıdır. Bu rehberde Visio diyagramına **watermark eklemeyi** ve artık gerekmediğinde **watermark kaldırmayı**, **groupdocs watermark java** kütüphanesiyle öğreneceksiniz. İster kurumsal düzeyde bir belge iş akışı oluşturuyor olun, ister hızlı bir yardımcı betik, bu adımlar diagram watermark'ı üzerinde tam kontrol sağlar.

## Hızlı Yanıtlar
- **Java'da diagram watermark'larını hangi kütüphane yönetir?** GroupDocs.Watermark for Java.  
- **Aynı çalıştırmada watermark ekleyip kaldırabilir miyim?** Evet – diyagramı bir kez yükleyip hem ekleme hem de kaldırma işlemlerini uygulayabilirsiniz.  
- **Hangi dosya formatları destekleniyor?** Visio formatları `.vsdx`, `.vdx` ve diğer diagram türleri.  
- **Lisans gerekli mi?** Geliştirme için deneme lisansı yeterlidir; üretim için tam lisans gerekir.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri.

## Diagram bağlamında “watermark ekleme” ne anlama gelir?
Watermark eklemek, bir diagram dosyasına görünür veya görünmez bir işaretçi—metin, logo veya görüntü—gömmek anlamına gelir. Bu işaretçi dosyayla birlikte taşınır, sahipliği kanıtlamayı veya taslak sürümleri işaretlemeyi kolaylaştırır.

## Neden GroupDocs.Watermark for Java Kullanmalısınız?
* **Zengin API** – Birkaç satır kodla hem metin hem de görüntü watermark'larını arayın, ekleyin ve silin.  
* **Çapraz format desteği** – Visio (`.vsdx`, `.vdx`) ve birçok diğer diagram türüyle çalışır.  
* **Performansa odaklı** – Watermark işlemleri için gereken diagram bölümlerini yalnızca yükler, bellek kullanımını düşük tutar.

## Önkoşullar
1. **Java Development Kit (JDK) 8+** – `java -version` komutunun 1.8 veya daha yeni bir sürüm gösterdiğinden emin olun.  
2. **IDE** – IntelliJ IDEA, Eclipse veya tercih ettiğiniz herhangi bir editör.  
3. **GroupDocs.Watermark for Java** – Maven ya da doğrudan JAR indirme yoluyla projenize ekleyin.  

### Gerekli Kütüphaneler ve Bağımlılıklar
Add the repository and dependency to your `pom.xml`:

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

*If you prefer not to use Maven, you can download the latest JAR from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### Lisans Edinme
- **Ücretsiz Deneme:** Lisans anahtarı olmadan tüm özellikleri test edin.  
- **Geçici Lisans:** Değerlendirme için zaman sınırlı bir anahtar isteyin.  
- **Tam Lisans:** Sınırsız üretim kullanımı için bir abonelik satın alın.

## GroupDocs.Watermark for Java'ı Kurma
1. **Kütüphaneyi ekleyin** projenize (Maven ya da manuel JAR).  
2. **`Watermarker` örneği oluşturun** – bu nesne diagramları yüklemek, aramak, eklemek ve kaldırmak için giriş noktasıdır.

## Uygulama Kılavuzu

### Diagram Belgesi Yükleme
Yükleme, **watermark eklemeden** veya **watermark kaldırmadan** önceki ilk adımdır. Aşağıdaki kod, özel yükleme seçenekleriyle bir `.vsdx` dosyasını nasıl açacağınızı gösterir.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Metin Watermark'larını Arama
Yeni bir watermark eklemeden önce, bir metin watermark'ının zaten mevcut olup olmadığını doğrulamak isteyebilirsiniz. Bu kod parçacığı “Company Name” ifadesini arar.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Görüntü Watermark'larını Arama
Bir logo veya watermark olarak kullanılan herhangi bir görüntüyü bulmanız gerekiyorsa, `ImageDctHashSearchCriteria` kullanın. Bu, bilinen bir logoya uyan **watermark kaldırmak** istediğinizde kullanışlıdır.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Watermark'ları Kaldırma
Watermark'ları—metin, görüntü veya her ikisini—belirlediğinizde, diagramdan temizleyebilirsiniz. Aşağıdaki örnek birleşik bir kaldırma işlemini gösterir.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Pratik Uygulamalar
1. **Kurumsal Yazılım Entegrasyonu** – ERP veya belge‑oluşturma platformunuza watermark yönetimini entegre ederek marka tutarlılığını sağlayın.  
2. **İçerik Yönetim Sistemleri (CMS)** – Yüklenen diagramları yetkisiz logolar için otomatik tarayın ve çıkarın.  
3. **Hukuki Belge İşleme** – Taslak aşamalarında “Confidential” metin watermark'ı ekleyin ve son dosyalamadan önce **watermark kaldırın**.

## Yaygın Sorunlar ve Çözümleri
| Belirti | Muhtemel Neden | Çözüm |
|---------|----------------|-------|
| Watermark bulunamadı | Arama metni/görüntüsü tam olarak eşleşmiyor | Kriterleri birleştirmek için `or()` kullanın veya büyük/küçük harf duyarlılığını ayarlayın. |
| Büyük dosyalarda `OutOfMemoryError` | Diagram tamamen belleğe yüklendi | Yalnızca gerekli sayfaları yüklemek için `DiagramLoadOptions.setLoadPages()` kullanın. |
| Kaydedilen dosya bozuk | `watermarker.save()` tüm watermark'lar temizlenmeden önce çağrıldı | `possibleWatermarks.clear()` tamamlandığından ve kaydetmeden sonra `watermarker.close()` çağrıldığından emin olun. |

## Sıkça Sorulan Sorular

**S: Hem metin hem de görüntüleri aynı anda arayabilir miyim?**  
C: Evet. `TextSearchCriteria` ve `ImageDctHashSearchCriteria`'yi `or()` yöntemiyle birleştirin; kaldırma örneğinde gösterildiği gibi.

**S: Watermark'ları diagramı zarar vermeden kaldırmak mümkün mü?**  
C: Kesinlikle. Kütüphane watermark nesnelerini izole eder, bu yüzden `clear()` çağrısı sadece watermark katmanlarını kaldırır ve orijinal diagram içeriğini korur.

**S: GroupDocs.Watermark birden fazla diagram formatını destekliyor mu?**  
C: Evet. `.vsdx`, `.vdx` ve diğer Visio‑uyumlu dosyalar tam olarak desteklenir.

**S: Büyük miktarda belgeyi verimli bir şekilde nasıl yönetebilirim?**  
C: Toplu işleme döngüleri uygulayın, mümkün olduğunda tek bir `Watermarker` örneğini yeniden kullanın ve sayfa yüklemeyi `DiagramLoadOptions` ile sınırlayın.

**S: CI/CD pipeline'ında watermark tespitini otomatikleştirmenin bir yolu var mı?**  
C: Sağlanan Java kod parçacıklarını (ör. Maven veya Gradle) derleme betiklerinize ekleyerek, artefaktları yayınlamadan önce yetkisiz watermark'ların bulunmadığını doğrulayabilirsiniz.

---

**Son Güncelleme:** 2026-02-18  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs