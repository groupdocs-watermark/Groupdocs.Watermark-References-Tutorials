---
title: Tambahkan Tanda Air ke Gambar di PDF
linktitle: Tambahkan Tanda Air ke Gambar di PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke gambar dalam dokumen PDF menggunakan GroupDocs.Watermark untuk .NET dengan tutorial langkah demi langkah kami yang mendetail. Amankan PDF Anda dengan mudah.
weight: 19
url: /id/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Perkenalan
Menambahkan tanda air ke gambar dalam dokumen PDF penting untuk melindungi kekayaan intelektual Anda atau memastikan keaslian dokumen Anda. Menggunakan GroupDocs.Watermark untuk .NET, tugas ini dapat dilakukan secara efisien dan mudah. Tutorial ini akan memandu Anda melalui setiap langkah proses, mulai dari menyiapkan lingkungan, menambahkan tanda air, hingga menyimpan dokumen akhir. Ayo selami!
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1. Visual Studio: Instal Visual Studio, Lingkungan Pengembangan Terpadu (IDE) untuk aplikasi .NET.
2.  GroupDocs.Watermark untuk .NET: Unduh dan instal perpustakaan GroupDocs.Watermark untuk .NET dari[halaman rilis](https://releases.groupdocs.com/Watermark/net/).
3. Dokumen PDF: Siapkan dokumen PDF dengan gambar untuk menguji fungsi watermarking.
4.  Lisensi Sementara: Mendapatkan a[izin sementara](https://purchase.groupdocs.com/temporary-license/) jika Anda mengevaluasi produk.
## Impor Namespace
Pertama, pastikan Anda mengimpor namespace yang diperlukan ke proyek Anda. Ini akan mencakup namespace inti yang diperlukan untuk bekerja dengan dokumen PDF dan tanda air.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Siapkan Jalur Dokumen dan Direktori Keluaran
Untuk memulai, tentukan jalur untuk dokumen masukan dan direktori keluaran tempat dokumen yang diberi tanda air akan disimpan. Langkah ini penting untuk memastikan bahwa program Anda mengetahui di mana menemukan dokumen sumber dan di mana menyimpan file yang diproses.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Langkah 2: Muat Dokumen PDF
 Selanjutnya, Anda perlu memuat dokumen PDF menggunakan`PdfLoadOptions`. Kelas ini memungkinkan Anda menentukan opsi untuk memuat PDF, seperti perlindungan kata sandi jika diperlukan.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda untuk watermarking akan ditempatkan di sini
}
```
## Langkah 3: Buat Tanda Air
Sekarang, inisialisasi tanda air. Dalam contoh ini, kami membuat tanda air teks bertuliskan "Gambar yang dilindungi". Sesuaikan font, perataan, rotasi, dan penskalaan sesuai kebutuhan Anda.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Langkah 4: Akses Konten PDF
Ambil konten dokumen PDF. Secara khusus, kita perlu mengakses gambar di dalam PDF. Di sini, kami berfokus pada halaman pertama, namun Anda dapat memperluasnya ke halaman lain sesuai kebutuhan.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Dapatkan semua gambar dari halaman pertama
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Langkah 5: Terapkan Tanda Air ke Gambar
Ulangi setiap gambar yang ditemukan di halaman pertama dan terapkan tanda air. Ini memastikan bahwa semua gambar pada halaman tertentu akan diberi tanda air.
```csharp
// Tambahkan tanda air ke semua gambar yang ditemukan
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Langkah 6: Simpan Dokumen yang diberi Watermark
Terakhir, simpan PDF yang diberi watermark ke direktori keluaran yang ditentukan. Langkah ini menyelesaikan proses dengan menulis perubahan pada file baru.
```csharp
watermarker.Save(outputFileName);
```
## Kesimpulan
Dan itu dia! Menambahkan tanda air ke gambar dalam PDF menggunakan GroupDocs untuk .NET adalah proses mudah yang dapat meningkatkan keamanan dan keaslian dokumen Anda. Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa kekayaan intelektual Anda terlindungi dan dokumen Anda aman.
## FAQ
### Apa itu GroupDocs.Watermark untuk .NET?
GroupDocs.Watermark for .NET adalah perpustakaan komprehensif yang memungkinkan pengembang menambahkan, mencari, dan menghapus tanda air dalam berbagai format dokumen, termasuk PDF.
### Bisakah saya menambahkan tanda air teks dan gambar menggunakan GroupDocs.Watermark?
Ya, GroupDocs.Watermark mendukung tanda air teks dan gambar, memberikan fleksibilitas untuk berbagai jenis kebutuhan tanda air.
### Apakah mungkin memberi tanda air pada banyak halaman dalam PDF?
Sangat! Anda dapat menelusuri setiap halaman dalam PDF dan menerapkan tanda air pada gambar di setiap halaman.
### Apakah saya memerlukan lisensi untuk menggunakan GroupDocs.Watermark untuk .NET?
 Ya, lisensi diperlukan. Anda dapat memperoleh a[izin sementara](https://purchase.groupdocs.com/temporary-license/) untuk tujuan evaluasi.
### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang GroupDocs.Watermark untuk .NET?
 Anda dapat menemukan dokumentasi lengkap di[Halaman dokumentasi GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).