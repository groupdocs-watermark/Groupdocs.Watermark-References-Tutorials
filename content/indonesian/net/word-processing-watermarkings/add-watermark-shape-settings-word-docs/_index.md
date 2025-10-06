---
title: Tambahkan Tanda Air dengan Pengaturan Bentuk di Word Docs
linktitle: Tambahkan Tanda Air dengan Pengaturan Bentuk di Word Docs
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air dengan pengaturan bentuk ke dokumen Word menggunakan GroupDocs untuk .NET. Lindungi dokumen Anda secara efektif.
weight: 20
url: /id/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
type: docs
---
# Tambahkan Tanda Air dengan Pengaturan Bentuk di Word Docs

## Perkenalan
Dalam tutorial ini, kita akan memandu proses menambahkan tanda air dengan pengaturan bentuk ke dokumen Word menggunakan GroupDocs.Watermark untuk .NET.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Watermark untuk .NET diinstal. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. Pengetahuan dasar tentang pemrograman C#.
3. Pemahaman tentang pemrosesan dokumen Word.

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan untuk mengakses kelas dan metode yang diperlukan.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
Muat dokumen Word yang ingin Anda tambahkan tanda airnya.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode tambahan tanda air ada di sini
}
```
## Langkah 2: Tambahkan Tanda Air
 Buat contoh a`TextWatermark` objek dan tentukan teks yang ingin Anda gunakan sebagai tanda air.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Langkah 3: Sesuaikan Pengaturan Tanda Air
Tetapkan berbagai pengaturan untuk tanda air, seperti perataan, sudut rotasi, warna, dan opacity.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Langkah 4: Tentukan Opsi Bagian Tanda Air
Tentukan opsi untuk bagian tanda air, seperti nama bentuk dan teks alternatif.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Langkah 5: Tambahkan Tanda Air ke Dokumen
Tambahkan tanda air ke dokumen dengan opsi yang ditentukan.
```csharp
watermarker.Add(watermark, options);
```
## Langkah 6: Simpan Dokumen
Simpan dokumen dengan tanda air tambahan.
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Menambahkan tanda air dengan pengaturan bentuk ke dokumen Word menggunakan GroupDocs untuk .NET adalah proses yang mudah. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat melindungi dokumen Anda secara efektif dengan tanda air yang disesuaikan.
## FAQ
### Bisakah saya menambahkan beberapa tanda air ke dokumen yang sama?
Ya, Anda dapat menambahkan beberapa tanda air dengan pengaturan berbeda ke dokumen yang sama.
### Apakah GroupDocs.Watermark mendukung format dokumen lain selain Word?
Ya, GroupDocs.Watermark mendukung berbagai format dokumen, termasuk Excel, PowerPoint, PDF, dan lainnya.
### Bisakah saya menyesuaikan tampilan tanda air lebih lanjut?
Tentu saja, Anda dapat menyesuaikan berbagai parameter seperti ukuran font, gaya, warna, dan posisi sesuai kebutuhan Anda.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark untuk .NET?
 Ya, Anda bisa mendapatkan uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dukungan untuk GroupDocs.Watermark?
 Anda dapat menemukan dukungan dan mengajukan pertanyaan di forum GroupDocs[Di Sini](https://forum.groupdocs.com/c/watermark/19).