---
title: PDF Boyutlarını Alın
linktitle: PDF Boyutlarını Alın
second_title: GroupDocs.Watermark .NET API'si
description: Groupdocs.Watermark for .NET'i kullanarak belgelerinizi kolaylıkla koruyun. Zahmetsizce filigran, damga ve açıklamalar ekleyin.
weight: 26
url: /tr/net/pdf-watermarking-attachments/get-pdf-dimensions/
---
## giriiş
Günümüzün dijital çağında belgelerinizi korumak çok önemlidir. İster iş profesyoneli, ister hukuk uzmanı, ister yaratıcı bir sanatçı olun, fikri mülkiyetinizi korumak çok önemlidir. Groupdocs.Watermark for .NET, belgelerinize filigranlar, damgalar ve açıklamalar eklemek için güçlü bir çözüm sunarak bunların güvenliğini ve orijinalliğini sağlar.
## Önkoşullar
Groupdocs.Watermark for .NET dünyasına dalmadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1.  Groupdocs.Watermark for .NET kurulumu: Groupdocs.Watermark for .NET'i şu adresten indirip yükleyin:[İndirme: {link](https://releases.groupdocs.com/Watermark/net/).
2.  Lisans Anahtarı (İsteğe bağlı): Groupdocs.Watermark for .NET ücretsiz deneme olanağı sunsa da, geçici bir lisansı tercih edebilir veya adresinden tam lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy) genişletilmiş işlevsellik için.
3. C#'a aşinalık: Verilen örnekleri anlamak ve uygulamak için temel C# programlama dili bilgisi önerilir.
4. Korunacak Belge: Deneme yapmak için yerel makinenizde örnek bir belgeyi (örneğin, PDF, Word, Excel) hazır bulundurun.

## Ad Alanlarını İçe Aktar
Groupdocs.Watermark for .NET ile çalışmaya başlamak için gerekli ad alanlarını C# projenize aktarmanız gerekir.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Adım 1: Değişkenleri Bildirin
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Adım 2: Belgeyi Yükleyin
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### 3. Adım: PDF İçeriğini Alın
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Adım 4: Boyutları Alma
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Çözüm
Sonuç olarak, Groupdocs.Watermark for .NET, belgelerinizi yetkisiz kullanıma ve dağıtıma karşı korumak için kapsamlı bir çözüm sunar. Yukarıda özetlenen adımları izleyerek ve Groupdocs.Watermark for .NET'in gücünden yararlanarak değerli dijital varlıklarınızın güvenliğini ve bütünlüğünü sağlayabilirsiniz.
## SSS'ler
### Groupdocs.Watermark for .NET'i ücretsiz kullanabilir miyim?
Evet, Groupdocs.Watermark for .NET, değerlendirme amacıyla ücretsiz deneme sürümü sunar. Ancak genişletilmiş işlevsellik için tam lisans satın almayı düşünebilirsiniz.
### Groupdocs.Watermark birden fazla belge biçimini destekliyor mu?
Evet, Groupdocs Filigran, PDF, Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Groupdocs.Watermark ile filigranları ve pulları özelleştirebilir miyim?
Kesinlikle! Groupdocs.Watermark, özel gereksinimlerinize uyacak şekilde filigranlar, damgalar ve ek açıklamalar için kapsamlı özelleştirme seçenekleri sunar.
### Groupdocs.Watermark kullanıcıları için teknik destek mevcut mu?
 Evet, teknik yardım alabilir ve Groupdocs topluluğuyla iletişim kurabilirsiniz.[destek Forumu](https://forum.groupdocs.com/c/watermark/19).
### Groupdocs.Watermark için nasıl geçici lisans alabilirim?
 Groupdocs.Watermark için geçici bir lisansı şuradan alabilirsiniz:[Burada](https://purchase.groupdocs.com/temporary-license/).