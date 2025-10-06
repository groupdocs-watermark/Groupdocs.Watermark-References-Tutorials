---
title: Penggunaan Jenis Bentuk di Word Docs
linktitle: Penggunaan Jenis Bentuk di Word Docs
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara memanipulasi bentuk di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Tutorial ini memberikan panduan untuk pemrosesan dokumen yang efisien.
weight: 37
url: /id/net/word-processing-watermarkings/shape-type-usage-word-docs/
type: docs
---
# Penggunaan Jenis Bentuk di Word Docs

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara memanfaatkan tipe bentuk di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Bentuk dalam dokumen Word dapat bervariasi, dan memahami cara memanipulasinya dapat menjadi sangat penting untuk berbagai tugas pemrosesan dokumen.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Watermark untuk .NET Library: Unduh dan instal perpustakaan GroupDocs.Watermark untuk .NET dari[tautan unduhan](https://releases.groupdocs.com/Watermark/net/).
2. Jalur Dokumen: Siapkan dokumen Word untuk diproses.
3. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai dengan dukungan kerangka .NET.

## Impor Namespace
Untuk memulai, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek Anda. Namespace ini akan memberikan akses ke kelas dan metode yang diperlukan untuk bekerja dengan dokumen Word.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Langkah 1: Muat Dokumen
Mulailah dengan memuat dokumen Word ke objek Watermarker. Pastikan untuk menentukan jalur dokumen dan opsi tambahan apa pun yang diperlukan selama proses pemuatan.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode pemrosesan dokumen ada di sini
}
```
## Langkah 2: Akses Konten Dokumen
 Akses konten dokumen Word yang dimuat menggunakan`GetContent<WordProcessingContent>()` metode. Ini akan memberikan akses ke bagian, paragraf, dan bentuk yang ada dalam dokumen.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Langkah 3: Iterasi Melalui Bagian dan Bentuk
Ulangi setiap bagian dan bentuk dalam dokumen untuk memeriksa dan memanipulasinya sesuai kebutuhan.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Kode manipulasi bentuk ada di sini
    }
}
```
## Langkah 4: Periksa Jenis Bentuk
Di dalam loop, periksa tipe bentuk tertentu menggunakan`ShapeType` Properti. Contoh ini menunjukkan cara mengidentifikasi dan menangani bentuk Bulat Sudut Diagonal.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Kode manipulasi bentuk khusus ada di sini
}
```
## Langkah 5: Memanipulasi Bentuk
Lakukan tindakan seperti menambahkan teks, mengubah pemformatan, atau menerapkan perubahan visual pada bentuk yang diidentifikasi.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Langkah 6: Simpan Dokumen
Setelah semua modifikasi yang diperlukan dilakukan, simpan dokumen dengan perubahan yang diterapkan ke file keluaran yang ditentukan.
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Memanipulasi bentuk dalam dokumen Word penting untuk berbagai tugas pemrosesan dokumen. Dengan GroupDocs.Watermark untuk .NET, Anda dapat dengan mudah mengidentifikasi, memodifikasi, dan memanipulasi bentuk untuk memenuhi kebutuhan Anda secara efisien.
## FAQ
### Bisakah GroupDocs.Watermark for .NET menangani format dokumen lain selain Word?
Ya, GroupDocs.Watermark untuk .NET mendukung berbagai format dokumen, termasuk PDF, Excel, PowerPoint, dan banyak lagi.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Watermark untuk .NET?
 Ya, Anda dapat mengakses versi uji coba gratis dari[halaman rilis](https://releases.groupdocs.com/).
### Apakah GroupDocs.Watermark untuk .NET menyediakan dukungan teknis?
 Ya, Anda dapat mencari bantuan dan terlibat dengan komunitas melalui[forum dukungan](https://forum.groupdocs.com/c/watermark/19).
### Bisakah saya menyesuaikan proses watermarking untuk persyaratan dokumen tertentu?
Tentu saja, GroupDocs.Watermark untuk .NET menawarkan opsi penyesuaian yang luas untuk menyesuaikan proses watermarking sesuai kebutuhan Anda.
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Watermark untuk .NET?
 Anda dapat memperoleh lisensi sementara dari[Halaman pembelian lisensi sementara](https://purchase.groupdocs.com/temporary-license/) untuk tujuan pengujian dan evaluasi.