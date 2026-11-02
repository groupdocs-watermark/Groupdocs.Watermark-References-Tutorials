---
date: '2025-12-31'
description: GroupDocs.Watermark for Java kullanarak e-posta metninde nasıl arama
  yapılacağını öğrenin, gövdeleri, konuları ve ekleri verimli bir şekilde yönetin.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: GroupDocs.Watermark Java ile E-posta Metnini Nasıl Ararsınız – Kapsamlı Bir
  Rehber
type: docs
url: /tr/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# GroupDocs.Watermark Java ile E-posta Metnini Arama

Bir e-postanın konu, gövde veya eklerinde belirli bir ifadeyi bulmak zorlayıcı olabilir—özellikle onlarca ya da yüzlerce mesajla çalışıyorsanız. Bu öğreticide **e-posta içeriğini** hızlı ve doğru bir şekilde aramayı **GroupDocs.Watermark for Java** kullanarak öğreneceksiniz. Kurulum, kod ve en iyi uygulama ipuçları üzerinden geçerek e-posta metni aramayı kendi uygulamalarınıza güvenle entegre edebileceksiniz.

## Hızlı Yanıtlar
- **Java’da e-posta metnini aramamı sağlayan kütüphane nedir?** GroupDocs.Watermark for Java.  
- **Lisans gerekir mi?** Test için ücretsiz deneme sürümü yeterlidir; üretim için ücretli lisans gereklidir.  
- **Hem konu hem de gövdeyi arayabilir miyim?** Evet—`EmailSearchableObjects`’ı Subject, HtmlBody ve PlainTextBody içerecek şekilde yapılandırın.  
- **API büyük/küçük harfe duyarlı mı?** `TextSearchCriteria` içinde uygun bayrağı ayarlayarak büyük/küçük harfe duyarsız arama yapabilirsiniz.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri; bağımlılık yönetimi için Maven önerilir.

## GroupDocs.Watermark ile “e-posta nasıl aranır” nedir?
GroupDocs.Watermark, **e-posta mesajları** (`.msg`, `.eml`) dahil olmak üzere birçok belge türünde filigranları ve düz metni bulmak, kaldırmak veya değiştirmek için birleşik bir API sunar. Aranabilir nesneler modelini kullanarak, ilgilendiğiniz e-posta bölümlerine tam olarak hedefleyebilir, toplu işleme hızlı ve güvenilir bir şekilde gerçekleştirebilirsiniz.

## Neden GroupDocs.Watermark Java’yı e-posta araması için kullanmalıyım?
- **Birleşik API** – PDF, görüntü, Office dosyaları ve e-postalar aynı kod kalıplarıyla çalışır.  
- **Performans‑optimizeli** – Arama işlemleri harici servislere ihtiyaç duymadan bellek içinde çalışır.  
- **Sağlam işleme** – HTML ve düz‑metin gövdeleri, ekler ve hatta şifre korumalı e-postaları destekler.  
- **Kolay entegrasyon** – Maven/Gradle uyumlu, net dokümantasyon ve aktif destek.

## Önkoşullar

- **Java Development Kit (JDK)** 8 veya daha yenisi.  
- **Maven** (veya Gradle) bağımlılık yönetimi için.  
- **IntelliJ IDEA** veya **Eclipse** gibi bir IDE.  
- Java sözdizimi ve e-posta dosya formatları (`.msg`, `.eml`) hakkında temel bilgi.

## GroupDocs.Watermark for Java’yı Kurma

### Maven Kurulumu
`pom.xml` dosyanıza depo ve bağımlılığı ekleyin:

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
Alternatif olarak, en yeni JAR dosyasını [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

### Lisans Edinme
- **Ücretsiz Deneme:** Lisans anahtarı olmadan temel özellikleri test edin.  
- **Geçici Lisans:** Uzun süreli değerlendirme için zaman sınırlı bir anahtar talep edin.  
- **Ücretli Lisans:** Sınırsız üretim kullanımı için satın alın.

#### Temel Başlatma
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Uygulama Kılavuzu

### Özellik 1: E-posta Gövdesinde Metin Arama

#### Genel Bakış
Belirli bir anahtar kelime için **konu**, **HTML gövde** ve **düz‑metin gövde** üzerinde tarama yapacak şekilde API’yı yapılandıracağız.

#### Adım 1: Belge Yollarını Tanımlama
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Adım 2: Yükleme Seçeneklerini ve Watermarker’ı Ayarlama
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Adım 3: Arama Kriterlerini Oluşturma
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Adım 4: Arama Konumlarını Belirleme
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Adım 5: Aramayı Çalıştırma ve Filigranları Temizleme
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Adım 6: Değişiklikleri Kaydetme
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Sorun Giderme İpuçları
- **Boş sonuçlar:** Anahtar kelimenin seçili e-posta bölümlerinde gerçekten bulunduğunu doğrulayın.  
- **Performans:** Büyük partilerde hız kazanmak için aranabilir nesneleri yalnızca ihtiyacınız olanlara (ör. Subject + PlainTextBody) sınırlayın.

### Özellik 2: E-posta Belge Seçeneklerini Yükleme

#### Genel Bakış
`EmailLoadOptions`, e-postanın nasıl ayrıştırılacağını kontrol etmenizi sağlar—şifreli mesajlar veya özel kodlamalar için faydalıdır.

#### Adım 1: Yükleme Seçeneklerini Yapılandırma
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Temel Yapılandırma Seçenekleri
- **Şifre Koruması:** Şifreli `.msg` dosyaları için `loadOptions.setPassword("yourPassword")` ayarlayın.  
- **Kodlama Ayarları:** Standart dışı karakter setleriyle çalışırken `loadOptions.setEncoding(Charset.forName("UTF-8"))` kullanın.

## Pratik Uygulamalar

- **Otomatik E-posta İşleme:** Gelen destek taleplerini “refund” veya “error” gibi anahtar kelimeler için toplu tarayın.  
- **Yasal Uyum Kontrolleri:** Şirket e-posta arşivlerinde SSN, kredi kartı numaraları gibi gizli terimleri hızlıca bulun.  
- **Müşteri Destek Otomasyonu:** Algılanan ifadelerle e-postaları doğru destek ekibine yönlendirin.

## Performans Düşünceleri
- **Kaynak Yönetimi:** İşlem tamamlandığında `watermarker.close()` çağrısı yaparak yerel kaynakları serbest bırakın.  
- **Bellek En İyi Uygulamaları:** Binlerce mesajla çalışırken onları partiler halinde işleyin ve mümkün olduğunca `Watermarker` örneğini yeniden kullanın.

## Sonuç
Artık **GroupDocs.Watermark Java** kullanarak **e-posta içeriğini nasıl ararsınız** konusunda sağlam, üretim‑hazır bir yaklaşıma sahipsiniz. API’nın esnekliği, e-postanın belirli bölümlerini hedeflemenize, istenmeyen filigranları temizlemenize ve mantığı daha büyük iş akışlarına entegre etmenize olanak tanır.

### Sonraki Adımlar
- **Birden fazla arama kriteri** deneyin (ör. “invoice” + “overdue”).  
- Hassas veri içeren e-postaları işaretlemek için **filigran ekleme** keşfedin.  
- Aynı Watermarker iş akışını kullanarak diğer belge türlerine (PDF, DOCX) geçiş yapın.

## Sıkça Sorulan Sorular

**S1:** GroupDocs.Watermark ile şifreli e-postalar nasıl işlenir?  
**C1:** `Watermarker` örneğini oluşturmadan önce `EmailLoadOptions.setPassword("yourPassword")` kullanın.

**S2:** Aynı anda birden fazla anahtar kelime arayabilir miyim?  
**C2:** Evet—her anahtar kelime için ayrı `SearchCriteria` nesnesi oluşturup mantıksal operatörlerle (ör. `OrSearchCriteria`) birleştirebilirsiniz.

**S3:** GroupDocs.Watermark Java ücretsiz mi?  
**C3:** Değerlendirme için ücretsiz bir deneme sürümü mevcuttur. Üretim kullanımı için ücretli lisans gerekir.

**S4:** Büyük miktarda e-postayı verimli bir şekilde nasıl işlerim?  
**C4:** Gereksiz aranabilir nesneleri dışarıda bırakın, e-postaları partiler halinde işleyin ve her zaman `Watermarker`’ı kapatarak kaynakları serbest bırakın.

**S5:** Ek yardım veya destek nereden bulunur?  
**C5:** Topluluk desteği için [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) adresini ziyaret edin ya da doğrudan GroupDocs destek ekibiyle iletişime geçin.

## Kaynaklar
- **Dokümantasyon:** Ayrıntılı kılavuzlar için [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) adresine bakın.  
- **API Referansı:** Teknik detaylar için [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) adresini inceleyin.

---

**Son Güncelleme:** 2025-12-31  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  

---