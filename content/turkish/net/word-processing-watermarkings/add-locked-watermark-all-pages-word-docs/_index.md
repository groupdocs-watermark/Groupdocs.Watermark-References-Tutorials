---
title: Word Dokümanlarındaki Tüm Sayfalara Kilitli Filigran Ekleme
linktitle: Word Dokümanlarındaki Tüm Sayfalara Kilitli Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak kilitli filigranlar ekleyerek belgelerinizi güvence altına alın. Kolay uygulama için adım adım kılavuzumuzu izleyin.
weight: 11
url: /tr/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

# Word Dokümanlarındaki Tüm Sayfalara Kilitli Filigran Ekleme

## giriiş
Belgelerinize filigran eklemek, içeriğinizi güvence altına almak ve markalamak için hayati bir adımdır. İster yetkisiz kullanımı engelliyor ister yalnızca profesyonel bir dokunuş ekliyor olun, filigranlar birçok amaca hizmet edebilir. Bu öğreticide, Groupdocs.Watermark for .NET'i kullanarak bir Word belgesinin tüm sayfalarına kilitli filigran ekleme sürecinde size yol göstereceğiz.
## Önkoşullar
Adım adım kılavuza dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
1. .NET için Groupdocs.Watermark: En son sürümü şu adresten indirin:[Burada](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Makinenizde .NET Framework'ün kurulu olduğundan emin olun.
3. Geliştirme Ortamı: Visual Studio gibi bir geliştirme ortamı.
4.  Lisans: Birini tercih edebilirsiniz.[ücretsiz deneme](https://releases.groupdocs.com/) veya bir satın alın[geçici lisans](https://purchase.groupdocs.com/temporary-license/).
## Ad Alanlarını İçe Aktar
Öncelikle projenize gerekli ad alanlarını içe aktarmanız gerekir. Bunlar Groupdocs.Watermark tarafından sağlanan sınıflara ve yöntemlere erişim için gereklidir.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Projenizi Kurun

Geliştirme ortamınızı açın ve yeni bir .NET projesi oluşturun. Bu bir konsol uygulaması veya ihtiyaçlarınıza uygun başka herhangi bir tür olabilir.

Groupdocs.Watermark paketini projenize eklemeniz gerekmektedir. Bu NuGet Paket Yöneticisi aracılığıyla yapılabilir. NuGet Paket Yöneticisi Konsolunda aşağıdaki komutu çalıştırın:
```sh
Install-Package GroupDocs.Watermark
```
## Adım 2: Word Belgesini Yükleyin
### Belge Yolunu Tanımlayın
Word belgenizin yolunu belirtin. Bu, filigranı eklemek istediğiniz belge olacaktır.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Yükleme Seçeneklerini Ayarla
 Bir örneğini oluşturun`WordProcessingLoadOptions` Word belgenizi belirli seçeneklerle yüklemek için.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 3. Adım: Filigranı Oluşturun
### Filigranı Başlat
 Kullanmak`Watermarker`sınıf, belgeyi belirtilen yükleme seçenekleriyle yükleyin.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Daha sonraki adımlar bu bloğun içinde olacak
}
```
### Filigran Özelliklerini Tanımlayın
 Oluşturmak`TextWatermark` örneğin istediğiniz metin, yazı tipi ve renk ile.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 4. Adım: Tüm Sayfalara Filigran Uygulayın
### Filigran Seçeneklerini Ayarlayın
 Tanımlamak`WordProcessingWatermarkPagesOptions` ve ayarlayın`IsLocked` Filigranı kilitlemek için özelliği true olarak ayarlayın. Bu, filigranın kolayca kaldırılamamasını sağlar.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### İsteğe bağlı: Parola Koruması Ekleyin
Ekstra bir güvenlik katmanı eklemek istiyorsanız filigran için bir şifre belirleyebilirsiniz.
```csharp
// Şifre ile korumak için
// options.Password = "7654321";
```
### Filigranı Ekle
 Kullan`Add` yöntemi`Watermarker` Filigranı belirtilen seçeneklerle belgeye eklemek için sınıf.
```csharp
watermarker.Add(watermark, options);
```
## Adım 5: Belgeyi Kaydedin
Son olarak, değiştirilen belgeyi belirtilen çıktı dosyasına kaydedin.
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Bu adımları izleyerek, Groupdocs.Watermark for .NET'i kullanarak Word belgelerinizin tüm sayfalarına kolayca kilitli filigran ekleyebilirsiniz. Bu yalnızca belgelerinizi yetkisiz kullanıma karşı korumaya yardımcı olmakla kalmaz, aynı zamanda içeriğinize profesyonel bir dokunuş da katar. Groupdocs.Watermark, filigranlama ihtiyaçları için kapsamlı bir çözüm sunarak belgelerinizin güvende ve markalı kalmasını sağlar.
## SSS'ler
### Bir resmi metin yerine filigran olarak kullanabilir miyim?
 Evet, Groupdocs Filigran hem metin hem de resim filigranlarını destekler. Değiştirebilirsin`TextWatermark` ile`ImageWatermark` ve resminizi belirtin.
### Filigranın konumunu özelleştirmek mümkün mü?
 Kesinlikle! Filigranın konumunu aşağıdaki gibi özellikleri kullanarak ayarlayabilirsiniz:`HorizontalAlignment` Ve`VerticalAlignment`.
### Belgenin farklı sayfalarına farklı filigranlar uygulayabilir miyim?
 Evet, filigranları belirli sayfalar için özelleştirebilirsiniz.`PageIndex` içindeki mülk`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark, Word'ün yanı sıra diğer belge formatlarını da destekliyor mu?
Evet, Groupdocs Filigran; PDF, Excel, PowerPoint ve daha fazlasını içeren çeşitli formatları destekler.
### Groupdocs.Watermark'ı kullanmak için sistem gereksinimleri nelerdir?
.NET Framework yüklü bir sisteme ve Visual Studio gibi bir geliştirme ortamına ihtiyacınız var.