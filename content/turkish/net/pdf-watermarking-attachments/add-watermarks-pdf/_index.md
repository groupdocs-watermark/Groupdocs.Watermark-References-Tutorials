---
title: PDF'ye Filigran Ekleme
linktitle: PDF'ye Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Kapsamlı adım adım kılavuzumuzla GroupDocs.Watermark for .NET'i kullanarak PDF'lerinize metin ve resim filigranlarını nasıl ekleyeceğinizi öğrenin.
type: docs
weight: 14
url: /tr/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## giriiş
Belgelerinizi korumak veya logonuzla markalamak için PDF'lerinize filigran mı eklemek istiyorsunuz? Başka yerde arama! Bu öğreticide, PDF dosyalarınıza hem metin hem de resim filigranları eklemek için GroupDocs.Watermark for .NET kullanma sürecini ayrıntılı olarak ele alacağız. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuz size her adımda yol gösterecek ve filigranları kolaylıkla ve hassas bir şekilde uygulayabilmenizi sağlayacaktır.
## Önkoşullar
Başlamadan önce, bu eğitimle birlikte takip etmeniz gereken her şeye sahip olduğunuzdan emin olalım:
-  GroupDocs.Watermark for .NET: En son sürümün yüklü olduğundan emin olun. Yapabilirsiniz[buradan indir](https://releases.groupdocs.com/Watermark/net/).
- .NET Geliştirme Ortamı: Visual Studio veya .NET'i destekleyen başka bir IDE.
- Temel C# Bilgisi: C# programlamanın temellerini anlamak, adımları kolaylıkla takip etmenize yardımcı olacaktır.
- PDF Belgesi: Filigranlama için örnek bir PDF belgesini hazır bulundurun.
- Filigran için Resim: Bir resim filigranı ekliyorsanız, resim dosyanızı hazır bulundurun.
## Ad Alanlarını İçe Aktar
Öncelikle C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu, GroupDocs.Watermark işlevine erişmenizi sağlayacaktır.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Şimdi süreci yönetilebilir adımlara ayıralım.
## 1. Adım: PDF Belgenizi Yükleyin
İlk adım, PDF belgenizi filigrana yüklemektir. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Buraya daha fazla adım eklenecek
}
```
## Adım 2: İlk Sayfaya Metin Filigranı Ekleme
Daha sonra PDF'nizin ilk sayfasına bir metin filigranı ekleyeceğiz. Şu talimatları izleyin:
```csharp
// İlk sayfaya metin filigranı ekleyin
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Metin filigranı eklemek, belgenizi yetkisiz kullanıma karşı korumanıza veya basitçe markalamanıza yardımcı olabilir. Belgenize görünmez bir orijinallik damgası bastığınızı hayal edin.
## 3. Adım: İkinci Sayfaya Görüntü Filigranı Ekleme
Şimdi ikinci sayfaya resim filigranı ekleyelim. Bu özellikle logolar veya herhangi bir grafik filigran için kullanışlıdır.
```csharp
// İkinci sayfaya resim filigranı ekleyin
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Resim filigranları belgelerinizin profesyonel görünmesini sağlayabilir ve markanızın her zaman görünür olmasını sağlayabilir. Her sayfaya imzanızı eklemek gibidir.
## 4. Adım: Filigranlı PDF'yi kaydedin
Filigranları ekledikten sonra son adım, filigranlı PDF'yi istediğiniz konuma kaydetmektir.
```csharp
watermarker.Save(outputFileName);
```
Belgenin kaydedilmesi, yaptığınız tüm değişiklikleri sonlandırır. Bu, çabalarınızın kullanıma veya dağıtıma hazır, somut bir sonuca dönüştüğü andır.
## Çözüm
Tebrikler! GroupDocs.Watermark for .NET'i kullanarak PDF'nize hem metin hem de resim filigranlarını başarıyla eklediniz. Bu süreç yalnızca basit olmakla kalmaz, aynı zamanda özel ihtiyaçlarınıza uyacak şekilde son derece özelleştirilebilir. İster belgelerinizi koruyor olun ister markalaştırıyor olun, filigranlar emrinizde olan güçlü bir araçtır.
## SSS'ler
### Aynı sayfaya birden fazla filigran ekleyebilir miyim?
 Evet, aynı sayfaya birden fazla filigran ekleyebilirsiniz.`Add` yöntemi farklı filigran nesneleriyle birden çok kez kullanın.
### Metin filigranının görünümünü nasıl özelleştirebilirim?
 Yazı tipi, boyut, renk ve opaklık gibi özellikleri ayarlayarak metin filigranını özelleştirebilirsiniz.`TextWatermark` nesne.
### Bir PDF'nin yalnızca belirli sayfalarına filigran eklemek mümkün mü?
 Evet, hangi sayfaların filigranlanacağını belirleyebilirsiniz.`PageIndex` içindeki mülk`PdfArtifactWatermarkOptions`.
### Filigranları PDF'den kaldırabilir miyim?
Evet, GroupDocs.Watermark, PDF belgelerinde filigran arama ve kaldırma işlevi sağlar.
### GroupDocs.Watermark için nasıl geçici lisans alabilirim?
adresini ziyaret ederek geçici lisans alabilirsiniz.[geçici lisans sayfası](https://purchase.groupdocs.com/temporary-license/).