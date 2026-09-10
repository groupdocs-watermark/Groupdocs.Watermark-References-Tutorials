---
date: '2025-12-19'
description: GroupDocs Watermark Maven'i Java ile .vsdx gibi diyagram dosyalarındaki
  filigranları yönetmek için nasıl kullanacağınızı öğrenin, belge bütünlüğünü artırın
  ve fikri mülkiyeti koruyun.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – Java ile Diyagram Filigranlarını Yönetin
type: docs
url: /tr/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – Diyagram Su İşaretlerini Java ile Yönet

Belgelerde su işaretlerini yönetmek, fikri mülkiyeti korumak ve belge bütünlüğünü sürdürmek için esastır. **Bu öğreticide, `.vsdx` gibi diyagram dosyalarından su işaretlerini verimli bir şekilde yüklemek, aramak ve kaldırmak için groupdocs watermark maven nasıl kullanılır gösterilecektir**. İster kurumsal yazılım geliştirin ister belge iş akışlarını otomatikleştirin, bu tekniklerde uzmanlaşmak diyagram su işareti yönetimi üzerinde tam kontrol sağlar.

## Hızlı Yanıtlar
- **Hangi kütüphane gerekiyor?** GroupDocs.Watermark for Java (Maven üzerinden temin edilebilir).  
- **Hangi diyagram formatları destekleniyor?** `.vsdx`, `.vdx` ve diğer Visio formatları.  
- **Metin ve görsel su işaretlerini aynı anda arayabilir miyim?** Evet – arama kriterlerini `or()` ile birleştirin.  
- **Üretim ortamında lisans gerekli mi?** Geçerli bir GroupDocs.Watermark lisansı gereklidir.  
- **Bunu Maven'e nasıl entegre ederim?** Aşağıda gösterilen depo ve bağımlılığı ekleyin.

## groupdocs watermark maven nedir?
`groupdocs watermark maven`, Java için GroupDocs.Watermark kütüphanesinin Maven tabanlı entegrasyonunu ifade eder. Kütüphaneyi `pom.xml` dosyanıza bildirerek, Maven gerekli tüm ikili dosyaları otomatik olarak çözer ve diyagramları yükleyen, su işaretlerini arayan ve programlı olarak kaldıran koda odaklanmanızı sağlar.

## Neden Diagram Su İşareti Yönetimi İçin GroupDocs.Watermark Kullanmalı?
- **Full‑featured API** – birçok diyagram türünde metin, görsel ve şekil su işaretlerini destekler.  
- **Precise removal** – su işaretlerini orijinal diyagram düzenini bozmadan ortadan kaldırır.  
- **Scalable** – büyük diyagram koleksiyonlarını toplu işleme için uygundur.  
- **Maven friendly** – basit bağımlılık yönetimi, projenizi temiz tutar.

## Önkoşullar
1. **Java Development Kit (JDK) 8+** – kütüphane ile uyumluluğu sağlar.  
2. **IDE** – IntelliJ IDEA, Eclipse veya herhangi bir Java‑uyumlu editör.  
3. **GroupDocs.Watermark for Java** – Maven aracılığıyla eklenir (önerilir) veya doğrudan JAR indirilir.  

### Gerekli Kütüphaneler ve Bağımlılıklar
#### Maven Kurulumu
Aşağıdaki yapılandırmayı `pom.xml` dosyanıza ekleyin:

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

#### Doğrudan İndirme
Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

### Lisans Edinme
- **Free Trial:** Kütüphaneyi deneme lisansı ile test edin.  
- **Temporary License:** Değerlendirme için kısa vadeli bir anahtar isteyin.  
- **Purchase:** Sınırsız kullanım için üretim lisansı edinin.

## groupdocs watermark maven ile Bir Diyagram Belgesi Yükleme
Bir diyagram belgesini yüklemek, herhangi bir su işareti işleminden önceki ilk adımdır. Aşağıda, `DiagramLoadOptions` ile bir `Watermarker` örneği oluşturan minimal bir örnek bulunmaktadır.

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

- **Parameters:**  
  - `inputFilePath` – `.vsdx` dosyanızın yolu.  
  - `loadOptions` – diyagramın nasıl ayrıştırılacağını kontrol etmenizi sağlar (ör. şifre koruması).

## groupdocs watermark maven ile Su İşaretlerini Arama
### Metin Su İşaretleri
Metin tabanlı su işaretlerini bulmak için bir `TextSearchCriteria` tanımlayın ve diyagramın ilk sayfasını sorgulayın.

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

- **Key Methods:**  
  - `TextSearchCriteria` – aranacak tam metni belirtir.  
  - `PossibleWatermarkCollection` – bulunan eşleşmeleri saklar.

### Görsel Su İşaretleri
Diyagramınız logo veya resim su işaretleri içeriyorsa, referans görsel ile karşılaştırmak için `ImageDctHashSearchCriteria` kullanın.

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

- **Key Methods:**  
  - `ImageDctHashSearchCriteria` – sağlam eşleşme için referans görselin algısal hash'ini oluşturur.

## Su İşaretlerini Kaldırma
İstenmeyen su işaretlerini belirledikten sonra, bunları temizleyebilir ve diyagramın temiz bir kopyasını kaydedebilirsiniz.

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

- **Key Method:** `clear()` birleştirilmiş kriterlerle bulunan tüm su işaretlerini kaldırır, diyagramı bozulmadan bırakır.

## Pratik Uygulamalar
1. **Enterprise Software Integration** – Özel diyagramları korumak için su işareti yönetimini iş uygulamalarına entegre edin.  
2. **Content Management Systems (CMS)** – Yayınlamadan önce yetkisiz logoların tespitini ve kaldırılmasını otomatikleştirin.  
3. **Legal Document Workflows** – Sözleşme işleme aşamalarında su işaretlerini ekleyin veya çıkarın.  

## Yaygın Sorunlar ve Çözümleme
- **License errors:** `Watermarker` oluşturulmadan önce lisans dosyasının doğru şekilde referans alındığından emin olun.  
- **Large files:** Akış API'lerini kullanın veya 100 MB üzerindeki diyagramlar için JVM yığın boyutunu (`-Xmx2g`) artırın.  
- **Missing watermarks:** Arama kriterlerinin (metin büyük/küçük harf duyarlılığı, görsel benzerlik eşiği) gerçek su işareti içeriğiyle eşleştiğini doğrulayın.

## Sıkça Sorulan Sorular

**Q: Metin ve görselleri aynı anda arayabilir miyim?**  
A: Evet. Kaldırma örneğinde gösterildiği gibi kriterleri `or()` ile birleştirin.

**Q: Diyagram düzenini değiştirmeden su işaretlerini kaldırmak güvenli mi?**  
A: Kesinlikle. API, su işareti nesnelerini hassas bir şekilde hedef alır ve diğer tüm diyagram öğelerini korur.

**Q: GroupDocs.Watermark hangi diyagram formatlarını destekliyor?**  
A: `.vsdx`, `.vdx` gibi Visio formatlarının yanı sıra diğer vektör diyagram türlerini destekler.

**Q: Yüzlerce diyagramı verimli bir şekilde nasıl işleyebilirim?**  
A: Bir toplu döngü uygulayın, mümkün olduğunda tek bir `Watermarker` örneğini yeniden kullanın ve Java’nın `ExecutorService` ile paralel işleme düşünün.

**Q: Su işareti tespitini bir CI/CD boru hattına entegre edebilir miyim?**  
A: Evet. Java kod parçacıklarını derleme betiklerinizde (ör. Maven eklentileri veya Gradle görevleri) dahil ederek dağıtımdan önce diyagramları doğrulayabilirsiniz.

## Sonuç
**groupdocs watermark maven** kullanarak, Java ile diyagram dosyalarından su işaretlerini yükleme, arama ve kaldırma konusunda güçlü ve Maven‑yönetimli bir yol elde edersiniz. Bu yetenek belge güvenliğini artırır, içerik iş akışlarını sadeleştirir ve büyük belge koleksiyonları üzerinde sorunsuz ölçeklenebilir.

---

**Son Güncelleme:** 2025-12-19  
**Test Edilen:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs