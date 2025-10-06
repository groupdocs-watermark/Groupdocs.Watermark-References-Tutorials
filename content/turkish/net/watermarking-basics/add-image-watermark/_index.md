---
title: Resim Filigranı Ekle
linktitle: Resim Filigranı Ekle
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak belgelerinize zahmetsizce görüntü filigranları ekleyin. Fikri mülkiyetinizi kolaylıkla koruyun.
weight: 10
url: /tr/net/watermarking-basics/add-image-watermark/
type: docs
---
# Resim Filigranı Ekle

## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak belgelerinize görüntü filigranı ekleme sürecini ayrıntılı olarak ele alacağız. Filigranlama belgeleri, fikri mülkiyetin ve markalaşmanın korunması için gereklidir. GroupDocs.Watermark for .NET ile filigranları Word, Excel, PowerPoint, PDF ve çok daha fazlası gibi çeşitli belge formatlarına sorunsuz bir şekilde entegre edebilirsiniz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1.  GroupDocs.Watermark for .NET Kitaplığı: GroupDocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[İnternet sitesi](https://releases.groupdocs.com/Watermark/net/).
2. Belge: Filigranı eklemek istediğiniz belgeyi hazır bulundurun.
3. Filigran için Resim: Filigran olarak kullanmak istediğiniz resim dosyasını hazırlayın.

## Ad Alanlarını İçe Aktar
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## 1. Adım: Belge Yolunu ve Çıktı Dizinini Başlatın
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"`belgenizin mutlak veya göreceli yolu ile ve`"Your Document Directory"` filigranlı belgeyi kaydetmek istediğiniz dizinle.
## 2. Adım: Belge Akışını açın ve Filigranı Başlatın
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Filigran ekleme işlemi buraya gelecek
    }
}
```
 Belge akışını şunu kullanarak açın:`FileStream` ve başlatın`Watermarker` nesne.
## 3. Adım: Resim Filigranı Ekleme
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Oluşturduğunuz bir`ImageWatermark` filigran olarak kullanmak istediğiniz görüntü dosyasının yolunu içeren nesneyi seçin. Filigranın yatay ve dikey hizalamasını ayarlayın.
## Adım 4: Filigranlı Belgeyi Kaydetme
```csharp
watermarker.Save(outputFileName);
```
Filigranlı belgeyi istenen dosya adıyla belirtilen çıktı dizinine kaydedin.

## Çözüm
Sonuç olarak, GroupDocs.Watermark for .NET, çeşitli belge formatlarına zahmetsizce filigran eklemek için kapsamlı bir çözüm sunar. Bu eğitimde özetlenen adımları izleyerek belgelerinize etkili bir şekilde görüntü filigranları ekleyebilir ve fikri mülkiyetinizi koruyabilirsiniz.
## SSS'ler
### GroupDocs.Watermark for .NET'i kullanarak metin filigranları ekleyebilir miyim?
Evet, GroupDocs.Watermark for .NET, belgelere hem resim hem de metin filigranlarının eklenmesini destekler.
### GroupDocs.Watermark for .NET farklı belge formatlarıyla uyumlu mu?
GroupDocs.Watermark for .NET kesinlikle Word, Excel, PowerPoint, PDF ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Watermark for .NET filigranlar için özelleştirme seçenekleri sağlıyor mu?
Evet, filigranın konum, boyut, opaklık ve döndürme gibi çeşitli yönlerini özelleştirebilirsiniz.
### GroupDocs.Watermark for .NET'i kullanarak filigranları belgelerden kaldırabilir miyim?
Evet, GroupDocs.Watermark for .NET, belgelerdeki filigranları tespit etme ve kaldırma işlevselliği sunar.
### GroupDocs.Watermark for .NET'in deneme sürümü mevcut mu?
 Evet, satın almadan önce özellikleri keşfetmek için web sitesinden ücretsiz deneme sürümünden yararlanabilirsiniz.[Burada](https://releases.groupdocs.com/).