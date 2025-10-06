---
title: Rasterisasi Dokumen PDF
linktitle: Rasterisasi Dokumen PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara melakukan rasterisasi dokumen PDF menggunakan GroupDocs.Watermark untuk .NET. Tingkatkan keamanan dokumen dan daya tarik visual dengan mudah.
weight: 27
url: /id/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# Rasterisasi Dokumen PDF

## Perkenalan
Dalam bidang manajemen dan manipulasi dokumen, GroupDocs.Watermark untuk .NET berdiri sebagai alat yang ampuh, menawarkan kemampuan canggih untuk menambah, menghapus, dan mencari tanda air dalam berbagai format dokumen. Baik itu melindungi dokumen Anda dengan pemberitahuan hak cipta, menambahkan logo perusahaan untuk pencitraan merek, atau sekadar memberi anotasi pada dokumen dengan stempel, GroupDocs.Watermark menyederhanakan proses dengan API intuitif dan rangkaian fitur ekstensif.
## Prasyarat
Sebelum terjun ke dunia watermarking dengan GroupDocs.Watermark untuk .NET, pastikan Anda memiliki prasyarat berikut:
### 1. Instal .NET Framework
Pastikan Anda telah menginstal .NET Framework di mesin pengembangan Anda. Anda dapat mengunduhnya dari situs web Microsoft atau menggunakan manajer paket pilihan Anda.
#### Langkah 1: Unduh .NET Framework
Kunjungi halaman unduh Microsoft .NET Framework.
#### Langkah 2: Instal .NET Framework
Ikuti petunjuk instalasi yang disediakan di halaman download untuk menginstal .NET Framework di sistem Anda.
### 2. Dapatkan Lisensi GroupDocs.Watermark
Untuk memanfaatkan kemampuan penuh GroupDocs.Watermark, Anda memerlukan lisensi yang valid. Anda dapat membeli lisensi atau memperoleh lisensi sementara untuk tujuan evaluasi.
#### Langkah 1: Dapatkan Lisensi
Kunjungi halaman pembelian GroupDocs.Watermark.
#### Langkah 2: Beli atau Dapatkan Lisensi Sementara
Pilih opsi lisensi yang sesuai berdasarkan kebutuhan Anda—beli lisensi untuk penggunaan berkelanjutan atau dapatkan lisensi sementara untuk tujuan evaluasi.

## Impor Namespace
Sebelum Anda mulai memberi watermark pada dokumen Anda, pastikan untuk mengimpor namespace yang diperlukan untuk mengakses fungsionalitas GroupDocs dengan lancar.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Sekarang setelah semuanya siap, mari selami rasterisasi dokumen PDF menggunakan GroupDocs.Watermark untuk .NET. Rasterisasi mengubah setiap halaman dokumen PDF menjadi format gambar raster, seperti PNG.
## Langkah 1: Inisialisasi Variabel
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Pastikan Anda mengganti "Jalur Dokumen Anda" dan "Direktori Dokumen Anda" dengan jalur sebenarnya ke dokumen PDF Anda dan direktori keluaran yang diinginkan.
## Langkah 2: Muat Dokumen dan Tambahkan Tanda Air
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Inisialisasi tanda air gambar atau teks
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Tambahkan tanda air jenis apa pun terlebih dahulu
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasterisasi semua halaman
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Konten semua halaman diganti dengan gambar raster
    watermarker.Save(outputFileName);
}
```
Pada langkah ini, kita memuat dokumen PDF dan menginisialisasi tanda air teks dengan properti tertentu seperti teks, font, perataan, sudut rotasi, jenis ukuran, faktor skala, dan opacity. Kemudian, kami menambahkan tanda air ke dokumen tersebut. Selanjutnya, kami mengambil konten dokumen PDF dan melakukan rasterisasi semua halaman ke format PNG dengan resolusi 100 DPI. Terakhir, kami menyimpan dokumen yang dimodifikasi dengan konten raster.

## Kesimpulan
GroupDocs.Watermark for .NET menawarkan solusi komprehensif untuk menambahkan tanda air ke berbagai format dokumen dengan mudah. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat melakukan rasterisasi dokumen PDF secara efektif dan meningkatkan keamanan serta daya tarik visualnya.
## FAQ
### Apakah GroupDocs.Watermark kompatibel dengan format dokumen lain selain PDF?
Ya, GroupDocs.Watermark mendukung berbagai format dokumen, termasuk Microsoft Word, Excel, PowerPoint, Visio, Outlook, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan tanda air yang ditambahkan menggunakan GroupDocs.Watermark?
Sangat! GroupDocs.Watermark menyediakan opsi ekstensif untuk menyesuaikan properti tanda air seperti teks, font, warna, ukuran, opacity, rotasi, dan posisi.
### Apakah GroupDocs.Watermark menawarkan dukungan untuk pemrosesan batch?
Ya, Anda dapat dengan mudah memproses banyak dokumen dalam mode batch menggunakan GroupDocs, menghemat waktu dan tenaga dalam memberi watermark pada kumpulan file besar.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark?
Ya, Anda dapat mengunduh GroupDocs.Watermark versi uji coba gratis dari situs web untuk mengevaluasi fitur-fiturnya sebelum melakukan pembelian.
### Bagaimana saya bisa mendapatkan bantuan jika saya mengalami masalah atau memiliki pertanyaan tentang GroupDocs.Watermark?
Anda dapat mengunjungi forum GroupDocs.Watermark untuk mencari dukungan dari komunitas atau menghubungi tim dukungan GroupDocs untuk mendapatkan bantuan.