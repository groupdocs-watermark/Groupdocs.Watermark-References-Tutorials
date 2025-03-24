---
title: Ganti Teks Bentuk dengan Teks Terformat di Dokumen Word
linktitle: Ganti Teks Bentuk dengan Teks Terformat di Dokumen Word
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara mengganti teks bentuk dengan teks berformat di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Kemampuan mengedit dokumen Anda dengan mudah.
weight: 34
url: /id/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses mengganti teks bentuk dengan teks berformat di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Pustaka ini menyediakan fitur canggih untuk bekerja dengan tanda air, termasuk mengganti teks di dalam bentuk.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Watermark untuk .NET: Pastikan Anda telah menginstal dan mengatur GroupDocs.Watermark untuk .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. Jalur Dokumen: Anda harus memiliki jalur ke dokumen Word tempat Anda ingin mengganti teks.

## Impor Namespace
Sebelum menulis kode, impor namespace yang diperlukan:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
 Muat dokumen Word menggunakan`Watermarker` kelas:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda berlanjut di sini...
}
```
## Langkah 2: Dapatkan Konten dan Ganti Teks
Setelah dokumen dimuat, ambil konten dan ganti teks di dalam bentuk:
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
## Langkah 3: Simpan Dokumen
Setelah mengganti teks, simpan dokumen yang diubah:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Kesimpulan
Mengganti teks bentuk dengan teks berformat di dokumen Word menjadi mudah dengan GroupDocs untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat mengelola dan memanipulasi teks dalam dokumen Anda secara efisien.

## FAQ
### Bisakah saya mengganti teks di jenis dokumen lain menggunakan GroupDocs.Watermark untuk .NET?
Ya, GroupDocs mendukung berbagai format dokumen seperti PDF, Excel, PowerPoint, dan lainnya.
### Apakah GroupDocs.Watermark kompatibel dengan .NET Core?
Ya, GroupDocs.Watermark mendukung .NET Framework dan .NET Core.
### Apakah GroupDocs.Watermark menyediakan dukungan untuk menambahkan gambar sebagai tanda air?
Tentu saja, GroupDocs.Watermark memungkinkan Anda menambahkan tanda air teks dan gambar ke dokumen Anda.
### Bisakah saya menyesuaikan tampilan tanda air yang ditambahkan menggunakan GroupDocs.Watermark?
Ya, Anda memiliki kendali penuh atas tampilan, posisi, dan properti tanda air lainnya.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark untuk .NET?
 Ya, Anda dapat mengunduh uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).