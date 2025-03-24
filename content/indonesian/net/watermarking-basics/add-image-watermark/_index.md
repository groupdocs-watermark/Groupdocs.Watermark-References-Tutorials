---
title: Tambahkan Tanda Air Gambar
linktitle: Tambahkan Tanda Air Gambar
second_title: GroupDocs.Tanda Air .NET API
description: Tambahkan tanda air gambar dengan mudah ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET. Lindungi kekayaan intelektual Anda dengan mudah.
weight: 10
url: /id/net/watermarking-basics/add-image-watermark/
---

# Tambahkan Tanda Air Gambar

## Perkenalan
Dalam tutorial ini, kita akan mempelajari proses menambahkan tanda air gambar ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET. Dokumen yang diberi watermark sangat penting untuk melindungi kekayaan intelektual dan branding. Dengan GroupDocs.Watermark untuk .NET, Anda dapat dengan mudah mengintegrasikan tanda air ke dalam berbagai format dokumen seperti Word, Excel, PowerPoint, PDF, dan banyak lagi.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Watermark untuk .NET Library: Unduh dan instal perpustakaan GroupDocs.Watermark untuk .NET dari[situs web](https://releases.groupdocs.com/Watermark/net/).
2. Dokumen: Siapkan dokumen yang ingin Anda tambahkan tanda airnya.
3. Gambar untuk Tanda Air: Siapkan file gambar yang ingin Anda gunakan sebagai tanda air.

## Impor Namespace
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Langkah 1: Inisialisasi Jalur Dokumen dan Direktori Keluaran
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"`dengan jalur absolut atau relatif ke dokumen Anda dan`"Your Document Directory"` dengan direktori tempat Anda ingin menyimpan dokumen yang diberi watermark.
## Langkah 2: Buka Aliran Dokumen dan Inisialisasi Penanda Air
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Proses watermarking akan dilakukan di sini
    }
}
```
 Buka aliran dokumen menggunakan`FileStream` dan inisialisasi`Watermarker` obyek.
## Langkah 3: Tambahkan Tanda Air Gambar
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Buat sebuah`ImageWatermark` objek dengan jalur ke file gambar yang ingin Anda gunakan sebagai tanda air. Atur perataan tanda air secara horizontal dan vertikal.
## Langkah 4: Simpan Dokumen yang diberi Watermark
```csharp
watermarker.Save(outputFileName);
```
Simpan dokumen yang diberi watermark ke direktori keluaran yang ditentukan dengan nama file yang diinginkan.

## Kesimpulan
Kesimpulannya, GroupDocs.Watermark untuk .NET memberikan solusi komprehensif untuk menambahkan tanda air ke berbagai format dokumen dengan mudah. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat menambahkan tanda air gambar ke dokumen Anda secara efisien dan melindungi kekayaan intelektual Anda.
## FAQ
### Bisakah saya menambahkan tanda air teks menggunakan GroupDocs.Watermark untuk .NET?
Ya, GroupDocs.Watermark untuk .NET mendukung penambahan tanda air gambar dan teks ke dokumen.
### Apakah GroupDocs.Watermark untuk .NET kompatibel dengan format dokumen berbeda?
Tentu saja, GroupDocs.Watermark untuk .NET mendukung berbagai format dokumen termasuk Word, Excel, PowerPoint, PDF, dan banyak lagi.
### Apakah GroupDocs.Watermark untuk .NET menyediakan opsi penyesuaian untuk tanda air?
Ya, Anda dapat menyesuaikan berbagai aspek tanda air seperti posisi, ukuran, opasitas, dan rotasi.
### Bisakah saya menghapus tanda air dari dokumen menggunakan GroupDocs.Watermark untuk .NET?
Ya, GroupDocs.Watermark untuk .NET menawarkan fungsionalitas untuk mendeteksi dan menghapus tanda air dari dokumen.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark untuk .NET?
 Ya, Anda dapat memanfaatkan versi uji coba gratis dari situs web untuk menjelajahi fitur-fiturnya sebelum membeli[Di Sini](https://releases.groupdocs.com/).