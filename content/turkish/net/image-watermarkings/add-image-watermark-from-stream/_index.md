---
title: Akıştan Resim Filigranı Ekle
linktitle: Akıştan Resim Filigranı Ekle
second_title: GroupDocs.Watermark .NET API'si
description: GroupDocs.Watermark for .NET'i kullanarak belgelere görüntü filigranlarını nasıl ekleyeceğinizi öğrenin. Sorunsuz filigran entegrasyonu için adım adım kılavuzumuzu izleyin.
weight: 12
url: /tr/net/image-watermarkings/add-image-watermark-from-stream/
---
## giriiş
Belge yönetimi ve güvenliği alanında filigranların dosyalara dahil edilmesi büyük önem taşıyor. Markalama, telif hakkı koruması veya belge bütünlüğünü koruma konusunda filigranlar çok önemli bir rol oynar. Neyse ki GroupDocs.Watermark for .NET, çeşitli belge formatlarındaki filigranları eklemek, kaldırmak ve aramak için güçlü bir çözüm sağlar.
## Önkoşullar
GroupDocs.Watermark for .NET'i kullanarak filigranların uygulanmasına dalmadan önce aşağıdaki önkoşulların karşılandığından emin olun:
1.  GroupDocs.Watermark for .NET'i yükleyin: GroupDocs.Watermark for .NET kitaplığını şuradan indirin ve yükleyin:[İndirme: {link](https://releases.groupdocs.com/Watermark/net/).
2. Belgeye Erişim: Filigran eklemek veya kaldırmak istediğiniz belgeye erişin.
3. Temel C# Bilgisi: Sağlanan kod parçacıklarını anlamak ve uygulamak için C# programlama diline aşinalık gereklidir.

## Ad Alanlarını İçe Aktar
Bir akıştan görüntü filigranları eklemeye devam etmeden önce gerekli ad alanlarını içe aktarın:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Adım 1: Belge Yolunu ve Çıktı Dizinini Tanımlayın
Öncelikle filigranı eklemek istediğiniz belgenin yolunu tanımlayın ve işlenen belgenin çıktı dizinini belirtin.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 2. Adım: Filigran Akışını açın
 Filigran görüntü dosyasını kullanarak akış olarak açın.`File.OpenRead` yöntem.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // Filigran işleme mantığı buraya gelecek
}
```
## 3. Adım: Belgeye Filigran Ekleme
 Bir başlat`Watermarker` belge yoluna sahip bir nesne oluşturun, ardından bir`ImageWatermark` Adım 2'de elde edilen filigran akışına sahip nesneyi seçin. Filigranı belgeye şunu kullanarak ekleyin:`Add` yöntemi`Watermarker` nesne.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Belgeye filigran ekleme
        watermarker.Add(watermark);
        // Belgeyi filigranla kaydedin
        watermarker.Save(outputFileName);
    }
}
```

## Çözüm
GroupDocs.Watermark for .NET, belgelere filigran eklemek, marka kimliğini, telif hakkı korumasını ve belge bütünlüğünü sağlamak için kusursuz bir çözüm sunar. Kullanıcılar, özetlenen adımları izleyerek ve sağlanan kod parçacıklarını kullanarak, filigranları belgelerine zahmetsizce dahil edebilir.
## SSS'ler
### GroupDocs.Watermark çeşitli belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Watermark, Word belgeleri, Excel elektronik tabloları, PowerPoint sunumları, PDF'ler ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Filigranların görünümünü ve konumunu özelleştirebilir miyim?
Kesinlikle GroupDocs.Watermark, filigranın görünümünü, konumunu, şeffaflığını, dönüşünü ve daha fazlasını belirli gereksinimlere uyacak şekilde özelleştirmek için kapsamlı seçenekler sunar.
### GroupDocs.Watermark mevcut filigranların kaldırılmasına yönelik API'ler sağlıyor mu?
Evet, GroupDocs.Watermark, kullanıcıların yalnızca filigran eklemesine değil aynı zamanda mevcut filigranları belgelerden kolaylıkla kaldırmasına da olanak tanır.
### GroupDocs.Watermark kullanıcıları için teknik destek mevcut mu?
 Evet, kullanıcılar özel destek aracılığıyla teknik destek ve yardımdan yararlanabilirler.[GroupDocs.Watermark forumu](https://forum.groupdocs.com/c/watermark/19).
### GroupDocs.Watermark'ı satın almadan önce değerlendirebilir miyim?
Elbette kullanıcılar, satın alma kararı vermeden önce özelliklerini ve işlevlerini keşfetmek için GroupDocs.Watermark'ın ücretsiz deneme sürümünü tercih edebilirler.