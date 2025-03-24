---
title: Tüm Ekleri PDF'den Çıkarın
linktitle: Tüm Ekleri PDF'den Çıkarın
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak PDF'deki tüm ekleri nasıl çıkaracağınızı öğrenin. Sorunsuz bir çıkarma işlemi için adım adım kılavuzumuzu izleyin.
weight: 22
url: /tr/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
---

# Tüm Ekleri PDF'den Çıkarın

## giriiş
Bir PDF belgesinden ekleri zahmetsizce çıkarmak mı istiyorsunuz? Peki, doğru yerdesiniz! Bu kapsamlı eğitimde, Groupdocs.Watermark for .NET'i kullanarak PDF'deki tüm ekleri çıkarma sürecinde size rehberlik edeceğiz. Bu güçlü kitaplık, geliştiricilerin çeşitli belge formatlarındaki filigranları yönetmesine olanak tanır, ancak aynı zamanda gömülü dosyaların çıkarılmasına yönelik güçlü yetenekler de içerir. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu adım adım kılavuz süreci kolaylaştıracaktır.
## Önkoşullar
Koda dalmadan önce, başlamanız için ihtiyaç duyacağınız temel bilgileri ele alalım. Hazır olduğunuzdan emin olmak için işte hızlı bir kontrol listesi:
1. .NET Ortamı: Bir .NET geliştirme ortamının kurulduğundan emin olun. Visual Studio'yu veya seçtiğiniz herhangi bir .NET IDE'yi kullanabilirsiniz.
2.  Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET'in en son sürümünü şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/Watermark/net/).
3. Geliştirme Becerileri: C# programlamanın temel anlayışı ve .NET kitaplıklarına aşinalık.
4. Örnek PDF Belgesi: Test için kullanabileceğiniz ekleri olan örnek bir PDF belgesine sahip olun.
## Ad Alanlarını İçe Aktar
Kodlamaya başlamadan önce gerekli ad alanlarını içe aktarmanız gerekir. Bu, kodunuzu düzenlemenize yardımcı olur ve kullanacağınız sınıflara ve yöntemlere erişmenizi sağlar.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## 1. Adım: Projenizi Kurun
Öncelikle projenizi oluşturalım. .NET geliştirme ortamınızı açın ve yeni bir konsol uygulaması oluşturun.
### Yeni Bir Proje Oluştur
1. Visual Studio'yu açın.
2. "Yeni bir proje oluştur"u seçin.
3. Tercihinize göre "Konsol Uygulaması (.NET Core)" veya ".NET Framework"ü seçin.
4. Projenize bir ad verin ve "Oluştur"u tıklayın.
### .NET için Groupdocs.Watermark'ı ekleyin
1. Solution Explorer'da projenize sağ tıklayın.
2. "NuGet Paketlerini Yönet"i seçin.
3. "Groupdocs.Watermark"ı arayın ve en son sürümü yükleyin.
## 2. Adım: Yollarınızı Tanımlayın
Daha sonra belgeniz ve çıktı dizininiz için yolları tanımlamanız gerekir. Burası PDF'nizin ve çıkarılan eklerin saklanacağı yerdir.

 senin içinde`Program.cs` dosyanıza, yollarınızı tanımlamak için aşağıdaki kodu ekleyin:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` Ve`"Your Document Directory"` sisteminizdeki gerçek yollarla.
## 3. Adım: PDF Belgenizi Yükleyin
 Şimdi Groupdocs.Watermark'ı kullanarak PDF belgenizi yükleyelim. Bu adım, yükleme seçenekleri oluşturmayı ve yüklemeyi başlatmayı içerir.`Watermarker` sınıf.
### Yükleme Seçenekleri Oluştur
 İlk önce bir örneğini oluşturun`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### Filigranı Başlat
 Daha sonra şunu kullanın:`Watermarker` belgenizi yüklemek için sınıf:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kodunuz buraya gelecek
}
```
## Adım 4: Ekleri Çıkarın
Belgeniz yüklendiğinde ekleri çıkarmanın zamanı geldi. Kullanacaksın`PdfContent` Eklere erişmek ve bunları belirttiğiniz çıktı dizinine kaydetmek için sınıfı kullanın.
### PDF İçeriğini Alın
 İçinde`using` engelle, PDF içeriğini al:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Ekler Arasında Döngü
PDF'deki her ekte döngü yapın:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // Ekli dosyayı diske kaydedin
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
Bu kod her eki ayıklar ve çıktı dizininize kaydeder. Ayrıca konsola eklenen her eklentiyle ilgili bazı temel bilgileri de yazdırır.
## Çözüm
İşte buyur! Groupdocs.Watermark for .NET'i kullanarak ekleri PDF'den başarıyla çıkardınız. Bu eğitim, projenizi oluşturma, belgenizi yükleme ve ekleri adım adım çıkarma konusunda size yol gösterdi. Bu becerilerle artık .NET uygulamalarınızdaki PDF eklerini kolaylıkla yönetebilir ve değiştirebilirsiniz.
## SSS'ler
### .NET için Groupdocs.Watermark nedir?
Groupdocs.Watermark for .NET, PDF'ler de dahil olmak üzere çeşitli belge formatlarındaki filigranları eklemek, kaldırmak ve yönetmek için kapsamlı bir kitaplıktır. Ayrıca gömülü dosyaları ayıklamak için yetenekler sunar.
### PDF'ye gömülü diğer dosya türlerini çıkarabilir miyim?
Evet, Groupdocs.Watermark for .NET, yalnızca ekleri değil, PDF'ye gömülü her türlü dosyayı çıkarmanıza olanak tanır.
### Ücretsiz deneme mevcut mu?
 Evet, Groupdocs.Watermark for .NET'in ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### Sorunla karşılaşırsam nasıl destek alabilirim?
 adresini ziyaret ederek destek alabilirsiniz.[Groupdocs.Filigran destek forumu](https://forum.groupdocs.com/c/watermark/19).
### Groupdocs.Watermark for .NET'i kullanmak için lisansa ihtiyacım var mı?
 Evet, kütüphaneyi üretimde kullanmak için lisansa ihtiyacınız var. Lisans satın alabilirsiniz[Burada](https://purchase.groupdocs.com/buy) veya geçici lisans alın[Burada](https://purchase.groupdocs.com/temporary-license/).