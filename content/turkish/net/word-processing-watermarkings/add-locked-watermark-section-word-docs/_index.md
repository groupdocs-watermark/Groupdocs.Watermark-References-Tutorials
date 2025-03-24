---
title: Word Dokümanlarındaki Bölüme Kilitli Filigran Ekleme
linktitle: Word Dokümanlarındaki Bölüme Kilitli Filigran Ekleme
second_title: GroupDocs.Watermark .NET API'si
description: Bu kapsamlı adım adım kılavuzla Groupdocs'u kullanarak Word belgelerindeki belirli bir bölüme nasıl kilitli filigran ekleyeceğinizi öğrenin.
weight: 13
url: /tr/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---

# Word Dokümanlarındaki Bölüme Kilitli Filigran Ekleme

## giriiş
Word belgelerinizdeki bir bölüme kilitli filigran eklemenin etkili bir yolunu mu arıyorsunuz? Başka yerde arama! Groupdocs.Watermark for .NET ile, Word belgelerine sorunsuz bir şekilde filigran ekleyebilir, aynı zamanda bunların kilitli ve kurcalanmaya karşı korumalı kalmasını sağlayabilirsiniz. Bu güçlü araç, markalama, gizlilik veya güvenlik amacıyla filigranlama ihtiyaçlarınızı karşılayacak çeşitli özellikler sunar. Bu adım adım öğreticide, Groupdocs.Watermark for .NET'i kullanarak bir Word belgesinin belirli bir bölümüne nasıl kilitli filigran ekleyeceğinizi anlatacağız. Hadi dalalım!
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1.  .NET için Groupdocs.Watermark: Groupdocs.Watermark kitaplığının kurulu olduğundan emin olun. İndirebilirsin[Burada](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Geliştirme ortamınızda .NET framework'ün kurulu olduğundan emin olun.
3. IDE: Visual Studio gibi bir Tümleşik Geliştirme Ortamı (IDE) kullanın.
4. Belge: Filigranı uygulamak için bir Word belgesi (.docx).
## Ad Alanlarını İçe Aktar
Başlamak için projenize gerekli ad alanlarını içe aktarmanız gerekir. Bunu nasıl yapacağınız aşağıda açıklanmıştır:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgenizi Yükleyin
 Öncelikle filigran eklemek istediğiniz belgeyi yüklemeniz gerekir. Bu adım, belgenizin yolunu belirtmeyi ve belgeyi kullanarak yüklemeyi içerir.`Watermarker` sınıf.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Filigran kodunuz buraya gelecek.
}
```
## Adım 2: Filigranı Oluşturun
Daha sonra belgenize eklemek istediğiniz filigranı oluşturun. Bu örnekte, belirli yazı tipi ayarları ve rengiyle bir metin filigranı oluşturacağız.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 3. Adım: Filigran Seçeneklerini Yapılandırma
Şimdi bölüm indeksini ve kilit ayarlarını belirtmek için filigran seçeneklerini yapılandırın. Bu, filigranın doğru bölüme eklenmesini ve kilitlenmesini sağlar.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // İlk bölüme ekle
options.IsLocked = true; // Filigranı kilitle
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Kilit tipi
```
## Adım 4: Filigranı Belgeye Ekleme
 Filigranınız ve seçenekleriniz yapılandırıldığında, filigranı belgeye ekleme zamanı geldi.`Add` yöntemi`Watermarker` sınıf.
```csharp
watermarker.Add(watermark, options);
```
## Adım 5: Değiştirilen Belgeyi Kaydedin
Son olarak, filigranın eklendiği belgeyi istediğiniz çıktı konumuna kaydedin.
```csharp
watermarker.Save(outputFileName);
```
## Çözüm
Groupdocs'u kullanarak Word belgesindeki belirli bir bölüme kilitli filigran eklemek basit bir işlemdir. Bu adımları izleyerek belgelerinizin güvenliğini ve bütünlüğünü artırabilir, önemli bilgilerin korunmasını sağlayabilirsiniz. İster hassas verileri koruyor olun ister belgelerinize profesyonel bir dokunuş ekliyor olun, Groupdocs.Watermark for .NET, hedeflerinize etkili bir şekilde ulaşmak için ihtiyaç duyduğunuz araçları sağlar.
## SSS'ler
### .NET için Groupdocs.Watermark nedir?
Groupdocs.Watermark for .NET, geliştiricilerin gelişmiş özelleştirme ve güvenlik özellikleriyle Word, PDF ve resimler de dahil olmak üzere çeşitli belge türlerine filigran eklemesine olanak tanıyan güçlü bir kitaplıktır.
### Bir filigranı parolayla kilitleyebilir miyim?
 Evet, filigranı bir parola ile koruyabilirsiniz.`options.Password` içindeki mülk`WordProcessingWatermarkSectionOptions` sınıf.
### Bir belgenin farklı bölümlerine farklı filigranlar uygulamak mümkün müdür?
 Kesinlikle! Farklı ayarlayarak`SectionIndex` içindeki değerler`WordProcessingWatermarkSectionOptions`belgenin farklı bölümlerine benzersiz filigranlar uygulayabilirsiniz.
### Groupdocs.Watermark'ı kullanarak ne tür filigranlar ekleyebilirim?
Groupdocs.Watermark, metin, resim ve şekil filigranları da dahil olmak üzere çeşitli filigran türlerini destekler ve her tür için kapsamlı özelleştirme seçenekleri sunar.
### Groupdocs.Watermark for .NET hakkında daha fazla bilgiyi nerede bulabilirim?
 Daha fazla bilgi için şu adresi ziyaret edebilirsiniz:[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/) Ve[destek Forumu](https://forum.groupdocs.com/c/watermark/19).