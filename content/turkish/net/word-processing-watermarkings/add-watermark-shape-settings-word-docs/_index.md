---
title: Word Dokümanlarında Şekil Ayarlarıyla Filigran Ekleme
linktitle: Word Dokümanlarında Şekil Ayarlarıyla Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs için Watermark'ı kullanarak Word belgelerine şekil ayarlarıyla filigran eklemeyi öğrenin. Belgelerinizi etkili bir şekilde koruyun.
type: docs
weight: 20
url: /tr/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerine şekil ayarlarıyla filigran ekleme sürecini anlatacağız.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  .NET için GroupDocs.Watermark yüklü. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/Watermark/net/).
2. Temel C# programlama bilgisi.
3. Word belgesi işlemenin anlaşılması.

## Ad Alanlarını İçe Aktar
Öncelikle gerekli sınıflara ve yöntemlere erişmek için gerekli ad alanlarını içe aktarmanız gerekir.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin
Filigranı eklemek istediğiniz Word belgesini yükleyin.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigran ekleme kodu buraya gelecek
}
```
## 2. Adım: Filigran Ekle
 Bir örnek oluştur`TextWatermark` nesneyi seçin ve filigran olarak kullanmak istediğiniz metni belirtin.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## 3. Adım: Filigran Ayarlarını Özelleştirin
Filigran için hizalama, döndürme açısı, renk ve opaklık gibi çeşitli ayarları yapın.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Adım 4: Filigran Bölümü Seçeneklerini Tanımlayın
Filigran bölümü için şekil adı ve alternatif metin gibi seçenekleri tanımlayın.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Adım 5: Belgeye Filigran Ekleme
Filigranı belirtilen seçeneklerle belgeye ekleyin.
```csharp
watermarker.Add(watermark, options);
```
## Adım 6: Belgeyi Kaydedin
Belgeyi eklenen filigranla kaydedin.
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
GroupDocs'u kullanarak Word belgelerine şekil ayarlarıyla filigran eklemek basit bir işlemdir. Bu eğitimde özetlenen adımları izleyerek belgelerinizi özelleştirilmiş filigranlarla etkili bir şekilde koruyabilirsiniz.
## SSS'ler
### Aynı belgeye birden fazla filigran ekleyebilir miyim?
Evet, aynı belgeye farklı ayarlarla birden fazla filigran ekleyebilirsiniz.
### GroupDocs.Watermark, Word'ün yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, GroupDocs.Watermark, Excel, PowerPoint, PDF ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### Filigranın görünümünü daha da özelleştirebilir miyim?
Kesinlikle yazı tipi boyutu, stili, rengi ve konumu gibi çeşitli parametreleri ihtiyaçlarınıza göre ayarlayabilirsiniz.
### GroupDocs.Watermark for .NET'in deneme sürümü mevcut mu?
 Evet, şu adresten ücretsiz deneme alabilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Watermark desteğini nerede bulabilirim?
 GroupDocs forumunda destek bulabilir ve soru sorabilirsiniz[Burada](https://forum.groupdocs.com/c/watermark/19).