---
title: Belgeyi Belirtilen Konuma Kaydet
linktitle: Belgeyi Belirtilen Konuma Kaydet
second_title: GroupDocs.Watermark .NET API'si
description: Bu adım adım kılavuzla GroupDocs.Watermark for .NET'i kullanarak belgelerinize nasıl kolayca filigran ekleyeceğinizi öğrenin. Belge güvenliğini geliştirin.
type: docs
weight: 11
url: /tr/net/document-savings/save-document-specified-location/
---
## giriiş
Dijital çağda belgelerin güvenliği her zamankinden daha önemli hale geldi. Filigranlama, belgelerinizi yetkisiz kullanıma karşı korumanın etkili bir yoludur. GroupDocs.Watermark for .NET, belgelerinize filigran eklemek için güçlü bir çözüm sunar. İster uygulamanıza filigran eklemeyi entegre etmek isteyen bir geliştirici olun, ister belgelerinizi korumakla ilgilenen biri olun, bu eğitim size süreç boyunca adım adım rehberlik edecektir.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
- .NET Geliştirme Ortamı: Visual Studio'nun veya başka herhangi bir .NET geliştirme ortamının kurulu olduğundan emin olun.
-  GroupDocs.Watermark for .NET Kitaplığı: Projenizdeki kitaplığı indirin ve referans verin.[.NET için GroupDocs.Watermark'ı indirin](https://releases.groupdocs.com/Watermark/net/)
- Temel C# Programlama Bilgisi: Temel C# programlama kavramlarını anlamak faydalı olacaktır.
- Belgeden Filigrana: Filigranı uygulamak istediğiniz örnek belgeyi hazır bulundurun.
## Ad Alanlarını İçe Aktar
Örneğe başlamadan önce gerekli ad alanlarını içe aktarmanız gerekir. Kod dosyanızın en üstüne aşağıdaki kullanma ifadelerini ekleyin:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
GroupDocs.Watermark for .NET kullanarak bir belgeye filigran ekleme sürecini yönetilebilir adımlara ayıralım. Başarılı bir şekilde filigran uygulamak ve belgenizi belirtilen konuma kaydetmek için bu adımları izleyin.
## 1. Adım: Projenizi Kurun
Visual Studio'da yeni bir .NET projesi oluşturarak başlayın. Kolaylık sağlamak için bir Konsol Uygulaması seçebilirsiniz.
1. Visual Studio'yu açın.
2.  Seçme`File` >`New` >`Project`.
3.  Seçmek`Console App (.NET Core)` veya`Console App (.NET Framework)`.
4.  Projenize bir ad verin ve tıklayın`Create`.

## Adım 2: Belgenizi ve Filigran Metninizi Hazırlayın
### Belge Yolunu Belirtin
Filigran eklemek istediğiniz belgenin yolunu tanımlayın. Bu örnek için bir yer tutucu yolu kullanalım.
```csharp
string documentPath = "Your Document Path";
```
### Çıkış Yolunu Tanımlayın
Filigranlı belgenin kaydedilmesini istediğiniz çıkış yolunu ayarlayın.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 3. Adım: Belgeyi Yükleyin
 Kullan`Watermarker` belgenizi yüklemek için sınıf. Bu sınıf filigran ekleme, kaldırma ve düzenleme yöntemlerini sağlar.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Filigranlama mantığını buraya ekleyin
}
```
## 4. Adım: Filigran Oluşturun ve Ekleyin

### Metin Filigranı Oluştur
 Bir örnek oluştur`TextWatermark` istediğiniz metin ve yazı tipi özelliklerine sahip nesne.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Belgeye Filigran Ekle
 Oluşturulan filigranı kullanarak belgenize ekleyin.`Add` yöntemi`Watermarker` sınıf.
```csharp
watermarker.Add(watermark);
```
## Adım 5: Belgeyi Kaydedin
Son olarak, filigranı içeren belgeyi belirtilen konuma kaydedin.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
GroupDocs'u kullanarak belgelerinizi filigranlamak, belge güvenliğinizi önemli ölçüde artırabilecek basit bir işlemdir. Bu adım adım kılavuzu takip ederek belgelerinize kolayca filigran ekleyebilir ve bunları istediğiniz konuma kaydedebilirsiniz. İster fikri mülkiyeti koruyor olun, ister belgenin orijinalliğini sağlayın, ister sadece profesyonel bir dokunuş ekleyin, GroupDocs.Watermark for .NET ihtiyacınız olan araçları sağlar.
## SSS'ler
### GroupDocs.Watermark for .NET ile görüntüleri filigran olarak kullanabilir miyim?
Evet, GroupDocs Watermark for .NET ile hem metin hem de resim filigranlarını kullanabilirsiniz. Kitaplık, ihtiyaçlarınıza uygun çeşitli filigran türlerini destekler.
### GroupDocs.Watermark for .NET'in ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[İnternet sitesi](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET lisansını nasıl satın alabilirim?
 adresinden lisans satın alabilirsiniz.[satın alma sayfası](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark for .NET toplu filigranlamayı destekliyor mu?
Evet, bir belge listesini yineleyerek ve filigran uygulayarak toplu işlemde birden fazla belgeye filigran uygulayabilirsiniz.
### .NET için GroupDocs.Watermark desteğini nereden alabilirim?
 Destek şu adreste mevcuttur:[GroupDocs forumu](https://forum.groupdocs.com/c/watermark/19).