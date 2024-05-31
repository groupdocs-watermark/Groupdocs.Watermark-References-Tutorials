---
title: Word Belgelerindeki Belirli Sayfalara Filigran Ekleme
linktitle: Word Belgelerindeki Belirli Sayfalara Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs for .NET'i kullanarak Word belgelerindeki belirli sayfalara zahmetsizce nasıl filigran ekleyeceğinizi öğrenin. Belge güvenliğini ve markalamayı geliştirin.
type: docs
weight: 18
url: /tr/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---
## giriiş
Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak Word belgelerindeki belirli sayfalara filigran ekleme sürecini anlatacağız. Filigranlama, belgeleriniz için güvenlik ve markalama sağlayan, belge yönetiminin çok önemli bir yönüdür. Groupdocs.Watermark for .NET ile Word belgelerinize hassas ve verimli bir şekilde kolayca metin veya resim filigranları ekleyebilirsiniz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET'i şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/Watermark/net/).
2. Belge: Filigran eklemek istediğiniz Word belgesini hazır bulundurun.
3. Geliştirme Ortamı: Geliştirme ortamınızı Visual Studio veya başka herhangi bir .NET geliştirme aracıyla kurun.

## Ad Alanlarını İçe Aktar
Koda dalmadan önce gerekli ad alanlarını içe aktaralım:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## 1. Adım: Belgeyi Yükleyin
Öncelikle Word belgesini filigran nesnesine yüklememiz gerekiyor.
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
Şimdi belgenin belirli sayfalarına metin filigranı ekleyelim.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Filigranın ekleneceği sayfaları belirtin
};
watermarker.Add(textWatermark);
```
## 3. Adım: Belgeyi Kaydedin
Son olarak filigranlı belgeyi istediğiniz konuma kaydedin.
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak Word belgelerindeki belirli sayfalara filigranların nasıl ekleneceğini öğrendik. Yalnızca birkaç satır kodla belgelerinizin güvenliğini ve markalaşmasını zahmetsizce artırabilirsiniz.
## SSS'ler
### Tek bir belgeye birden fazla filigran ekleyebilir miyim?
Evet, her filigran için filigran ekleme işlemini tekrarlayarak birden fazla filigran ekleyebilirsiniz.
### Groupdocs.Watermark, Word'ün yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, Groupdocs, PDF, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Filigranın görünümünü özelleştirebilir miyim?
Kesinlikle filigranın yazı tipi, boyutu, rengi ve opaklığı gibi çeşitli yönlerini özelleştirebilirsiniz.
### Teknik destek mevcut mu?
 Evet, Groupdocs forumunda teknik destek ve kaynaklar bulabilirsiniz[Burada](https://forum.groupdocs.com/c/watermark/19).