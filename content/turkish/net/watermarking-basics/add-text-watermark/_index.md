---
title: Metin Filigranı Ekle
linktitle: Metin Filigranı Ekle
second_title: GroupDocs.Watermark .NET API'si
description: Bu adım adım kılavuzla Groupdocs for .NET'i kullanarak belgelerinize nasıl metin filigranı ekleyeceğinizi öğrenin.
weight: 11
url: /tr/net/watermarking-basics/add-text-watermark/
---

# Metin Filigranı Ekle

## giriiş
GroupDocs.Watermark for .NET, geliştiricilerin .NET uygulamalarındaki çeşitli belge formatlarındaki filigranları eklemesine, aramasına ve kaldırmasına olanak tanıyan güçlü bir kitaplıktır. Bu eğitimde GroupDocs.Watermark'ı kullanarak bir belgeye metin filigranı eklemeye odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Temel C# programlama dili bilgisi.
2. Sisteminizde Visual Studio yüklü.
3.  .NET kitaplığı için GroupDocs.Watermark yüklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/Watermark/net/).

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# projenize aktarmanız gerekir.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Adım 1: Belge Yolunu ve Çıktı Dizinini Tanımlayın
Giriş belgenizin yolunu ve filigranlı belgenin kaydedileceği çıktı dizinini tanımlayın.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` giriş belgenizin mutlak veya göreceli yolu ile örneğin:`@"C:\Docs\document.pdf"`. Ayrıca filigranlı belgeyi kaydetmek istediğiniz dizini de belirtin.
## 2. Adım: Metin Filigranı Ekleme
 Örnekleyin`Watermarker` giriş belgesi yolunu içeren sınıf. Ardından, bir`TextWatermark` İstenilen metin ve yazı tipi ayarlarıyla nesneyi seçin.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Çözüm
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak bir belgeye nasıl metin filigranı ekleyeceğimizi öğrendik. Sezgisel API'si sayesinde geliştiriciler, çeşitli belge formatlarındaki filigranları kolayca işleyebilir.
## SSS'ler
### GroupDocs.Watermark for .NET tüm belge formatlarıyla uyumlu mu?
GroupDocs.Watermark, PDF, Microsoft Word, Excel, PowerPoint ve çok daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Metin filigranının görünümünü özelleştirebilir miyim?
Evet, metin filigranının yazı tipi, rengi, hizalaması ve opaklığı gibi çeşitli özelliklerini özelleştirebilirsiniz.
### GroupDocs.Watermark, filigranların belgelerden kaldırılmasına yönelik destek sağlıyor mu?
Evet, GroupDocs.Watermark, belgelerdeki filigranları arama ve kaldırma işlevi sunar.
### Satın almadan önce GroupDocs.Watermark for .NET'i deneyebilir miyim?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Watermark için nasıl teknik destek alabilirim?
 adresini ziyaret ederek teknik destek alabilirsiniz.[GroupDocs.Watermark forumu](https://forum.groupdocs.com/c/watermark/19).