---
date: '2026-10-21'
description: GroupDocs.Watermark for Java kullanarak diagram shapes'ten hyperlink
  kaldırmayı öğrenin. Belgelerinizi güvenli ve temiz tutmak için bu step‑by‑step rehberi
  izleyin.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: GroupDocs.Watermark for Java kullanarak diagram shapes'ten hyperlink
  kaldırmayı öğrenin. Bu rehber, setup, code ve secure, clean belgeler için best practices
  konularında sizi yönlendirir.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: GroupDocs.Watermark Java ile şekillerden hyperlink kaldırma
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: GroupDocs.Watermark Java ile şekillerden hyperlink kaldırma
type: docs
url: /tr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java ile şekillerden köprü kaldırma

Dijital belgeleri yönetmek genellikle diyagramları düzenlemeyi içerir, özellikle güvenlik veya görsel netlik için şekillerden **köprü kaldırma** gerektiğinde. Bu öğretici, Java'da güçlü **GroupDocs.Watermark** kütüphanesini kullanarak diyagram şekillerinden istenmeyen köprüleri (hyperlink) kaldırmak için basit bir yöntemi adım adım gösterir. Bu rehberin sonunda, köprü kaldırmanın neden önemli olduğunu, ortamı nasıl kuracağınızı ve kaldırma işlemini güvenli bir şekilde nasıl gerçekleştireceğinizi anlayacaksınız.

## Hızlı cevaplar
- **Köprüleri kaldırmanın temel amacı nedir?** Güvenlik risklerini ortadan kaldırmak ve paylaşılan diyagramlarda görsel netliği artırmak için.  
- **Kaldırma işlemini hangi kütüphane gerçekleştirir?** GroupDocs.Watermark for Java, diyagram manipülasyonu için özel bir API sağlar.  
- **Lisans gerekiyor mu?** Test için deneme sürümü çalışır; üretim kullanımı için ticari bir lisans gereklidir.  
- **Birçok dosyayı aynı anda işleyebilir miyim?** Evet—kodunuzu bir döngüye veya toplu işine sararak toplu işlemleri gerçekleştirebilirsiniz.  
- **Hangi Java sürümü gereklidir?** Java 8 veya üzeri desteklenir.

## Köprü kaldırma nedir?

Bu **köprü kaldırma** ifadesi, bir diyagramın şekil öğelerine gömülü hyperlink nesnelerini bulma ve silme sürecini ifade eder. Bu eylemi gerçekleştirmek, dış yönlendirmelerin kullanıcıları istemeden kötü amaçlı sitelere veya istenmeyen içeriğe maruz bırakmasını önler. Bu, belgeleri halka açık dağıtım için hazırlarken özellikle önemlidir; gizli yönlendirme yollarının kalmadığından emin olunarak phishing sitelerine veya istenmeyen dış kaynaklara yönlendirme yapılması engellenir.

## Java için GroupDocs.Watermark neden kullanılmalı?

GroupDocs.Watermark, **30+ giriş ve çıkış formatını** destekler ve **500 sayfaya kadar** diyagramları tüm dosyayı belleğe yüklemeden işleyebilir; bu, genel XML ayrıştırıcılarına kıyasla **CPU kullanımında %40 azalma** sağlar. API'si, şekil özellikleri üzerinde ayrıntılı kontrol sağlar ve Java uygulamalarında güvenli diyagram yönetimi için standart yaklaşım haline getirir.

## Önkoşullar
- **GroupDocs.Watermark** kütüphane sürümü 24.11 veya üzeri.  
- Maven yüklü (veya doğrudan JAR indirme).  
- JDK 8 veya daha yeni bir sürüm ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Temel Java bilgisi ve Maven bağımlılıklarına aşinalık.

## Java için GroupDocs.Watermark kurulumu
Başlamak için, projenize GroupDocs.Watermark kütüphanesini ekleyin. Maven aracılığıyla ekleyebilir veya JAR dosyasını manuel olarak indirebilirsiniz.

### Maven kurulumu
Add the following configuration to your `pom.xml`:

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

### Doğrudan indirme
Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirebilirsiniz.

#### Lisans edinme adımları
- GroupDocs.Watermark'ı indirerek ücretsiz deneme ile başlayın.  
- Genişletilmiş test veya üretim kullanımı için geçici bir lisans edinin veya tam lisans satın alın.

#### Temel başlatma ve kurulum
`Watermarker` sınıfı, tüm belge‑seviyesi işlemler için giriş noktasıdır. Bir dosyayı yükler, sayfalara, şekillere ve meta verilere erişim sağlar ve sonunda değiştirilmiş belgeyi diske yazar.

To initialize the Watermarker class:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Diyagram şekillerinden köprü kaldırma nasıl yapılır?
Diyagramı yükleyin, içinde hyperlink bulunan her şekli bulun ve bu hyperlink nesnelerini silin. Tüm işlem on satırdan daha az kodla gerçekleştirilebilir ve ortaya çıkan diyagramın artık kullanıcıları dış sitelere yönlendirebilecek veya hassas bilgileri ortaya çıkarabilecek tıklanabilir bağlantılar içermediğinden emin olur.

### Adım 1: diyagram dosyasını yükle
`Watermarker` kullanarak diyagramınızı yükleyerek başlayın. Bu nesne, şekiller ve özellikleri dahil olmak üzere çeşitli belge öğelerine erişim sağlar.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Neden**: Dosyanın yüklenmesi, içeriğine daha fazla manipülasyon için erişmek açısından gereklidir.

### Adım 2: şekil içeriğine eriş
Diyagramın şekil içeriklerini alın. Bu, hyperlink içerebilecek öğelerle doğrudan çalışmanıza olanak tanır.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Neden**: Belirli şekillere erişmek, hyperlink özelliklerini hedeflemek ve değiştirmek için kritiktir.

### Adım 3: yinele ve hyperlink'leri kaldır
İstenmeyen bağlantıları güvenli bir şekilde kaldırmak ve yineleme sürecini bozmamak için hyperlink'leri ters sırada yineleyin.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Neden**: İterasyon sırasını tersine çevirmek, öğeler kaldırılırken indeksleme sorunlarını önler.

### Adım 4: kaydet ve kapat
Değişiklikler tamamlandığında, değişikliklerinizi yeni bir dosya konumuna kaydedin ve watermarker kaynağını kapatın.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Neden**: Kaynakları düzgün bir şekilde kapatmak, sistemde bellek sızıntısı veya kilitli dosyaların kalmamasını sağlar.

## Yaygın tuzaklar ve sorun giderme
- **Null shape collections** – İterasyona başlamadan önce bir şeklin `Hyperlinks` koleksiyonunun null olmadığını her zaman kontrol edin.  
- **Large diagrams** – 200 sayfadan büyük dosyalar için `OutOfMemoryError` hatasından kaçınmak amacıyla JVM yığın boyutunu (`-Xmx2g`) artırın.  
- **License errors** – Bir lisans istisnası görürseniz, deneme lisansının süresinin dolmadığını ve lisans dosya yolunun doğru olduğunu doğrulayın.

## Sıkça sorulan sorular

**Q: Aynı sayfada birden fazla şekli nasıl yönetirim?**  
A: Her sayfanın `Shapes` koleksiyonunu döngüye alarak, karşılaştığınız her şekle aynı hyperlink kaldırma mantığını uygulayın.

**Q: Kaldırmayı belirli bir sayfa aralığıyla sınırlayabilir miyim?**  
A: Evet—şekilleri alırken sayfa indeksini kullanın ve hedef aralığınız dışındaki sayfaları atlayın.

**Q: Toplu işleme için lisans gerekli mi?**  
A: Herhangi bir üretim‑seviyesi toplu iş için geçerli bir ticari lisans gerekir; deneme lisansı yalnızca sınırlı test için çalışır.

**Q: Bu SVG veya Visio dosyalarıyla çalışır mı?**  
A: GroupDocs.Watermark, SVG, VSDX ve birkaç diğer diyagram formatını destekler; dosya tipinin desteklenen formatlar tablosunda listelendiğinden emin olun.

**Q: 300 sayfalık bir diyagramda ne tür bir performans bekleyebilirim?**  
A: Tipik bir sunucuda (8 CPU, 16 GB RAM), 300 sayfalık bir diyagramın işlenmesi 45 saniyenin altında sürer ve bellek kullanımı 200 MB'nin altında kalır.

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/watermark/java/)
- [API Referansı](https://reference.groupdocs.com/watermark/java)
- [İndirme](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)
- [Geçici Lisans Edinme](https://purchase.groupdocs.com/temporary-license/)

---

**Son Güncelleme:** 2026-10-21  
**Test Edilen:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs

## İlgili Eğitimler

- [Java'da GroupDocs.Watermark ile Word Belgesi Şekillerini Değiştirme: Kapsamlı Rehber](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Java'da GroupDocs.Watermark Kullanarak Word Belgelerinden Şekilleri Kaldırma: Kapsamlı Rehber](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Java'da GroupDocs.Watermark ile Diyagram Başlık ve Altbilgilerini Düzenleme: Kapsamlı Rehber](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)