---
title: PDF'deki XObjects'e Filigran Ekleme
linktitle: PDF'deki XObjects'e Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak PDF'deki XObjects'e nasıl filigran ekleyeceğinizi öğrenin. Kolay uygulama için adım adım kılavuzumuzu izleyin.
type: docs
weight: 20
url: /tr/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## giriiş
PDF'lere filigran eklemek, belgelerinizin yetkisiz kullanıma karşı korunmasını sağlamak için çok önemli bir adımdır. Groupdocs.Watermark for .NET ile PDF'lerinizdeki XObject'lere filigran eklemek hiç bu kadar kolay olmamıştı. Bu eğitimde, filigranları PDF belgelerinize güvenle uygulayabilmenizi sağlamak için süreç boyunca size adım adım yol göstereceğiz. Başlayalım!
## Önkoşullar
Eğiticiye dalmadan önce, sorunsuz bir şekilde takip etmek için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
-  Groupdocs.Watermark for .NET: En son sürümü şuradan indirin ve yükleyin:[Burada](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Geliştirme makinenizde .NET Framework'ün kurulu olduğundan emin olun.
- Geliştirme Ortamı: Visual Studio'yu veya .NET geliştirmeyi destekleyen başka bir IDE'yi kullanın.
-  Geçici Lisans: Alın[geçici lisans](https://purchase.groupdocs.com/temporary-license/) Ürünü değerlendiriyorsanız.
Bu önkoşulları yerine getirdikten sonra PDF'lerinize filigran eklemeye hazırsınız.
## Ad Alanlarını İçe Aktar
Öncelikle projenize gerekli ad alanlarını içe aktarmanız gerekir. C# projenizi açın ve aşağıdaki kullanarak yönergeleri ekleyin:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belge Yollarınızı Ayarlayın
İlk adım, belgenizin yollarını ayarlamayı içerir. PDF'nizin bulunduğu yolu ve filigranlı PDF'yi kaydetmek istediğiniz yolu tanımlayın.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` Ve`"Your Document Directory"` makinenizdeki gerçek yollarla.
## 2. Adım: PDF Yükleme Seçeneklerini Başlatın
Daha sonra PDF yükleme seçeneklerini başlatmanız gerekecek. Bu, PDF içeriğinin doğru şekilde yüklenmesi için çok önemlidir.
```csharp
var loadOptions = new PdfLoadOptions();
```
## 3. Adım: PDF Belgesini Yükleyin
Yükleme seçeneklerini kullanarak PDF belgesini`Watermarker` sınıf.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 4. Adım: Filigranı Oluşturun
Şimdi PDF'ye eklenecek filigranı oluşturmanız gerekiyor. Bu eğitim için bir metin filigranı oluşturacağız.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Adım 5: XObjects'e Filigran Ekleme
Filigranı uygulamak için PDF içindeki her sayfayı ve her XObject'i yineleyin.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Resme filigran ekleyin
            xObject.Image.Add(watermark);
        }
    }
}
```
## Adım 6: Filigranlı PDF'yi kaydedin
Son olarak filigranlı PDF'yi belirtilen çıktı dosyasına kaydedin.
```csharp
    watermarker.Save(outputFileName);
}
```
İşte buyur! PDF'niz artık tüm XObject'lerinde filigranlar içeriyor.
## Çözüm
 Groupdocs'u kullanarak PDF belgelerinize filigran eklemek, ek bir güvenlik katmanı sağlayan basit bir işlemdir. Bu eğitimde özetlenen adımları izleyerek belgelerinizin yetkisiz kullanıma karşı korunmasını sağlayabilirsiniz. Unutmayın, her zaman başvurabilirsiniz[dokümantasyon](https://reference.groupdocs.com/Watermark/net/) daha ayrıntılı bilgi ve gelişmiş özellikler için.
## SSS'ler
### Bir resmi metin yerine filigran olarak kullanabilir miyim?
Evet, Groupdocs.Watermark for .NET hem metin hem de resim filigranlarını destekler.
### Groupdocs.Watermark'ı satın almadan nasıl test edebilirim?
 Bir kullanabilirsiniz[geçici lisans](https://purchase.groupdocs.com/temporary-license/) Ürünü değerlendirmek için.
### Filigranın görünümünü özelleştirmek mümkün mü?
Kesinlikle! Yazı tipini, boyutunu, döndürme açısını ve daha fazlasını özelleştirebilirsiniz.
### Groupdocs.Watermark diğer belge formatlarını destekliyor mu?
Evet, Word, Excel ve PowerPoint dahil olmak üzere çeşitli formatları destekler.
### Sorunlarla karşılaşırsam nereden destek alabilirim?
 adresinden destek alabilirsiniz.[Grup belgeleri forumu](https://forum.groupdocs.com/c/watermark/19).