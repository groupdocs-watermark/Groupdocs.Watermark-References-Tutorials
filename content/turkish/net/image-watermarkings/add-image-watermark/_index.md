---
title: Resim Filigranı Ekle
linktitle: Resim Filigranı Ekle
second_title: GroupDocs.Watermark .NET API'si
description: Ayrıntılı, adım adım eğitimimizle GroupDocs.Watermark for .NET'i kullanarak belgelerinize görüntü filigranlarını nasıl ekleyeceğinizi öğrenin.
type: docs
weight: 11
url: /tr/net/image-watermarkings/add-image-watermark/
---
## giriiş
GroupDocs.Watermark for .NET'i kullanarak görüntü filigranları eklemeye ilişkin bu kapsamlı kılavuza hoş geldiniz! Filigranlama, belgelerinizi ve görsellerinizi yetkisiz kullanıma karşı korumanın güçlü bir yoludur ve fikri mülkiyetinizin güvende kalmasını sağlar. Bu eğitimde, ortamınızı ayarlamaktan belgelerinize filigran uygulamaya kadar tüm süreç boyunca size yol göstereceğiz. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuzu yararlı ve takip edilmesi kolay bulacaksınız.
## Önkoşullar
Eğiticiye dalmadan önce, ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
- Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE
- .NET Framework: .NET Framework 4.0 veya üzeri
-  GroupDocs.Watermark for .NET: Buradan indirebilirsiniz.[GroupDocs web sitesi](https://releases.groupdocs.com/Watermark/net/)
-  Resim Dosyası: Filigran olarak kullanılacak bir resim dosyası (örn.`watermark.jpg`)
- Belge Dosyası: Filigranı eklemek istediğiniz belge (örn.`presentation.pptx`)
## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını projenize aktarmanız gerekir. Bu, GroupDocs işlevlerine erişim için gereklidir.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Bu bölümde görüntü filigranı ekleme sürecini anlaşılır, yönetilebilir adımlara ayıracağız. Belgenize başarılı bir şekilde filigran eklemek için her adımı dikkatlice izleyin.
## 1. Adım: Ortamınızı Kurun
 Öncelikle geliştirme ortamınızın doğru şekilde kurulduğundan emin olun. GroupDocs.Watermark kitaplığını şuradan indirerek yükleyin:[GroupDocs web sitesi](https://releases.groupdocs.com/Watermark/net/).
1. Projenizi Visual Studio'da açın.
2. Solution Explorer'da projenize sağ tıklayın.
3. "NuGet Paketlerini Yönet..." seçeneğini seçin
4.  Aramak`GroupDocs.Watermark` ve yükleyin.
## 2. Adım: Dosya Yollarını Tanımlayın
Daha sonra, giriş belgeniz ve çıkış dizininiz için yolları tanımlamanız gerekecektir. Bu, programın çalışması gereken dosyaları bulmasına yardımcı olur.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` Ve`"Your Document Directory"` belgenize giden gerçek yollar ve istenen çıktı dizini ile birlikte.
## 3. Adım: Filigranı Başlatın
Şimdi, başlat`Watermarker` belgenizin yolunu içeren sınıf. Bu sınıf filigranlama sürecinin yönetilmesinden sorumludur.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Bu kullanım bloğundaki sonraki adımlara geçin
}
```
## 4. Adım: Resim Filigranı Oluşturun
 İçinde`Watermarker` bloğun bir örneğini oluşturun`ImageWatermark` filigran görüntünüzün yolunu kullanarak sınıf. Bu sınıf, filigran olarak kullanmak istediğiniz görüntüyü temsil eder.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Bu kullanım bloğundaki bir sonraki adıma geçin
}
```
## Adım 5: Belgeye Filigran Ekleme
 İle`ImageWatermark` örnek hazırsa, bunu kullanarak belgenize ekleyin`Add` yöntemi`Watermarker` sınıf.
```csharp
watermarker.Add(watermark);
```
## Adım 6: Belgeyi Kaydedin
Son olarak filigranlı belgeyi belirtilen çıktı dizinine kaydedin. Bu adım, değişikliklerinizin yeni bir dosyaya yazılmasını sağlar.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
Tebrikler! GroupDocs.Watermark for .NET'i kullanarak belgenize başarıyla bir görüntü filigranı eklediniz. Bu adım adım kılavuzu takip ederek belgelerinizi özel filigranlarla kolayca koruyabilirsiniz. Filigranın dijital varlıklarınızı yetkisiz kullanıma karşı korumada çok önemli bir adım olduğunu unutmayın.

## SSS'ler
### GroupDocs.Watermark hangi dosya formatlarını destekler?
GroupDocs.Watermark, PDF, DOCX, PPTX, XLSX dahil olmak üzere çok çeşitli dosya formatlarını ve JPEG ve PNG gibi görüntü dosyalarını destekler.
### GroupDocs.Watermark'ı .NET Core ile kullanabilir miyim?
Evet, GroupDocs.Watermark hem .NET Framework hem de .NET Core ile uyumludur.
### GroupDocs.Watermark için nasıl geçici lisans alabilirim?
 Geçici lisansı adresinden alabilirsiniz.[GroupDocs web sitesi](https://purchase.groupdocs.com/temporary-license/).
### Tek bir belgeye birden fazla filigran eklemek mümkün mü?
 Kesinlikle! numaralı telefonu arayarak birden fazla filigran ekleyebilirsiniz.`Add` yöntemi farklı filigran örnekleriyle birden çok kez kullanın.
### Daha fazla örnek ve belgeyi nerede bulabilirim?
 Daha fazla örnek ve ayrıntılı belgeler için şu adresi ziyaret edin:[GroupDocs.Watermark belgeleri](https://reference.groupdocs.com/Watermark/net/).