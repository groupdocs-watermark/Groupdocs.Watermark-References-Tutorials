---
date: '2025-12-19'
description: GroupDocs.Watermark Java kullanarak diyagram şekillerindeki hiperlinkleri
  nasıl kaldıracağınızı öğrenin; bu, Java belge güvenliği için önemli bir adımdır
  ve hiperlinkleri toplu olarak kaldırır.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: GroupDocs.Watermark Java ile Diyagram Şekillerindeki Hipermetin Bağlantılarını
  Nasıl Kaldırılır
type: docs
url: /tr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Diagram Şekillerinden Hipermetin Bağlantılarını Kaldırma – GroupDocs.Watermark Java Kullanarak

Dijital belgeleri yönetmek, özellikle **hipermetin bağlantılarını kaldırma** gerektiğinde diyagramları düzenlemeyi içerir. Bu öğreticide, dosyalarınızın temiz, güvenli ve profesyonel kalmasını sağlayarak GroupDocs.Watermark for Java ile diyagram şekillerinden **hipermetin bağlantılarını nasıl kaldıracağınızı** öğreneceksiniz.

## Hızlı Yanıtlar
- **Birincil amaç nedir?** Diyagram şekillerindeki istenmeyen hipermetin bağlantılarını kaldırarak belge güvenliğini artırmak.  
- **Hangi kütüphane kullanılıyor?** GroupDocs.Watermark for Java (sürüm 24.11 veya üzeri).  
- **Lisans gerekli mi?** Test için bir deneme sürümü yeterlidir; üretim ortamı için geçerli bir lisans gerekir.  
- **Birden çok dosyayı aynı anda işleyebilir miyim?** Evet – aynı mantık bir toplu döngü içinde kullanılabilir.  
- **Java 8 yeterli mi?** Java 8+ desteklenir; daha yeni JDK’lar önerilir.

## “Diyagramlarda hipermetin bağlantılarını kaldırma” ne anlama geliyor?
Hipermetin bağlantılarını kaldırmak, bir diyagram dosyasındaki (ör. Visio *.vsdx) şekillere eklenmiş URL referanslarını silmek demektir. Bu işlem, dış sitelere yanlışlıkla yönlendirmeyi önler ve uyumluluk ya da iç güvenlik politikalarına uymaya yardımcı olur.

## Bu görev için GroupDocs.Watermark Java neden tercih edilmeli?
- **Geniş format desteği** – çok çeşitli diyagram türleriyle çalışır.  
- **İnce ayarlı API** – tek tek şekilleri ve onların hipermetin koleksiyonlarını hedeflemenizi sağlar.  
- **Performans odaklı** – tek dosya ve toplu işleme için uygundur.  

## Ön Koşullar
- **GroupDocs.Watermark** kütüphanesi sürüm 24.11 veya üzeri.  
- Maven veya doğrudan JAR indirme (aşağıdaki kurulum adımlarına bakın).  
- Java Development Kit (JDK 8 veya daha yeni) ve IntelliJ IDEA veya Eclipse gibi bir IDE.  

## GroupDocs.Watermark for Java Kurulumu
Projeye kütüphaneyi Maven üzerinden ekleyebilir ya da JAR dosyasını doğrudan indirebilirsiniz.

### Maven Kurulumu
`pom.xml` dosyanıza aşağıdaki yapılandırmayı ekleyin:

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
Alternatif olarak, en son sürümü [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) adresinden indirin.

#### Lisans Edinme Adımları
- API’yı değerlendirmek için ücretsiz deneme sürümüyle başlayın.  
- Üretim için, GroupDocs portalından geçici ya da tam lisans alın.

#### Temel Başlatma ve Kurulum
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Diyagram Şekillerinden Hipermetin Bağlantılarını Kaldırma
Aşağıda, bir diyagramı yükleme, şekilleri bulma ve istenmeyen hipermetin bağlantılarını temizleme adımlarını gösteren adım‑adım bir kılavuz yer almaktadır.

### Adım 1: Diyagram Dosyasını Yükle
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Neden?* Dosyayı yüklemek, iç yapısına programatik erişim sağlar.

### Adım 2: Şekil İçeriğine Eriş
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Neden?* Hipermetin içerebilecek belirli bir şekle referans almanız gerekir.

### Adım 3: Döngüyle Geç ve Hipermetin Bağlantılarını Kaldır
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Neden?* Koleksiyondan öğe silinirken indeks hatalarını önlemek için geriye doğru döngü kullanılır.

### Adım 4: Kaydet ve Kapat
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Neden?* Değişiklikleri kalıcı hâle getirmek ve kaynakları serbest bırakmak bellek sızıntılarını ve dosya kilitlenmelerini önler.

## Toplu Hipermetin Bağlantı Kaldırma (İleri Seviye Kullanım)
Birden çok diyagramı aynı anda temizlemeniz gerekiyorsa, yukarıdaki mantığı dosya yolu listesi üzerinde dönen bir döngüye yerleştirin. Aynı API çağrıları geçerlidir; sadece her yineleme için giriş ve çıkış dizinlerini değiştirmeniz yeterlidir. Bu yaklaşım, büyük belge depoları için **toplu hipermetin kaldırma** gereksinimleriyle uyumludur.

## Pratik Kullanım Alanları
Diyagram şekillerinden hipermetin bağlantılarını kaldırmak, aşağıdaki gerçek dünya senaryolarında faydalı olabilir:

1. **Güvenlik Amaçlı** – Ağınızı phishing veya kötü amaçlı yazılımlara maruz bırakabilecek dış bağlantıları engelleyin.  
2. **Uyumluluk** – Paylaşılan belgelerde dış URL’lerin yasak olduğu kurumsal politikalara uyun.  
3. **Netlik** – Hipermetin bağlantılarının gereksiz ya da dikkat dağıtıcı olduğu durumlarda daha temiz sunumlar üretin.  

## Performans Düşünceleri
### Performans Optimizasyonu
- Yukarıda gösterilen ters‑döngü desenini kullanarak döngüleri verimli tutun.  
- İşiniz bittiğinde `Watermarker` nesnesini hemen kapatarak belleği serbest bırakın.

### Kaynak Kullanım Rehberi
- Büyük diyagramları işlerken CPU ve RAM kullanımını izleyin.  
- Toplu işler için dosyaları tek tek yüklemek yerine akış (stream) yöntemi tercih edin.

### Java Bellek Yönetimi İçin En İyi Uygulamalar
- Sıkı döngüler içinde nesne oluşturmaktan kaçının.  
- Mümkün olduğunda otomatik temizlik için try‑with‑resources kullanın.

## Sık Sorulan Sorular
1. **Birden çok şekil nasıl işlenir?**  
   Tüm sayfalar ve şekiller üzerinde yineleme yapın; aynı hipermetin kaldırma mantığını her şekle uygulayın.  

2. **Bu işlem büyük diyagram topluları için otomatikleştirilebilir mi?**  
   Evet – kodu bir toplu‑işleme rutinine yerleştirin ya da belge‑yönetim sisteminizle entegre edin.  

3. **Sadece belirli sayfalardan hipermetin kaldırmak istesem ne yapmalıyım?**  
   İstenen sayfayı `content.getPages().get_Item(pageIndex)` ile alın ve yalnızca o sayfadaki şekillere odaklanın.  

4 **GroupDocs.Watermark’ın üretim kullanımı için lisans gerekli mi?**  
   Deneme süresi dışında geçerli bir ticari lisans gerekir.  

5. **Bu yöntem diğer diyagram formatlarıyla çalışır mı?**  
   GroupDocs.Watermark birçok diyagram türünü destekler; uyumluluğu resmi dokümantasyonda kontrol edin.  

**Ek Soru‑Cevap**

**S:** *Kaldırılan hipermetin bağlantılarını kaydetmek mümkün mü?*  
**C:** Evet – `removeAt(i)` çağrısından önce `shape.getHyperlinks().get_Item(i).getAddress()` değerini alın ve bir log dosyasına yazın.

**S:** *Hipermetin kaldırmak şeklin görsel görünümünü etkiler mi?*  
**C:** Hayır. Şeklin geometrisi değişmez; yalnızca bağlantı meta verisi silinir.

**S:** *Kaldırma sonrası stil yeniden uygulanmalı mı?*  
**C:** Genellikle gerekmez. Hipermetin kaldırma dolgu, çizgi veya metin stillerini etkilemez.

## Sonuç
Artık GroupDocs.Watermark for Java kullanarak diyagram şekillerinden **hipermetin bağlantılarını nasıl kaldıracağınız** konusunda eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Yukarıdaki adımları izleyerek diyagramlarınızı güvence altına alabilir, politikalara uyum sağlayabilir ve belgelerinizin profesyonel görünümünü koruyabilirsiniz.

**Kaynaklar**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Son Güncelleme:** 2025-12-19  
**Test Edilen Sürüm:** GroupDocs.Watermark 24.11 for Java  
**Yazar:** GroupDocs  
