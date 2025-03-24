---
title: PDF'deki Ek Açıklama Görüntülerine Filigran Ekleme
linktitle: PDF'deki Ek Açıklama Görüntülerine Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak açıklama görüntülerine filigran ekleyerek PDF belgelerinizi nasıl koruyacağınızı öğrenin.
weight: 17
url: /tr/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---

# PDF'deki Ek Açıklama Görüntülerine Filigran Ekleme

## giriiş
Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak PDF belgelerindeki ek açıklama görüntülerine filigranların nasıl ekleneceğini inceleyeceğiz. Filigranlama, belgelerinizi izinsiz kullanıma veya dağıtıma karşı korumak için çok önemlidir. Bu adım adım kılavuzu izleyerek, metin filigranlarını PDF'lerdeki açıklama görüntülerine etkili bir şekilde nasıl uygulayacağınızı öğreneceksiniz.
## Önkoşullar
Devam etmeden önce aşağıdakilere sahip olduğunuzdan emin olun:
1. C# programlama dilinin temel anlayışı.
2. .NET kitaplığı için Groupdocs.Watermark yüklendi.
3. Visual Studio gibi bir geliştirme ortamına erişim.
4. Filigran eklenecek açıklama görüntüleri içeren bir PDF belgesi.

## Ad Alanlarını İçe Aktarma
Öncelikle gerekli ad alanlarını C# kodunuza aktarmanız gerekir:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## 2. Adım: PDF İçeriğini Alın ve Filigranı Başlatın
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Resim veya metin filigranını başlat
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## 3. Adım: PDF Sayfalarını ve Ek Açıklama Görüntülerini Yineleyin
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Resme filigran ekleyin
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Adım 4: Belgeyi Filigranla Kaydetme
```csharp
    watermarker.Save(outputFileName);
}
```
Bu adımları uyguladıktan sonra, PDF belgenizde, açıklama resimlerine belirtilen filigran eklenecektir.

## Çözüm
PDF'lerdeki açıklama görsellerine filigran eklemek, belgelerinizin bütünlüğünü korumak ve kötüye kullanılmamasını sağlamak açısından çok önemlidir. Groupdocs.Watermark for .NET ile bu süreç basit ve verimli hale gelir ve PDF dosyalarınızı etkili bir şekilde korumanıza olanak tanır.
## SSS'ler
### Aynı PDF belgesine birden fazla filigran ekleyebilir miyim?
Evet, Groupdocs.Watermark for .NET'i kullanarak aynı PDF belgesine birden fazla filigran ekleyebilirsiniz.
### Groupdocs.Watermark, PDF'nin yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, Groupdocs Filigran, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### Filigranın görünümünü özelleştirmek mümkün mü?
Kesinlikle filigranın metnini, yazı tipini, rengini, boyutunu ve konumunu tercihlerinize göre özelleştirebilirsiniz.
### Groupdocs.Watermark'ı kullanarak PDF belgelerinden filigranları kaldırabilir miyim?
Evet, Groupdocs.Watermark, filigranları PDF belgelerinden zahmetsizce kaldırma işlevi sağlar.
### Groupdocs.Watermark for .NET'in ücretsiz deneme sürümü var mı?
Evet, web sitesinden Groupdocs.Watermark for .NET'in ücretsiz denemesinden yararlanabilirsiniz.