---
date: '2026-08-25'
description: GroupDocs.Watermark for Java kullanarak diyagram dosyalarını nasıl düzenleyeceğinizi
  ve hiperlinkleri nasıl kaldıracağınızı öğrenin. Diyagramlarınızı adım adım rehberlikle
  hızlı bir şekilde güvenceye alın.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: GroupDocs.Watermark for Java kullanarak diyagram dosyalarını nasıl
  düzenleyeceğinizi ve hiperlinkleri nasıl kaldıracağınızı öğrenin. Belgelerinizi
  korumak için net adımları izleyin.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Java ile diyagramı düzenleme ve hiperlinkleri kaldırma
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Java ile diyagramı düzenleme ve hiperlinkleri kaldırma
type: docs
url: /tr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Java ile diyagramı düzenleme ve hiperlinkleri kaldırma  

Dijital belgeleri yönetmek genellikle diyagramları düzenlemeyi içerir, özellikle güvenlik veya görsel netlik için hiperlinkleri kaldırmanız gereken **edit diagram** dosyaları olduğunda. Bu öğretici, güçlü **GroupDocs.Watermark** Java kütüphanesini kullanarak diyagram dosyalarını nasıl düzenleyeceğinizi ve diyagram şekillerindeki istenmeyen hiperlinkleri nasıl kaldıracağınızı tam olarak gösterir. Bu rehberin sonunda, dağıtıma hazır, temiz ve bağlantısız bir diyagrama sahip olacaksınız.  

## Hızlı cevaplar  
- **Ana hedef nedir?** Güvenliği ve sunumu iyileştirmek için diyagram şekillerindeki tüm hiperlinkleri kaldırın.  
- **Hangi kütüphane gereklidir?** GroupDocs.Watermark for Java, version 24.11 or newer.  
- **Lisans gerekli mi?** Test için ücretsiz deneme çalışır; üretim için ticari bir lisans gereklidir.  
- **Birçok dosyayı aynı anda işleyebilir miyim?** Evet – aynı kod bir döngü içinde yerleştirilerek toplu işleme yapılabilir.  
- **Hangi Java sürümü destekleniyor?** Java 8 or higher (Java 11 recommended).  

## “how to edit diagram” nedir?  
**How to edit diagram**, bir diyagram dosyasını programlı olarak açma, iç öğelerini (şekiller, metin veya hiperlinkler gibi) değiştirme ve sonucu kaydetme sürecine atıfta bulunur. GroupDocs.Watermark kullanarak, orijinal oluşturma aracına ihtiyaç duymadan diyagram dosyalarını düzenleyebilirsiniz.  

## Java için GroupDocs.Watermark neden kullanılmalı?  
GroupDocs.Watermark, **30+ diyagram ve görüntü formatını** (VSDX, SVG ve WMF dahil) destekler ve tüm belgeyi belleğe yüklemeden **500 MB**'a kadar dosyaları işleyebilir, birçok rakibe kıyasla **%20 daha hızlı** işleme hızı sunar.  

## Önkoşullar  
- **GroupDocs.Watermark** kütüphane sürümü 24.11 veya üzeri.  
- Maven yüklü (veya manuel kurulum tercih ediyorsanız JAR dosyaları).  
- Java Development Kit 8 veya üzeri ve IntelliJ IDEA veya Eclipse gibi bir IDE.  

### Gerekli kütüphaneler, sürümler ve bağımlılıklar  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (Maven yaklaşımını kullanıyorsanız)  

### Ortam kurulum gereksinimleri  
JDK `bin` dizininin `PATH`'inizde olduğundan ve IDE'nizin doğru JDK sürümüne işaret ettiğinden emin olun.  

### Bilgi önkoşulları  
Temel Java sözdizimi, Maven bağımlılık yönetimi ve dosya I/O işlemleri konusunda rahat olmalısınız.  

## Java için GroupDocs.Watermark nasıl kurulur?  
`Watermarker` sınıfı, belgeleri yüklemek ve değiştirmek için API giriş noktasını sağlar.  

GroupDocs.Watermark'ı kullanmaya başlamak için Maven koordinatlarını projenizin `pom.xml` dosyasına ekleyin. Bu, kütüphaneyi ve bağımlılıklarını çeker, Watermarker sınıfını örneklemenize ve diyagram dosyalarıyla doğrudan Java kodundan çalışmanıza olanak tanır. Ardından, herhangi bir belgeyi işlemeye başlamadan önce lisanslamayı yapılandırabilir ve çıktı seçeneklerini ayarlayabilirsiniz.  

`pom.xml` dosyanıza GroupDocs.Watermark bağımlılığını ekleyin.  

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

Maven kullanmayı tercih etmiyorsanız, resmi sürüm sayfasından en son JAR dosyasını indirin.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Lisans edinme adımları  
- API'yi değerlendirmek için ücretsiz deneme ile başlayın.  
- Üretim için, satıcı portalından geçici veya kalıcı bir lisans edinin.  

#### Temel başlatma ve kurulum  

`Watermarker` sınıfı, tüm belge‑işleme işlemleri için giriş noktasıdır.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## GroupDocs.Watermark ile diyagramı düzenleme ve hiperlinkleri kaldırma?  
`Watermarker` sınıfı, belgeleri yüklemek ve değiştirmek için API giriş noktasını sağlar.  

İlk olarak, diyagram dosyasını bir Watermarker örneğine yükleyin. Ardından şekil koleksiyonunu alın, hiperlink nesneleri içerenleri belirleyin ve koleksiyon indekslemesini etkilemeden her bağlantıyı güvenli bir şekilde silmek için ters sırada yineleyin. Bu, tüm gömülü URL'lerin kaldırılmasını sağlarken diyagramın görsel bütünlüğünü korur.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Bu adımın önemi**: Dosyayı yüklemek, her şekle ve ilişkili özelliklerine programlı erişim sağlar.  

## Diyagramda şekil içeriğine nasıl erişilir?  
`DiagramShape` nesnesi, bir diyagram içindeki tek bir şekli temsil eder ve özelliklerini ve ek meta verilerini ortaya çıkarır.  

Diyagramı yükledikten sonra, Watermarker üzerinde `getShapes()` çağırarak `DiagramShape` nesnelerinin bir listesini elde edin. Her şekil, hiperlink koleksiyonları için incelenebilir, böylece kaldırma veya değiştirme için bağlantılara kesin hedefleme yapılabilir. Ayrıca, daha fazla ayarlama gerekirse şekil metnini, renklerini ve geometrisini okuyabilirsiniz.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Bu adımın önemi**: Tam olarak doğru şekli hedeflemek, istenmeyen bağlantıları yalnızca o şekilden kaldırmanızı sağlar ve diğer görsel öğeleri etkilemez.  

## Hiperlinkleri güvenli bir şekilde nasıl yineleyip kaldırabilirsiniz?  
`removeHyperlink(int index)` yöntemi, bir şeklin hiperlink koleksiyonundaki belirtilen konumdaki hiperlinki siler.  

Hiperlink listesini son indeksten sıfıra doğru yineleyin. Bu ters döngü, öğeler kaldırıldığında oluşan indeks kaymasını önler ve her hiperlinkin atlanmadan işlenmesini sağlar. Kaldırma işleminden sonra, şeklin durumunu yenileyebilir veya diyagramdaki bir sonraki şekle geçebilirsiniz.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Bu adımın önemi**: Ters bir döngü, hiçbir giriş atlanmadan tüm hiperlinklerin kaldırılmasını garanti eder.  

## Düzenlenmiş diyagramı nasıl kaydedip kaynakları serbest bırakırsınız?  
`save(String path)` yöntemi, değiştirilmiş belgeyi belirtilen dosya konumuna yazar ve tüm değişiklikleri tamamlar.  

Tüm hiperlinkler kaldırıldıktan sonra, Watermarker örneğinde `save` yöntemini çağırarak orijinali üzerine yazmamak için yeni bir dosya adı sağlayın. Ardından, dosya tutamaçlarını serbest bırakmak ve belleği boşaltmak için `close()` metodunu çağırın; bu, uzun süren toplu işlemler için gereklidir. Bu, dosyanın düzgün bir şekilde kapatılmasını ve sonraki kullanım için hazır olmasını sağlar.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Bu adımın önemi**: Kaynakları düzgün bir şekilde kapatmak, sunucuda bellek sızıntılarını ve dosya kilitleme sorunlarını önler.  

## Pratik uygulamalar  
Diyagram şekillerinden hiperlinkleri kaldırmak, çeşitli gerçek dünya senaryolarında faydalı olabilir:  

1. **Güvenlik** – Kötü amaçlı sitelere yönlendirebilecek dış bağlantıları önleyin.  
2. **Uyumluluk** – Paylaşılan varlıklarda gömülü URL'leri yasaklayan kurumsal politikalara uyun.  
3. **Netlik** – Bağlantıların dikkat dağıtıcı olabileceği daha temiz sunumlar üretin.  

Bu mantığı, intranete yayınlanmadan önce tüm diyagramları temizleyen gece toplu işleri gibi daha büyük otomasyon hatlarına entegre edebilirsiniz.  

## Performans değerlendirmeleri  
### Performansı optimize etme  
- Aşırı yükü azaltmak için dosya başına tek bir `Watermarker` örneği kullanın.  
- Maliyetli liste yeniden indekslemeyi önlemek için ters yinelemeyi (gösterildiği gibi) tercih edin.  

### Kaynak kullanım yönergeleri  
- 200 MB'den büyük diyagramlar için yığın kullanımını izleyin ve JVM `-Xmx` bayrağını artırmayı düşünün.  
- VisualVM gibi profil oluşturma araçları, büyük ölçekli toplu çalışmalardaki darboğazları belirlemenize yardımcı olabilir.  

### Java bellek yönetimi için en iyi uygulamalar  
- Nesneleri mümkün olan en küçük kapsam içinde tanımlayın.  
- Akışlarla çalışırken otomatik kapanmayı sağlamak için try‑with‑resources kullanın.  

## Sıkça Sorulan Sorular  

**Q: Binlerce şekil içeren diyagramları nasıl yönetirim?**  
A: Diyagramı sayfa sayfa işleyin ve bir sonraki sayfaya geçmeden önce her sayfanın kaynaklarını serbest bırakarak bellek kullanımını düşük tutun.  

**Q: Hiperlink kaldırmayı yalnızca belirli sayfalara sınırlayabilir miyim?**  
A: Evet – istediğiniz sayfa indeksini alın, ardından kaldırma döngüsünü yalnızca o sayfadaki şekillere uygulayın.  

**Q: Toplu işleme için ticari lisans zorunlu mu?**  
A: Herhangi bir üretim‑seviyesi dağıtım için geçerli bir lisans gereklidir; ücretsiz deneme 30 gün ve 5 belge ile sınırlıdır.  

**Q: GroupDocs.Watermark SVG diyagramlarını destekliyor mu?**  
A: Kesinlikle – SVG, 30+ desteklenen format arasında yer alır ve aynı API çağrılarıyla hiperlinkler temizlenebilir.  

**Q: Bir şeklin birden fazla hiperlinki olursa ne olur?**  
A: Ters‑yineleme döngüsü, her hiperlink girişini ayrı ayrı kaldırır ve tüm bağlantıların temizlenmesini sağlar.  

## Kaynaklar  

- [Dokümantasyon](https://docs.groupdocs.com/watermark/java/)  
- [API Referansı](https://reference.groupdocs.com/watermark/java)  
- [İndirme](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)  
- [Geçici Lisans Edinme](https://purchase.groupdocs.com/temporary-license/)  

---  

**Son Güncelleme:** 2026-08-25  
**Test Edilen Versiyon:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  

## İlgili Eğitimler

- [GroupDocs.Watermark Java için Diyagram Su İşareti Eğitimleri](/watermark/java/diagram-document-watermarking/)  
- [Java'da GroupDocs.Watermark Kullanarak Diyagram Başlık ve Altbilgilerini Düzenleme: Kapsamlı Rehber](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [GroupDocs.Watermark for Java Kullanarak Diyagramlardan Şekilleri Verimli Bir Şekilde Kaldırma](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)