---
title: Tambahkan Tanda Air ke Gambar Bagian di Dokumen Word
linktitle: Tambahkan Tanda Air ke Gambar Bagian di Dokumen Word
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke gambar di dokumen Word menggunakan Groupdocs untuk .NET. Ikuti panduan kami untuk perlindungan dokumen yang aman dan profesional.
weight: 16
url: /id/net/word-processing-watermarkings/add-watermark-section-images-word-docs/
---
## Perkenalan
Di dunia digital saat ini, melindungi dokumen Anda sangatlah penting. Menambahkan tanda air ke dokumen Word Anda adalah cara sederhana namun efektif untuk mengamankan konten Anda. Tutorial ini akan memandu Anda melalui proses menambahkan tanda air ke gambar bagian di dokumen Word menggunakan Groupdocs.Watermark untuk .NET. Baik Anda seorang pengembang yang ingin mengintegrasikan fitur ini ke dalam aplikasi Anda atau sekadar ingin melindungi dokumen Anda, panduan ini cocok untuk Anda.
## Prasyarat
Sebelum kita mendalami detailnya, pastikan Anda memiliki hal berikut:
1.  Groupdocs.Watermark untuk .NET: Unduh[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework di mesin Anda.
3. Dokumen Word: Siapkan dokumen Word yang ingin Anda tambahkan tanda air.
4. Lingkungan Pengembangan: Visual Studio atau IDE lain yang kompatibel dengan .NET.
5.  Lisensi Sementara: Mendapatkan a[izin sementara](https://purchase.groupdocs.com/temporary-license/) untuk Groupdocs.Tanda Air.
## Impor Namespace
Untuk memulai, impor namespace yang diperlukan ke dalam proyek Anda. Ini adalah langkah penting untuk memastikan bahwa semua fungsi Groupdocs.Watermark tersedia.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Sekarang, mari kita bagi prosesnya menjadi langkah-langkah yang dapat dikelola.
## Langkah 1: Menyiapkan Proyek Anda
Pertama, siapkan proyek Anda di IDE pilihan Anda. Buat proyek .NET baru dan instal perpustakaan Groupdocs.Watermark.
```bash
dotnet add package GroupDocs.Watermark
```
## Langkah 2: Muat Dokumen Word
Muat dokumen Word yang ingin Anda beri tanda air. Pastikan jalur ke dokumen Anda sudah benar.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda akan ditempatkan di sini
}
```
## Langkah 3: Buat Tanda Air
Buat tanda air teks yang akan Anda terapkan pada gambar di dokumen Word. Sesuaikan teks, font, ukuran, dan perataan sesuai kebutuhan Anda.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Langkah 4: Ambil Gambar dari Bagian Pertama
Akses konten dokumen Word dan temukan semua gambar di bagian pertama. Langkah ini penting karena mengidentifikasi gambar yang akan diberi tanda air.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WatermarkableImageCollection images = content.Sections[0].FindImages();
```
## Langkah 5: Terapkan Tanda Air ke Gambar
Ulangi setiap gambar di bagian pertama dan terapkan tanda air yang dibuat. Ini memastikan bahwa semua gambar di bagian tersebut terlindungi.
```csharp
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Langkah 6: Simpan Dokumen
Terakhir, simpan dokumen yang diberi watermark ke jalur yang ditentukan. Ini menyelesaikan proses menambahkan tanda air ke gambar bagian dalam dokumen Word.
```csharp
watermarker.Save(outputFileName);
```
## Kesimpulan
Menambahkan tanda air ke gambar dalam dokumen Word Anda adalah cara ampuh untuk melindungi konten Anda. Dengan Groupdocs.Watermark untuk .NET, proses ini mudah dan efisien. Ikuti langkah-langkah yang diuraikan dalam tutorial ini untuk memastikan dokumen Anda aman dan terlindungi dengan baik.
 Untuk dokumentasi lebih rinci, kunjungi[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) . Jika Anda memiliki pertanyaan atau memerlukan bantuan lebih lanjut, lihat[forum dukungan](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Bisakah saya menyesuaikan teks tanda air?
Ya, Anda dapat menyesuaikan teks tanda air, font, ukuran, perataan, dan rotasi sesuai kebutuhan Anda.
### Apakah mungkin menambahkan tanda air ke beberapa bagian?
Ya, Anda dapat mengulang setiap bagian dan menerapkan tanda air ke gambar di semua bagian.
### Bisakah saya menggunakan metode ini untuk format dokumen lain?
 Groupdocs.Tanda Air mendukung berbagai format dokumen. Periksalah[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) untuk lebih jelasnya.
### Bagaimana saya bisa mendapatkan lisensi sementara?
 Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Bagaimana jika saya mengalami masalah saat menggunakan Groupdocs.Watermark?
 Mengunjungi[forum dukungan](https://forum.groupdocs.com/c/watermark/19)untuk bantuan dengan masalah apa pun yang mungkin Anda temui.