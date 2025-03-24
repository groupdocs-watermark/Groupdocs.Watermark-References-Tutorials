---
title: Döşenmiş Resim Filigranı Ekle
linktitle: Döşenmiş Resim Filigranı Ekle
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak belgelerinize döşemeli görüntü filigranlarını nasıl ekleyeceğinizi öğrenin. Kolay, verimli ve özelleştirilebilir.
weight: 10
url: /tr/net/image-watermarkings/add-tiled-image-watermark/
---
## giriiş
GroupDocs.Watermark for .NET, geliştiricilerin program aracılığıyla çeşitli belge formatlarındaki filigranları eklemesine, kaldırmasına ve aramasına olanak tanıyan güçlü bir API'dir. Bu eğitimde, GroupDocs.Watermark for .NET'i kullanarak belgelerinize döşemeli görüntü filigranı ekleme sürecinde size rehberlik edeceğiz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Temel C# programlama dili bilgisi.
- Sisteminizde Visual Studio yüklü.
- GroupDocs.Watermark for .NET kitaplığı projenize eklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/Watermark/net/).

## Ad Alanlarını İçe Aktar
C# dosyanızın başında gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Adım 1: Belge Yolunu ve Çıktı Dizinini Ayarlayın
Giriş belgenizin yolunu ve çıktı belgesini kaydetmek istediğiniz dizini tanımlayın:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` giriş belgenizin mutlak veya göreceli yolu ile.
## 2. Adım: Filigran Nesnesini Başlatın
Giriş belgesi yolunu kullanarak bir Filigran nesnesi oluşturun:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Buraya filigran ekleyin
}
```
## 3. Adım: Döşenmiş Resim Filigranı Ekleme
Filigran olarak kullanmak istediğiniz görüntü dosyasının yolunu içeren bir ImageWatermark nesnesinin örneğini oluşturun:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Kutucuk seçeneklerini yapılandırma
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Belgeye filigran ekleme
    watermarker.Add(watermark);
    // Değiştirilen belgeyi kaydet
    watermarker.Save(outputFileName);
}
```
 Yer değiştirmek`"Path to Your Image"` filigran resim dosyanızın gerçek yolunu içerir.

## Çözüm
Bu adımları izleyerek, GroupDocs.Watermark for .NET'i kullanarak belgelerinize kolayca döşenmiş görüntü filigranı ekleyebilirsiniz. İstenilen sonucu elde etmek için farklı seçenekler ve konfigürasyonlarla denemeler yapın.
## SSS'ler
### Tek bir belgeye birden fazla filigran ekleyebilir miyim?
Evet, GroupDocs.Watermark for .NET'i kullanarak bir belgeye farklı türde birden fazla filigran ekleyebilirsiniz.
### GroupDocs.Watermark tüm belge formatlarını destekliyor mu?
GroupDocs.Watermark, PDF, Word, Excel, PowerPoint ve çok daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Watermark'ın deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Filigranın görünümünü özelleştirebilir miyim?
Evet, filigranın konum, boyut, döndürme, şeffaflık vb. gibi çeşitli yönlerini özelleştirebilirsiniz.
### GroupDocs.Watermark teknik destek sunuyor mu?
 Evet, GroupDocs.Watermark forumundan teknik destek alabilirsiniz.[Burada](https://forum.groupdocs.com/c/watermark/19).