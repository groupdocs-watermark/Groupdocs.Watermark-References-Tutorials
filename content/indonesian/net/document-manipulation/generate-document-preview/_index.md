---
title: Hasilkan Pratinjau Dokumen
linktitle: Hasilkan Pratinjau Dokumen
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara membuat pratinjau dokumen menggunakan GroupDocs.Watermark untuk .NET dengan panduan ini. Tingkatkan keamanan dan pengelolaan dokumen Anda dengan mudah.
type: docs
weight: 10
url: /id/net/document-manipulation/generate-document-preview/
---
## Perkenalan
Dalam dunia pengelolaan dokumen digital, watermarking memegang peranan penting dalam menjamin keamanan dan keaslian dokumen. GroupDocs.Watermark for .NET adalah alat canggih yang memungkinkan pengembang menambahkan tanda air ke dokumen dengan mudah. Dalam tutorial ini, kami akan memandu Anda melalui proses pembuatan pratinjau dokumen menggunakan GroupDocs.Watermark untuk .NET. Baik Anda seorang pengembang berpengalaman atau baru memulai, panduan ini akan memberi Anda proses langkah demi langkah yang komprehensif untuk mencapai tujuan Anda.
## Prasyarat
Sebelum mendalami penerapannya, pastikan Anda memiliki semua yang diperlukan untuk memulai:
- Pemahaman dasar tentang kerangka C# dan .NET.
- Visual Studio diinstal pada mesin Anda.
- GroupDocs.Watermark untuk perpustakaan .NET. Kamu bisa[Unduh di sini](https://releases.groupdocs.com/Watermark/net/).
-  Lisensi yang valid untuk GroupDocs.Watermark. Anda bisa membelinya[Di Sini](https://purchase.groupdocs.com/buy) atau memperoleh a[izin sementara](https://purchase.groupdocs.com/temporary-license/) untuk tujuan evaluasi.
## Impor Namespace
Untuk mulai menggunakan GroupDocs.Watermark di proyek Anda, Anda harus mengimpor namespace yang diperlukan. Ini dapat dilakukan dengan menambahkan arahan penggunaan berikut ke kode Anda:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Namespace ini akan memberikan akses ke kelas dan metode yang diperlukan untuk menandai air dan menghasilkan pratinjau dokumen.

Mari kita uraikan proses pembuatan pratinjau dokumen menjadi langkah-langkah sederhana dan mudah diikuti.
## Langkah 1: Siapkan Proyek Anda
Hal pertama yang pertama, siapkan proyek .NET Anda di Visual Studio. Jika Anda belum memiliki proyek, buat proyek baru dengan mengikuti langkah-langkah berikut:
1. Buka Visual Studio.
2. Klik "Buat proyek baru".
3. Pilih "Aplikasi Konsol (.NET Core)" dan klik "Berikutnya".
4. Beri nama proyek Anda dan pilih lokasi untuk menyimpannya, lalu klik "Buat".
## Langkah 2: Instal GroupDocs.Watermark untuk .NET
Untuk menggunakan GroupDocs.Watermark di proyek Anda, Anda perlu menginstal perpustakaan. Ini dapat dilakukan dengan menggunakan NuGet Package Manager:
1. Klik kanan pada proyek Anda di Solution Explorer.
2. Pilih "Kelola Paket NuGet."
3. Cari "GroupDocs.Watermark" di tab Telusuri.
4. Klik "Instal" untuk menambahkan perpustakaan ke proyek Anda.
Alternatifnya, Anda dapat menginstalnya melalui Package Manager Console:
```powershell
Install-Package GroupDocs.Watermark
```
## Langkah 3: Tentukan Jalur Dokumen dan Direktori Keluaran
Sebelum membuat pratinjau, Anda perlu menentukan jalur dokumen yang ingin Anda pratinjau dan direktori tempat gambar pratinjau akan disimpan:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Ganti "Jalur Dokumen Anda" dengan jalur ke dokumen Anda dan "Direktori Dokumen Anda" dengan direktori tempat Anda ingin menyimpan gambar pratinjau.
## Langkah 4: Inisialisasi Objek Watermarker
Buat sebuah instance dari`Watermarker` kelas dengan meneruskan jalur dokumen ke konstruktornya. Objek ini akan digunakan untuk melakukan semua operasi watermarking:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Kode Anda di sini
}
```
## Langkah 5: Buat Metode Delegasi untuk Penanganan Aliran
Untuk menghasilkan pratinjau, Anda perlu menentukan metode delegasi untuk membuat dan merilis streaming. Metode berikut akan menangani pembuatan dan pelepasan aliran untuk setiap halaman dokumen:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 Itu`createPageStreamDelegate` metode membuat aliran untuk setiap halaman dokumen, sedangkan`releasePageStreamDelegate` metode menutup aliran setelah pratinjau dibuat.
## Langkah 6: Konfigurasikan Opsi Pratinjau
 Selanjutnya, konfigurasikan opsi pratinjau dengan membuat instance dari`PreviewOptions` kelas. Tentukan metode delegasi dan atur format pratinjau ke PNG. Anda juga dapat menentukan halaman mana yang akan disertakan dalam pratinjau:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
Dalam contoh ini, kami membuat pratinjau untuk dua halaman pertama dokumen.
## Langkah 7: Hasilkan Pratinjau Dokumen
 Terakhir, hubungi`GeneratePreview` metode pada`Watermarker`objek, meneruskan konfigurasi`PreviewOptions`. Ini akan menghasilkan gambar pratinjau dan menyimpannya ke direktori yang ditentukan:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Kesimpulan
Membuat pratinjau dokumen menggunakan GroupDocs.Watermark untuk .NET adalah proses mudah yang dapat diselesaikan hanya dengan beberapa baris kode. Dengan mengikuti langkah-langkah yang diuraikan dalam panduan ini, Anda dapat dengan mudah menyiapkan proyek, mengonfigurasi opsi yang diperlukan, dan membuat pratinjau untuk dokumen Anda. Pustaka canggih ini tidak hanya menyederhanakan proses penandaan air tetapi juga menyediakan fitur canggih untuk mengelola dan memanipulasi tanda air.
 Jika Anda memiliki pertanyaan atau memerlukan bantuan lebih lanjut, jangan ragu untuk mengunjungi[GroupDocs.Forum Dukungan Tanda Air](https://forum.groupdocs.com/c/watermark/19) atau rujuk ke[dokumentasi](https://reference.groupdocs.com/Watermark/net/).
## FAQ
### Format file apa yang didukung oleh GroupDocs.Watermark untuk .NET?
 GroupDocs.Watermark untuk .NET mendukung berbagai format file, termasuk PDF, DOCX, PPTX, XLSX, dan banyak lagi. Untuk daftar lengkap format yang didukung, lihat[dokumentasi](https://reference.groupdocs.com/Watermark/net/).
### Bisakah saya menyesuaikan tampilan tanda air?
Ya, GroupDocs.Watermark memungkinkan Anda menyesuaikan sepenuhnya tampilan tanda air, termasuk tanda air teks, gambar, dan bentuk. Anda dapat menyesuaikan properti seperti font, warna, ukuran, dan transparansi.
### Apakah ada versi uji coba yang tersedia?
 Ya, Anda bisa mendapatkan a[uji coba gratis](https://releases.groupdocs.com/) dari GroupDocs.Watermark untuk .NET untuk mengevaluasi fitur-fiturnya sebelum melakukan pembelian.
### Bagaimana saya bisa membeli lisensi untuk GroupDocs.Watermark?
 Anda dapat membeli lisensi untuk GroupDocs.Watermark[Di Sini](https://purchase.groupdocs.com/buy). Ada berbagai pilihan lisensi yang tersedia untuk memenuhi kebutuhan yang berbeda.
### Bisakah saya menggunakan GroupDocs.Watermark dalam proyek komersial?
 Ya, dengan lisensi yang valid, Anda dapat menggunakan GroupDocs.Watermark dalam proyek komersial. Pastikan untuk meninjau syarat dan ketentuan lisensi di[halaman pembelian](https://purchase.groupdocs.com/buy).