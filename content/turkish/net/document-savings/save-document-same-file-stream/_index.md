---
title: Belgeyi Aynı Dosyaya veya Akışa Kaydetme
linktitle: Belgeyi Aynı Dosyaya veya Akışa Kaydetme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak belgelere nasıl filigran ekleyeceğinizi öğrenin. Bu kılavuz, belgenin korunmasını ve bütünlüğünü sağlamaya yönelik talimatlar sağlar.
type: docs
weight: 10
url: /tr/net/document-savings/save-document-same-file-stream/
---
## giriiş
Günümüzün dijital çağında, fikri mülkiyetin korunması ve marka bütünlüğünün sağlanması açısından belgelere filigran eklenmesi zorunlu hale geldi. Groupdocs.Watermark for .NET, filigranları belgelere sorunsuz bir şekilde gömmek isteyen geliştiriciler için güçlü bir çözüm sunar. Bu kapsamlı kılavuz, Groupdocs.Watermark for .NET'i kullanarak filigran içeren bir belgeyi aynı dosyaya veya akışa kaydetme adımlarında size yol gösterecektir.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Geliştirme Ortamı: Makinenizde Visual Studio kuruludur.
2. .NET Framework: .NET Framework 4.0 veya sonraki bir sürüme sahip olduğunuzdan emin olun.
3.  Groupdocs.Watermark for .NET: En son sürümü şuradan indirin ve yükleyin:[alan](https://releases.groupdocs.com/Watermark/net/).
4.  Lisans: Geçici veya kalıcı bir lisans alın.[Burada](https://purchase.groupdocs.com/temporary-license/).
## Ad Alanlarını İçe Aktar
.NET projenizde Groupdocs.Watermark'ı kullanmaya başlamak için gerekli ad alanlarını içe aktarmanız gerekir:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 1. Adım: Projenizi Kurun
Belgelerimize filigran eklemeden önce .NET projemizi kurmamız gerekiyor. İşte nasıl:
1. Yeni Bir Proje Oluşturun: Visual Studio'yu açın ve yeni bir Konsol Uygulaması oluşturun.
2. Groupdocs.Watermark Referansını Ekle: Solution Explorer'da projeye sağ tıklayın, "NuGet Paketlerini Yönet"i seçin ve Groupdocs.Watermark paketini yükleyin.
## Adım 2: Belgeyi Yeni Bir Konuma Kopyalayın
Orijinal belgeyi doğrudan değiştirmekten kaçınmak için önce onu yeni bir konuma kopyalamak iyi bir uygulamadır. İşte bunu nasıl yapacağınız:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## 3. Adım: Filigranı Başlatın
Artık belgemizi kopyaladığımıza göre, filigranımızı eklemek için Watermarker sınıfını başlatabiliriz:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Filigranlama buraya gelecek
}
```
## 4. Adım: Metin Filigranı Oluşturun ve Ekleyin
Daha sonra bir metin filigranı oluşturup bunu belgemize ekliyoruz:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Adım 5: Belgeyi Kaydedin
Son olarak, filigranın uygulandığı belgeyi kaydedin:
```csharp
watermarker.Save();
```
## Çözüm
Groupdocs'u kullanarak belgelerinize filigran eklemek basit ve etkilidir. Yukarıda özetlenen adımları takip ederek belgelerinizi koruyabilir ve bütünlüklerini zahmetsizce koruyabilirsiniz. Daha fazla ayrıntı için şuraya başvurabilirsiniz:[dokümantasyon](https://reference.groupdocs.com/Watermark/net/).
## SSS'ler
### Bir resmi metin yerine filigran olarak kullanabilir miyim?
Evet, Groupdocs.Watermark görselleri, şekilleri ve metni filigran olarak kullanmanıza olanak tanır.
### Bir belgeden filigranı nasıl kaldırabilirim?
 Belgedeki filigran koleksiyonuna erişerek ve filigranı kullanarak filigranı kaldırabilirsiniz.`Remove` yöntem.
### Filigranın görünümünü özelleştirmek mümkün mü?
Kesinlikle. Filigranın yazı tipini, boyutunu, rengini ve konumunu özelleştirebilirsiniz.
### Tek bir belgeye birden fazla filigran uygulayabilir miyim?
 Evet, çağrı yaparak birden fazla filigran ekleyebilirsiniz.`Add` yöntemi farklı filigran nesneleriyle birden çok kez kullanın.
### Groupdocs.Watermark tüm belge formatlarıyla uyumlu mu?
Groupdocs.Watermark, PDF, DOCX, PPTX ve diğerleri dahil çok çeşitli belge formatlarını destekler.