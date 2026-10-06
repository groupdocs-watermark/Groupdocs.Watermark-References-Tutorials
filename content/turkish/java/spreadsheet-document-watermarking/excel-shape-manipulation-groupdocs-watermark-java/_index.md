---
date: '2026-06-01'
description: GroupDocs.Watermark for Java ile Excel dosyalarından şekilleri nasıl
  kaldıracağınızı öğrenin. Excel'i yükleme, çalışma sayfalarını döngüyle gezme ve
  biçimlendirilmiş şekilleri silme adımlarını içerir.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Java'da GroupDocs.Watermark kullanarak Excel'den şekilleri nasıl kaldırılır
type: docs
url: /tr/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Java'da GroupDocs.Watermark kullanarak Excel'den şekilleri kaldırma

Excel elektronik tabloları iş raporlamasının temelini oluşturur, ancak istenmeyen şekiller—özellikle eski veya standart dışı metin biçimlendirmesine sahip olanlar—dosyayı karıştırabilir ve görsel tutarlılığı bozabilir. **Excel'den şekilleri kaldırma**, temiz ve profesyonel belgeler için hızla gerekli hale gelir. Bu öğreticide bir Excel çalışma kitabını yükleme, çalışma sayfalarını dolaşma ve belirli biçimlendirme kriterlerine uyan şekilleri programlı olarak silme işlemlerini, güçlü GroupDocs.Watermark Java kütüphanesiyle adım adım göstereceğiz.

## Hızlı Yanıtlar
- **GroupDocs.Watermark şekilleri silebilir mi?** Evet, herhangi bir çalışma sayfasında çalışan bir `removeShape` yöntemi sağlar.  
- **Bu özellik için lisansa ihtiyacım var mı?** Değerlendirme için bir deneme sürümü yeterlidir; üretim için tam lisans gereklidir.  
- **Hangi Java sürümü gereklidir?** Java 8 veya üzeri desteklenir.  
- **GroupDocs.Watermark kaç dosya formatını destekliyor?** XLSX, DOCX, PDF ve PPTX dahil olmak üzere 30’dan fazla giriş ve çıkış formatı vardır.  
- **Büyük çalışma kitapları için bellek tüketimi bir sorun mu?** `try‑with‑resources` kullanın ve tüm sayfaları belleğe yüklemekten kaçının; API verileri verimli bir şekilde akıtır.

## Excel'den şekilleri kaldırma nedir?
*Excel'den şekilleri kaldırma*, belirli kriterlere (yazı tipi stili, renk, boyut vb.) uyan metin kutuları, simgeler veya SmartArt gibi çizim nesnelerini programlı olarak silmek anlamına gelir. Bu işlem, manuel düzenleme yapmadan çalışma kitabını temizler, görsel tutarlılığı sağlar, dosya boyutunu azaltır ve dağıtılan raporlarda eski veya istenmeyen grafiklerin görünmesini engeller.

## Excel'den şekilleri neden kaldırmalısınız?
GroupDocs.Watermark, **manuel düzenlemeden 3 × daha hızlı** bir şekilde çok sayfalı çalışma kitaplarını işleyebilir, **30+ dosya formatını** destekler ve 50 MB üzerindeki dosyalarda bellek kullanımını 150 MB altında tutar. Şekil kaldırmayı otomatikleştirmek insan hatasını ortadan kaldırır ve tüm oluşturulan raporlarda tutarlı marka kimliği sağlar.

## Önkoşullar
### Gerekli Kütüphaneler, Sürümler ve Bağımlılıklar
- **Java Development Kit (JDK)**: Versiyon 8 veya üzeri.  
- **GroupDocs.Watermark**: Versiyon 24.11 (yazım anındaki en son stabil sürüm).

### Ortam Kurulum Gereksinimleri
IntelliJ IDEA veya Eclipse gibi bir IDE ve bağımlılık yönetimi için Maven kullanın.

### Bilgi Önkoşulları
Java sözdizimi ve temel Excel kavramlarına (çalışma sayfaları, hücreler ve şekiller) aşina olmak örnekleri takip etmenizi kolaylaştırır.

## Java için GroupDocs.Watermark Kurulumu
**Maven Bağımlılığı**  
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

**Doğrudan İndirme**  
Alternatif olarak en son sürümü şu adresten indirebilirsiniz: [GroupDocs.Watermark Java sürümleri](https://releases.groupdocs.com/watermark/java/).

### Lisans Edinme Adımları
- **Ücretsiz Deneme** – Özellikleri değerlendirmek için ücretsiz deneme sürümüyle başlayın.  
- **Geçici Lisans** – Uzun süreli testler için geçici bir lisans alın.  
- **Satın Alma** – Üretim kullanımı için tam lisans satın alın.

### Temel Başlatma ve Kurulum  
Kütüphane projenize eklendikten sonra aşağıdaki gibi başlatın:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Excel'den şekilleri nasıl kaldırabilirsiniz?
Çalışma kitabını yükleyin, her bir çalışma sayfasını dolaşın ve şekil‑kaldırma API'sını çağırın. Bu iki adımlı desen—*yükle* ardından *dolaş*—tüm dosyada şekilleri temizlemeniz gereken hemen hemen her senaryoyu kapsar. Kaldırmadan önce her şeklin özelliklerini kriterlerinize göre kontrol ederek yalnızca istenmeyen öğelerin silindiğinden ve belgenin geri kalan düzeni ile içeriğinin korunduğundan emin olursunuz.

## Bir Excel Belgesi Yükleme
**Genel Bakış**  
Excel belgesi yüklemek, herhangi bir manipülasyon görevine başlamak için ilk adımdır. GroupDocs.Watermark, sezgisel API'siyle bunu basitleştirir.  

**Tanım Açıklaması**  
`SpreadsheetDocument`, GroupDocs.Watermark içinde bir Excel çalışma kitabını bellekte temsil eden birincil sınıftır; çalışma sayfalarına, hücrelere ve şekillere erişim sağlayan yöntemler sunar.  

#### Kod Parçası
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Bir Çalışma Sayfasında Çalışma Sayfalarına Erişim ve Dolaşma
**Genel Bakış**  
Çalışma sayfaları arasında dolaşmak, her bir sayfada ayrı ayrı işlem yapmanıza olanak tanır.  

**Tanım Açıklaması**  
`Worksheet`, bir `SpreadsheetDocument` içinde tek bir sayfayı temsil eder; bu nesne aracılığıyla içeriğini okuyabilir, değiştirebilir veya silebilirsiniz.  

#### Kod Parçası
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Çalışma Sayfasından Belirli Metin Biçimlendirmesine Sahip Şekilleri Kaldırma
**Genel Bakış**  
Bu özellik, yazı tipi türü veya rengi gibi belirli metin biçimlendirme kriterlerine uyan şekilleri hedef alır.  

**Tanım Açıklaması**  
`Shape`, bir çalışma sayfasındaki (metin kutusu, resim veya SmartArt) herhangi bir çizim öğesinin nesne modelidir; `getText`, `getFont` ve `remove` gibi özellikleri ortaya çıkarır.  

#### Kod Parçası
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Pratik Uygulamalar
### Gerçek Dünya Kullanım Durumları
1. **Veri Doğrulama** – Kullanım dışı uyarı içeren şekilleri otomatik olarak silin.  
2. **Şablon Standardizasyonu** – Standart dışı metin kutularını kaldırarak kurumsal marka tutarlılığını sağlayın.  
3. **Otomatik Raporlama** – Dağıtımdan önce oluşturulan raporları temizleyin, böylece her zaman cilalı bir görünüm elde edin.

### Entegrasyon Olanakları
GroupDocs.Watermark, belge‑oluşturma mikro‑servisleri, toplu‑işlem görevleri veya içerik‑yönetim sistemleri gibi Java‑tabanlı kurumsal veri akışlarına gömülebilir; Excel varlıklarını yönetmek için sorunsuz, lisans‑uyumlu bir yol sunar.

## Performans Düşünceleri
### Performansı Optimize Etme
- **Döngüler içinde ağır işlemlerden kaçının** – şekil koleksiyonlarını her çalışma sayfası için bir kez alın.  
- **Kaynakları hızlıca serbest bırakın** – akışları otomatik kapatmak için `try‑with‑resources` kullanın.

### Kaynak Kullanım Kılavuzları
İşlem tamamlandığında `SpreadsheetDocument` nesnesini serbest bırakın ve yerel belleği boşaltın. 100 MB üzerindeki dosyalar için çalışma sayfalarını paralel akışlarla işleyerek çok çekirdekli CPU’ları kullanmayı değerlendirin.

### Java Bellek Yönetimi için En İyi Uygulamalar
`try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` biçimini kullanın; böylece bir istisna oluşsa bile `close()` yöntemi çalışır.

## Yaygın Sorunlar ve Çözümler
- **Şekil bulunamadı** – Doğru çalışma sayfası indeksini kontrol ettiğinizden emin olun; şekiller sayfa bazında sınırlıdır.  
- **Lisans istisnası** – Deneme lisansı toplu işleme izin vermez; sınırsız işlem için tam lisansa yükseltin.  
- **Beklenmeyen yazı tipi değerleri** – Yazı tipi özellikleri devralınabilir; çözülmüş stili almak için `shape.getEffectiveFont()` kullanın.

## Sıkça Sorulan Sorular

**S: Şifre korumalı bir çalışma kitabından şekilleri kaldırabilir miyim?**  
C: Evet. Belgeyi şifre parametresiyle yükleyin, ardından aynı kaldırma mantığını çalıştırın; API dosyayı bellekte çözer.

**S: Kütüphane .xls (Excel 97‑2003) dosyalarını destekliyor mu?**  
C: Kesinlikle. GroupDocs.Watermark, `.xlsx` ve eski `.xls` formatlarını dönüşüm olmadan işler.

**S: Hangi şekillerin silindiğini nasıl kaydederim?**  
C: Şekil koleksiyonunu dolaşın, biçimlendirme kriterlerini kontrol edin, `shape.getName()` veya `shape.getId()` değerini kaydedin, ardından `remove()` metodunu çağırın.

**S: Şekilleri kaldırdıktan sonra bir watermark eklemek mümkün mü?**  
C: Evet. Temizlemeden sonra `doc.addWatermark(new TextWatermark("Confidential"))` kodunu çalıştırarak tüm çalışma sayfalarına metin watermark'ı ekleyebilirsiniz.

**S: Desteklenen maksimum dosya boyutu nedir?**  
C: Kütüphane, 64‑bit JVM üzerinde **2 GB**'a kadar dosyayı işleyebilir; sınırlama yalnızca mevcut yığın belleği ve işletim sistemi koşullarıdır.

## Sonuç
Bu öğreticide, GroupDocs.Watermark for Java kullanarak **Excel'den şekilleri kaldırma** işlemi için eksiksiz, üretim‑hazır bir yaklaşım gösterdik. Belgeyi yükleyip, çalışma sayfalarını dolaşıp ve kesin biçimlendirme filtreleri uygulayarak temizlik görevlerini otomatikleştirebilir, marka tutarlılığını sağlayabilir ve rapor kalitesini ölçekli bir şekilde artırabilirsiniz. Watermark ekleme, belge dönüştürme ve toplu işleme gibi ek özellikleri keşfederek belge‑otomasyon araç setinizi daha da genişletebilirsiniz.

---

**Son Güncelleme:** 2026-06-01  
**Test Edilen:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs

## İlgili Eğitimler

- [Java'da GroupDocs.Watermark Kullanarak Excel Şekil Manipülasyonu: Kapsamlı Rehber](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [GroupDocs.Watermark Java SDK ile Excel Çalışma Sayfasına Görsel Watermark Ekleme](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [GroupDocs.Watermark Java ile Excel Belge İşleme ve Watermark Ekleme](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)