---
title: Dapatkan Info Dokumen dari Disk Lokal
linktitle: Dapatkan Info Dokumen dari Disk Lokal
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan, menghapus, dan mengekstrak tanda air dalam dokumen menggunakan GroupDocs untuk .NET dengan panduan langkah demi langkah yang komprehensif ini.
weight: 11
url: /id/net/document-manipulation/get-document-info-local-disk/
---

# Dapatkan Info Dokumen dari Disk Lokal

## Perkenalan
Selamat datang di panduan utama tentang penggunaan GroupDocs.Watermark untuk .NET! Baik Anda seorang pengembang berpengalaman atau baru memulai, artikel ini akan memandu Anda memahami pentingnya memberi tanda air pada dokumen Anda dengan alat canggih ini. Pada akhirnya, Anda akan menjadi ahli dalam menyematkan tanda air di dokumen Anda, memastikan dokumen tersebut dilindungi dan diberi merek sesuai spesifikasi Anda.
## Prasyarat
Sebelum mempelajari panduan langkah demi langkah, ada beberapa prasyarat yang harus Anda penuhi:
1.  .NET Framework: Pastikan Anda telah menginstal .NET Framework di sistem Anda. GroupDocs.Watermark untuk .NET kompatibel dengan berbagai versi .NET Framework, jadi periksalah[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) untuk detail kompatibilitas.
2.  GroupDocs.Watermark untuk .NET Library: Unduh dan instal versi terbaru dari[Unduh Halaman](https://releases.groupdocs.com/Watermark/net/).
3. Lingkungan Pengembangan: Anda harus menyiapkan lingkungan pengembangan. Visual Studio adalah pilihan populer untuk pengembangan .NET.
4. Pengetahuan Dasar C#: Memahami dasar-dasar pemrograman C# akan membantu Anda mengikuti contoh.
## Impor Namespace
Sebelum Anda dapat menggunakan GroupDocs.Watermark untuk .NET, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek Anda. Ini adalah proses yang mudah dan penting untuk mengakses fitur perpustakaan.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Mari kita uraikan proses pemberian watermark pada dokumen menjadi langkah-langkah yang jelas dan mudah dikelola. Setiap langkah dirancang untuk membantu Anda memahami dan menerapkan fungsionalitas dengan mudah.
## Langkah 1: Muat Dokumen Anda
 Langkah pertama adalah memuat dokumen yang ingin Anda beri tanda air. Ini dilakukan dengan menggunakan`Watermarker` kelas, yang memungkinkan Anda mengakses dan memanipulasi dokumen Anda.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Dokumen sekarang dimuat dan siap untuk diberi tanda air
}
```
 Pada langkah ini, ganti`"Your Document Path"` dengan jalur sebenarnya ke dokumen Anda. Ini menginisialisasi`Watermarker`objek, memberi Anda akses ke berbagai fungsi watermarking.
## Langkah 2: Dapatkan Informasi Dokumen
Sebelum menambahkan tanda air, Anda mungkin ingin mengumpulkan beberapa informasi tentang dokumen tersebut. Ini berguna untuk menyesuaikan tanda air Anda berdasarkan properti dokumen.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Pada langkah ini,`GetDocumentInfo` metode mengambil detail seperti jenis file, jumlah halaman, dan ukuran dokumen. Informasi ini dicetak ke konsol, namun Anda dapat menggunakannya dalam aplikasi Anda sesuai kebutuhan.
## Langkah 3: Tambahkan Tanda Air Teks
Sekarang setelah dokumen Anda dimuat dan informasinya tersedia, sekarang saatnya menambahkan tanda air. Kita akan mulai dengan tanda air teks sederhana.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Di sini, Anda membuat`TextWatermark` objek dengan teks, font, dan gaya yang Anda inginkan. Sesuaikan properti seperti warna, opacity, dan sudut rotasi agar sesuai dengan kebutuhan Anda. Terakhir, tanda air ditambahkan ke dokumen dan disimpan ke jalur tertentu.
## Langkah 4: Tambahkan Tanda Air Gambar
Tanda air teks memang bagus, tetapi bagaimana jika Anda ingin menambahkan logo atau gambar lain? Langkah ini mencakup cara menambahkan tanda air pada gambar.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Mengganti`"Path to Your Image"` dengan jalur ke gambar tanda air Anda. Atur properti seperti opasitas dan sudut rotasi untuk menyesuaikan tampilan tanda air gambar Anda. Proses menambahkan dan menyimpan watermark mirip dengan proses watermark teks.
## Langkah 5: Hapus Tanda Air yang Ada
 Terkadang, Anda mungkin perlu menghapus tanda air yang ada dari dokumen. Ini dapat dilakukan dengan menggunakan`Remove` metode yang disediakan oleh`Watermarker` kelas.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Di sini, itu`Remove` metode ini digunakan untuk menghapus tanda air teks dari dokumen. Anda dapat menentukan berbagai jenis tanda air yang ingin dihapus, seperti gambar atau teks, tergantung kebutuhan Anda. Simpan dokumen ke jalur baru untuk melihat perubahannya.
## Langkah 6: Ekstrak Tanda Air
Jika Anda perlu mengekstrak dan memeriksa tanda air dari dokumen, GroupDocs.Watermark untuk .NET memungkinkan hal ini dengan mudah.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Properti dan logika tambahan untuk setiap tanda air
    }
}
```
 Langkah ini melibatkan penggunaan`GetWatermarks`metode untuk mengambil semua tanda air dalam dokumen. Anda kemudian dapat mengulangi daftar tanda air dan memeriksa propertinya atau melakukan tindakan tambahan sesuai kebutuhan.
## Kesimpulan
 Selamat! Anda sekarang telah mempelajari cara menggunakan GroupDocs.Watermark untuk .NET untuk menambah, menghapus, dan mengekstrak tanda air dari dokumen Anda. Dengan keterampilan ini, Anda dapat melindungi dan memberi merek pada dokumen Anda secara efektif. Ingat, itu[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) selalu ada jika Anda memerlukan informasi lebih detail atau fungsionalitas tingkat lanjut.
## FAQ
### Bisakah saya menggunakan GroupDocs.Watermark untuk .NET dengan versi .NET apa pun?
 Ya, GroupDocs.Watermark untuk .NET kompatibel dengan berbagai versi .NET Framework. Periksalah[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) untuk spesifik.
### Di mana saya dapat mengunduh GroupDocs.Watermark untuk .NET?
 Anda dapat mengunduh versi terbaru dari[Unduh Halaman](https://releases.groupdocs.com/Watermark/net/).
### Bagaimana cara mendapatkan lisensi sementara?
 Anda dapat memperoleh lisensi sementara dari[halaman lisensi sementara](https://purchase.groupdocs.com/temporary-license/).
### Apakah ada uji coba gratis yang tersedia?
 Ya, Anda dapat memulai uji coba gratis dengan mengunjungi[halaman uji coba gratis](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Dukungan tersedia di[Forum Tanda Air GroupDocs](https://forum.groupdocs.com/c/watermark/19).