---
title: Belgeyi Yerel Diskten Yükle
linktitle: Belgeyi Yerel Diskten Yükle
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs for .NET ile belgelerinizi koruyun ve yönetin. Sorunsuz bir şekilde filigran eklemek için ayrıntılı kılavuzumuzu izleyin.
type: docs
weight: 10
url: /tr/net/document-loadings/load-document-from-local-disk/
---
## giriiş
Belgelerin filigranlanması, günümüzün dijital çağında içeriğin korunması, mülkiyet iddiası ve gizliliğin sağlanması açısından önemlidir. Groupdocs.Watermark for .NET, geliştiricilerin çeşitli belge formatlarındaki filigranları eklemesine, aramasına ve yönetmesine olanak tanıyan güçlü bir kitaplıktır. Bu öğreticide, ayrıntılı adım adım talimatlarla belgelerinize filigran eklemek için Groupdocs.Watermark for .NET kullanma sürecini anlatacağız.
## Önkoşullar
Uygulamaya geçmeden önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Visual Studio Yüklü: Visual Studio'ya veya başka bir uyumlu .NET IDE'ye ihtiyacınız olacak.
2.  Groupdocs.Watermark for .NET: Kitaplığı şuradan indirin:[İndirme: {link](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: .NET Framework 4.6.1 veya üstünün kurulu olduğundan emin olun.
4. Örnek Belge: Filigranlama işlemini test etmek için örnek belge hazırlayın.
## Ad Alanlarını İçe Aktar
Başlamak için projenize gerekli ad alanlarını içe aktarmanız gerekir. Bunlar filigranlama için gereken sınıflara ve yöntemlere erişim için gereklidir.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yerel Diskten Yükleyin
Öncelikle belgeyi yerel diskinizden yüklemeniz gerekir. Bu belge filigran ekleyeceğiniz belge olacaktır.
Filigran eklemek istediğiniz belgenin yolunu tanımlayın.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Adım 2: Yükleme Seçeneklerini Başlatın
 Ardından yükleme seçeneklerini başlatın. Örneğin, bir Word belgesiyle çalışıyorsanız şunu kullanacaksınız:`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 3. Adım: Filigran Oluşturun ve Yapılandırın
 Şimdi, şunun bir örneğini oluşturacaksınız:`Watermarker` sınıf. Bu örnek, filigranları yönetmek ve belgenize uygulamak için kullanılacaktır.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Bu blok, filigranı eklemek ve kaydetmek için başka adımlar içerecektir
}
```
## 4. Adım: Filigran Oluşturun
Bir metin filigranı oluşturun. Bu filigran seçtiğiniz herhangi bir metni içerebilir. Burada "Test filigranı" kullanacağız.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Adım 5: Belgeye Filigran Ekleme
Oluşturulan filigranı kullanarak belgeye ekleyin.`Add` yöntemi`Watermarker` sınıf.
```csharp
watermarker.Add(watermark);
```
## Adım 6: Filigranlı Belgeyi Kaydetme
Son olarak filigranlı belgeyi belirtilen yola kaydedin.
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Groupdocs'u kullanarak belgelerinize filigran eklemek basit ve etkilidir. Bu kılavuz, ortamınızı ayarlamaktan filigranlı bir belgeyi kaydetmeye kadar tüm süreç boyunca size yol göstermiştir. Bu güçlü araçla belgelerinizin korunduğundan ve fikri mülkiyetinizin güvende olduğundan emin olabilirsiniz. 
 Daha fazla ayrıntı için şurayı kontrol edin:[dokümantasyon](https://reference.groupdocs.com/Watermark/net/) ve herhangi bir sorunla karşılaşırsanız,[destek Forumu](https://forum.groupdocs.com/c/watermark/19) yardım için mükemmel bir yerdir. 
## SSS'ler
### Filigranlar için özel yazı tipleri kullanabilir miyim?
Evet, Groupdocs, özel yazı tiplerini destekler. Sisteminizde yüklü olan herhangi bir yazı tipini belirtebilirsiniz.
### Ne tür belgeler desteklenir?
Groupdocs.Watermark, Word, Excel, PDF, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Bir belgeden filigranı nasıl kaldırabilirim?
 Şunu kullanabilirsiniz:`Remove` tarafından sağlanan yöntem`Watermarker` filigranları kaldırmak için sınıf.
### Görüntü filigranları eklemek mümkün mü?
 Evet, kullanarak resim filigranları ekleyebilirsiniz.`ImageWatermark` sınıf.
### Groupdocs.Watermark'ı ücretsiz deneyebilir miyim?
 Kesinlikle indirebilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) Kütüphaneyi satın almadan önce değerlendirmek.