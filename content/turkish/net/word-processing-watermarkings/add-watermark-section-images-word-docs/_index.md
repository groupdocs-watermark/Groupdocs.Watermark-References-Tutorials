---
title: Word Dokümanlarındaki Bölüm Resimlerine Filigran Ekleme
linktitle: Word Dokümanlarındaki Bölüm Resimlerine Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: .NET için Filigran'ı kullanarak Word belgelerindeki görüntülere nasıl filigran ekleyeceğinizi öğrenin. Güvenli ve profesyonel belge koruması için kılavuzumuzu takip edin.
weight: 16
url: /tr/net/word-processing-watermarkings/add-watermark-section-images-word-docs/
---
## giriiş
Günümüzün dijital dünyasında belgelerinizi korumak çok önemlidir. Word belgelerinize filigran eklemek, içeriğinizi korumanın basit ama etkili bir yoludur. Bu eğitim, Groupdocs.Watermark for .NET'i kullanarak Word belgelerindeki bölüm görüntülerine filigran ekleme sürecinde size rehberlik edecektir. İster bu özelliği uygulamanıza entegre etmek isteyen bir geliştirici olun, ister yalnızca belgelerinizi korumak isteyin, bu kılavuz tam size göre.
## Önkoşullar
Ayrıntılara dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  .NET için Groupdocs.Watermark: İndirin[Burada](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Makinenizde .NET Framework'ün kurulu olduğundan emin olun.
3. Word Belgesi: Filigran eklemek istediğiniz bir Word belgesini hazır bulundurun.
4. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
5.  Geçici Lisans: Alın[geçici lisans](https://purchase.groupdocs.com/temporary-license/) Groupdocs.Watermark için.
## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını projenize aktarın. Bu, Groupdocs.Watermark'ın tüm işlevlerinin kullanılabilir olmasını sağlamak için çok önemli bir adımdır.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Şimdi süreci yönetilebilir adımlara ayıralım.
## 1. Adım: Projenizi Kurma
Öncelikle projenizi tercih ettiğiniz IDE'de kurun. Yeni bir .NET projesi oluşturun ve Groupdocs.Watermark kitaplığını yükleyin.
```bash
dotnet add package GroupDocs.Watermark
```
## Adım 2: Word Belgesini Yükleyin
Filigran eklemek istediğiniz Word belgesini yükleyin. Belgenizin yolunun doğru olduğundan emin olun.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kodunuz buraya gelecek
}
```
## 3. Adım: Filigranı Oluşturun
Word belgesindeki görsellere uygulayacağınız bir metin filigranı oluşturun. İhtiyaçlarınıza uyacak şekilde metni, yazı tipini, boyutu ve hizalamayı özelleştirin.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Adım 4: İlk Bölümden Görüntüleri Alın
Word belgesinin içeriğine erişin ve ilk bölümde tüm görselleri bulun. Bu adım, filigranın uygulanacağı görüntüleri tanımladığı için çok önemlidir.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WatermarkableImageCollection images = content.Sections[0].FindImages();
```
## Adım 5: Görüntülere Filigran Uygulayın
İlk bölümdeki her görüntüde dolaşın ve oluşturulan filigranı uygulayın. Bu, bölümdeki tüm görsellerin korunmasını sağlar.
```csharp
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Adım 6: Belgeyi Kaydedin
Son olarak filigranlı belgeyi belirtilen yola kaydedin. Bu, bir Word belgesindeki bölüm görüntülerine filigran ekleme işlemini tamamlar.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
Word belgelerinizdeki resimlere filigran eklemek, içeriğinizi korumanın güçlü bir yoludur. Groupdocs.Watermark for .NET ile bu süreç basit ve etkilidir. Belgelerinizin güvenli ve iyi korunduğundan emin olmak için bu eğitimde özetlenen adımları izleyin.
 Daha ayrıntılı belgeler için şu adresi ziyaret edin:[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/) . Herhangi bir sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, şuraya göz atın:[destek Forumu](https://forum.groupdocs.com/c/watermark/19).
## SSS'ler
### Filigran metnini özelleştirebilir miyim?
Evet, filigran metnini, yazı tipini, boyutunu, hizalamasını ve dönüşünü ihtiyaçlarınıza göre özelleştirebilirsiniz.
### Birden fazla bölüme filigran eklemek mümkün mü?
Evet, her bölümde döngü yapabilir ve filigranı tüm bölümlerdeki resimlere uygulayabilirsiniz.
### Bu yöntemi diğer belge formatları için kullanabilir miyim?
 Groupdocs Filigran çeşitli belge formatlarını destekler. Kontrol edin[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/) daha fazla ayrıntı için.
### Geçici lisansı nasıl alabilirim?
 Geçici lisans alabilirsiniz[Burada](https://purchase.groupdocs.com/temporary-license/).
### Groupdocs.Watermark'ı kullanırken sorunlarla karşılaşırsam ne olur?
 Ziyaret edin[destek Forumu](https://forum.groupdocs.com/c/watermark/19)Karşılaşabileceğiniz her türlü sorunla ilgili yardım için.