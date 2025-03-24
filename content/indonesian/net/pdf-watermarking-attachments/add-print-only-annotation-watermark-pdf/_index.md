---
title: Tambahkan Tanda Air Anotasi Cetak Saja ke PDF
linktitle: Tambahkan Tanda Air Anotasi Cetak Saja ke PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air anotasi khusus cetak ke PDF menggunakan GroupDocs.Watermark untuk .NET. Tingkatkan keamanan dokumen dan branding dengan mudah.
weight: 13
url: /id/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Tambahkan Tanda Air Anotasi Cetak Saja ke PDF

## Perkenalan
Dalam tutorial ini, kita akan mempelajari proses menambahkan tanda air anotasi khusus cetak ke PDF menggunakan GroupDocs.Watermark untuk .NET. Pemberian watermark pada dokumen adalah aspek penting dalam keamanan dan pencitraan merek dokumen, dan GroupDocs.Watermark memberikan solusi sempurna bagi pengembang .NET untuk mencapai hal ini.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
- Pemahaman dasar bahasa pemrograman C#.
- Visual Studio diinstal pada mesin Anda.
- GroupDocs.Watermark untuk perpustakaan .NET diinstal di proyek Anda.

## Impor Namespace
Untuk memulai, pastikan Anda mengimpor namespace yang diperlukan:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
 Pertama, Anda perlu memuat dokumen PDF yang ingin Anda beri tanda air. Mengganti`"Your Document Path"` dengan jalur ke file PDF Anda dan`"Your Document Directory"` dengan direktori tempat Anda ingin menyimpan file output.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode watermarking akan ditambahkan di sini
}
```
## Langkah 2: Tambahkan Tanda Air
Selanjutnya buat objek text watermark dengan teks dan font yang diinginkan. Mengatur`isPrintOnly` ke`true` untuk memastikan bahwa tanda air hanya terlihat saat dokumen dicetak, bukan dalam mode tampilan.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Langkah 3: Konfigurasikan Opsi Tanda Air
Tentukan opsi untuk tanda air, seperti indeks halaman tempat tanda air harus ditambahkan dan tentukan sebagai anotasi hanya cetak.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Langkah 4: Terapkan Tanda Air
Tambahkan tanda air ke dokumen menggunakan opsi yang ditentukan dan simpan file keluaran.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menambahkan tanda air anotasi khusus cetak ke dokumen PDF menggunakan GroupDocs.Watermark untuk .NET. Hal ini memungkinkan pengembang untuk meningkatkan keamanan dokumen dan branding dengan mudah.
## FAQ
### Apakah GroupDocs.Watermark kompatibel dengan format dokumen lain selain PDF?
Ya, GroupDocs mendukung berbagai format dokumen seperti Word, Excel, PowerPoint, dan gambar.
### Bisakah saya menyesuaikan tampilan tanda air?
Tentu saja, GroupDocs.Watermark menyediakan opsi ekstensif untuk menyesuaikan teks, font, warna, ukuran, dan posisi tanda air.
### Apakah GroupDocs.Watermark menawarkan kemampuan pemrosesan batch?
Tentu saja, pengembang dapat memberi tanda air pada beberapa dokumen secara bersamaan menggunakan fitur pemrosesan batch.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark?
Ya, Anda dapat mengakses GroupDocs.Watermark versi uji coba gratis dari tautan yang disediakan.
### Bagaimana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Watermark?
Anda dapat mencari bantuan teknis dari forum GroupDocs.Watermark yang tersedia di tautan dukungan yang disediakan.