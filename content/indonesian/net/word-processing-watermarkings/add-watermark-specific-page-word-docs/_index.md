---
title: Tambahkan Tanda Air ke Halaman Tertentu di Word Docs
linktitle: Tambahkan Tanda Air ke Halaman Tertentu di Word Docs
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke halaman tertentu di dokumen Word menggunakan GroupDocs untuk .NET. Lindungi konten Anda dengan mudah.
weight: 14
url: /id/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---

# Tambahkan Tanda Air ke Halaman Tertentu di Word Docs

## Perkenalan
Dokumen yang diberi watermark adalah aspek penting dalam keamanan dan pencitraan merek dokumen. Dalam tutorial ini, kita akan mempelajari cara menambahkan tanda air ke halaman tertentu di dokumen Word menggunakan GroupDocs.Watermark untuk .NET.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
- Pengetahuan dasar tentang pemrograman C#.
- Menginstal Visual Studio IDE.
- GroupDocs.Watermark untuk .NET diinstal di proyek Anda.

## Mengimpor Namespace
Sebelum mendalami kode, pastikan Anda mengimpor namespace yang diperlukan:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda akan ditempatkan di sini
}
```
## Langkah 2: Tambahkan Tanda Air
```csharp
// Tentukan teks dan gaya tanda air
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Tambahkan tanda air ke halaman terakhir
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Langkah 3: Simpan Dokumen
```csharp
// Simpan dokumen dengan tanda air
watermarker.Save(outputFileName);
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan tanda air ke halaman tertentu di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat melindungi dokumen Anda secara efektif dan menambahkan elemen pencitraan merek sesuai kebutuhan.
## FAQ
### Bisakah saya menyesuaikan teks dan gaya tanda air?
Ya, Anda dapat menyesuaikan teks, font, ukuran, warna, dan posisi tanda air sesuai kebutuhan Anda.
### Apakah GroupDocs.Watermark untuk .NET kompatibel dengan format dokumen lain?
Ya, GroupDocs.Watermark mendukung berbagai format dokumen, termasuk Word, Excel, PowerPoint, PDF, dan lainnya.
### Bisakah saya menambahkan beberapa tanda air ke satu dokumen?
Tentu saja, Anda dapat menambahkan beberapa tanda air dengan konten dan gaya berbeda ke dokumen yang sama.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Watermark untuk .NET?
 Ya, Anda dapat menjelajahi fitur GroupDocs.Watermark dengan uji coba gratis. Cukup kunjungi tautan yang disediakan untuk memulai[Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Watermark?
 Anda dapat menemukan sumber daya yang bermanfaat dan mendapatkan dukungan teknis dari[Di Sini](https://forum.groupdocs.com/c/watermark/19)forum GroupDocs.Watermark. Kunjungi tautan yang disediakan untuk bergabung dengan komunitas.