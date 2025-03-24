---
title: Word Belgelerindeki Belirli Sayfalara Kilitli Filigran Ekleme
linktitle: Word Belgelerindeki Belirli Sayfalara Kilitli Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Kolay adım adım kılavuzumuzla GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki belirli sayfalara nasıl kilitli filigran ekleyeceğinizi öğrenin.
weight: 12
url: /tr/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## giriiş
Word belgelerinizdeki belirli sayfalara filigran eklemek istiyorsunuz, ancak kolayca kaldırılamayacak veya düzenlenemeyecek şekilde kilitlenmesini mi istiyorsunuz? Doğru yerdesiniz! Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki belirli sayfalara kilitli filigran ekleme sürecinde size rehberlik edeceğiz. Bu güçlü kitaplık, filigranların çeşitli belge türlerine uygulanmasını, yönetilmesini ve özelleştirilmesini kolaylaştırır. İster bir geliştirici olun ister yalnızca belgelerini güvence altına alması gereken biri olun, bu kılavuz size her adımda basit bir şekilde yol gösterecektir.
## Önkoşullar
Eğiticiye dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
1.  .NET için GroupDocs.Watermark: Şunları yapabilirsiniz:[indirmek](https://releases.groupdocs.com/Watermark/net/) Son sürüm.
2. Geliştirme Ortamı: Visual Studio benzeri bir IDE.
3. Temel C# Bilgisi: C# programlamaya aşinalık faydalı olacaktır.
4. Filigran Eklenecek Belge: Filigran eklemek istediğiniz bir Word belgesi (.docx veya .doc).
## Ad Alanlarını İçe Aktar
Öncelikle C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu ad alanları, GroupDocs.Watermark ile çalışmak için gereken sınıflara ve yöntemlere erişim sağlar.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Artık önkoşulları ele aldığımıza ve gerekli ad alanlarını içe aktardığımıza göre, süreci adım adım inceleyelim.
## Adım 1: Word Belgesini Yükleyin
 Başlangıç olarak filigran eklemek istediğiniz Word belgesini yüklemeniz gerekir. Bu, kullanılarak yapılabilir.`Watermarker` birlikte sınıf`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Sonraki adımlara geçin
}
```
## Adım 2: Metin Filigranını Oluşturun
Daha sonra bir metin filigranı oluşturun. Metni, yazı tipini, rengi ve diğer özellikleri gereksinimlerinize göre özelleştirebilirsiniz.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 3. Adım: Filigran Seçeneklerini Yapılandırma
 Filigranı belirli sayfalara uygulamak ve kilitlemek için`WordProcessingWatermarkPagesOptions`Burada filigranın görünmesi gereken sayfa numaralarını belirtir ve kilitleme seçeneklerini ayarlarsınız.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Sayfaları belirtin
options.IsLocked = true; // Filigranı kilitle
options.LockType = WordProcessingLockType.AllowOnlyComments; // Kilit türünü ayarla
// Şifre ile korumak için
// options.Password = "7654321";
```
## Adım 4: Filigranı Belgeye Ekleme
Filigranınız ve seçenekleriniz yapılandırıldığında artık filigranı belgeye ekleyebilirsiniz.
```csharp
watermarker.Add(watermark, options);
```
## Adım 5: Belgeyi Kaydedin
Son olarak, filigranın uygulandığı belgeyi kaydedin. Uygun bir çıktı yolu seçin ve dosyayı kaydedin.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Çözüm
Tebrikler! GroupDocs.Watermark for .NET'i kullanarak Word belgesindeki belirli sayfalara başarıyla kilitli filigran eklediniz. Bu eğitim, belgenin yüklenmesinden filigranlı dosyanın kaydedilmesine kadar tüm önemli adımları kapsıyordu. Bu adımları izleyerek belgelerinizin güvenli bir şekilde filigranlandığından ve içeriğinizin yetkisiz düzenleme ve kullanıma karşı korunduğundan emin olabilirsiniz.
 Daha fazla bilgi için şu adrese başvurabilirsiniz:[GroupDocs.Watermark belgeleri](https://tutorials.groupdocs.com/Watermark/net/) . Herhangi bir sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, şu adresi ziyaret etmekten çekinmeyin:[destek Forumu](https://forum.groupdocs.com/c/watermark/19).
## SSS'ler
### .NET için GroupDocs.Watermark nedir?
GroupDocs.Watermark for .NET, geliştiricilerin Word, PDF, Excel ve daha fazlasını içeren çeşitli belge türlerine filigran eklemesine olanak tanıyan güçlü bir kitaplıktır.
### Bir belgedeki birden fazla sayfaya filigran uygulayabilir miyim?
 Evet, birden fazla sayfa numarası belirtebilirsiniz.`PageNumbers` birden fazla sayfaya filigran uygulamak için dizi.
### Filigranı parolayla nasıl koruyabilirim?
 Bir filigranı parolayla koruyabilirsiniz.`Password` içindeki mülk`WordProcessingWatermarkPagesOptions`.
### Filigranın görünümünü özelleştirmek mümkün mü?
Kesinlikle! Filigranın metnini, yazı tipini, rengini, boyutunu ve diğer özelliklerini ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Watermark için nereden geçici lisans alabilirim?
 adresinden geçici lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).