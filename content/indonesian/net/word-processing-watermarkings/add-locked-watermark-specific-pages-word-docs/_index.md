---
title: Tambahkan Tanda Air Terkunci ke Halaman Tertentu di Dokumen Word
linktitle: Tambahkan Tanda Air Terkunci ke Halaman Tertentu di Dokumen Word
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air terkunci ke halaman tertentu di dokumen Word menggunakan GroupDocs.Watermark untuk .NET dengan panduan langkah demi langkah kami yang mudah.
weight: 12
url: /id/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# Tambahkan Tanda Air Terkunci ke Halaman Tertentu di Dokumen Word

## Perkenalan
Apakah Anda ingin menambahkan tanda air ke halaman tertentu di dokumen Word Anda, tetapi ingin halaman tersebut dikunci sehingga tidak mudah dihapus atau diedit? Anda berada di tempat yang tepat! Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan tanda air terkunci ke halaman tertentu di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Pustaka canggih ini memudahkan penerapan, pengelolaan, dan penyesuaian tanda air pada berbagai jenis dokumen. Baik Anda seorang pengembang atau hanya seseorang yang perlu mengamankan dokumennya, panduan ini akan memandu Anda melalui setiap langkah dengan cara yang mudah.
## Prasyarat
Sebelum kita masuk ke tutorialnya, pastikan Anda memiliki semua yang Anda butuhkan:
1.  GroupDocs.Watermark untuk .NET: Anda bisa[unduh](https://releases.groupdocs.com/Watermark/net/) versi terbaru.
2. Lingkungan Pengembangan: IDE seperti Visual Studio.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan sangat membantu.
4. Dokumen ke Tanda Air: Dokumen Word (.docx atau .doc) yang ingin Anda tambahkan tanda air.
## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda. Namespace ini menyediakan akses ke kelas dan metode yang diperlukan untuk bekerja dengan GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Kini setelah prasyaratnya terpenuhi dan namespace yang diperlukan telah diimpor, mari kita uraikan prosesnya langkah demi langkah.
## Langkah 1: Muat Dokumen Word
 Untuk memulainya, Anda perlu memuat dokumen Word yang ingin Anda tambahkan tanda air. Ini dapat dilakukan dengan menggunakan`Watermarker` kelas bersama dengan`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Lanjutkan ke langkah berikutnya
}
```
## Langkah 2: Buat Tanda Air Teks
Selanjutnya, buat tanda air teks. Anda dapat menyesuaikan teks, font, warna, dan properti lainnya sesuai kebutuhan Anda.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Langkah 3: Konfigurasikan Opsi Tanda Air
 Untuk menerapkan tanda air ke halaman tertentu dan menguncinya, konfigurasikan`WordProcessingWatermarkPagesOptions`Di sini, Anda menentukan nomor halaman tempat tanda air akan muncul dan mengatur opsi penguncian.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Tentukan halamannya
options.IsLocked = true; // Kunci tanda air
options.LockType = WordProcessingLockType.AllowOnlyComments; // Setel jenis kunci
// Untuk melindungi dengan kata sandi
// pilihan.Kata Sandi = "7654321";
```
## Langkah 4: Tambahkan Tanda Air ke Dokumen
Dengan tanda air dan opsi yang dikonfigurasi, kini Anda dapat menambahkan tanda air ke dokumen.
```csharp
watermarker.Add(watermark, options);
```
## Langkah 5: Simpan Dokumen
Terakhir, simpan dokumen dengan tanda air yang diterapkan. Pilih jalur keluaran yang sesuai dan simpan file.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Kesimpulan
Selamat! Anda telah berhasil menambahkan tanda air terkunci ke halaman tertentu di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Tutorial ini mencakup semua langkah penting mulai dari memuat dokumen hingga menyimpan file yang diberi watermark. Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa dokumen Anda diberi tanda air dengan aman, sehingga melindungi konten Anda dari pengeditan dan penggunaan yang tidak sah.
 Untuk informasi lebih lanjut, Anda dapat merujuk ke[Dokumentasi GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . Jika Anda memiliki pertanyaan atau memerlukan bantuan lebih lanjut, silakan kunjungi[forum dukungan](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Apa itu GroupDocs.Watermark untuk .NET?
GroupDocs.Watermark for .NET adalah perpustakaan canggih yang memungkinkan pengembang menambahkan tanda air ke berbagai jenis dokumen, termasuk Word, PDF, Excel, dan banyak lagi.
### Bisakah saya menerapkan tanda air ke beberapa halaman dalam satu dokumen?
 Ya, Anda dapat menentukan beberapa nomor halaman di`PageNumbers` array untuk menerapkan tanda air ke beberapa halaman.
### Bagaimana cara melindungi tanda air dengan kata sandi?
 Anda dapat melindungi tanda air dengan kata sandi dengan mengatur`Password` properti di`WordProcessingWatermarkPagesOptions`.
### Apakah mungkin untuk menyesuaikan tampilan tanda air?
Sangat! Anda dapat menyesuaikan teks, font, warna, ukuran, dan properti tanda air lainnya agar sesuai dengan kebutuhan Anda.
### Di mana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Watermark?
 Anda dapat memperoleh lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).