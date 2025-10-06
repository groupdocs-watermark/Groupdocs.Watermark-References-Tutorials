---
title: PDF'deki Belirli Sayfalara Filigran Ekleme
linktitle: PDF'deki Belirli Sayfalara Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs'u kullanarak PDF'lerdeki belirli sayfalara metin ve resim filigranları eklemeyi öğrenin. Belgelerinizi güvence altına almak için ayrıntılı kılavuzumuzu izleyin.
weight: 15
url: /tr/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
type: docs
---
# PDF'deki Belirli Sayfalara Filigran Ekleme

## giriiş
PDF belgelerinize filigran eklemek, içeriğinizi korumak ve sahipliğinizi iddia etmek için çok önemli bir adımdır. İster bir taslağı işaretliyor, ister hassas bilgileri güvence altına alıyor, ister yalnızca markalama ekliyor olun, filigranlar etkili bir araçtır. Bu öğreticide, PDF dosyalarınızdaki belirli sayfalara hem metin hem de resim filigranları eklemek için Groupdocs.Watermark for .NET'in nasıl kullanılacağını keşfedeceğiz. Süreci yönetilebilir adımlara bölerek bu özellikleri takip edebilmenizi ve projelerinizde uygulayabilmenizi sağlayacağız.
## Önkoşullar
Uygulamaya geçmeden önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
- Visual Studio Yüklü: .NET kodunuzu yazmak ve çalıştırmak için Visual Studio gibi bir IDE'ye ihtiyacınız olacak.
- .NET Framework: Makinenizde .NET framework'ün kurulu olduğundan emin olun.
-  .NET için Groupdocs.Watermark: .NET için Groupdocs.Watermark'ı indirip yükleyin. Alabilirsin[Burada](https://releases.groupdocs.com/Watermark/net/).
- Temel C# Bilgisi: C# programlama diline aşina olmak faydalı olacaktır.
- Bir PDF Belgesi: Filigran eklemeyi test etmek için kullanabileceğiniz bir PDF dosyasını hazır bulundurun.
## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını projenize aktarmanız gerekir. Bu adım, Groupdocs sınıflarına ve yöntemlerine erişmenize izin verdiği için çok önemlidir.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Adım 1: Projeyi Kurma
### Yeni Bir Proje Oluştur
Öncelikle Visual Studio'yu açın ve yeni bir C# projesi oluşturun. Basitlik açısından bir Konsol Uygulaması seçebilirsiniz.
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### Groupdocs.Watermark'ı yükleyin
Ardından Groupdocs.Watermark kitaplığını NuGet Paket Yöneticisi aracılığıyla yükleyin.
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
"Groupdocs.Watermark"ı arayın ve yükleyin.
## Adım 2: PDF Belgenizi Yükleyin
### Belge Yollarını Tanımlayın
PDF belgenizin yolunu ve filigranlı PDF'nin kaydedileceği çıktı dizinini belirtin.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### PDF Belgesini Yükle
 Kullan`PdfLoadOptions` PDF belgenizi yüklemek için sınıf.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigran ekleme kodunuz buraya gelecek
}
```
## 3. Adım: Tek Sayfalara Metin Filigranı Ekleme
### Metin Filigranı Oluşturma
 Oluşturmak`TextWatermark` istediğiniz metin ve yazı tipi ayarlarıyla nesneyi seçin.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### Metin Filigran Seçeneklerini Uygula
 Kullanmak`PdfArtifactWatermarkOptions` filigranın nasıl uygulanması gerektiğini belirtmek için.
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## 4. Adım: İlk Sayfaya Resim Filigranı Ekleme
Filigran olarak kullanılacak bir resim yükleyin. Görüntü yolunun doğru olduğundan emin olun.
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## Adım 5: Filigranlı PDF'yi kaydedin
Son olarak filigranlı PDF'nizi belirtilen çıktı dizinine kaydedin.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
Groupdocs için Watermark'ı kullanarak PDF'lerinize filigran eklemek basit bir işlemdir. Bu adımları izleyerek PDF belgelerinizdeki belirli sayfalara etkili bir şekilde metin ve resim filigranları ekleyebilirsiniz. Bu yalnızca belgelerinizi korumanıza yardımcı olmakla kalmaz, aynı zamanda profesyonel bir görünümün korunmasına da yardımcı olur. Deneyin ve filigranlarınızı benzersiz ve etkili kılmak için mevcut çeşitli özelleştirme seçeneklerini keşfedin.
## SSS'ler
### .NET için Groupdocs.Watermark nedir?
Groupdocs.Watermark for .NET, PDF, Word, Excel ve daha fazlasını içeren çeşitli belge formatlarında filigran eklemenizi, aramanızı ve kaldırmanızı sağlayan bir kitaplıktır.
### Filigran görünümünü özelleştirebilir miyim?
Evet, metin filigranlarının metin yazı tipini, boyutunu, rengini ve konumunu özelleştirebilir ve görüntü filigranlarının boyutunu, opaklığını ve konumunu ayarlayabilirsiniz.
### Yalnızca belirli sayfalara filigran eklemek mümkün mü?
Kesinlikle. Groupdocs.Watermark for .NET, belirli sayfalara, tek veya çift sayfalara veya bir dizi sayfaya filigran ekleme seçenekleri sunar.
### Groupdocs.Watermark'ın ücretsiz deneme sürümünü nasıl edinebilirim?
 Ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Grupdocs web sitesi](https://releases.groupdocs.com/).
### Daha ayrıntılı belgeleri nerede bulabilirim?
 Daha detaylı bilgi için şu adrese başvurabilirsiniz:[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/).