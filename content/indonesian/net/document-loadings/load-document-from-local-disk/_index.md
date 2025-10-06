---
title: Muat Dokumen dari Disk Lokal
linktitle: Muat Dokumen dari Disk Lokal
second_title: GroupDocs.Tanda Air .NET API
description: Lindungi dan kelola dokumen Anda dengan Groupdocs untuk .NET. Ikuti panduan terperinci kami untuk menambahkan tanda air dengan lancar.
weight: 10
url: /id/net/document-loadings/load-document-from-local-disk/
type: docs
---
# Muat Dokumen dari Disk Lokal

## Perkenalan
Dokumen yang diberi watermark sangat penting di era digital saat ini untuk memastikan perlindungan konten, penegasan kepemilikan, dan kerahasiaan. Groupdocs.Watermark untuk .NET adalah perpustakaan canggih yang memungkinkan pengembang menambahkan, mencari, dan mengelola tanda air dalam berbagai format dokumen. Dalam tutorial ini, kami akan memandu proses penggunaan Groupdocs.Watermark untuk .NET guna menambahkan tanda air ke dokumen Anda dengan petunjuk langkah demi langkah yang mendetail.
## Prasyarat
Sebelum mendalami penerapannya, pastikan Anda memiliki hal berikut:
1. Visual Studio Terpasang: Anda memerlukan Visual Studio atau .NET IDE lain yang kompatibel.
2.  Groupdocs.Watermark untuk .NET: Unduh perpustakaan dari[tautan unduhan](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework 4.6.1 atau lebih tinggi.
4. Contoh Dokumen: Siapkan contoh dokumen untuk menguji proses watermarking.
## Impor Namespace
Untuk memulai, Anda harus mengimpor namespace yang diperlukan dalam proyek Anda. Ini penting untuk mengakses kelas dan metode yang diperlukan untuk watermarking.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen dari Disk Lokal
Pertama, Anda perlu memuat dokumen dari disk lokal Anda. Dokumen inilah yang akan Anda tambahkan tanda airnya.
Tentukan jalur dokumen yang ingin Anda beri tanda air.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Langkah 2: Inisialisasi Opsi Pemuatan
 Selanjutnya, inisialisasi opsi pemuatan. Misalnya, jika Anda bekerja dengan dokumen Word, Anda akan menggunakan`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Langkah 3: Buat dan Konfigurasikan Watermarker
 Sekarang, Anda akan membuat sebuah instance dari`Watermarker` kelas. Contoh ini akan digunakan untuk mengelola dan menerapkan tanda air pada dokumen Anda.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Blok ini akan berisi langkah lebih lanjut untuk menambahkan dan menyimpan tanda air
}
```
## Langkah 4: Buat Tanda Air
Buat tanda air teks. Tanda air ini dapat berisi teks apa pun yang Anda pilih. Di sini, kita akan menggunakan "Uji tanda air".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Langkah 5: Tambahkan Tanda Air ke Dokumen
Tambahkan tanda air yang dibuat ke dokumen menggunakan`Add` metode`Watermarker` kelas.
```csharp
watermarker.Add(watermark);
```
## Langkah 6: Simpan Dokumen yang diberi Watermark
Terakhir, simpan dokumen yang diberi watermark ke jalur yang ditentukan.
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Menambahkan tanda air ke dokumen Anda menggunakan Groupdocs untuk .NET sangatlah mudah dan efisien. Panduan ini telah memandu Anda melalui seluruh proses mulai dari menyiapkan lingkungan hingga menyimpan dokumen yang diberi tanda air. Dengan alat canggih ini, Anda dapat memastikan dokumen Anda terlindungi dan kekayaan intelektual Anda aman. 
 Untuk rincian lebih lanjut, periksa[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) , dan jika Anda mengalami masalah apa pun,[forum dukungan](https://forum.groupdocs.com/c/watermark/19) adalah tempat yang tepat untuk mendapatkan bantuan. 
## FAQ
### Bisakah saya menggunakan font khusus untuk tanda air?
Ya, Groupdocs mendukung font khusus. Anda dapat menentukan font apa pun yang diinstal pada sistem Anda.
### Jenis dokumen apa yang didukung?
Groupdocs.Watermark mendukung berbagai format dokumen termasuk Word, Excel, PDF, PowerPoint, dan banyak lagi.
### Bagaimana cara menghapus tanda air dari dokumen?
 Anda dapat menggunakan`Remove` metode yang disediakan oleh`Watermarker` kelas untuk menghilangkan tanda air.
### Apakah mungkin untuk menambahkan tanda air pada gambar?
 Ya, Anda dapat menambahkan tanda air gambar menggunakan`ImageWatermark` kelas.
### Bisakah saya mencoba Groupdocs.Watermark secara gratis?
 Tentu saja, Anda dapat mengunduh a[uji coba gratis](https://releases.groupdocs.com/) untuk mengevaluasi perpustakaan sebelum membeli.