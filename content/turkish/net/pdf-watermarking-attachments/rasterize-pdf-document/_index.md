---
title: PDF Belgesini Rasterleştir
linktitle: PDF Belgesini Rasterleştir
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak PDF belgelerini nasıl rasterleştireceğinizi öğrenin. Belge güvenliğini ve görsel çekiciliği zahmetsizce artırın.
weight: 27
url: /tr/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# PDF Belgesini Rasterleştir

## giriiş
Belge yönetimi ve manipülasyonu alanında GroupDocs.Watermark for .NET, çeşitli belge formatlarındaki filigranları eklemek, kaldırmak ve aramak için güçlü yetenekler sunan güçlü bir araç olarak öne çıkıyor. Belgelerinizi telif hakkı bildirimleriyle korumak, markalama için kurumsal logolar eklemek veya belgelere yalnızca damgalarla açıklama eklemek olsun, GroupDocs.Watermark, sezgisel API'si ve kapsamlı özellik seti ile süreci basitleştirir.
## Önkoşullar
GroupDocs.Watermark for .NET ile filigranlama dünyasına dalmadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
### 1. .NET Framework'ü yükleyin
Geliştirme makinenizde .NET Framework'ün kurulu olduğundan emin olun. Microsoft web sitesinden indirebilir veya tercih ettiğiniz paket yöneticisini kullanabilirsiniz.
#### 1. Adım: .NET Framework'ü indirin
Microsoft .NET Framework indirme sayfasını ziyaret edin.
#### Adım 2: .NET Framework'ü yükleyin
.NET Framework'ü sisteminize yüklemek için indirme sayfasında verilen kurulum talimatlarını izleyin.
### 2. GroupDocs.Watermark Lisansını Alın
GroupDocs.Watermark'ın tüm özelliklerinden yararlanmak için geçerli bir lisansa ihtiyacınız vardır. Bir lisans satın alabilir veya değerlendirme amacıyla geçici bir lisans alabilirsiniz.
#### 1. Adım: Lisans Alın
GroupDocs.Watermark satın alma sayfasını ziyaret edin.
#### 2. Adım: Geçici Lisans Satın Alın veya Alın
İhtiyaçlarınıza göre uygun lisanslama seçeneğini seçin; sürekli kullanım için bir lisans satın alın veya değerlendirme amacıyla geçici bir lisans edinin.

## Ad Alanlarını İçe Aktar
Belgelerinizi filigranlamaya başlamadan önce, GroupDocs'un işlevlerine sorunsuz bir şekilde erişmek için gerekli ad alanlarını içe aktardığınızdan emin olun.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Artık her şeyi ayarladığınıza göre, GroupDocs.Watermark for .NET'i kullanarak bir PDF belgesini rasterleştirmeye geçelim. Rasterleştirme, PDF belgesinin her sayfasını PNG gibi bir raster görüntü formatına dönüştürür.
## Adım 1: Değişkenleri Başlatın
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
"Belge Yolunuz" ve "Belge Dizininiz"i sırasıyla PDF belgenizin gerçek yolu ve istediğiniz çıktı dizini ile değiştirdiğinizden emin olun.
## Adım 2: Belgeyi Yükleyin ve Filigran Ekleyin
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Resim veya metin filigranını başlat
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Önce herhangi bir türden filigran ekleyin
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Tüm sayfaları rasterleştir
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Tüm sayfaların içeriği taramalı görüntülerle değiştirilir
    watermarker.Save(outputFileName);
}
```
Bu adımda PDF belgesini yüklüyoruz ve metin, yazı tipi, hizalama, döndürme açısı, boyutlandırma türü, ölçek faktörü ve opaklık gibi belirtilen özelliklere sahip bir metin filigranı başlatıyoruz. Daha sonra filigranı belgeye ekliyoruz. Daha sonra, PDF belgesinin içeriğini alıyoruz ve tüm sayfaları 100 DPI çözünürlükte PNG formatında rasterleştiriyoruz. Son olarak, değiştirilen belgeyi rasterleştirilmiş içerikle kaydediyoruz.

## Çözüm
GroupDocs.Watermark for .NET, çeşitli belge formatlarına kolaylıkla filigran eklemek için kapsamlı bir çözüm sunar. Bu eğitimde özetlenen adımları izleyerek PDF belgelerini etkili bir şekilde rasterleştirebilir ve güvenliklerini ve görsel çekiciliğini artırabilirsiniz.
## SSS'ler
### GroupDocs.Watermark, PDF'nin yanı sıra diğer belge formatlarıyla da uyumlu mudur?
Evet, GroupDocs.Watermark, Microsoft Word, Excel, PowerPoint, Visio, Outlook ve çok daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Watermark kullanılarak eklenen filigranların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Watermark, metin, yazı tipi, renk, boyut, opaklık, döndürme ve konum gibi filigran özelliklerini özelleştirmek için kapsamlı seçenekler sunar.
### GroupDocs.Watermark toplu işleme desteği sunuyor mu?
Evet, GroupDocs'u kullanarak birden çok belgeyi toplu modda kolayca işleyebilir, büyük dosya kümelerine filigran eklemede zamandan ve emekten tasarruf edebilirsiniz.
### GroupDocs.Watermark'ın deneme sürümü mevcut mu?
Evet, satın alma işlemi yapmadan önce özelliklerini değerlendirmek için GroupDocs.Watermark'ın ücretsiz deneme sürümünü web sitesinden indirebilirsiniz.
### GroupDocs.Watermark ile ilgili herhangi bir sorunla karşılaşırsam veya sorularım olursa nasıl yardım alabilirim?
Topluluktan destek almak için GroupDocs.Watermark forumunu ziyaret edebilir veya yardım için GroupDocs destek ekibine ulaşabilirsiniz.