---
title: PDF'deki Görüntü Yapılarına Filigran Ekleme
linktitle: PDF'deki Görüntü Yapılarına Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak PDF dosyalarınızı kişiselleştirilmiş filigranlarla koruyun. PDF belgelerindeki görüntü yapılarına kolayca metin veya görüntü filigranları ekleyin.
weight: 18
url: /tr/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
type: docs
---
# PDF'deki Görüntü Yapılarına Filigran Ekleme

## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak bir PDF belgesindeki görüntü yapıtlarına filigran ekleme sürecinde size rehberlik edeceğiz. Bu adımları izleyerek PDF dosyalarınızı kişiselleştirilmiş filigranlarla etkili bir şekilde koruyabilirsiniz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/Watermark/net/).
2. Belge Yolu: Filigranı eklemek istediğiniz PDF belgesinin yolunu belirtin.
3. Çıkış Dizini: Filigranlı belgenin kaydedileceği bir dizin oluşturun.

## Ad Alanlarını İçe Aktar
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin ve Filigranı Başlatın
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Adım 2: PDF İçeriğini Alın ve Filigran Ekleyin
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Resim veya metin filigranını başlat
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Resme filigran ekleyin
				artifact.Image.Add(watermark);
			}
		}
	}
```
## 3. Adım: Filigranlı Belgeyi Kaydedin
```csharp
	watermarker.Save(outputFileName);
}
```

## Çözüm
GroupDocs.Watermark for .NET ile PDF belgelerindeki görüntü yapılarına filigran eklemek sorunsuz bir süreç haline gelir. Bu öğreticiyi izleyerek PDF dosyalarınızı özelleştirilmiş filigranlarla etkili bir şekilde koruyabilir, güvenliklerini ve orijinalliklerini sağlayabilirsiniz.
## SSS'ler
### PDF belgeme hem resim hem de metin filigranları ekleyebilir miyim?
Evet, GroupDocs.Watermark for .NET aynı anda hem resim hem de metin filigranlarının eklenmesini destekler.
### Bir belgeye ekleyebileceğim filigran sayısında herhangi bir sınırlama var mı?
Hayır, bir belgeye herhangi bir sınırlama olmaksızın birden fazla filigran ekleyebilirsiniz.
### Filigranın görünümünü ve konumunu özelleştirebilir miyim?
Kesinlikle filigranın görünümü, konumu ve özellikleri üzerinde tam kontrole sahipsiniz.
### GroupDocs.Watermark for .NET, PDF'nin yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, Word, Excel, PowerPoint ve daha fazlasını içeren çeşitli belge formatlarını destekler.
### Bir belgedeki filigranları kaldırmanın bir yolu var mı?
Evet, GroupDocs.Watermark for .NET, gerekirse filigranları belgelerden kaldırmaya yönelik yöntemler sağlar.