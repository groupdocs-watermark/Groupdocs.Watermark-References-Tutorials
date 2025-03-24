---
title: Word Dokümanlarındaki Tüm Başlıklara Resim Filigranı Ekleme
linktitle: Word Dokümanlarındaki Tüm Başlıklara Resim Filigranı Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki tüm başlıklara kolayca görüntü filigranları ekleyin. Ayrıntılı kod örneklerinin yer aldığı adım adım kılavuzumuzu takip edin.
weight: 10
url: /tr/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---

# Word Dokümanlarındaki Tüm Başlıklara Resim Filigranı Ekleme

## giriiş
Filigranlar, sahiplik, gizlilik veya markalama gibi bilgilerin belgelere yerleştirilmesi için bir yol sağlayarak belge yönetiminin önemli bir parçası olabilir. Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki tüm üstbilgilere görüntü filigranı ekleme adımlarını açıklayacağız. İster programlamada yeni olun ister deneyimli bir geliştirici olun, bu kılavuz filigranlama hedeflerinize kolaylıkla ulaşmanıza yardımcı olacaktır.
## Önkoşullar
Koda dalmadan önce ihtiyacımız olan her şeye sahip olduğumuzdan emin olalım. Başlamanıza yardımcı olacak bir kontrol listesi:
1.  .NET için GroupDocs.Watermark: En son sürümü şu adresten indirin:[Burada](https://releases.groupdocs.com/Watermark/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
3. .NET Framework: .NET framework'ün kurulu olduğundan emin olun.
4. Örnek Word Belgesi: Filigranı eklemek istediğiniz Word belgesi.
5. Filigran için Resim: Filigran olarak kullanmak istediğiniz bir resim dosyası.
Bunları hazırladıktan sonra projemizi oluşturmaya başlayabiliriz.
## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını içe aktaralım. Bu ad alanları, belgelerimizdeki filigranlarla çalışmamıza yardımcı olacak sınıfları ve yöntemleri içerir.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Projenizi Kurma
Başlamak için Visual Studio'da yeni bir konsol uygulaması oluşturun. Projenizdeki GroupDocs.Watermark DLL dosyasına referanslar ekleyin. Bu, GroupDocs.Watermark NuGet paketi yüklenerek yapılabilir.
```bash
Install-Package GroupDocs.Watermark
```
## 2. Adım: Belgenizi Yükleyin
 Filigran eklemenin ilk adımı, belgeyi filigranın ekleneceği yere yüklemektir. Burada kullanacağımız`WordProcessingLoadOptions` Bir Word belgesini yüklemek için.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigran eklenecek kod buraya gelecek
}
```
## 3. Adım: Görüntü Filigranını Oluşturun
Daha sonra bir resim filigranı oluşturacağız. Bu, filigran olarak kullanmak istediğiniz görüntü dosyasını belirtmeyi içerir.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Filigranı uygulama kodu buraya gelecek
}
```
## Adım 4: İlk Bölüm Başlıklarına Filigran Ekleme
 Filigranı Word belgesinin ilk bölümündeki tüm başlıklara eklememiz gerekiyor. Bunun için kullanıyoruz`WordProcessingWatermarkSectionOptions` ve bölüm dizinini belirtin.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Adım 5: Üstbilgileri ve Altbilgileri Bağlayın
Filigranın tüm bölümlerin başlıklarında görünmesini sağlamak için diğer tüm üstbilgileri ve altbilgileri ilk bölümün üstbilgilerine ve altbilgilerine bağlarız.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Adım 6: Belgeyi Kaydedin
Son olarak filigranlı belgeyi belirtilen yola kaydediyoruz. Bu adım, değişikliklerinizin orijinal belge korunarak yeni bir dosyaya yazılmasını sağlar.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Çözüm
İşte buyur! GroupDocs.Watermark for .NET'i kullanarak Word belgesindeki tüm üstbilgilere başarıyla görüntü filigranı eklediniz. Bu güçlü kitaplık, filigranları yönetmeyi ve çeşitli belge türlerine uygulamayı kolaylaştırarak içeriğinizin korunmasını ve profesyonelce markalanmasını sağlar.
## SSS'ler
### Resimlerin yanı sıra başka filigran türlerini de kullanabilir miyim?
Evet, GroupDocs, metin, resim ve hatta bileşik filigranları destekler.
### Belgenin başlıkların yanı sıra diğer bölümlerine de filigran eklemek mümkün müdür?
Kesinlikle! Altbilgileri, gövdeyi ve hatta belirli sayfaları veya bölümleri filigranlayabilirsiniz.
### GroupDocs.Watermark diğer belge formatlarını destekliyor mu?
Evet, PDF'ler, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli formatları destekler.
### Filigranın konumunu ve görünümünü özelleştirebilir miyim?
Evet, filigranın boyutunu, konumunu, opaklığını ve diğer birçok özelliğini özelleştirebilirsiniz.
### GroupDocs.Watermark'ın ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).