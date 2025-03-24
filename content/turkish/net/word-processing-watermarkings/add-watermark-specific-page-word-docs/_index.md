---
title: Word Dokümanlarında Belirli Sayfaya Filigran Ekleme
linktitle: Word Dokümanlarında Belirli Sayfaya Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs'u kullanarak Word belgelerindeki belirli sayfalara nasıl filigran ekleyeceğinizi öğrenin. İçeriğinizi zahmetsizce koruyun.
weight: 14
url: /tr/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---
## giriiş
Belgelere filigran eklemek, belge güvenliği ve markalamanın çok önemli bir yönüdür. Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki belirli bir sayfaya nasıl filigran ekleneceğini inceleyeceğiz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- Temel C# programlama bilgisi.
- Visual Studio IDE'yi yükledim.
- GroupDocs.Watermark for .NET projenizde yüklü.

## Ad Alanlarını İçe Aktarma
Koda dalmadan önce gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kodunuz buraya gelecek
}
```
## 2. Adım: Filigranı ekleyin
```csharp
// Filigran metnini ve stilini tanımlayın
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Son sayfaya filigran ekle
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## 3. Adım: Belgeyi Kaydedin
```csharp
// Belgeyi filigranla kaydedin
watermarker.Save(outputFileName);
```

## Çözüm
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki belirli bir sayfaya nasıl filigran ekleyeceğimizi öğrendik. Bu adımları izleyerek belgelerinizi etkili bir şekilde koruyabilir ve gerektiğinde markalama öğeleri ekleyebilirsiniz.
## SSS'ler
### Filigran metnini ve stilini özelleştirebilir miyim?
Evet, filigranın metnini, yazı tipini, boyutunu, rengini ve konumunu gereksinimlerinize göre özelleştirebilirsiniz.
### GroupDocs.Watermark for .NET diğer belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Watermark, Word, Excel, PowerPoint, PDF ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### Tek bir belgeye birden fazla filigran ekleyebilir miyim?
Kesinlikle aynı belgeye farklı içerik ve stillere sahip birden fazla filigran ekleyebilirsiniz.
### GroupDocs.Watermark for .NET'in ücretsiz deneme sürümü var mı?
 Evet, GroupDocs.Watermark'ın özelliklerini ücretsiz denemeyle keşfedebilirsiniz. Başlamak için verilen bağlantıyı ziyaret etmeniz yeterli[Burada](https://releases.groupdocs.com/).
### GroupDocs.Watermark için nereden teknik destek alabilirim?
 Yararlı kaynaklar bulabilir ve teknik destek alabilirsiniz.[Burada](https://forum.groupdocs.com/c/watermark/19)GroupDocs.Watermark forumu. Topluluğa katılmak için sağlanan bağlantıyı ziyaret edin.