---
title: PDF'deki Görüntülere Filigran Ekleme
linktitle: PDF'deki Görüntülere Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Ayrıntılı, adım adım eğitimimizle GroupDocs.Watermark for .NET'i kullanarak PDF belgelerindeki görüntülere filigran eklemeyi öğrenin. PDF'lerinizi kolayca güvenceye alın.
weight: 19
url: /tr/net/pdf-watermarking-attachments/add-watermark-images-pdf/
type: docs
---
# PDF'deki Görüntülere Filigran Ekleme

## giriiş
Bir PDF belgesindeki görüntülere filigran eklemek, fikri mülkiyetinizi korumak veya belgelerinizin orijinalliğini sağlamak için önemli olabilir. GroupDocs.Watermark for .NET kullanılarak bu görev verimli ve kolay bir şekilde gerçekleştirilebilir. Bu eğitim, ortamınızı ayarlamaktan filigran eklemeye ve son belgeyi kaydetmeye kadar sürecin her adımında size rehberlik edecektir. Hadi dalalım!
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Visual Studio: .NET uygulamaları için Tümleşik Geliştirme Ortamı (IDE) olan Visual Studio'yu yükleyin.
2.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[yayın sayfası](https://releases.groupdocs.com/Watermark/net/).
3. Bir PDF Belgesi: Filigranlama işlevini test etmeye hazır, görüntülerin bulunduğu bir PDF belgesine sahip olun.
4.  Geçici Lisans: Alın[geçici lisans](https://purchase.groupdocs.com/temporary-license/) Ürünü değerlendiriyorsanız.
## Ad Alanlarını İçe Aktar
Öncelikle projenize gerekli ad alanlarının aktarıldığından emin olun. Bu, PDF belgeleri ve filigranlarla çalışmak için gereken temel ad alanlarını içerecektir.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belge Yolunu ve Çıktı Dizinini Ayarlayın
Başlamak için, giriş belgesinin yollarını ve filigranlı belgenin kaydedileceği çıktı dizinini tanımlayın. Bu adım, programınızın kaynak belgeyi nerede bulacağını ve işlenen dosyayı nerede saklayacağını bilmesini sağlamak için çok önemlidir.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Adım 2: PDF Belgesini Yükleyin
 Daha sonra, PDF belgesini şunu kullanarak yüklemeniz gerekir:`PdfLoadOptions`. Bu sınıf, gerekirse parola koruması gibi PDF'yi yükleme seçeneklerini belirtmenize olanak tanır.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigranlama kodunuz buraya gelecek
}
```
## 3. Adım: Filigranı Oluşturun
Şimdi filigranı başlatın. Bu örnekte "Korunan resim" yazan bir metin filigranı oluşturuyoruz. Yazı tipini, hizalamayı, döndürmeyi ve ölçeklendirmeyi ihtiyaçlarınıza göre özelleştirin.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 4. Adım: PDF İçeriğine Erişin
PDF belgesinin içeriğini alın. Özellikle PDF içindeki görsellere erişmemiz gerekiyor. Burada ilk sayfaya odaklanıyoruz ancak bunu gerektiği gibi diğer sayfalara da genişletebilirsiniz.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// İlk sayfadaki tüm görselleri alın
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Adım 5: Filigranı Görüntülere Uygulayın
İlk sayfada bulunan her görselde döngü yapın ve filigranı uygulayın. Bu, belirtilen sayfadaki tüm resimlere filigranın uygulanmasını sağlar.
```csharp
// Bulunan tüm görsellere filigran ekleyin
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Adım 6: Filigranlı Belgeyi Kaydetme
Son olarak filigranlı PDF'yi belirtilen çıktı dizinine kaydedin. Bu adım, değişiklikleri yeni bir dosyaya yazarak işlemi sonlandırır.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
İşte buyur! GroupDocs'u kullanarak PDF içindeki görüntülere filigran eklemek, belgelerinizin güvenliğini ve orijinalliğini büyük ölçüde artırabilecek basit bir işlemdir. Bu adımları izleyerek fikri mülkiyetinizin korunmasını ve belgelerinizin güvende olmasını sağlayabilirsiniz.
## SSS'ler
### .NET için GroupDocs.Watermark nedir?
GroupDocs.Watermark for .NET, geliştiricilerin PDF'ler de dahil olmak üzere çeşitli belge formatlarındaki filigranları eklemesine, aramasına ve kaldırmasına olanak tanıyan kapsamlı bir kitaplıktır.
### GroupDocs.Watermark'ı kullanarak hem metin hem de resim filigranları ekleyebilir miyim?
Evet, GroupDocs.Watermark hem metin hem de resim filigranlarını destekleyerek farklı türdeki filigran ihtiyaçları için esneklik sağlar.
### Bir PDF'de birden fazla sayfayı filigranlamak mümkün müdür?
Kesinlikle! PDF'deki her sayfada döngü yapabilir ve her sayfadaki görüntülere filigran uygulayabilirsiniz.
### GroupDocs.Watermark for .NET'i kullanmak için lisansa ihtiyacım var mı?
 Evet, lisans gereklidir. Bir[geçici lisans](https://purchase.groupdocs.com/temporary-license/) değerlendirme amaçlı.
### GroupDocs.Watermark for .NET hakkında daha fazla belgeyi nerede bulabilirim?
 Hakkında kapsamlı belgeler bulabilirsiniz.[GroupDocs.Watermark belgelendirme sayfası](https://tutorials.groupdocs.com/Watermark/net/).