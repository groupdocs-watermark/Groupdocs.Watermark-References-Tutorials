---
title: PDF'ye Sayfa Kenar Boşluğu Türüyle Filigran Ekleme
linktitle: PDF'ye Sayfa Kenar Boşluğu Türüyle Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs için Filigran'ı kullanarak PDF'ye sayfa kenar boşluğu türüyle filigran eklemeyi öğrenin. Belgelerinizi zahmetsizce koruyun.
weight: 21
url: /tr/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---
## giriiş
Günümüzün dijital çağında, belgelerin güvenliğini sağlamak her zamankinden daha önemli. Belgelerinizin bütünlüğünü ve orijinalliğini sağlamanın bir yolu filigran eklemektir. Groupdocs.Watermark for .NET, bu süreci zahmetsiz hale getirmek için tasarlanmış olağanüstü bir araçtır. Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak PDF'ye sayfa kenar boşluğu türüyle filigran ekleme adımlarında size yol göstereceğiz.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
-  Groupdocs.Watermark for .NET: İndirin ve yükleyin.[En son sürüm](https://releases.groupdocs.com/Watermark/net/) .NET için Groupdocs.Watermark'ın.
- Geliştirme Ortamı: Visual Studio gibi bir .NET geliştirme ortamı.
- Temel C# Bilgisi: C# programlama diline aşinalık.
- PDF Belgesi: Filigran eklemek istediğiniz PDF belgesi.
## Ad Alanlarını İçe Aktar
Öncelikle C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu ad alanları, Groupdocs işlevlerine erişim sağlayacaktır.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Şimdi süreci yönetilebilir adımlara ayıralım. PDF belgenize filigran eklemek için her adımı dikkatlice izleyin.
## 1. Adım: Belge Yolunuzu ve Çıktı Dizininizi Ayarlayın
Öncelikle belgenizin yolunu ve filigranlı PDF'nin kaydedileceği çıktı dizinini belirtmeniz gerekir.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Adım 2: PDF Belgenizi Yükleyin
 Daha sonra, PDF belgenizi şunu kullanarak yükleyeceksiniz:`PdfLoadOptions` sınıf. Bu sınıf, PDF'nizi yüklemek için gereken seçenekleri belirtmenize olanak tanır.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 3. Adım: Metin Filigranını Oluşturun
Şimdi filigranı oluşturmanın zamanı geldi. Bu örnekte yazı tipi, boyut ve hizalama gibi belirli özelliklere sahip bir metin filigranı oluşturacağız.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Adım 4: Sayfa Kenar Boşluğu Türünü Ayarlayın
 Filigranınızı uygun şekilde konumlandırmak için sayfa kenar boşluğu türünü ayarlamanız gerekir. Burada sayfa kenar boşluğu tipini şu şekilde ayarlıyoruz:`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## Adım 5: Filigranı Ekleme ve Kaydetme
Son olarak filigranı belgenize ekleyin ve değiştirilen PDF'yi belirtilen çıktı dizinine kaydedin.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## Çözüm
İşte buyur! Bu adımları izleyerek, Groupdocs.Watermark for .NET'i kullanarak PDF belgelerinize belirli bir sayfa kenar boşluğu türüne sahip bir filigranı kolayca ekleyebilirsiniz. Bu yalnızca belgelerinizi korumaya yardımcı olmakla kalmaz, aynı zamanda orijinalliklerini de garanti eder. İster gizli raporlarla, ister yasal belgelerle, ister yaratıcı çalışmalarla ilgileniyor olun, filigranlama, içeriğinizi korumanın basit ama etkili bir yoludur.
## SSS'ler
### .NET için Groupdocs.Watermark nedir?
Groupdocs.Watermark for .NET, program aracılığıyla çeşitli belge biçimlerine filigran eklemek için güçlü bir kitaplıktır. Kapsamlı özelleştirmeye olanak tanıyan görüntüleri, metinleri ve daha fazlasını destekler.
### Bu yöntemi diğer belge türlerine filigran eklemek için kullanabilir miyim?
Evet, Groupdocs.Watermark for .NET, Word, Excel, PowerPoint ve resimler de dahil olmak üzere çok çeşitli belge formatlarını destekler. Süreç benzerdir ancak farklı seçenekler ve sınıflar içerebilir.
### Groupdocs.Watermark for .NET'in ücretsiz deneme sürümünü nasıl edinebilirim?
 Yapabilirsiniz[Ücretsiz deneme sürümünü indirin](https://releases.groupdocs.com/) Kitaplığın özelliklerini ve işlevlerini keşfetmek için Groupdocs web sitesinden.
### Filigranın görünümünü özelleştirmek mümkün mü?
Kesinlikle! Filigranın yazı tipini, boyutunu, rengini, opaklığını, hizalamasını ve diğer özelliklerini ihtiyaçlarınıza uyacak şekilde özelleştirebilirsiniz.
### .NET için Groupdocs.Watermark desteğini nereden alabilirim?
 Destek için şu adresi ziyaret edebilirsiniz:[Groupdocs Filigran destek forumu](https://forum.groupdocs.com/c/watermark/19) topluluktan ve Groupdocs ekibinden soru sorabileceğiniz ve yardım alabileceğiniz yer.