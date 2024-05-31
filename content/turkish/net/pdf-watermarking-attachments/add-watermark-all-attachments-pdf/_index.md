---
title: PDF'deki Tüm Eklere Filigran Ekleme
linktitle: PDF'deki Tüm Eklere Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak PDF eklerine nasıl filigran ekleyeceğinizi öğrenin. Belgelerinizi özel filigranlarla kolayca güvence altına alın.
type: docs
weight: 16
url: /tr/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## giriiş
PDF eklerine filigran eklemek, özellikle güvenliği veya markalamayı sağlarken belge yönetiminde çok önemli bir adım olabilir. GroupDocs.Watermark for .NET, filigranları PDF dosyalarına sorunsuz bir şekilde gömmek için kapsamlı bir çözüm sunar. Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak bir PDF belgesindeki tüm eklere filigran ekleme sürecinde size yol göstereceğiz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Watermark for .NET: Henüz yapmadıysanız, GroupDocs.Watermark for .NET'i şu adresten indirip yükleyin:[İnternet sitesi](https://releases.groupdocs.com/Watermark/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE ile uygun bir geliştirme ortamı kurun.
3. PDF Belgesi: Filigran eklemek istediğiniz PDF belgesini, filigran eklemek istediğiniz eklerle birlikte hazırlayın.

## Ad Alanlarını İçe Aktarma
Kodun ayrıntılarına dalmadan önce GroupDocs.Watermark for .NET işlevlerine erişmek için gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Adım 1: Belge Yolunu ve Çıktı Dizinini Tanımlayın
İlk olarak, giriş PDF belgenizin yolunu ve filigranlı belgenin kaydedileceği dizini tanımlayın:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Adım 2: Yükleme Seçeneklerini ve Filigranı Başlatın
Ardından, PDF belgesi için yükleme seçeneklerini başlatın ve bir metin filigranı oluşturun:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## 3. Adım: Belgeyi ve Ekleri Yükleyin
PDF belgesini yükleyin ve eklerini yineleyin:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Adım 4: Ek Desteğini Kontrol Edin
Ekli dosyanın GroupDocs.Watermark tarafından desteklenip desteklenmediğini kontrol edin:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Adım 5: Eklere Filigran Ekleme
Ekli belgeyi yükleyin ve filigranı ekleyin:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Adım 6: Değişiklikleri Kaydet
Son olarak filigranlı PDF belgesindeki değişiklikleri kaydedin:
```csharp
    watermarker.Save(outputFileName);
}
```

## Çözüm
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak bir PDF belgesindeki tüm eklere filigranların nasıl ekleneceğini araştırdık. Adım adım kılavuzu izleyerek filigranları PDF dosyalarınıza sorunsuz bir şekilde entegre edebilir, belge güvenliğini ve markalaşmayı sağlayabilirsiniz.
## SSS'ler
### Filigranın görünümünü özelleştirebilir miyim?
Evet, filigranın metin, yazı tipi, boyutu, rengi ve konumu gibi çeşitli özelliklerini ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Watermark, PDF'nin yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, GroupDocs.Watermark, Microsoft Word, Excel, PowerPoint, Visio, Outlook ve Görseller dahil çok çeşitli belge formatlarını destekler.
### GroupDocs.Watermark'ın deneme sürümü mevcut mu?
Evet, web sitesinden ücretsiz deneme sürümünü indirerek GroupDocs.Watermark'ın özelliklerini keşfedebilirsiniz.
### Tek bir belgeye birden fazla filigran ekleyebilir miyim?
Kesinlikle GroupDocs.Watermark, belge güvenliğini ve markalamayı geliştirmek için metin, resim ve açıklama dahil olmak üzere birden fazla filigranı aynı anda eklemenize olanak tanır.
### GroupDocs.Watermark kullanıcıları için teknik destek mevcut mu?
Evet, GroupDocs, kullanıcılara karşılaşabilecekleri herhangi bir soru veya sorun konusunda yardımcı olmak amacıyla forumlar ve özel destek kanalları aracılığıyla kapsamlı teknik destek sağlar.