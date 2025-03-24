---
title: PDF'ye Salt Yazdır Açıklama Filigranı Ekleme
linktitle: PDF'ye Salt Yazdır Açıklama Filigranı Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak PDF'lere salt yazdırılabilir açıklama filigranlarını nasıl ekleyeceğinizi öğrenin. Belge güvenliğini ve markalamayı zahmetsizce geliştirin.
weight: 13
url: /tr/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# PDF'ye Salt Yazdır Açıklama Filigranı Ekleme

## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak PDF'ye salt yazdırılabilir açıklama filigranı ekleme sürecini ayrıntılı olarak ele alacağız. Belgelere filigran eklemek, belge güvenliği ve markalamanın çok önemli bir yönüdür ve GroupDocs.Watermark, .NET geliştiricilerinin bunu başarması için kusursuz bir çözüm sağlar.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- C# programlama dilinin temel anlayışı.
- Makinenizde Visual Studio yüklü.
- Projenizde yüklü olan .NET kitaplığı için GroupDocs.Watermark.

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin
 Öncelikle filigran eklemek istediğiniz PDF belgesini yüklemeniz gerekir. Yer değiştirmek`"Your Document Path"` PDF dosyanızın yolu ile ve`"Your Document Directory"` çıktı dosyasını kaydetmek istediğiniz dizinle.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigran kodu buraya eklenecek
}
```
## 2. Adım: Filigran Ekle
Daha sonra istediğiniz metin ve yazı tipiyle bir metin filigranı nesnesi oluşturun. Ayarlamak`isPrintOnly` ile`true` filigranın görüntüleme modunda değil, yalnızca belge yazdırıldığında görünmesini sağlamak için.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## 3. Adım: Filigran Seçeneklerini Yapılandırma
Filigranın eklenmesi gereken sayfa dizini ve bunu salt yazdırılan bir açıklama olarak belirtme gibi filigran seçeneklerini tanımlayın.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## 4. Adım: Filigran Uygulayın
Belirtilen seçenekleri kullanarak filigranı belgeye ekleyin ve çıktı dosyasını kaydedin.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Çözüm
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak bir PDF belgesine salt yazdırılabilir açıklama filigranının nasıl ekleneceğini öğrendik. Bu, geliştiricilerin belge güvenliğini ve markalamayı kolaylıkla geliştirmesine olanak tanır.
## SSS'ler
### GroupDocs.Watermark, PDF'nin yanı sıra diğer belge formatlarıyla da uyumlu mudur?
Evet, GroupDocs Filigran, Word, Excel, PowerPoint ve resimler gibi çeşitli belge formatlarını destekler.
### Filigranın görünümünü özelleştirebilir miyim?
Kesinlikle GroupDocs.Watermark, filigran metnini, yazı tipini, rengini, boyutunu ve konumunu özelleştirmek için kapsamlı seçenekler sunar.
### GroupDocs.Watermark toplu işleme yetenekleri sunuyor mu?
Kesinlikle, geliştiriciler toplu işleme özelliklerini kullanarak aynı anda birden fazla belgeye filigran ekleyebilir.
### GroupDocs.Watermark'ın deneme sürümü mevcut mu?
Evet, sağlanan bağlantıdan GroupDocs.Watermark'ın ücretsiz deneme sürümüne erişebilirsiniz.
### GroupDocs.Watermark için nasıl teknik destek alabilirim?
Sağlanan destek bağlantısında bulunan GroupDocs.Watermark forumundan teknik yardım alabilirsiniz.