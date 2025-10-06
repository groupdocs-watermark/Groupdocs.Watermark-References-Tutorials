---
title: Parola Korumalı Belgeyi Yükle
linktitle: Parola Korumalı Belgeyi Yükle
second_title: GroupDocs.Watermark .NET API'si
description: Adım adım kılavuzumuzla Groupdocs for .NET'i kullanarak parola korumalı belgelere nasıl filigran ekleyeceğinizi öğrenin. Dosyalarınızı kolayca güvence altına alın ve markalayın.
weight: 13
url: /tr/net/document-loadings/load-password-protected-document/
type: docs
---
# Parola Korumalı Belgeyi Yükle

## giriiş
Parola korumalı olsalar bile belgelerinizi filigran ekleyerek korumak mı istiyorsunuz? Groupdocs.Watermark for .NET, tam da bunu yapmanıza olanak tanıyan güçlü bir araçtır. Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak parola korumalı bir belge yükleme ve bu belgeye filigran ekleme sürecinde size rehberlik edeceğiz. Hadi dalalım!
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Visual Studio: Makinenizde yüklü olan herhangi bir Visual Studio sürümü.
2. .NET Framework: .NET Framework 4.6.1 veya sonraki bir sürüme sahip olduğunuzdan emin olun.
3. Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[İndirme: {link](https://releases.groupdocs.com/Watermark/net/).
## Ad Alanlarını İçe Aktar
Öncelikle gerekli namespace’leri projemize import etmemiz gerekiyor. Bu, Groupdocs.Watermark for .NET tarafından sağlanan tüm yöntem ve özelliklere erişebilmemizi sağlar.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Şimdi süreci basit, takip edilmesi kolay adımlara ayıralım.
## 1. Adım: Projenizi Kurun
Başlamak için Visual Studio'da yeni bir C# Konsol Uygulaması oluşturun. Projeniz ayarlandıktan sonra NuGet Paket Yöneticisi aracılığıyla Groupdocs.Watermark for .NET kitaplığını yükleyin.
1. Visual Studio'yu açın ve yeni bir Konsol Uygulaması (.NET Framework) oluşturun.
2.  Git`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Aramak`GroupDocs.Watermark` ve paketi yükleyin.
## 2. Adım: Belge Yollarını Tanımlayın
Daha sonra, parola korumalı belgenizin yolunu ve filigranlı belgenin kaydedileceği çıktı dosyası yolunu tanımlamanız gerekir.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` Ve`"Your Document Directory"` makinenizdeki gerçek yollarla.
## Adım 3: Yükleme Seçeneklerini Şifreyle Ayarlayın
Parola korumalı bir belgeyi açmak için yükleme seçeneklerinde parolayı girmeniz gerekir.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Yer değiştirmek`"P@$w0rd"` belgenizin gerçek şifresiyle.
## Adım 4: Belgeyi Yükleyin
 Şimdi belgeyi kullanarak yükleyelim.`Watermarker` sınıf.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigran ekleme kodunuz buraya gelecek
}
```
## Adım 5: Filigran Oluşturun
Belgeye ekleyebileceğimiz bir metin filigranı oluşturacağız. Metni, yazı tipini, boyutu ve diğer özellikleri gerektiği gibi özelleştirebilirsiniz.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Değiştirmekten çekinmeyin`"Test watermark"`, `"Arial"` , Ve`12` tercih ettiğiniz metne, yazı tipine ve boyuta göre.
## Adım 6: Filigranı Ekleyin
 kullanarak filigranı belgeye ekleyin.`Add` yöntemi`Watermarker` sınıf.
```csharp
watermarker.Add(watermark);
```
## Adım 7: Filigranlı Belgeyi Kaydedin
Son olarak filigranlı belgeyi belirtilen çıktı dosyası yoluna kaydedin.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
Parola korumalı belgelerinize filigran eklemek, Groupdocs for .NET ile basit bir işlemdir. Bu basit adımları takip ederek belgelerinizin ihtiyaçlarınıza göre korunmasını ve markalanmasını sağlayabilirsiniz. İster güvenlik, ister marka bilinci oluşturma veya uyumluluk olsun, belgelerinize filigran eklemek hiç bu kadar kolay olmamıştı.
## SSS'ler
### Groupdocs.Watermark for .NET'i kullanarak görüntü filigranları ekleyebilir miyim?
 Evet, hem metin hem de resim filigranları ekleyebilirsiniz. Basitçe kullanın`ImageWatermark` bunun yerine sınıf`TextWatermark`.
### Filigranı bir belgeden kaldırmak mümkün mü?
Evet, Groupdocs.Watermark for .NET, filigranları aramak ve kaldırmak için yöntemler sağlar.
### Groupdocs.Watermark for .NET, PDF'lerin yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli formatları destekler.
### Filigranın görünümünü özelleştirebilir miyim?
Kesinlikle! Yazı tipini, boyutunu, rengini, opaklığını ve daha fazlasını özelleştirebilirsiniz.
### Sorunlarla karşılaşırsam nereden destek alabilirim?
 Ziyaret edebilirsiniz[Groupdocs Destek Forumu](https://forum.groupdocs.com/c/watermark/19) yardım ve rehberlik için.