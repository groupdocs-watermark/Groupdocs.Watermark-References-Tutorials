---
title: Word Belgelerindeki Şekil Görüntüsünü Değiştirme
linktitle: Word Belgelerindeki Şekil Görüntüsünü Değiştirme
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki şekil görüntülerini programlı olarak nasıl değiştireceğinizi öğrenin. Belge işleme görevlerini zahmetsizce basitleştirin.
weight: 33
url: /tr/net/word-processing-watermarkings/replace-shape-image-word-docs/
type: docs
---
# Word Belgelerindeki Şekil Görüntüsünü Değiştirme

## giriiş
Yazılım geliştirme alanında, özellikle .NET ortamında, belge manipülasyonunun verimli ve güvenli bir şekilde ele alınması çok önemlidir. Geliştiricilerin sıklıkla karşılaştığı sayısız görev arasında en sık karşılaşılan zorluklardan biri, Word belgelerindeki şekil görüntülerini program aracılığıyla değiştirmektir. Doğru araçlar ve kütüphaneler olmadan bu sıkıcı bir görev olabilir.
Neyse ki GroupDocs, Word belgeleri de dahil olmak üzere çeşitli belge formatlarında filigran ekleme ve filigranları işlemek için tasarlanmış çok yönlü bir kitaplık olan GroupDocs.Watermark for .NET biçiminde güçlü bir çözüm sunuyor. Bu öğreticide, GroupDocs.Watermark for .NET'i kullanarak Word belgelerindeki şekil görüntülerini değiştirme işlemini adım adım inceleyeceğiz.
## Önkoşullar
Bu eğitime başlamadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1.  GroupDocs.Watermark for .NET Kitaplığı: GroupDocs.Watermark for .NET kitaplığını şuradan indirip yükleyin:[İndirme: {link](https://releases.groupdocs.com/Watermark/net/).
2. Düzenlenecek Belge: Program aracılığıyla değiştirmeyi planladığınız şekil görüntülerini içeren bir Word belgesi hazırlayın.
3. Geliştirme Ortamı: .NET özelliklerine sahip, tercihen Visual Studio olmak üzere, çalışan bir geliştirme ortamı kurun.
4. Temel C# Programlama Bilgisi: GroupDocs ile etkileşimde bulunmak için C# kullanacağımız için C# programlamanın temellerini öğrenin.
## Ad Alanlarını İçe Aktar
Kodlama kısmına geçmeden önce gerekli ad alanlarını C# projemize aktaralım:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System;
using System.IO;
```
## 1. Adım: Belgeyi Yükleyin
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Belge başarıyla yüklendi
}
```
 Bu adımda manipüle etmek istediğimiz Word belgesinin yolunu tanımlıyoruz. Daha sonra örneğini oluşturuyoruz`WordProcessingLoadOptions` Word belgesinin yükleme seçeneklerini belirlemek için. Daha sonra, bir başlangıç başlatıyoruz`Watermarker` belge yolu ve yükleme seçenekleriyle birlikte nesne.
## 2. Adım: Belge İçeriğine Erişin
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Burada Word belgesinin içeriğini aşağıdaki komutu kullanarak alıyoruz:`GetContent` yöntemi`Watermarker` nesne. İçerik bir dosyada saklanır`WordProcessingContent` belge içindeki çeşitli öğelere erişmemizi ve bunları değiştirmemizi sağlayan nesne.
## 3. Adım: Şekil Görüntülerini Değiştirin
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Image != null)
    {
        shape.Image = new WordProcessingWatermarkableImage(File.ReadAllBytes(Constants.TestPng));
    }
}
```
Bu adımda belgenin ilk bölümündeki her şekli yineliyoruz. Bir görüntü içeren her şekil için (`shape.Image != null`), mevcut görüntüyü yenisiyle değiştiririz. Bu örnekte bir sabit kullanıyoruz`TestPng` yedek resim olarak. Bunu istediğiniz görüntünün yolu ile değiştirdiğinizden emin olun.
## Adım 4: Belgeyi Kaydedin
```csharp
watermarker.Save(outputFileName);
```
Son olarak, değiştirilen belgeyi, değiştirilen resimlerle birlikte belirtilen çıktı dosyası adına kaydederiz.

## Çözüm
GroupDocs.Watermark for .NET, Word belgelerindeki şekil görüntülerini program aracılığıyla değiştirme işlemini basitleştirir. Bu öğreticide özetlenen adımları izleyerek, bu işlevselliği .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilir, belge işleme görevlerinde zamandan ve emekten tasarruf edebilirsiniz.
## SSS'ler
### GroupDocs.Watermark for .NET, Word belgelerinin farklı sürümleriyle uyumlu mu?
Evet, GroupDocs.Watermark for .NET, .doc ve .docx biçimleri de dahil olmak üzere Word belgelerinin çeşitli sürümlerini destekler.
### GroupDocs.Watermark'ı kullanarak şekil görüntülerinin yanı sıra diğer öğe türlerini de değiştirebilir miyim?
Kesinlikle. GroupDocs.Watermark, farklı formatlardaki belgelerdeki filigranları, resimleri, metinleri ve diğer öğeleri değiştirmek için kapsamlı işlevsellik sunar.
### GroupDocs.Watermark for .NET'in deneme sürümü mevcut mu?
 Evet, şu adresten ücretsiz deneme sürümünü indirerek GroupDocs.Watermark for .NET'in yeteneklerini keşfedebilirsiniz.[Burada](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET, PDF belgelerindeki filigranların işlenmesine yönelik destek sağlıyor mu?
Evet, GroupDocs.Watermark for .NET, Word, Excel, PowerPoint ve daha fazlası gibi diğer formatların yanı sıra PDF belgelerinde filigran eklemeyi ve filigranları değiştirmeyi destekler.
### GroupDocs.Watermark for .NET için nasıl yardım veya destek alabilirim?
 GroupDocs.Watermark forumunu ziyaret edebilirsiniz.[Burada](https://forum.groupdocs.com/c/watermark/19) Karşılaşabileceğiniz herhangi bir soru veya sorun için yardım istemek veya toplulukla etkileşime geçmek.