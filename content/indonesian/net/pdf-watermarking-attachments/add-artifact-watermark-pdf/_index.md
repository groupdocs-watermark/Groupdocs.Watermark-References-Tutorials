---
title: Tambahkan Tanda Air Artefak ke PDF
linktitle: Tambahkan Tanda Air Artefak ke PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air artefak ke file PDF dengan mudah menggunakan Groupdocs.Watermark untuk .NET. Lindungi dokumen Anda dengan mudah.
weight: 11
url: /id/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Perkenalan
Menambahkan tanda air ke file PDF adalah aspek penting dalam pengelolaan dokumen, terutama dalam hal melindungi kekayaan intelektual atau dokumen merek. Groupdocs.Watermark untuk .NET memberikan solusi tangguh untuk menambahkan tanda air ke file PDF dengan mudah. Dalam tutorial ini, kita akan memandu proses menambahkan tanda air artefak ke file PDF langkah demi langkah.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  Groupdocs.Watermark untuk .NET: Unduh dan instal Groupdocs.Watermark untuk .NET dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET.
3. Dokumen PDF: Siapkan dokumen PDF yang ingin Anda tambahkan tanda air.
4. Direktori Output: Buat direktori untuk menyimpan file PDF yang diberi watermark.

## Mengimpor Namespace
Untuk memulainya, impor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Langkah 2: Tentukan Opsi Tanda Air
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Langkah 3: Tambahkan Tanda Air Teks
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Langkah 4: Tambahkan Tanda Air Gambar
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Langkah 5: Simpan PDF yang diberi Watermark
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan tanda air artefak ke file PDF menggunakan Groupdocs.Watermark untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengintegrasikan fungsi watermarking ke dalam aplikasi .NET Anda, memastikan keamanan dan integritas dokumen Anda.
## FAQ
### Bisakah saya menyesuaikan tampilan tanda air teks?
Ya, Anda dapat menyesuaikan berbagai aspek seperti font, ukuran, warna, dan perataan tanda air teks sesuai preferensi Anda.
### Apakah Groupdocs.Watermark mendukung penambahan tanda air ke format dokumen lain?
Ya, Groupdocs.Watermark mendukung penambahan tanda air ke berbagai format dokumen termasuk Word, Excel, PowerPoint, dan banyak lagi.
### Apakah ada versi uji coba yang tersedia untuk Groupdocs.Watermark untuk .NET?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk masalah atau pertanyaan apa pun yang terkait dengan Groupdocs.Watermark?
 Anda bisa mendapatkan dukungan dari forum komunitas Groupdocs[Di Sini](https://forum.groupdocs.com/c/watermark/19).
### Bisakah saya menggunakan Groupdocs.Watermark untuk tujuan komersial?
Ya, Anda dapat membeli lisensi untuk penggunaan komersial dari[Di Sini](https://purchase.groupdocs.com/buy).