---
title: Tambahkan Tanda Air dengan Efek Teks di Word Docs
linktitle: Tambahkan Tanda Air dengan Efek Teks di Word Docs
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air khusus dengan efek teks ke dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Keamanan dokumen dan daya tarik visual dengan mudah.
weight: 21
url: /id/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menambahkan tanda air dengan efek teks ke dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Dengan mengikuti petunjuk langkah demi langkah ini, Anda akan dapat menyempurnakan dokumen Anda dengan tanda air khusus yang menyertakan berbagai efek teks.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Watermark untuk .NET: Unduh dan instal perpustakaan dari[situs web](https://releases.groupdocs.com/Watermark/net/).
2. Jalur Dokumen: Ketahui jalur dokumen Word yang ingin Anda tambahkan tanda air.
3. Direktori Keluaran: Memiliki direktori tempat Anda ingin menyimpan dokumen yang dimodifikasi.

## Impor Namespace
Pastikan untuk mengimpor namespace yang diperlukan untuk mengakses kelas dan metode yang diperlukan:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
Muat dokumen Word yang ingin Anda tambahkan tanda air.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode untuk penambahan tanda air ada di sini
}
```
## Langkah 2: Tambahkan Tanda Air dengan Efek Teks
Buat tanda air teks dengan teks dan font yang diinginkan, lalu tentukan efek teks seperti format garis.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## Langkah 3: Sesuaikan Opsi Tanda Air
Tentukan opsi bagian tanda air, seperti efek teks, dan tetapkan ke tanda air.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Langkah 4: Simpan Dokumen
Simpan dokumen yang dimodifikasi dengan tanda air tambahan.
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Menambahkan tanda air dengan efek teks ke dokumen Word dapat meningkatkan daya tarik visual dan perlindungannya secara signifikan. Dengan GroupDocs.Watermark untuk .NET, proses ini menjadi efisien dan dapat disesuaikan, memungkinkan Anda membuat dokumen yang terlihat profesional secara efisien.
## FAQ
### Bisakah saya menyesuaikan font dan ukuran teks tanda air?
Ya, Anda dapat menentukan font dan ukuran saat membuat objek TextWatermark.
### Apakah mungkin menambahkan banyak tanda air ke satu dokumen?
Tentu saja, GroupDocs.Watermark untuk .NET mendukung penambahan beberapa tanda air dengan pengaturan berbeda ke satu dokumen.
### Apakah GroupDocs.Watermark mendukung format dokumen lain selain Word?
Ya, ini mendukung berbagai format dokumen termasuk PDF, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menghapus tanda air setelah ditambahkan ke dokumen?
Ya, perpustakaan menyediakan metode untuk menghapus tanda air dari dokumen dengan mudah.
### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).