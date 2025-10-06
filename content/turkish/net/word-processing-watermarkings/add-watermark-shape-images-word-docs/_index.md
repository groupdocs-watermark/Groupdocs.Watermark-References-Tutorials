---
title: Word Dokümanlarındaki Şekil Görüntülerine Filigran Ekleme
linktitle: Word Dokümanlarındaki Şekil Görüntülerine Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki görselleri şekillendirmek için nasıl filigran ekleyeceğinizi öğrenin. Bu eğitimle belge güvenliğini artırın.
weight: 17
url: /tr/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
---
# Word Dokümanlarındaki Şekil Görüntülerine Filigran Ekleme

## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki görselleri şekillendirmek için nasıl filigran ekleneceğini keşfedeceğiz. Filigranlama, özellikle hassas veya gizli bilgiler söz konusu olduğunda belge korumasının çok önemli bir yönüdür. Şekil görsellerine filigran ekleyerek belgelerinizin bütünlüğünü ve güvenliğini sağlayabilirsiniz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark kitaplığını şuradan indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/Watermark/net/).
2. Belge: Filigranı eklemek istediğiniz Word belgesini hazırlayın.
3. Geliştirme Ortamı: Tercih ettiğiniz .NET geliştirme ortamını kurun.
## Ad Alanlarını İçe Aktar
Kodu yazmadan önce gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin
Öncelikle belgenizin yolunu tanımlayın ve çıktı dosyasının adını belirtin:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 2. Adım: Filigranı Başlatın
 Bir örnek oluştur`Watermarker` belge yolunu ve isteğe bağlı yükleme seçeneklerini sağlayarak nesneyi:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigranlama mantığını buraya ekleyin
}
```
## 3. Adım: Metin Filigranı Oluşturun
Metin filigranını metin, yazı tipi, hizalama, döndürme, boyutlandırma vb. gibi istenen özelliklerle tanımlayın:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Adım 4: Şekil Görüntülerine Filigran Uygulayın
Şekil görüntülerini tanımlamak ve filigranı eklemek için belge bölümlerini ve şekillerini yineleyin:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Adım 5: Belgeyi Kaydedin
Filigranın eklendiği belgeyi belirtilen çıktı dosyasına kaydedin:
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki şekil görüntülerine filigranların nasıl ekleneceğini öğrendik. Adım adım kılavuzu takip ederek ve GroupDocs.Watermark'ın güçlü özelliklerinden yararlanarak belgelerinizin güvenliğini ve korunmasını etkili bir şekilde artırabilirsiniz.
## SSS'ler
### Filigran metninin görünümünü özelleştirebilir miyim?
Evet, filigranı tercihlerinize göre özelleştirmek için yazı tipi, boyut, renk, döndürme açısı ve hizalama gibi çeşitli özellikleri ayarlayabilirsiniz.
### GroupDocs.Watermark, Word'ün yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, GroupDocs.Watermark, PDF, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatları için destek sağlar.
### Tek bir belgeye birden fazla filigran eklemek mümkün mü?
Kesinlikle aynı belgeye farklı içerik, stil ve konumlara sahip birden fazla filigran ekleyebilirsiniz.
### GroupDocs.Watermark'ı kullanarak belgelerdeki filigranları kaldırabilir miyim?
Evet, GroupDocs.Watermark, belgelerdeki filigranları etkili bir şekilde algılamak ve kaldırmak için özellikler sunar.
### GroupDocs.Watermark platformlar arası uyumluluk sağlıyor mu?
Evet, GroupDocs.Watermark .NET Framework, .NET Core ve .NET Standard ile uyumludur ve farklı platformlar arasında kusursuz entegrasyon sağlar.