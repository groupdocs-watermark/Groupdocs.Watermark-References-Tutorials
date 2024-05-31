---
title: Ek Açıklama Bilgilerini PDF'den Çıkarın
linktitle: Ek Açıklama Bilgilerini PDF'den Çıkarın
second_title: GroupDocs.Watermark .NET API'si
description: Bu ayrıntılı, adım adım kılavuzda GroupDocs.Watermark for .NET'i kullanarak PDF belgelerinden ek açıklama bilgilerini nasıl çıkaracağınızı öğrenin.
type: docs
weight: 23
url: /tr/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## giriiş
Sık sık PDF belgelerinizden ayrıntılı açıklama bilgileri çıkarmaya ihtiyaç duyuyor musunuz? İster belge yönetim sistemleri üzerinde çalışan bir geliştirici olun, ister çok sayıda PDF'yi işleyen bir profesyonel olun, ek açıklamaları verimli bir şekilde çıkarmak ve işlemek çok önemli olabilir. GroupDocs.Watermark for .NET ile bu görevi basit ve verimli hale getirecek güçlü bir araç setiniz elinizin altında.
## Önkoşullar
Koda dalmadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
1. Visual Studio: Visual Studio'nun kurulu olduğundan emin olun. Bu, kodu yazmak ve çalıştırmak için IDE'miz olacak.
2.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET kitaplığına sahip olmanız gerekir. Yapabilirsiniz[buradan indir](https://releases.groupdocs.com/Watermark/net/).
3. Temel C# Bilgisi: Örnekleri takip etmek için C# programlamaya aşinalık gereklidir.
## Ad Alanlarını İçe Aktar
Başlangıç olarak gerekli ad alanlarını projenize aktarmanız gerekir. Bu ad alanları, PDF dosyalarıyla çalışmak ve ek açıklamaları çıkarmak için gereken sınıfları ve yöntemleri içerir.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## 1. Adım: Projenizi Kurun
Öncelikle Visual Studio'da projemizi oluşturalım. Yeni bir Konsol Uygulaması (.NET Core) projesi oluşturun. Projeniz oluşturulduktan sonra GroupDocs.Watermark for .NET kitaplığına bir başvuru eklemeniz gerekir.
1. NuGet Paket Yöneticisini açın.
2.  Aramak`GroupDocs.Watermark`.
3.  Yükle`GroupDocs.Watermark` paket.
## 2. Adım: Belge Yollarını Tanımlayın
Daha sonra, giriş PDF belgenizin yollarını ve çıkarılan bilgilerin kaydedileceği çıktı dizinini belirtmeniz gerekecektir. Bu, uygulamanızın PDF dosyasını nerede bulacağını ve sonuçları nerede saklayacağını bilmesini sağlar.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 3. Adım: PDF Belgesini Yükleyin
 PDF belgesiyle çalışmak için onu kullanarak yüklememiz gerekir.`PdfLoadOptions`. Bu sınıf, yükleme işlemini yapılandırmak için seçenekler sunar.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ek açıklamaları çıkarmaya yönelik kod buraya gelecek
}
```
## 4. Adım: PDF İçeriğine Erişin
Belge yüklendikten sonra içeriğine erişebiliriz. Özellikle, sayfalar ve açıklamalar arasında geçiş yapabilmek için PDF içeriğini almak istiyoruz.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Adım 5: Sayfaları ve Ek Açıklamaları Yineleyin
Elimizde PDF içeriği varken, her sayfada ve ardından bu sayfalardaki her ek açıklamada döngü oluşturabiliriz. Bu, ihtiyacımız olan bilgiyi çıkarmamızı sağlar.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Ek açıklama ayrıntılarını buraya çıkarın
    }
}
```
## Adım 6: Ek Açıklama Ayrıntılarını Çıkarın
İç içe geçmiş döngüler içerisinde her bir açıklamayla ilgili çeşitli ayrıntıları çıkarırız. Bu, ek açıklama türünü, ilgili görselleri, metni ve konumsal verileri içerir.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Adım 7: Çıkarılan Verileri Kaydedin veya İşleyin
Son olarak, çıkarılan ek açıklama bilgileriyle ne yapmak istediğinize karar verin. İhtiyaçlarınıza bağlı olarak bunu konsola yazdırabilir, bir dosyaya kaydedebilir ve hatta bir veritabanında saklayabilirsiniz.
```csharp
// Çıkarılan verileri bir dosyaya kaydetme örneği
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Çözüm
GroupDocs.Watermark for .NET'i kullanarak PDF belgelerinden ek açıklama bilgilerinin çıkarılması, size çok fazla zaman ve emek kazandırabilecek basit bir işlemdir. Bu kılavuzda özetlenen adımları izleyerek bu işlevselliği projelerinize kolayca entegre edebilir ve değerli açıklama verilerinin çıkarılmasını otomatikleştirebilirsiniz.
 İster büyük hacimli PDF'leri yönetiyor olun, ister yalnızca belirli bilgileri ayıklamak istiyor olun, GroupDocs.Watermark for .NET güvenilir ve etkili bir çözüm sunar. Kontrol etmeyi unutmayın[dokümantasyon](https://reference.groupdocs.com/Watermark/net/) daha gelişmiş özellikler ve kişiselleştirme seçenekleri için.
## SSS'ler
### .NET için GroupDocs.Watermark nedir?
GroupDocs.Watermark for .NET, geliştiricilerin PDF'ler, Word belgeleri ve resimler de dahil olmak üzere çeşitli belge formatlarındaki filigranları eklemesine, aramasına ve kaldırmasına olanak tanıyan kapsamlı bir kitaplıktır.
### GroupDocs.Watermark'ı ücretsiz deneyebilir miyim?
 Evet, alabilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) Bir satın alma işlemi yapmadan önce kütüphanenin özelliklerini test etmek için.
### Sorunla karşılaşırsam nasıl destek alabilirim?
 GroupDocs ekibini ziyaret ederek destek alabilirsiniz[destek Forumu](https://forum.groupdocs.com/c/watermark/19).
### Test için geçici lisans almak mümkün mü?
 Evet, talep edebilirsiniz[geçici lisans](https://purchase.groupdocs.com/temporary-license/)test amaçlı.
### GroupDocs.Watermark for .NET'in tam sürümünü nereden satın alabilirim?
 Tam sürümünü adresinden satın alabilirsiniz.[GroupDocs web sitesi](https://purchase.groupdocs.com/buy).