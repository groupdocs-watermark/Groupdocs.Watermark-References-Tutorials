---
title: Ekstrak Informasi Anotasi dari PDF
linktitle: Ekstrak Informasi Anotasi dari PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara mengekstrak informasi anotasi dari dokumen PDF menggunakan GroupDocs.Watermark untuk .NET dalam panduan langkah demi langkah yang mendetail ini.
weight: 23
url: /id/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# Ekstrak Informasi Anotasi dari PDF

## Perkenalan
Apakah Anda sering merasa perlu mengekstrak informasi anotasi mendetail dari dokumen PDF Anda? Baik Anda seorang pengembang yang mengerjakan sistem manajemen dokumen atau profesional bisnis yang menangani banyak PDF, mengekstraksi dan memproses anotasi secara efisien dapat menjadi hal yang sangat penting. Dengan GroupDocs.Watermark untuk .NET, Anda memiliki perangkat canggih yang dapat Anda gunakan untuk menjadikan tugas ini mudah dan efisien.
## Prasyarat
Sebelum kita mendalami kodenya, pastikan Anda memiliki semua yang dibutuhkan untuk memulai:
1. Visual Studio: Pastikan Anda telah menginstal Visual Studio. Ini akan menjadi IDE kami untuk menulis dan menjalankan kode.
2.  GroupDocs.Watermark untuk .NET: Anda harus memiliki perpustakaan GroupDocs.Watermark untuk .NET. Kamu bisa[Unduh di sini](https://releases.groupdocs.com/Watermark/net/).
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# diperlukan untuk mengikuti contoh.
## Impor Namespace
Untuk memulainya, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek Anda. Namespace ini berisi kelas dan metode yang diperlukan untuk bekerja dengan file PDF dan mengekstrak anotasi.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Langkah 1: Siapkan Proyek Anda
Pertama, mari kita siapkan proyek kita di Visual Studio. Buat proyek Aplikasi Konsol (.NET Core) baru. Setelah proyek Anda dibuat, Anda perlu menambahkan referensi ke perpustakaan GroupDocs.Watermark untuk .NET.
1. Buka Manajer Paket NuGet.
2.  Pencarian untuk`GroupDocs.Watermark`.
3.  Instal`GroupDocs.Watermark` kemasan.
## Langkah 2: Tentukan Jalur Dokumen
Selanjutnya, Anda harus menentukan jalur untuk dokumen PDF masukan Anda dan direktori keluaran tempat informasi yang diekstraksi akan disimpan. Ini memastikan aplikasi Anda mengetahui di mana menemukan file PDF dan di mana menyimpan hasilnya.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Langkah 3: Muat Dokumen PDF
 Untuk bekerja dengan dokumen PDF, kita perlu memuatnya menggunakan`PdfLoadOptions`. Kelas ini menyediakan opsi untuk mengkonfigurasi proses pemuatan.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode untuk mengekstrak anotasi akan ditempatkan di sini
}
```
## Langkah 4: Akses Konten PDF
Setelah dokumen dimuat, kita dapat mengakses isinya. Secara khusus, kami ingin mendapatkan konten PDF sehingga kami dapat mengulangi halaman dan anotasi.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Langkah 5: Ulangi Halaman dan Anotasi
Dengan konten PDF di tangan, kita dapat menelusuri setiap halaman dan kemudian melalui setiap anotasi pada halaman tersebut. Hal ini memungkinkan kita untuk mengekstrak informasi yang kita butuhkan.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Ekstrak detail anotasi di sini
    }
}
```
## Langkah 6: Ekstrak Detail Anotasi
Dalam loop bersarang, kami mengekstrak berbagai detail tentang setiap anotasi. Ini mencakup jenis anotasi, gambar terkait, teks, dan data posisi.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Langkah 7: Simpan atau Proses Data yang Diekstraksi
Terakhir, putuskan apa yang ingin Anda lakukan dengan informasi anotasi yang diekstraksi. Anda dapat mencetaknya ke konsol, menyimpannya ke file, atau bahkan menyimpannya dalam database, tergantung kebutuhan Anda.
```csharp
// Contoh menyimpan data yang diekstrak ke file
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Kesimpulan
Mengekstrak informasi anotasi dari dokumen PDF menggunakan GroupDocs.Watermark untuk .NET adalah proses mudah yang dapat menghemat banyak waktu dan tenaga Anda. Dengan mengikuti langkah-langkah yang diuraikan dalam panduan ini, Anda dapat dengan mudah mengintegrasikan fungsi ini ke dalam proyek Anda dan mengotomatiskan ekstraksi data anotasi yang berharga.
 Baik Anda mengelola PDF dalam jumlah besar atau hanya perlu mengekstrak informasi spesifik, GroupDocs.Watermark untuk .NET memberikan solusi yang andal dan efisien. Jangan lupa untuk memeriksa[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) untuk fitur lanjutan dan opsi penyesuaian lainnya.
## FAQ
### Apa itu GroupDocs.Watermark untuk .NET?
GroupDocs.Watermark for .NET adalah perpustakaan komprehensif yang memungkinkan pengembang menambahkan, mencari, dan menghapus tanda air dari berbagai format dokumen, termasuk PDF, dokumen Word, dan gambar.
### Bisakah saya mencoba GroupDocs.Watermark secara gratis?
 Ya, Anda bisa mendapatkan[uji coba gratis](https://releases.groupdocs.com/) untuk menguji fitur perpustakaan sebelum melakukan pembelian.
### Bagaimana cara mendapatkan dukungan jika saya mengalami masalah?
 Anda bisa mendapatkan dukungan dari tim GroupDocs dengan mengunjungi mereka[forum dukungan](https://forum.groupdocs.com/c/watermark/19).
### Apakah mungkin untuk mendapatkan lisensi sementara untuk pengujian?
 Ya, Anda dapat meminta a[izin sementara](https://purchase.groupdocs.com/temporary-license/)untuk tujuan pengujian.
### Di mana saya dapat membeli versi lengkap GroupDocs.Watermark untuk .NET?
 Anda dapat membeli versi lengkap dari[Situs web GroupDocs](https://purchase.groupdocs.com/buy).