---
title: Ekstrak Semua Lampiran dari PDF
linktitle: Ekstrak Semua Lampiran dari PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara mengekstrak semua lampiran dari PDF menggunakan Groupdocs.Watermark untuk .NET. Ikuti panduan langkah demi langkah kami untuk proses ekstraksi yang lancar.
weight: 22
url: /id/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
---
## Perkenalan
Apakah Anda ingin mengekstrak lampiran dari dokumen PDF dengan mudah? Nah, Anda berada di tempat yang tepat! Dalam tutorial komprehensif ini, kami akan memandu Anda melalui proses mengekstraksi semua lampiran dari PDF menggunakan Groupdocs.Watermark untuk .NET. Pustaka yang kuat ini memungkinkan pengembang untuk mengelola tanda air dalam berbagai format dokumen, tetapi juga mencakup kemampuan yang kuat untuk mengekstraksi file yang tertanam. Baik Anda seorang pengembang berpengalaman atau baru memulai, panduan langkah demi langkah ini akan membuat prosesnya menjadi mudah.
## Prasyarat
Sebelum mendalami kodenya, mari kita bahas dasar-dasar yang Anda perlukan untuk memulai. Berikut daftar periksa singkat untuk memastikan Anda siap:
1. Lingkungan .NET: Pastikan Anda telah menyiapkan lingkungan pengembangan .NET. Anda dapat menggunakan Visual Studio atau .NET IDE lainnya pilihan Anda.
2.  Groupdocs.Watermark for .NET: Unduh dan instal versi terbaru Groupdocs.Watermark for .NET dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
3. Keterampilan Pengembangan: Pemahaman dasar pemrograman C# dan keakraban dengan perpustakaan .NET.
4. Contoh Dokumen PDF: Miliki contoh dokumen PDF dengan lampiran yang dapat Anda gunakan untuk pengujian.
## Impor Namespace
Sebelum memulai coding, Anda harus mengimpor namespace yang diperlukan. Ini membantu mengatur kode Anda dan memberi Anda akses ke kelas dan metode yang akan Anda gunakan.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Langkah 1: Siapkan Proyek Anda
Hal pertama yang pertama, mari siapkan proyek Anda. Buka lingkungan pengembangan .NET Anda dan buat aplikasi konsol baru.
### Buat Proyek Baru
1. Buka Visual Studio.
2. Pilih "Buat proyek baru".
3. Pilih "Aplikasi Konsol (.NET Core)" atau ".NET Framework" tergantung pada preferensi Anda.
4. Beri nama proyek Anda dan klik "Buat".
### Tambahkan Groupdocs.Watermark untuk .NET
1. Klik kanan pada proyek Anda di Solution Explorer.
2. Pilih "Kelola Paket NuGet."
3. Cari "Groupdocs.Watermark" dan instal versi terbaru.
## Langkah 2: Tentukan Jalur Anda
Selanjutnya, Anda perlu menentukan jalur untuk dokumen dan direktori keluaran Anda. Di sinilah PDF Anda dan lampiran yang diekstraksi akan disimpan.

 Di dalam kamu`Program.cs` file, tambahkan kode berikut untuk menentukan jalur Anda:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"` Dan`"Your Document Directory"` dengan jalur sebenarnya di sistem Anda.
## Langkah 3: Muat Dokumen PDF Anda
 Sekarang, mari muat dokumen PDF Anda menggunakan Groupdocs.Watermark. Langkah ini melibatkan pembuatan opsi beban dan inisialisasi`Watermarker` kelas.
### Buat Opsi Muat
 Pertama, buat sebuah instance dari`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### Inisialisasi Penanda Air
 Selanjutnya, gunakan`Watermarker` kelas untuk memuat dokumen Anda:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda akan ditempatkan di sini
}
```
## Langkah 4: Ekstrak Lampiran
Dengan dokumen Anda dimuat, saatnya mengekstrak lampiran. Anda akan menggunakan`PdfContent` kelas untuk mengakses lampiran dan kemudian menyimpannya ke direktori keluaran yang Anda tentukan.
### Dapatkan Konten PDF
 Di dalam`using` blok, dapatkan konten PDF:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Ulangi Lampiran
Ulangi setiap lampiran dalam PDF:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // Simpan file terlampir pada disk
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
Kode ini mengekstrak setiap lampiran dan menyimpannya ke direktori keluaran Anda. Itu juga mencetak beberapa informasi dasar tentang setiap lampiran ke konsol.
## Kesimpulan
Dan itu dia! Anda telah berhasil mengekstrak lampiran dari PDF menggunakan Groupdocs.Watermark untuk .NET. Tutorial ini memandu Anda dalam menyiapkan proyek, memuat dokumen, dan mengekstrak lampiran langkah demi langkah. Dengan keterampilan ini, kini Anda dapat mengelola dan memanipulasi lampiran PDF di aplikasi .NET Anda dengan mudah.
## FAQ
### Apa itu Groupdocs.Watermark untuk .NET?
Groupdocs.Watermark for .NET adalah perpustakaan lengkap untuk menambah, menghapus, dan mengelola tanda air dalam berbagai format dokumen, termasuk PDF. Ia juga menawarkan kemampuan untuk mengekstraksi file yang tertanam.
### Bisakah saya mengekstrak jenis file lain yang tertanam dalam PDF?
Ya, Groupdocs.Watermark untuk .NET memungkinkan Anda mengekstrak semua jenis file yang tertanam dalam PDF, bukan hanya lampiran.
### Apakah ada uji coba gratis yang tersedia?
 Ya, Anda dapat mengunduh uji coba gratis Groupdocs.Watermark untuk .NET dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Anda bisa mendapatkan dukungan dengan mengunjungi[Groupdocs.Forum dukungan Watermark](https://forum.groupdocs.com/c/watermark/19).
### Apakah saya memerlukan lisensi untuk menggunakan Groupdocs.Watermark untuk .NET?
 Ya, Anda memerlukan lisensi untuk menggunakan perpustakaan dalam produksi. Anda dapat membeli lisensi[Di Sini](https://purchase.groupdocs.com/buy) atau mendapatkan izin sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).