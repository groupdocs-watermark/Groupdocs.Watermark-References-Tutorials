---
title: PDF'ye Yapı Filigranı Ekleme
linktitle: PDF'ye Yapı Filigranı Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak PDF dosyalarına yapay filigranları zahmetsizce nasıl ekleyeceğinizi öğrenin. Belgelerinizi kolaylıkla koruyun.
weight: 11
url: /tr/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
type: docs
---
# PDF'ye Yapı Filigranı Ekleme

## giriiş
PDF dosyalarına filigran eklemek, özellikle fikri mülkiyet veya markalama belgelerinin korunması söz konusu olduğunda, belge yönetiminin çok önemli bir yönüdür. Groupdocs.Watermark for .NET, PDF dosyalarına zahmetsizce filigran eklemek için güçlü bir çözüm sağlar. Bu eğitimde, PDF dosyalarına yapı filigranı ekleme sürecini adım adım anlatacağız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET'i şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/Watermark/net/).
2. Geliştirme Ortamı: Bir .NET geliştirme ortamı kurun.
3. PDF Belgesi: Filigranı eklemek istediğiniz PDF belgesini hazırlayın.
4. Çıktı Dizini: Filigranlı PDF dosyasını kaydetmek için bir dizin oluşturun.

## Ad Alanlarını İçe Aktarma
Başlangıç olarak C# projenize gerekli ad alanlarını içe aktarın:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: PDF Belgesini Yükleyin
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 2. Adım: Filigran Seçeneklerini Tanımlayın
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## 3. Adım: Metin Filigranı Ekleme
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## 4. Adım: Resim Filigranı Ekleme
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Adım 5: Filigranlı PDF'yi kaydedin
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak PDF dosyalarına yapay filigranların nasıl ekleneceğini öğrendik. Bu adımları izleyerek filigran işlevini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilir, belgelerinizin güvenliğini ve bütünlüğünü sağlayabilirsiniz.
## SSS'ler
### Metin filigranının görünümünü özelleştirebilir miyim?
Evet, metin filigranının yazı tipi, boyutu, rengi ve hizalaması gibi çeşitli hususları tercihlerinize göre özelleştirebilirsiniz.
### Groupdocs.Watermark diğer belge biçimlerine filigran eklemeyi destekliyor mu?
Evet, Groupdocs.Watermark, Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarına filigran eklemeyi destekler.
### Groupdocs.Watermark for .NET'in deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Groupdocs.Watermark ile ilgili herhangi bir sorun veya soru için nasıl destek alabilirim?
 Groupdocs topluluk forumundan destek alabilirsiniz[Burada](https://forum.groupdocs.com/c/watermark/19).
### Groupdocs.Watermark'ı ticari amaçlarla kullanabilir miyim?
Evet, ticari kullanım için lisansı şuradan satın alabilirsiniz:[Burada](https://purchase.groupdocs.com/buy).