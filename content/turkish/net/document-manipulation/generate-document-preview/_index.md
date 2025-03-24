---
title: Belge Önizlemesi Oluştur
linktitle: Belge Önizlemesi Oluştur
second_title: GroupDocs.Watermark .NET API'si
description: Bu kılavuzla GroupDocs.Watermark for .NET'i kullanarak belge önizlemelerini nasıl oluşturacağınızı öğrenin. Belge güvenliğinizi ve yönetiminizi zahmetsizce geliştirin.
weight: 10
url: /tr/net/document-manipulation/generate-document-preview/
---

# Belge Önizlemesi Oluştur

## giriiş
Dijital belge yönetimi dünyasında filigranlama, belgelerin güvenliğini ve orijinalliğini sağlamada çok önemli bir rol oynar. GroupDocs.Watermark for .NET, geliştiricilerin belgelere zahmetsizce filigran eklemesine olanak tanıyan güçlü bir araçtır. Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak belge önizlemeleri oluşturma sürecinde size yol göstereceğiz. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuz size hedefinize ulaşmanız için kapsamlı, adım adım bir süreç sağlayacaktır.
## Önkoşullar
Uygulamaya geçmeden önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
- C# ve .NET çerçevesine ilişkin temel anlayış.
- Makinenizde Visual Studio yüklü.
- .NET kitaplığı için GroupDocs.Watermark. Yapabilirsiniz[buradan indir](https://releases.groupdocs.com/Watermark/net/).
-  GroupDocs.Watermark için geçerli bir lisans. Ya satın alabilirsiniz[Burada](https://purchase.groupdocs.com/buy) veya bir tane edinin[geçici lisans](https://purchase.groupdocs.com/temporary-license/) değerlendirme amaçlı.
## Ad Alanlarını İçe Aktar
GroupDocs.Watermark'ı projenizde kullanmaya başlamak için gerekli ad alanlarını içe aktarmanız gerekir. Bu, kodunuza aşağıdaki kullanma yönergelerini ekleyerek yapılabilir:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Bu ad alanları, filigran eklemek ve belge önizlemeleri oluşturmak için gereken sınıflara ve yöntemlere erişim sağlayacaktır.

Belge önizlemesi oluşturma sürecini basit, takip edilmesi kolay adımlara ayıralım.
## 1. Adım: Projenizi Kurun
Öncelikle .NET projenizi Visual Studio'da kurun. Henüz bir projeniz yoksa aşağıdaki adımları izleyerek yeni bir proje oluşturun:
1. Visual Studio'yu açın.
2. "Yeni bir proje oluştur"a tıklayın.
3. "Konsol Uygulaması (.NET Core)" seçeneğini seçin ve "İleri"ye tıklayın.
4. Projenize bir ad verin ve kaydedileceği konumu seçin, ardından "Oluştur"u tıklayın.
## Adım 2: .NET için GroupDocs.Watermark'ı yükleyin
GroupDocs.Watermark'ı projenizde kullanmak için kitaplığı yüklemeniz gerekir. Bu, NuGet Paket Yöneticisi kullanılarak yapılabilir:
1. Solution Explorer'da projenize sağ tıklayın.
2. "NuGet Paketlerini Yönet"i seçin.
3. Gözat sekmesinde "GroupDocs.Watermark" ifadesini arayın.
4. Kütüphaneyi projenize eklemek için "Yükle"ye tıklayın.
Alternatif olarak Paket Yönetici Konsolu aracılığıyla da kurabilirsiniz:
```powershell
Install-Package GroupDocs.Watermark
```
## 3. Adım: Belge Yolunu ve Çıktı Dizinini Tanımlayın
Önizlemeyi oluşturmadan önce, önizlemek istediğiniz belgenin yolunu ve önizleme görüntülerinin kaydedileceği dizini belirtmeniz gerekir:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
"Belge Yolunuz"u belgenizin yolu ile ve "Belge Dizininiz"i önizleme resimlerini kaydetmek istediğiniz dizinle değiştirin.
## 4. Adım: Filigran Nesnesini Başlatın
Bir örneğini oluşturun`Watermarker` belge yolunu yapıcısına ileterek sınıf. Bu nesne tüm filigranlama işlemlerini gerçekleştirmek için kullanılacaktır:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Kodunuz burada
}
```
## Adım 5: Akış İşleme için Temsilci Yöntemleri Oluşturun
Önizlemeyi oluşturmak için akış oluşturmaya ve yayınlamaya yönelik temsilci yöntemlerini tanımlamanız gerekir. Bu yöntemler, belgenin her sayfası için akışların oluşturulmasını ve yayınlanmasını yönetecektir:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
`createPageStreamDelegate` yöntem belgenin her sayfası için bir akış oluştururken,`releasePageStreamDelegate` yöntemi, önizleme oluşturulduktan sonra akışı kapatır.
## 6. Adım: Önizleme Seçeneklerini Yapılandırın
 Daha sonra, önizleme seçeneklerini, örneğini oluşturarak yapılandırın.`PreviewOptions` sınıf. Temsilci yöntemlerini belirtin ve önizleme biçimini PNG olarak ayarlayın. Ayrıca önizlemeye hangi sayfaların dahil edileceğini de belirleyebilirsiniz:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
Bu örnekte belgenin ilk iki sayfası için önizlemeler oluşturuyoruz.
## Adım 7: Belge Önizlemesini Oluşturun
 Son olarak, şu numarayı arayın:`GeneratePreview` konusundaki yöntem`Watermarker`yapılandırılmış olandan geçen nesne`PreviewOptions`. Bu, önizleme görüntülerini oluşturacak ve bunları belirtilen dizine kaydedecektir:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Çözüm
GroupDocs.Watermark for .NET'i kullanarak belge önizlemeleri oluşturmak, yalnızca birkaç satır kodla gerçekleştirilebilecek basit bir işlemdir. Bu kılavuzda özetlenen adımları izleyerek projenizi kolayca kurabilir, gerekli seçenekleri yapılandırabilir ve belgeleriniz için önizlemeler oluşturabilirsiniz. Bu güçlü kitaplık yalnızca filigran ekleme işlemini basitleştirmekle kalmaz, aynı zamanda filigranları yönetmek ve değiştirmek için güçlü özellikler de sağlar.
 Herhangi bir sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, şu adresi ziyaret etmekten çekinmeyin:[GroupDocs.Watermark Destek Forumu](https://forum.groupdocs.com/c/watermark/19) veya şuraya bakın:[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/).
## SSS'ler
### GroupDocs.Watermark for .NET hangi dosya formatlarını destekler?
 GroupDocs.Watermark for .NET, PDF, DOCX, PPTX, XLSX ve çok daha fazlasını içeren çok çeşitli dosya formatlarını destekler. Desteklenen formatların tam listesi için bkz.[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/).
### Filigranların görünümünü özelleştirebilir miyim?
Evet, GroupDocs.Watermark; metin, resim ve şekil filigranları da dahil olmak üzere filigranların görünümünü tamamen özelleştirmenize olanak tanır. Yazı tipi, renk, boyut ve şeffaflık gibi özellikleri ayarlayabilirsiniz.
### Deneme sürümü mevcut mu?
 Evet, alabilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) Satın almadan önce özelliklerini değerlendirmek için GroupDocs.Watermark for .NET'i kullanın.
### GroupDocs.Watermark lisansını nasıl satın alabilirim?
 GroupDocs.Watermark için bir lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy). Farklı ihtiyaçlara uyacak çeşitli lisanslama seçenekleri mevcuttur.
### GroupDocs.Watermark'ı ticari bir projede kullanabilir miyim?
 Evet, geçerli bir lisansla GroupDocs.Watermark'ı ticari projelerde kullanabilirsiniz. Lisanslama hüküm ve koşullarını incelediğinizden emin olun.[satın alma sayfası](https://purchase.groupdocs.com/buy).