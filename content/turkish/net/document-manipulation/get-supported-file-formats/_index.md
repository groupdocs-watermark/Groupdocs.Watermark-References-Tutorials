---
title: Desteklenen Dosya Formatlarını Alın
linktitle: Desteklenen Dosya Formatlarını Alın
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak belgelerinize zahmetsizce filigran ekleyin. Dijital varlıklarınızı korumak için kapsamlı, adım adım kılavuzumuzu izleyin.
weight: 13
url: /tr/net/document-manipulation/get-supported-file-formats/
---
## giriiş
Belgelerinize filigran eklemek, dijital varlıklarınızı korumada çok önemli bir adımdır. Fikri mülkiyetin korunması, gizliliğin sağlanması veya sadece markalama için filigranlar hayati bir rol oynamaktadır. Filigran özelliklerini uygulamalarınıza entegre etmek isteyen bir .NET geliştiricisiyseniz, GroupDocs.Watermark for .NET, göz önünde bulundurmanız gereken güçlü ve çok yönlü bir araçtır. Bu eğitim, kurulumdan ilk filigranınızı uygulamaya kadar GroupDocs.Watermark'ı kullanmanın temelleri konusunda size rehberlik edecek ve kolayca takip edebilmenizi sağlamak için her adımı ayrıntılı olarak anlatacaktır.
## Önkoşullar
Ayrıntılara dalmadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
1.  Visual Studio: Makinenizde Visual Studio'nun kurulu olduğundan emin olun. adresinden indirebilirsiniz.[Visual Studio web sitesi](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark, .NET Framework'ün çeşitli sürümlerini destekler. Projenizin uyumlu bir sürümü hedeflediğinden emin olun.
3. GroupDocs.Watermark for .NET: En son sürümü şuradan indirebilirsiniz:[yayın sayfası](https://releases.groupdocs.com/Watermark/net/).
4. Temel C# Bilgisi: Bu eğitimde, C# ve .NET geliştirme konusunda temel bir anlayışa sahip olduğunuz varsayılmaktadır.
## Ad Alanlarını İçe Aktar
Öncelikle projenize gerekli ad alanlarını aktaralım. C# dosyanızı açın ve en üste aşağıdaki kullanarak yönergeleri ekleyin:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Bu ad alanlarının içe aktarılmasıyla belgelerinize filigran eklemeye hazırsınız.

## Adım 1: Filigran Motorunu Başlatın
 İlk adım filigran motorunu başlatmaktır. Bu, bir örneğinin oluşturulmasını içerir.`Watermarker` filigran eklemek istediğiniz belgenin bulunduğu sınıf.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Bu kod parçacığı,`Watermarker` belgenize filigran uygulamak için kullanacağınız nesne.
## 2. Adım: Metin Filigranı Ekleme
Şimdi belgenize basit bir metin filigranı ekleyelim. Metin filigranları "Gizli" veya "Taslak" gibi etiketler eklemek için idealdir.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Burada bir oluşturduk`TextWatermark`"Gizli" metnini içeren nesneyi seçin, yazı tipini ve rengini ayarlayın ve onu belgenin ortasına hizalayın.
## 3. Adım: Resim Filigranı Ekleme
Bir görüntüyü filigran olarak kullanmayı tercih ederseniz GroupDocs.Watermark bunu yapmanızı kolaylaştırır.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 Bu örnekte, bir oluşturuyoruz`ImageWatermark` nesneyi seçin, boyutlarını ayarlayın ve onu belgenin sağ üst köşesine hizalayın.
## Adım 4: Belgeyi Kaydedin
İstenilen filigranları ekledikten sonra son adım, değiştirilen belgeyi kaydetmektir.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Bu, filigranlı belgeyi belirtilen yola kaydedecek ve kullandığı tüm kaynakları serbest bırakacaktır.`Watermarker` misal.
## 5. Adım: Desteklenen Dosya Formatlarını Alın
GroupDocs.Watermark'ın hangi dosya formatlarını desteklediğini görmek için aşağıdaki kod parçacığını kullanabilirsiniz:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Bu, GroupDocs.Watermark'ın işleyebileceği tüm dosya türlerini yazdıracak ve size onun yeteneklerinin kapsamlı bir görünümünü sunacaktır.
## Çözüm
GroupDocs ile belgelerinizi filigranlamak basit ve etkilidir. Bu öğreticiyi takip ederek filigran motorunu nasıl başlatacağınızı, metin ve görüntü filigranlarını nasıl ekleyeceğinizi, filigranlı belgelerinizi nasıl kaydedeceğinizi ve desteklenen dosya formatlarını nasıl listeleyeceğinizi öğrendiniz. Bu araçlarla belgelerinizi güvenle koruyabilirsiniz.
 Herhangi bir sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, şu adresi ziyaret etmekten çekinmeyin:[GroupDocs.Watermark destek forumu](https://forum.groupdocs.com/c/watermark/19).
## SSS'ler
### .NET için GroupDocs.Watermark'ı nasıl yüklerim?
 adresinden indirebilirsiniz.[yayın sayfası](https://releases.groupdocs.com/Watermark/net/) ve DLL'yi projenize ekleyin.
### GroupDocs.Watermark'ı ücretsiz deneyebilir miyim?
 Evet, talep edebilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) Satın almadan önce yazılımı değerlendirmek için.
### GroupDocs.Watermark hangi dosya formatlarını destekler?
Desteklenen tüm dosya formatlarını listelemek için sağlanan kod pasajını kullanabilirsiniz.
### GroupDocs.Watermark lisansını nasıl satın alabilirim?
 Lisanslar doğrudan adresinden satın alınabilir.[satın alma sayfası](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark için herhangi bir belge mevcut mu?
 Evet, kapsamlı belgeler mevcut[Burada](https://tutorials.groupdocs.com/Watermark/net/).