---
title: Word Belgelerine Metin Efektleriyle Filigran Ekleme
linktitle: Word Belgelerine Metin Efektleriyle Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak Word belgelerine metin efektli özel filigranların nasıl ekleneceğini öğrenin. Zahmetsizce belge güvenliği ve görsel çekicilik.
weight: 21
url: /tr/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerine metin efektli filigranların nasıl ekleneceğini inceleyeceğiz. Bu adım adım talimatları izleyerek belgelerinizi çeşitli metin efektleri içeren özelleştirilmiş filigranlarla geliştirebileceksiniz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Watermark for .NET: Kitaplığı şuradan indirin ve yükleyin:[İnternet sitesi](https://releases.groupdocs.com/Watermark/net/).
2. Belge Yolu: Filigranı eklemek istediğiniz Word belgesinin yolunu öğrenin.
3. Çıkış Dizini: Değiştirilen belgeyi kaydetmek istediğiniz bir dizine sahip olun.

## Ad Alanlarını İçe Aktar
Gerekli sınıflara ve yöntemlere erişmek için gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using GroupDocs.Watermark.Contents;
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
## Adım 2: Metin Efektleriyle Filigran Ekleme
İstediğiniz metin ve yazı tipiyle bir metin filigranı oluşturun, ardından satır formatı gibi metin efektlerini tanımlayın.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## 3. Adım: Filigran Seçeneklerini Özelleştirin
Metin efektleri gibi filigran bölümü seçeneklerini tanımlayın ve bunları filigrana atayın.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Adım 4: Belgeyi Kaydedin
Değiştirilen belgeyi eklenen filigranla kaydedin.
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Word belgelerine metin efektli filigranlar eklemek, bunların görsel çekiciliğini ve korumasını önemli ölçüde artırabilir. GroupDocs.Watermark for .NET ile bu süreç kolaylaştırılmış ve özelleştirilebilir hale gelir ve profesyonel görünümlü belgeleri verimli bir şekilde oluşturmanıza olanak tanır.
## SSS'ler
### Filigran metninin yazı tipini ve boyutunu özelleştirebilir miyim?
Evet, TextWatermark nesnesini oluştururken yazı tipini ve boyutunu belirleyebilirsiniz.
### Tek bir belgeye birden fazla filigran eklemek mümkün mü?
GroupDocs.Watermark for .NET kesinlikle tek bir belgeye farklı ayarlarla birden fazla filigran eklemeyi destekler.
### GroupDocs.Watermark, Word'ün yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, PDF, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Bir belgeye eklendikten sonra filigranı kaldırabilir miyim?
Evet, kitaplık filigranları belgelerden kolayca kaldırmaya yönelik yöntemler sağlar.
### Test amaçlı deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).