---
title: Word Dokümanlarında Şekil Türü Kullanımı
linktitle: Word Dokümanlarında Şekil Türü Kullanımı
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki şekilleri nasıl değiştireceğinizi öğrenin. Bu eğitim, verimli belge işleme için rehberlik sağlar.
weight: 37
url: /tr/net/word-processing-watermarkings/shape-type-usage-word-docs/
---
## giriiş
Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerinde şekil türlerinin nasıl kullanılacağını keşfedeceğiz. Word belgelerindeki şekiller farklılık gösterebilir ve bunların nasıl değiştirileceğini anlamak, çeşitli belge işleme görevleri için çok önemli olabilir.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1.  GroupDocs.Watermark for .NET Kitaplığı: GroupDocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[İndirme: {link](https://releases.groupdocs.com/Watermark/net/).
2. Belge Yolu: Bir Word belgesini işlenmeye hazır hale getirin.
3. Geliştirme Ortamı: .NET framework desteği ile uygun bir geliştirme ortamı kurun.

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını projenize aktarmanız gerekir. Bu ad alanları, Word belgeleriyle çalışmak için gerekli sınıflara ve yöntemlere erişim sağlayacaktır.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 1. Adım: Belgeyi Yükleyin
Word belgesini Filigran nesnesine yükleyerek başlayın. Yükleme işlemi sırasında belge yolunu ve gerekli ek seçenekleri belirttiğinizden emin olun.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Belge işleme kodu buraya gelir
}
```
## 2. Adım: Belge İçeriğine Erişin
 Yüklenen Word belgesinin içeriğine aşağıdaki komutu kullanarak erişin:`GetContent<WordProcessingContent>()` yöntem. Bu, belgede bulunan bölümlere, paragraflara ve şekillere erişim sağlayacaktır.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Adım 3: Bölümleri ve Şekilleri Yineleyin
Gerektiğinde incelemek ve değiştirmek için belgedeki her bölüm ve şekli yineleyin.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Şekil işleme kodu buraya gelecek
    }
}
```
## Adım 4: Şekil Türlerini Kontrol Edin
Döngü içinde, belirli şekil türlerini kullanarak kontrol edin.`ShapeType` mülk. Bu örnek, Çapraz Köşeler Yuvarlatılmış şekillerin tanımlanmasını ve işlenmesini gösterir.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Şekle özgü manipülasyon kodu buraya gelir
}
```
## Adım 5: Şekilleri Yönetin
Tanımlanan şekillere metin ekleme, biçimlendirmeyi değiştirme veya görsel değişiklikler uygulama gibi eylemleri gerçekleştirin.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Adım 6: Belgeyi Kaydedin
Gerekli tüm değişiklikler yapıldıktan sonra, uygulanan değişiklikleri içeren belgeyi belirtilen çıktı dosyasına kaydedin.
```csharp
watermarker.Save(outputFileName);
```

## Çözüm
Word belgelerindeki şekilleri değiştirmek, çeşitli belge işleme görevleri için gerekli olabilir. GroupDocs.Watermark for .NET ile gereksinimlerinizi verimli bir şekilde karşılamak için şekilleri kolayca tanımlayabilir, değiştirebilir ve değiştirebilirsiniz.
## SSS'ler
### GroupDocs.Watermark for .NET, Word'ün yanı sıra diğer belge formatlarını da işleyebilir mi?
Evet, GroupDocs.Watermark for .NET, PDF, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Watermark for .NET'in ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümüne şuradan erişebilirsiniz:[sürümler sayfası](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET teknik destek sağlıyor mu?
 Evet, yardım isteyebilir ve toplulukla iletişim kurabilirsiniz.[destek Forumu](https://forum.groupdocs.com/c/watermark/19).
### Filigranlama sürecini belirli belge gereksinimlerine göre özelleştirebilir miyim?
Kesinlikle GroupDocs.Watermark for .NET, filigranlama sürecini ihtiyaçlarınıza göre uyarlamak için kapsamlı özelleştirme seçenekleri sunar.
### GroupDocs.Watermark for .NET için nasıl geçici lisans alabilirim?
 adresinden geçici lisans alabilirsiniz.[Geçici lisans satın alma sayfası](https://purchase.groupdocs.com/temporary-license/) test ve değerlendirme amaçlıdır.