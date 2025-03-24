---
title: Word Belgelerindeki Şekil Metnini Biçimlendirilmiş Metinle Değiştirme
linktitle: Word Belgelerindeki Şekil Metnini Biçimlendirilmiş Metinle Değiştirme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki şekil metnini biçimlendirilmiş metinle nasıl değiştireceğinizi öğrenin. Belge düzenleme yetenekleriniz zahmetsizce.
weight: 34
url: /tr/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki şekil metnini biçimlendirilmiş metinle değiştirme sürecinde size yol göstereceğiz. Bu kitaplık, şekillerin içindeki metni değiştirmek de dahil olmak üzere filigranlarla çalışmaya yönelik güçlü özellikler sağlar.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET'i yüklediğinizden ve ayarladığınızdan emin olun. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/Watermark/net/).
2. Belge Yolu: Metni değiştirmek istediğiniz Word belgesinin yoluna sahip olmalısınız.

## Ad Alanlarını İçe Aktar
Kodu yazmadan önce gerekli ad alanlarını içe aktarın:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. Adım: Belgeyi Yükleyin
 Word belgesini kullanarak yükleyin`Watermarker` sınıf:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kodunuz burada devam ediyor...
}
```
## 2. Adım: İçeriği Alın ve Metni Değiştirin
Belge yüklendikten sonra içeriği alın ve şekillerin içindeki metni değiştirin:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## 3. Adım: Belgeyi Kaydedin
Metni değiştirdikten sonra değiştirilen belgeyi kaydedin:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Çözüm
Word belgelerindeki şekil metnini biçimlendirilmiş metinle değiştirmek, GroupDocs for .NET ile artık çok kolay. Bu eğitimde özetlenen adımları izleyerek belgelerinizdeki metni verimli bir şekilde yönetebilir ve değiştirebilirsiniz.

## SSS'ler
### GroupDocs.Watermark for .NET'i kullanarak diğer belge türlerindeki metni değiştirebilir miyim?
Evet, GroupDocs Filigran, PDF, Excel, PowerPoint ve daha fazlası gibi çeşitli belge formatlarını destekler.
### GroupDocs.Watermark .NET Core ile uyumlu mu?
Evet, GroupDocs.Watermark hem .NET Framework'ü hem de .NET Core'u destekler.
### GroupDocs.Watermark, resimleri filigran olarak eklemek için destek sağlıyor mu?
Kesinlikle GroupDocs.Watermark, belgelerinize hem metin hem de resim filigranları eklemenizi sağlar.
### GroupDocs.Watermark kullanılarak eklenen filigranların görünümünü özelleştirebilir miyim?
Evet, filigranların görünümü, konumu ve diğer özellikleri üzerinde tam kontrole sahipsiniz.
### GroupDocs.Watermark for .NET'in deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).