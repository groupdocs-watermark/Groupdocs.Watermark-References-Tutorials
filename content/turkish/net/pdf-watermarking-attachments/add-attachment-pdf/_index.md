---
title: PDF'ye Ek Ekle
linktitle: PDF'ye Ek Ekle
second_title: GroupDocs.Watermark .NET API'si
description: Sorunsuz filigran ekleme ve ek yönetimi için GroupDocs.Watermark ile .NET belge yönetimi yeteneklerinizi geliştirin.
weight: 12
url: /tr/net/pdf-watermarking-attachments/add-attachment-pdf/
type: docs
---
# PDF'ye Ek Ekle

## giriiş
.NET geliştirme alanında GroupDocs.Watermark, çeşitli belge formatlarındaki filigranları, ek açıklamaları ve daha fazlasını yönetmek için güçlü bir araç olarak öne çıkıyor. İster PDF'lerle, ister Word belgeleriyle, ister görüntülerle çalışıyor olun, GroupDocs.Watermark for .NET, geliştiricilerin belgeleri kolaylıkla işlemesine olanak tanıyan kusursuz bir entegrasyon sağlar.
## Önkoşullar
GroupDocs.Watermark for .NET'i kullanmanın inceliklerine dalmadan önce, aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1.  Kurulum: GroupDocs.Watermark for .NET'i yüklediğinizden emin olun. adresinden indirebilirsiniz.[yayın sayfası](https://releases.groupdocs.com/Watermark/net/).
2. Belge Hazırlama: Üzerinde filigran veya diğer işlemleri gerçekleştirmek istediğiniz bir belgeyi hazır bulundurun.
3. Temel C# Bilgisi: GroupDocs.Watermark API ile etkileşimde bulunmak için kullanacağımız C# programlama dilinin temellerine aşina olun.

## Ad Alanlarını İçe Aktar
Uygulamaya başlamadan önce GroupDocs.Watermark'ın işlevselliğine erişmek için gerekli ad alanlarını içe aktarmak çok önemlidir. Aşağıda gerekli ad alanları verilmiştir:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## 1. Adım: Belgeyi Yükleyin
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 Bu adımda çalışmak istediğimiz belgenin yolunu belirtiyoruz ve bir dosya oluşturuyoruz.`PdfLoadOptions` PDF belgelerini yüklemek için nesne. Daha sonra, bir başlangıç başlatıyoruz`Watermarker` belge yolu ve yükleme seçenekleriyle birlikte nesne.
## 2. Adım: PDF İçeriğini Alın
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 Burada, PDF belgesinin içeriğini aşağıdakileri kullanarak elde ederiz:`GetContent<PdfContent>()` yöntem.
## 3. Adım: Ek Ekle
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
Bu adım, PDF belgesine bir ek eklemeyi içerir. Ek dosyası baytlarını, adını ve açıklamasını sağlamanız gerekir.
## 4. Adım: Değişiklikleri Kaydet
```csharp
watermarker.Save(outputFileName);
```
Son olarak belgede yaptığımız değişiklikleri eklenen ek ile kaydediyoruz.

## Çözüm
GroupDocs.Watermark for .NET, belge filigranlarını ve eklerini sorunsuz bir şekilde yönetmek için güçlü bir çözüm sunar. Yukarıda özetlenen adımları izleyerek filigran ve ek işlevlerini .NET uygulamalarınıza kolayca entegre edebilirsiniz.
## SSS'ler
### GroupDocs.Watermark tüm .NET çerçeveleriyle uyumlu mu?
Evet, GroupDocs.Watermark .NET Framework 2.0 ve üstünü destekler.
### GroupDocs.Watermark kullanılarak eklenen filigranları kaldırabilir miyim?
Evet, GroupDocs.Watermark, filigranları belgelerden kaldırmaya yönelik yöntemler sağlar.
### GroupDocs.Watermark belge şifrelemeyi destekliyor mu?
Evet, GroupDocs.Watermark şifrelenmiş belgelerle çalışmanıza olanak tanır.
### Filigranların görünümünü özelleştirebilir miyim?
GroupDocs.Watermark kesinlikle filigranlar için çeşitli özelleştirme seçenekleri sunar.
### Test amaçlı deneme sürümü mevcut mu?
 Evet deneme sürümüne şuradan ulaşabilirsiniz.[sürümler sayfası](https://releases.groupdocs.com/).