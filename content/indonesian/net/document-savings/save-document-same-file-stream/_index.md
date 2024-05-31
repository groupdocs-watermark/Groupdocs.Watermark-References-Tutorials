---
title: Simpan Dokumen ke File atau Aliran yang Sama
linktitle: Simpan Dokumen ke File atau Aliran yang Sama
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke dokumen menggunakan Groupdocs.Watermark untuk .NET. Panduan ini memberikan instruksi untuk memastikan perlindungan dan integritas dokumen.
type: docs
weight: 10
url: /id/net/document-savings/save-document-same-file-stream/
---
## Perkenalan
Di era digital saat ini, menambahkan tanda air ke dokumen menjadi hal yang penting untuk melindungi kekayaan intelektual dan memastikan integritas merek. Groupdocs.Watermark untuk .NET menawarkan solusi tangguh bagi pengembang yang ingin menyematkan tanda air ke dalam dokumen dengan lancar. Panduan komprehensif ini akan memandu Anda melalui langkah-langkah menyimpan dokumen dengan tanda air ke file atau aliran yang sama menggunakan Groupdocs.Watermark untuk .NET.
## Prasyarat
Sebelum mendalami tutorial, pastikan Anda memiliki hal berikut:
1. Lingkungan Pengembangan: Visual Studio diinstal pada mesin Anda.
2. .NET Framework: Pastikan Anda memiliki .NET Framework 4.0 atau lebih baru.
3.  Groupdocs.Watermark untuk .NET: Unduh dan instal versi terbaru dari[lokasi](https://releases.groupdocs.com/Watermark/net/).
4.  Lisensi: Dapatkan lisensi sementara atau permanen dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
## Impor Namespace
Untuk mulai menggunakan Groupdocs.Watermark di proyek .NET Anda, Anda perlu mengimpor namespace yang diperlukan:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Langkah 1: Siapkan Proyek Anda
Sebelum kita menambahkan tanda air ke dokumen kita, kita perlu menyiapkan proyek .NET kita. Begini caranya:
1. Buat Proyek Baru: Buka Visual Studio dan buat Aplikasi Konsol baru.
2. Tambahkan Referensi Groupdocs.Watermark: Klik kanan pada proyek di Solution Explorer, pilih "Kelola Paket NuGet," dan instal paket Groupdocs.Watermark.
## Langkah 2: Salin Dokumen ke Lokasi Baru
Untuk menghindari perubahan langsung pada dokumen asli, sebaiknya salin ke lokasi baru terlebih dahulu. Inilah cara Anda melakukannya:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Langkah 3: Inisialisasi Penanda Air
Sekarang setelah dokumen kita disalin, kita dapat menginisialisasi kelas Watermarker untuk menambahkan watermark kita:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Tanda air ada di sini
}
```
## Langkah 4: Buat dan Tambahkan Tanda Air Teks
Selanjutnya, kita membuat tanda air teks dan menambahkannya ke dokumen kita:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Langkah 5: Simpan Dokumen
Terakhir, simpan dokumen dengan tanda air yang diterapkan:
```csharp
watermarker.Save();
```
## Kesimpulan
Menambahkan tanda air ke dokumen Anda menggunakan Groupdocs untuk .NET sangatlah mudah dan efisien. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat melindungi dokumen Anda dan menjaga integritasnya dengan mudah. Untuk lebih jelasnya, Anda dapat merujuk ke[dokumentasi](https://reference.groupdocs.com/Watermark/net/).
## FAQ
### Bisakah saya menggunakan gambar sebagai tanda air dan bukan teks?
Ya, Groupdocs.Watermark memungkinkan Anda menggunakan gambar, bentuk, dan teks sebagai tanda air.
### Bagaimana cara menghapus tanda air dari dokumen?
 Anda dapat menghapus tanda air dengan mengakses koleksi tanda air di dokumen dan menggunakan`Remove` metode.
### Apakah mungkin untuk menyesuaikan tampilan tanda air?
Sangat. Anda dapat menyesuaikan font, ukuran, warna, dan posisi tanda air.
### Bisakah saya menerapkan banyak tanda air pada satu dokumen?
 Ya, Anda dapat menambahkan beberapa tanda air dengan memanggil`Add` metode beberapa kali dengan objek tanda air yang berbeda.
### Apakah Groupdocs.Watermark kompatibel dengan semua format dokumen?
Groupdocs.Watermark mendukung berbagai format dokumen termasuk PDF, DOCX, PPTX, dan banyak lainnya.