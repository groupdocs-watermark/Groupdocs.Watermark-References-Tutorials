---
title: Yerel Diskten Belge Bilgilerini Al
linktitle: Yerel Diskten Belge Bilgilerini Al
second_title: GroupDocs.Watermark .NET API'si
description: Bu kapsamlı adım adım kılavuzla, GroupDocs for .NET'i kullanarak filigranları nasıl ekleyeceğinizi, kaldıracağınızı ve çıkaracağınızı öğrenin.
type: docs
weight: 11
url: /tr/net/document-manipulation/get-document-info-local-disk/
---
## giriiş
.NET için GroupDocs.Watermark'ın kullanımına ilişkin nihai kılavuza hoş geldiniz! İster deneyimli bir geliştirici olun, ister yeni başlıyor olun, bu makale, bu güçlü araçla belgelerinize filigran eklemenin temelleri konusunda size yol gösterecektir. Sonunda, belgelerinize filigran yerleştirme konusunda uzmanlaşacak, onların korunmasını ve sizin spesifikasyonlarınıza göre markalanmasını sağlayacaksınız.
## Önkoşullar
Adım adım kılavuza dalmadan önce yerine getirmeniz gereken birkaç önkoşul vardır:
1.  .NET Framework: Sisteminizde .NET Framework'ün kurulu olduğundan emin olun. GroupDocs.Watermark for .NET, .NET Framework'ün çeşitli sürümleriyle uyumludur;[dokümantasyon](https://reference.groupdocs.com/Watermark/net/) uyumluluk ayrıntıları için.
2.  GroupDocs.Watermark for .NET Kitaplığı: En son sürümü şuradan indirin ve yükleyin:[indirme sayfası](https://releases.groupdocs.com/Watermark/net/).
3. Geliştirme Ortamı: Bir geliştirme ortamı kurmuş olmalısınız. Visual Studio, .NET geliştirme için popüler bir seçimdir.
4. Temel C# Bilgisi: C# programlamanın temellerini anlamak, örnekleri takip etmenize yardımcı olacaktır.
## Ad Alanlarını İçe Aktar
GroupDocs.Watermark for .NET'i kullanabilmeniz için gerekli ad alanlarını projenize aktarmanız gerekir. Bu basit bir işlemdir ve kitaplığın özelliklerine erişim için gereklidir.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Bir belgeye filigran ekleme sürecini anlaşılır, yönetilebilir adımlara ayıralım. Her adım, işlevselliği kolaylıkla anlamanıza ve uygulamanıza yardımcı olmak için tasarlanmıştır.
## 1. Adım: Belgenizi Yükleyin
 İlk adım, filigran eklemek istediğiniz belgeyi yüklemektir. Bu, kullanılarak yapılır.`Watermarker` belgenize erişmenizi ve değiştirmenizi sağlayan sınıf.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Belge artık yüklendi ve filigran eklemeye hazır
}
```
 Bu adımda değiştirin`"Your Document Path"` belgenizin gerçek yolu ile. Bu,`Watermarker`çeşitli filigranlama işlevlerine erişmenizi sağlar.
## 2. Adım: Belge Bilgilerini Alın
Filigran eklemeden önce belge hakkında bazı bilgiler toplamak isteyebilirsiniz. Bu, filigranınızı belge özelliklerine göre özelleştirmek için yararlı olabilir.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Bu adımda,`GetDocumentInfo` yöntem, dosya türü, sayfa sayısı ve belge boyutu gibi ayrıntıları alır. Bu bilgiler konsola yazdırılır ancak gerektiğinde uygulamanızda kullanabilirsiniz.
## 3. Adım: Metin Filigranı Ekleme
Artık belgenizi yüklediğinize ve bilgileri elinizin altında olduğuna göre filigran ekleme zamanı geldi. Basit bir metin filigranı ile başlayacağız.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Burada bir`TextWatermark` istediğiniz metin, yazı tipi ve stil ile nesneyi oluşturun. Renk, opaklık ve döndürme açısı gibi özellikleri ihtiyaçlarınıza uyacak şekilde ayarlayın. Son olarak filigran belgeye eklenir ve belirtilen yola kaydedilir.
## 4. Adım: Resim Filigranı Ekleme
Metin filigranları harikadır, peki ya bir logo veya başka bir resim eklemek isterseniz? Bu adım, görüntü filigranının nasıl ekleneceğini kapsar.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Yer değiştirmek`"Path to Your Image"` filigran görüntünüzün yolu ile birlikte. Görüntü filigranınızın görünümünü özelleştirmek için opaklık ve döndürme açısı gibi özellikleri ayarlayın. Filigranı ekleme ve kaydetme işlemi, metin filigranına benzer.
## Adım 5: Mevcut Filigranları Kaldır
 Bazen bir belgedeki mevcut filigranları kaldırmanız gerekebilir. Bu, kullanılarak yapılabilir.`Remove` tarafından sağlanan yöntem`Watermarker` sınıf.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Burada,`Remove` Belgedeki metin filigranlarını kaldırmak için kullanılan yöntem. İhtiyaçlarınıza bağlı olarak resim veya metin gibi kaldırılacak farklı filigran türleri belirleyebilirsiniz. Değişiklikleri görmek için belgeyi yeni bir yola kaydedin.
## Adım 6: Filigranları Çıkarın
Bir belgeden filigran çıkarmanız ve incelemeniz gerekiyorsa, GroupDocs.Watermark for .NET bunu kolaylıkla mümkün kılar.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Her filigran için ek özellikler ve mantık
    }
}
```
 Bu adım,`GetWatermarks`Bir belgedeki tüm filigranları alma yöntemi. Daha sonra filigran listesini yineleyebilir ve özelliklerini inceleyebilir veya gerektiğinde ek eylemler gerçekleştirebilirsiniz.
## Çözüm
 Tebrikler! Artık belgelerinize filigran eklemek, kaldırmak ve filigranları çıkarmak için GroupDocs.Watermark for .NET'i nasıl kullanacağınızı öğrendiniz. Bu becerilerle belgelerinizi etkili bir şekilde koruyabilir ve markalayabilirsiniz. Unutmayın,[dokümantasyon](https://reference.groupdocs.com/Watermark/net/) Daha ayrıntılı bilgiye veya gelişmiş işlevselliğe ihtiyacınız varsa her zaman yanınızda.
## SSS'ler
### GroupDocs.Watermark for .NET'i herhangi bir .NET sürümüyle kullanabilir miyim?
 Evet, GroupDocs.Watermark for .NET, çeşitli .NET Framework sürümleriyle uyumludur. Kontrol edin[dokümantasyon](https://reference.groupdocs.com/Watermark/net/) ayrıntılar için.
### .NET için GroupDocs.Watermark'ı nereden indirebilirim?
 En son sürümü adresinden indirebilirsiniz.[indirme sayfası](https://releases.groupdocs.com/Watermark/net/).
### Geçici lisansı nasıl alabilirim?
 Geçici lisansı adresinden alabilirsiniz.[geçici lisans sayfası](https://purchase.groupdocs.com/temporary-license/).
### Ücretsiz deneme mevcut mu?
 Evet, adresini ziyaret ederek ücretsiz denemeyi başlatabilirsiniz.[ücretsiz deneme sayfası](https://releases.groupdocs.com/).
### Sorunlarla karşılaşırsam nereden destek alabilirim?
 Destek şu adreste mevcuttur:[GroupDocs Filigran forumu](https://forum.groupdocs.com/c/watermark/19).