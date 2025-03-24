---
title: Belgeyi Akıştan Yükle
linktitle: Belgeyi Akıştan Yükle
second_title: GroupDocs.Watermark .NET API'si
description: Bu kılavuzla GroupDocs.Watermark for .NET'i kullanarak belgelere nasıl filigran ekleyeceğinizi öğrenin. Belge güvenliğini artırmak isteyen geliştiriciler için mükemmeldir.
weight: 11
url: /tr/net/document-loadings/load-document-from-stream/
---
## giriiş
.NET'i kullanarak belgelerinize sorunsuz bir şekilde filigran eklemek mi istiyorsunuz? Başka yerde arama! GroupDocs.Watermark for .NET, çeşitli belge formatlarındaki filigranları yönetmenize olanak tanıyan güçlü ve kullanımı kolay bir kitaplıktır. İster PDF'lerle, ister Word belgeleriyle, ister resimlerle çalışıyor olun, bu araç ihtiyacınızı karşılar. Bu öğreticide, bir akıştan belge yükleme ve filigran ekleme işlemini adım adım anlatacağız. Öyleyse hemen dalalım!
## Önkoşullar
Başlamadan önce aşağıdaki kurulumlara sahip olduğunuzdan emin olun:
1. Visual Studio: Visual Studio'nun herhangi bir güncel sürümü düzgün çalışacaktır.
2. .NET Framework: .NET Framework 4.0 veya üzerinin kurulu olduğundan emin olun.
3.  GroupDocs.Watermark for .NET: Şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/Watermark/net/).
4. Temel C# Bilgisi: C# ve nesne yönelimli programlama kavramlarına aşinalık faydalı olacaktır.

## Ad Alanlarını İçe Aktar
GroupDocs.Watermark'ı projenizde kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Bu, kütüphanenin özelliklerine herhangi bir sorun yaşamadan erişmenizi sağlayacaktır.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 1. Adım: Projenizi Kurma
Öncelikle projenizi Visual Studio'da kurmanız gerekiyor. İşte bunu nasıl yapacağınız:
1. Yeni Bir Proje Oluşturun: Visual Studio'yu açın ve yeni bir C# Konsol Uygulaması projesi oluşturun.
2.  GroupDocs.Watermark'ı yükleyin: GroupDocs.Watermark kitaplığını NuGet Paket Yöneticisi aracılığıyla yükleyin. Basitçe arayın`GroupDocs.Watermark` ve yükleyin.
## 2. Adım: Belge Yollarını Tanımlayın
Daha sonra, belgenizin yollarını ve filigranlı belgenin kaydedileceği çıktı dosyasını tanımlamanız gerekir.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Yer değiştirmek`"Your Document Path"` filigran eklemek istediğiniz belgenin gerçek yolu ile ve`"Your Document Directory"` filigranlı belgeyi kaydetmek istediğiniz dizinle.
## 3. Adım: Belgeyi Akıştan Yükleme
Şimdi belgeyi bir akıştan yükleyelim. Bu, belgenin bir akış olarak açılmasını ve ardından`Watermarker` yönetmek için GroupDocs.Watermark kitaplığından sınıf.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Filigranları yönetme kodunuz buraya gelecek
}
```
 Bu kod parçacığı, belgenin bir akış olarak açılmasını ve`Watermarker` sınıf bu akışla başlatılır.`using` Açıklamalar, kaynakların kullanımdan sonra uygun şekilde bertaraf edilmesini sağlar.
## 4. Adım: Filigran Oluşturun ve Ekleyin
GroupDocs.Watermark ile filigran oluşturmak çok kolaydır. Bu örnekte basit bir metin filigranı oluşturacağız.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Burada bir oluşturuyoruz`TextWatermark` "Test filigranı" metnini içeren nesneyi seçin ve yazı tipi ayrıntılarını belirtin. Daha sonra bu filigranı belgeye şunu kullanarak ekliyoruz:`Add` yöntemi`Watermarker` sınıf.
## Adım 5: Filigranlı Belgeyi Kaydetme
Son olarak filigranlı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
watermarker.Save(outputFileName);
```
 Bu kod, belgeyi yeni eklenen filigranla kaydeder`outputFileName` daha önce tanımladığınız yol.

## Çözüm
Tebrikler! GroupDocs.Watermark for .NET'i kullanarak belgenize başarıyla filigran eklediniz. Bu kitaplık, çeşitli belge formatlarındaki filigranları yönetmeyi inanılmaz derecede kolaylaştırır. Metin, resim veya diğer filigran türlerini eklemeniz gerekip gerekmediğini GroupDocs.Watermark'ta ihtiyacınız olan araçlar vardır. Kontrol etmeyi unutmayın[dokümantasyon](https://tutorials.groupdocs.com/Watermark/net/) daha gelişmiş özellikler ve kişiselleştirme seçenekleri için.
## SSS'ler
### GroupDocs.Watermark for .NET'i kullanarak ne tür filigranlar ekleyebilirim?
Metin filigranları, görüntü filigranları ve hatta karmaşık şekiller ve logolar ekleyebilirsiniz. Kitaplık çok çeşitli özelleştirme seçeneklerini destekler.
### GroupDocs.Watermark'ı kullanarak belgelerdeki filigranları kaldırabilir miyim?
Evet, GroupDocs.Watermark, mevcut filigranları belgelerden de kaldırmanıza olanak tanır.
### GroupDocs.Watermark'ın ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Watermark lisansını nasıl satın alabilirim?
Lisansı doğrudan adresinden satın alabilirsiniz.[GroupDocs web sitesi](https://purchase.groupdocs.com/buy).
### Sorunlarla karşılaşırsam nereden destek alabilirim?
 Destek için şu adresi ziyaret edebilirsiniz:[GroupDocs.Watermark destek forumu](https://forum.groupdocs.com/c/watermark/19).