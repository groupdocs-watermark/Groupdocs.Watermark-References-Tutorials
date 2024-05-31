---
title: Muat Dokumen dari Aliran
linktitle: Muat Dokumen dari Aliran
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke dokumen menggunakan GroupDocs.Watermark untuk .NET dengan panduan ini. Sempurna untuk pengembang yang ingin meningkatkan keamanan dokumen.
type: docs
weight: 11
url: /id/net/document-loadings/load-document-from-stream/
---
## Perkenalan
Apakah Anda ingin menambahkan tanda air ke dokumen Anda dengan lancar menggunakan .NET? Tidak perlu mencari lagi! GroupDocs.Watermark for .NET adalah perpustakaan yang kuat dan mudah digunakan yang memungkinkan Anda mengelola tanda air dalam berbagai format dokumen. Baik Anda bekerja dengan PDF, dokumen Word, atau gambar, alat ini siap membantu Anda. Dalam tutorial ini, kami akan memandu Anda melalui proses memuat dokumen dari aliran dan menambahkan tanda air langkah demi langkah. Jadi, mari selami!
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan yang berikut:
1. Visual Studio: Visual Studio versi terbaru apa pun akan berfungsi dengan baik.
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework 4.0 atau lebih tinggi.
3.  GroupDocs.Watermark untuk .NET: Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
4. Pengetahuan Dasar C#: Keakraban dengan C# dan konsep pemrograman berorientasi objek akan sangat membantu.

## Impor Namespace
Untuk menggunakan GroupDocs.Watermark di proyek Anda, Anda harus mengimpor namespace yang diperlukan. Ini akan memungkinkan Anda mengakses fitur perpustakaan tanpa masalah apa pun.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Langkah 1: Menyiapkan Proyek Anda
Hal pertama yang pertama, Anda perlu menyiapkan proyek Anda di Visual Studio. Inilah cara Anda melakukannya:
1. Buat Proyek Baru: Buka Visual Studio dan buat proyek Aplikasi Konsol C# baru.
2.  Instal GroupDocs.Watermark: Instal perpustakaan GroupDocs.Watermark melalui NuGet Package Manager. Cukup cari`GroupDocs.Watermark` dan menginstalnya.
## Langkah 2: Tentukan Jalur Dokumen
Selanjutnya, Anda perlu menentukan jalur untuk dokumen Anda dan file keluaran tempat dokumen yang diberi tanda air akan disimpan.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"` dengan jalur sebenarnya dari dokumen yang ingin Anda beri tanda air dan`"Your Document Directory"` dengan direktori tempat Anda ingin menyimpan dokumen yang diberi watermark.
## Langkah 3: Muat Dokumen dari Aliran
Sekarang, mari kita memuat dokumen dari aliran. Ini melibatkan membuka dokumen sebagai aliran dan kemudian menggunakan`Watermarker` kelas dari perpustakaan GroupDocs.Watermark untuk mengelolanya.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Kode Anda untuk mengelola tanda air akan ditempatkan di sini
}
```
 Cuplikan kode ini memastikan bahwa dokumen dibuka sebagai aliran dan`Watermarker` kelas diinisialisasi dengan aliran ini. Itu`using` Pernyataan memastikan bahwa sumber daya dibuang dengan benar setelah digunakan.
## Langkah 4: Buat dan Tambahkan Tanda Air
Membuat tanda air sangatlah mudah dengan GroupDocs.Watermark. Dalam contoh ini, kita akan membuat tanda air teks sederhana.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Di sini, kami membuat a`TextWatermark` objek dengan teks "Uji tanda air" dan tentukan detail font. Kemudian, kami menambahkan tanda air ini ke dokumen menggunakan`Add` metode`Watermarker` kelas.
## Langkah 5: Simpan Dokumen yang diberi Watermark
Terakhir, simpan dokumen yang diberi watermark ke jalur keluaran yang ditentukan.
```csharp
watermarker.Save(outputFileName);
```
 Kode ini menyimpan dokumen dengan tanda air yang baru ditambahkan`outputFileName` jalur yang Anda tentukan sebelumnya.

## Kesimpulan
Selamat! Anda telah berhasil menambahkan tanda air ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET. Pustaka ini sangat memudahkan pengelolaan tanda air di berbagai format dokumen. Baik Anda perlu menambahkan teks, gambar, atau jenis tanda air lainnya, GroupDocs.Watermark memiliki alat yang Anda perlukan. Jangan lupa untuk memeriksa[dokumentasi](https://reference.groupdocs.com/Watermark/net/) untuk fitur lanjutan dan opsi penyesuaian lainnya.
## FAQ
### Jenis tanda air apa yang dapat saya tambahkan menggunakan GroupDocs.Watermark untuk .NET?
Anda dapat menambahkan tanda air teks, tanda air gambar, dan bahkan bentuk dan logo yang rumit. Perpustakaan mendukung berbagai pilihan penyesuaian.
### Bisakah saya menghapus tanda air dari dokumen menggunakan GroupDocs.Watermark?
Ya, GroupDocs.Watermark juga memungkinkan Anda menghapus tanda air yang ada dari dokumen.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Watermark?
 Ya, Anda dapat mengunduh uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana cara membeli lisensi untuk GroupDocs.Watermark?
Anda dapat membeli lisensi langsung dari[Situs web GroupDocs](https://purchase.groupdocs.com/buy).
### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Untuk dukungan, Anda dapat mengunjungi[Forum dukungan GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).