---
title: PDF'ye Ek Açıklama Filigranı Ekleme
linktitle: PDF'ye Ek Açıklama Filigranı Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak PDF belgelerine zahmetsizce açıklama filigranlarını nasıl ekleyeceğinizi öğrenin. Belge markalamayı ve güvenliği kolaylıkla geliştirin.
weight: 10
url: /tr/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
type: docs
---
# PDF'ye Ek Açıklama Filigranı Ekleme

## giriiş
Belge yönetimi alanında, PDF dosyalarına filigran eklemek, özellikle markalama, güvenlik ve belge tanımlama amaçları açısından çok önemli bir husustur. GroupDocs.Watermark for .NET, filigranların PDF'ler de dahil olmak üzere çeşitli belge formatlarına kusursuz entegrasyonunu kolaylaştıran güçlü bir kitaplıktır. Bu öğreticide, GroupDocs.Watermark for .NET tarafından sağlanan işlevleri kullanarak PDF belgelerine açıklama filigranları ekleme sürecini adım adım ele alacağız.
## Önkoşullar
Eğiticiye devam etmeden önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1.  GroupDocs.Watermark for .NET Kitaplığı: GroupDocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[İnternet sitesi](https://releases.groupdocs.com/Watermark/net/).
2. Geliştirme Ortamı: Visual Studio veya başka herhangi bir .NET IDE gibi uygun bir geliştirme ortamı kurun.
3. Temel C# Anlayışı: C# programlama dilinin temellerine aşinalık önerilir.

## Gerekli Ad Alanlarını İçe Aktarma
Başlamak için gerekli ad alanlarını C# projenize aktarın:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
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
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## 3. Adım: Metin Filigranı Ekleme
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## 4. Adım: Resim Filigranı Ekleme
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## Adım 5: Belgeyi Filigranla Kaydetme
```csharp
	watermarker.Save(outputFileName);
}
```

## Çözüm
Sonuç olarak, GroupDocs.Watermark for .NET, PDF belgelerine program aracılığıyla açıklama filigranları eklemek için kapsamlı bir çözüm sunar. Kullanıcılar özetlenen adımları izleyerek metin ve resim filigranlarını PDF dosyalarına sorunsuz bir şekilde entegre edebilir, böylece belge markalama ve güvenliğini artırabilir.
## SSS'ler
### GroupDocs.Watermark, PDF'nin yanı sıra diğer belge formatlarıyla da uyumlu mudur?
Evet, GroupDocs.Watermark, aralarında Word, Excel, PowerPoint ve daha fazlasının da bulunduğu çok çeşitli belge formatlarını destekler.
### Filigranın görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Watermark, hem metin hem de resim filigranları için kapsamlı özelleştirme seçenekleri sunarak kullanıcıların boyutu, konumu, opaklığı ve diğer parametreleri ayarlamasına olanak tanır.
### GroupDocs.Watermark belgelerin toplu işlenmesi için uygun mudur?
Kesinlikle! GroupDocs.Watermark, etkili toplu işleme yetenekleri sunarak kullanıcıların aynı anda birden fazla belgeye filigran uygulamasına olanak tanır.
### GroupDocs.Watermark .NET Core geliştirmeyi destekliyor mu?
Evet, GroupDocs.Watermark, geliştiricilerin filigranlama işlevlerini platformlar arası uygulamalara entegre etmesine olanak tanıyan .NET Core'u destekler.
### GroupDocs.Watermark kullanıcıları için teknik destek mevcut mu?
Evet, GroupDocs, özel forumları ve müşteri hizmetleri kanalları aracılığıyla kapsamlı teknik destek sağlar.