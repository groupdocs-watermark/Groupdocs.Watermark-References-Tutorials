---
date: '2026-01-21'
description: GroupDocs.Watermark for Java kullanarak PDF'ye metin filigranı eklemeyi
  ve görüntü açıklamalarına eklemeyi öğrenin; belgelerinizi etkili bir şekilde koruyun.
keywords:
- Add Text Watermark to PDF
- Java PDF Watermarking
- GroupDocs.Watermark for Java
title: GroupDocs.Watermark for Java ile Görüntü Açıklamalarına PDF Üzerinde Metin
  Filigranı Ekleme
type: docs
url: /tr/java/pdf-document-watermarking/add-text-watermark-pdf-annotations-java/
weight: 1
---

# GroupDocs.Watermark for Java Kullanarak Görüntü Açıklamalarına Metin Su İşareti PDF Ekleme

## Giriş
PDF belgelerinizi yetkisiz kullanım veya dağıtımdan korumak çok önemlidir. Bu öğreticide **how to add text watermark pdf** yöntemini görüntü açıklamalarına nasıl ekleyeceğinizi öğreneceksiniz; bu teknik, içeriğinizi korurken orijinal düzeni de korur. GroupDocs.Watermark for Java kurulumu, su işaretinin uygulanması ve su işaretli PDF'nin kaydedilmesi adımlarını adım adım göstereceğiz, böylece PDF'lerinizi güvenle koruyabilirsiniz.

### Hızlı Yanıtlar
- **Hangi kütüphane kullanılıyor?** GroupDocs.Watermark for Java  
- **Bu rehberin hedeflediği anahtar kelime nedir?** add text watermark pdf  
- **Lisans gerekiyor mu?** Üretim kullanımı için geçici veya tam lisans gereklidir  
- **Büyük dosyalarda su işaretiyle pdf koruyabilir miyim?** Evet, toplu işleme ve doğru bellek yönetimi yardımcı olur  
- **Su işareti pdf java daha sonra kaldırılabilir mi?** Evet, GroupDocs.Watermark kaldırma API'leri sağlar  

## “add text watermark pdf” nedir?
Metin su işareti PDF eklemek, yarı saydam bir metni (ör. “Confidential”) doğrudan PDF sayfalarına veya görüntü açıklamaları gibi belirli öğelere gömmek anlamına gelir. Bu görsel uyarı, yetkisiz kopyalamayı engeller ve belgenin sahipliğini açıkça işaretler.

## Neden GroupDocs.Watermark for Java kullanmalı?
GroupDocs.Watermark, PDF iç yapısının karmaşıklığını soyutlayan yüksek seviyeli bir API sunar, çok çeşitli açıklama türlerini destekler ve tüm ana Java sürümlerinde çalışır. Ayrıca yerleşik lisanslama, toplu işleme ve performans iyileştirmeleri içerir—kurumsal düzeyde PDF koruması için mükemmeldir.

## Önkoşullar
- **Java Development Kit (JDK)** 8 veya üzeri  
- **Maven** (veya manuel JAR yönetimi) bağımlılık yönetimi için  
- PDF temel kavramları ve Java sözdizimi hakkında bilgi  

## GroupDocs.Watermark for Java Kurulumu
**GroupDocs.Watermark**'i Java projenize aşağıdaki talimatları izleyerek dahil edin:

### Maven Kurulumu
Aşağıdakileri `pom.xml` dosyanıza ekleyin:
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
Alternatif olarak, en yeni sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirin.

#### Lisans Edinme
- **Ücretsiz Deneme** – lisans olmadan temel özellikleri keşfedin.  
- **Geçici Lisans** – geliştirme sırasında tam yetenekleri açar.  
- **Satın Alma** – üretim ve premium destek için kalıcı lisans edinin.

### Temel Başlatma
GroupDocs.Watermark kullanmaya başlamak için:
```java
import com.groupdocs.watermark.Watermarker;

public class WatermarkDemo {
    public static void main(String[] args) {
        // Initialize the watermarker with your PDF document path
        PdfLoadOptions loadOptions = new PdfLoadOptions();
        try (Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.pdf", loadOptions)) {
            System.out.println("Setup complete!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## PDF Görüntü Açıklamalarına Metin Su İşareti PDF Ekleme
Aşağıda, bir metin su işaretini görüntü açıklamalarına nasıl gömeceğinizi adım adım gösteren bir kılavuz bulunmaktadır.

### Adım 1: PDF Belgesini Yükleyin
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PdfLoadOptions;

PdfLoadOptions loadOptions = new PdfLoadOptions();
try (Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.pdf", loadOptions)) {
    System.out.println("PDF loaded successfully.");
}
```

### Adım 2: Metin Su İşaretini Oluşturun
```java
import com.groupdocs.watermark.contents.PdfAnnotation;
import com.groupdocs.watermark.watermarks.TextWatermark;
import java.awt.Font;
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.saving.SizingType;

TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Bottom);
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(0.5);
```

### Adım 3: Su İşaretini Görüntü Açıklamalarına Uygulayın
```java
import com.groupdocs.watermark.contents.PdfPage;

for (PdfPage page : watermarker.getContent().getPages()) {
    for (PdfAnnotation annotation : page.getAnnotations()) {
        // Add watermark to image annotations
        if (annotation.getImageData() != null) {
            annotation.addWatermark(textWatermark);
        }
    }
}
```

### Adım 4: Su İşaretli PDF'yi Kaydedin
```java
watermarker.save("YOUR_DOCUMENT_DIRECTORY/watermarked_document.pdf");
System.out.println("Document saved with watermark.");
```

## Yaygın Sorunlar ve Çözümleri
- **Eksik Bağımlılıklar** – `pom.xml` içindeki her `<dependency>` kaydının yukarıda gösterilen sürümlerle eşleştiğini doğrulayın.  
- **Dosya Yolu Sorunları** – Mutlak yollar kullanınYOUR_DOCUMENT_DIRECTORY Formatlar** – GroupDocs.Watermark PDF, DOCX, PPTX ve çeşitli görüntü tiplerini destekler; diğer formatlar bir istisna oluşturur.  
- **remove watermark pdf işaretini kaldırmanız gerekirse, belgeyi kaydetmeden önce `watermarker.removeWatermarks()` kullanın.  

## Pratik Uygulamalar
Metin su iş.arlama Varlıkları** – PDF'leri şirket sloganlarıyla markalayın.  
4. **Akademik Taslak Düşünceleri
- **Toplu İşleme** – PDF koleksiyonunu döngüye alıp mümkün olduğunda tek bir `Watermarker` örneğini yeniden kullanın.  
- **Bellek Yönetimi** – Büyük dosyalar için JVM yığınını (`-Xmx2g` veya daha yüksek) artırın ve `Watermarker`'ı gösterildiği gibi try‑with‑resources bloğunda kapatın işare**ileri için su işareti sürecini özelleştirebilirsiniz.  
2. **Sayfa başına su işareti sayısında bir limit var mı?**  
   Katı bir limit yok, ancak aşırı su işareti okunabilirliği ve işleme süresini etkileyebilir.  
3. **Gerekirse su işaretini nasıl kaldırırım?**  
   GroupDocs.Watermark’ın kaldırma API'sini (`watermarker.removeWatermarks()`) kullanın.  
4. **Bu yöntem şifreli PDF'leri sağladığınız sürece.  
5. **Hangi dosya boyutlarıyi suurum?**  
A: `TextWatermark`'i `SizingType.ScaleToParentDimensions` ile kullanıp uygun bir `scaleFactor` ayarlayarak su işareti, açıklama boyutuna uyum sağlar ve PDF'yi bozmadan görünür olur.  

** Java kullanarak bir PDF'den programlı olarak su işareti kaldırmanın bir yolu var mı?()` çağırın. Bu, “remove watermark pdf java” senaryosu için önerilen yaklaşımdır.  

**Q: GroupDocs.Watermark şifre korumalı PDF'leri destekliyor: Kesinlikle. `Watermarker`'ı başlatırken şifreyi `PdfLoadOptions` içine geçirin.  

**QA: Kütüphane JDK 8 ve üzeri, Java 11, 17 ve 21 dahil olmak üzere tüm modern sürümlerle çalışır.  

**Q: Tek bir çalıştırmada onlarca PDF'yi toplu iş  
A: Evet.arak görüntıripsiniz. Yukarıdaki adımları izleyerek hassas belgeleri, pazarlama materyallerini ve akademik taslakları koruyabilir, kodunuzu temiz ve sürdürülebilir tutabilirsiniz. Görüntü su işaretleri, dinamik metinler ve OCR‑tabanlı su işaretleme gibi ek özellikleri keşfederek PDF koruma stratejinizi daha da genişletebilirsiniz.

---

**Last Updated:** 2026-01-21  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

## Kaynaklar
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)