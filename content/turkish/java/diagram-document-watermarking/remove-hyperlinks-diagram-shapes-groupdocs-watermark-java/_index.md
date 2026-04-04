---
date: '2026-04-04'
description: GroupDocs.Watermark Java ile diyagram şekillerindeki bağlantıları nasıl
  kaldıracağınızı öğrenin, belge güvenliğini ve netliğini sağlayarak.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: GroupDocs.Watermark Java kullanarak Diyagram Şekillerinden Bağlantıları Nasıl
  Kaldırılır
type: docs
url: /tr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java Kullanarak Diyagram Şekillerinden Bağlantıları Kaldırma

Dijital belgeleri yönetmek genellikle diyagramları düzenlemeyi içerir, özellikle güvenlik veya netlik için **bağlantıları kaldırma** gerektiğinde. Bu öğreticide, güçlü **GroupDocs.Watermark** Java kütüphanesini kullanarak diyagram şekillerindeki istenmeyen hiperlinkleri kaldırmanın basit, adım adım bir yolunu öğreneceksiniz. Sonunda, paylaşmaya güvenli, temiz ve bağlantısız diyagramlara sahip olacaksınız.

## Hızlı Yanıtlar
- **“bağlantıları kaldırma” ne anlama geliyor?** Bu, diyagram şekillerine gömülmüş hiperlink nesnelerini kaldırmayı ifade eder.  
- **Bu işlemi hangi kütüphane gerçekleştirir?** GroupDocs.Watermark for Java (version 24.11 or newer).  
- **Lisans gerekir mi?** Test için ücretsiz deneme sürümü çalışır; üretim için geçerli bir lisans gereklidir.  
- **Birçok dosyayı aynı anda işleyebilir miyim?** Evet – kodu bir döngü veya toplu iş içinde sarabilirsiniz.  
- **Bu yaklaşım dil‑spesifik mi?** Örnek Java'dır, ancak aynı konsept diğer .NET/Java API'lerine de uygulanabilir.

## Diyagram düzenlemede “bağlantıları kaldırma” nedir?
Bağlantıları kaldırmak, bir diyagram içindeki şekillere (örneğin Visio *.vsdx) eklenmiş hiperlink nesnelerini bulup silmek anlamına gelir. Bu, hassas bilgileri ortaya çıkarabilecek veya sunum akışını bozabilecek dış URL'leri ortadan kaldırır.

## Neden GroupDocs.Watermark for Java kullanmalı?
- **Precision** – Şekil nesnelerine ve onların hiperlink koleksiyonlarına doğrudan erişim.  
- **Performance** – Tüm belgeyi belleğe yüklemeden büyük diyagramlar için optimize edilmiştir.  
- **Cross‑format support** – Birçok diyagram formatı (Visio, Draw.io vb.) ile çalışır.

## Ön Koşullar
- **GroupDocs.Watermark** kütüphanesi ≥ 24.11.  
- Maven (veya manuel JAR ekleme).  
- Java JDK 8 veya daha yeni.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.

## GroupDocs.Watermark for Java'ı Kurma
### Maven Kurulumu
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

### Doğrudan İndirme
Maven kullanmak istemiyorsanız, resmi siteden en son JAR'ı indirin:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### Lisans Edinme Adımları
- Ücretsiz deneme indirmesiyle başlayın.  
- Üretim için, GroupDocs portalından geçici veya tam lisans edinin.

#### Temel Başlatma ve Kurulum
Create a `Watermarker` instance that points to the folder containing your diagram:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Diyagram Şekillerinden Bağlantıları Kaldırma
Aşağıda, **remove hyperlinks java**'nın nasıl çalıştığını gösteren özlü, dört adımlı bir süreç bulunmaktadır.

### Adım 1: Diyagram Dosyasını Yükle
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Neden?* Dosyayı yüklemek, sayfalarına, şekillerine ve hiperlink koleksiyonlarına programatik erişim sağlar.

### Adım 2: Şekil İçeriğine Erişme
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Neden?* Hiperlink içerebilecek belirli bir şekle referansa ihtiyacınız var.

### Adım 3: Döngüyle Gezin ve Hiperlinkleri Kaldır
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Neden?* Ters yönde döngü, koleksiyondan öğe silinirken indeks kayması sorunlarını önler.

### Adım 4: Kaydet ve Kapat
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Neden?* Kaydetmek, temizlenmiş diyagramı diske yazar ve kapatmak, bellek sızıntılarını önlemek için dosya tutamaçlarını serbest bırakır.

## Bağlantı Kaldırmanın Pratik Uygulamaları
1. **Security** – Phishing veya veri sızıntısına yol açabilecek dış URL'leri kaldırın.  
2. **Compliance** – Diyagramların dağıtımdan önce iç politikalarla uyumlu olmasını sağlayın.  
3. **Presentation Cleanliness** – İzleyicileri dağıtan gereksiz tıklanabilir alanları ortadan kaldırın.

## Performans Düşünceleri
- **Loop Efficiency** – Yukarıda gösterilen ters‑iterasyon desenini kullanın.  
- **Resource Management** – `try‑with‑resources` veya açık `close()` çağrılarını tercih edin.  
- **Large Files** – CPU/belleği izleyin; sayfaları toplu olarak işlemeyi düşünün.

## Yaygın Sorunlar ve Çözümler
- **No hyperlinks found** – Diyagramın gerçekten hiperlink nesneleri içerdiğini doğrulayın; bazı formatlar bunları farklı şekilde depolar.  
- **IndexOutOfBoundsException** – Bir koleksiyondan öğe kaldırırken her zaman ters yönde yineleyin.  
- **License errors** – Lisans dosyanızın doğru konumlandırıldığından veya `Watermarker` yapıcısına geçirildiğinden emin olun.

## Sık Sorulan Sorular

**Q: Birden fazla sayfada birden fazla şekli nasıl yönetirim?**  
A: `content.getPages()` üzerinden döngü yapın ve ardından her sayfanın `getShapes()` koleksiyonunda aynı kaldırma mantığını her şekle uygulayın.

**Q: Bağlantıları tam URL yerine alan adına göre filtreleyebilir miyim?**  
A: Evet – `contains` kontrolünü alan adı dizesini (ör. `"example.com"`) arayacak şekilde değiştirin.

**Q: Hangi bağlantıların kaldırıldığını kaydetmenin bir yolu var mı?**  
A: Döngü içinde, kaldırmadan önce `shape.getHyperlinks().get_Item(i).getAddress()` değerini yakalayın ve bir log dosyasına yazın.

**Q: Bu, diğer belgelerde gömülü PDF diyagramlarıyla çalışır mı?**  
A: GroupDocs.Watermark birçok formatı destekler; dosya türünün bir diyagram (Visio, VDX vb.) olarak tanındığından emin olun.

**Q: Toplu işleme için hangi lisanslama gerekir?**  
A: Deneme dışı, yüksek hacimli işlemler için tam bir üretim lisansı gereklidir.

## Sonuç
Artık GroupDocs.Watermark for Java kullanarak diyagram şekillerinden **bağlantıları kaldırma** için eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Bu yöntemi belge‑işleme hatlarınıza entegre ederek güvenliği, uyumu ve görsel kaliteyi artırın.

### Sonraki Adımlar
- Filigran ekleme veya metin damgalama gibi diğer manipülasyon özelliklerini keşfedin.  
- Bu rutini bir dosya‑izleyici servisiyle birleştirerek yüklenirken diyagramları otomatik olarak temizleyin.

---

**Son Güncelleme:** 2026-04-04  
**Test Edilen:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/watermark/java/)
- [API Referansı](https://reference.groupdocs.com/watermark/java)
- [İndirme](https://releases.groupdocs.com/watermark/java/)
- [GitHub Deposu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/watermark/10)
- [Geçici Lisans Edinme](https://purchase.groupdocs.com/temporary-license/)