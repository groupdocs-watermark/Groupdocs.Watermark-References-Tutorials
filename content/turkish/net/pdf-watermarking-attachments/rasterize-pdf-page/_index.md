---
title: PDF Sayfasını Rasterleştir
linktitle: PDF Sayfasını Rasterleştir
second_title: GroupDocs.Watermark .NET API'si
description: .NET için Watermark ile belge güvenliğini geliştirin. PDF'ye ve diğer formatlara sorunsuz bir şekilde filigran ekleyin.
weight: 28
url: /tr/net/pdf-watermarking-attachments/rasterize-pdf-page/
---

# PDF Sayfasını Rasterleştir

## giriiş
GroupDocs.Watermark for .NET, geliştiricilerin PDF, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarına sorunsuz bir şekilde filigran eklemesine olanak tanıyan güçlü bir API'dir. Sezgisel arayüzü ve kapsamlı özellikleriyle GroupDocs.Watermark, belgelere metin veya resim filigranları ekleme sürecini basitleştirerek kullanıcıların fikri mülkiyetlerini korumalarına ve belge güvenliğini zahmetsizce geliştirmelerine olanak tanır.
## Önkoşullar
GroupDocs.Watermark for .NET'i kullanmaya başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1. Kurulum: GroupDocs.Watermark for .NET'i şu adresten indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/Watermark/net/).
2.  Lisans: GroupDocs.Watermark for .NET için bir lisans edinin. Değerlendirme amacıyla geçici bir lisansı şu adresten alabilirsiniz:[Burada](https://purchase.groupdocs.com/temporary-license/) veya tam lisansı satın alın[satın alma sayfası](https://purchase.groupdocs.com/buy).
3. .NET Framework: Geliştirme makinenizde .NET Framework'ün kurulu olduğundan emin olun.
4. Belge: Filigran eklemek istediğiniz belgeyi hazırlayın.

## Ad Alanlarını İçe Aktar
GroupDocs.Watermark for .NET'i kullanmaya başlamak için gerekli ad alanlarını projenize aktarın:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: Filigranı Başlat
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## 3. Adım: Filigran Ekle
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Adım 4: Sayfayı Rasterleştirin
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Adım 5: Belgeyi Kaydedin
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Sonuç olarak, GroupDocs.Watermark for .NET, PDF'ye ve diğer belge formatlarına filigran eklemek için kusursuz bir çözüm sunar. Geliştiriciler, yukarıda özetlenen adım adım kılavuzu izleyerek PDF sayfalarını verimli bir şekilde rasterleştirebilir ve belge güvenliğini kolaylıkla geliştirebilir.
## SSS'ler
### GroupDocs.Watermark, PDF'nin yanı sıra diğer belge formatlarıyla da uyumlu mudur?
Evet, GroupDocs.Watermark, aralarında Word, Excel, PowerPoint, Visio ve daha fazlasının da bulunduğu çok çeşitli belge formatlarını destekler.
### Belgeye eklenen filigranın görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Watermark, metin ve resim filigranları için kapsamlı özelleştirme seçenekleri sunarak kullanıcıların yazı tipini, boyutunu, rengini, opaklığını ve konumunu tercihlerine göre ayarlamasına olanak tanır.
### GroupDocs.Watermark hem kişisel hem de ticari kullanıma uygun mudur?
Evet, GroupDocs.Watermark, hem bireysel hem de kurumsal ihtiyaçları karşılamak için esnek lisanslama seçenekleri sunarak onu kişisel projelerin yanı sıra büyük ölçekli ticari uygulamalar için de uygun hale getirir.
### GroupDocs.Watermark geliştiricilere teknik destek sunuyor mu?
Evet, geliştiriciler GroupDocs.Watermark forumu aracılığıyla kapsamlı teknik desteğe erişebilir; burada yardım arayabilirler, deneyimlerini paylaşabilirler ve diğer geliştiricilerle iletişim kurabilirler.
### Satın alma işlemi yapmadan önce GroupDocs.Watermark'ı deneyebilir miyim?
Kesinlikle! GroupDocs.Watermark'ın ücretsiz deneme sürümünden şu adresten yararlanabilirsiniz:[sürümler sayfası](https://releases.groupdocs.com/), bir satın alma işlemine başlamadan önce özelliklerini ve işlevlerini keşfetmenize olanak tanır.