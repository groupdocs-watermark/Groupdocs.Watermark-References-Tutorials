---
title: Dapatkan Format File yang Didukung
linktitle: Dapatkan Format File yang Didukung
second_title: GroupDocs.Tanda Air .NET API
description: Tambahkan tanda air ke dokumen Anda dengan mudah menggunakan GroupDocs.Watermark untuk .NET. Ikuti panduan komprehensif langkah demi langkah kami untuk melindungi aset digital Anda.
type: docs
weight: 13
url: /id/net/document-manipulation/get-supported-file-formats/
---
## Perkenalan
Memberi tanda air pada dokumen Anda adalah langkah penting dalam melindungi aset digital Anda. Baik untuk melindungi kekayaan intelektual, memastikan kerahasiaan, atau sekadar pencitraan merek, tanda air memainkan peran penting. Jika Anda seorang pengembang .NET yang ingin mengintegrasikan kemampuan watermarking ke dalam aplikasi Anda, GroupDocs.Watermark untuk .NET adalah alat yang ampuh dan serbaguna yang harus Anda pertimbangkan. Tutorial ini akan memandu Anda melalui hal-hal penting dalam menggunakan GroupDocs.Watermark, mulai dari instalasi hingga penerapan tanda air pertama Anda, menguraikan setiap langkah untuk memastikan Anda dapat mengikutinya dengan mudah.
## Prasyarat
Sebelum kita mendalami secara spesifik, pastikan Anda memiliki semua yang Anda perlukan untuk memulai:
1.  Visual Studio: Pastikan Anda telah menginstal Visual Studio di mesin Anda. Anda dapat mengunduhnya dari[Situs web Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark mendukung berbagai versi .NET Framework. Pastikan proyek Anda menargetkan versi yang kompatibel.
3. GroupDocs.Watermark untuk .NET: Anda dapat mengunduh versi terbaru dari[halaman rilis](https://releases.groupdocs.com/Watermark/net/).
4. Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman mendasar tentang pengembangan C# dan .NET.
## Impor Namespace
Pertama, mari impor namespace yang diperlukan dalam proyek Anda. Buka file C# Anda dan tambahkan arahan penggunaan berikut di atas:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Dengan mengimpor namespace ini, Anda siap untuk mulai menambahkan tanda air ke dokumen Anda.

## Langkah 1: Inisialisasi Mesin Watermarking
 Langkah pertama adalah menginisialisasi mesin watermarking. Ini melibatkan pembuatan sebuah instance dari`Watermarker` kelas dengan dokumen yang ingin Anda beri tanda air.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Cuplikan kode ini menyiapkan`Watermarker` objek, yang akan Anda gunakan untuk menerapkan tanda air pada dokumen Anda.
## Langkah 2: Tambahkan Tanda Air Teks
Sekarang, mari tambahkan tanda air teks sederhana ke dokumen Anda. Tanda air teks sangat bagus untuk menambahkan label seperti "Rahasia" atau "Draf".
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Di sini, kami telah membuat`TextWatermark`objek dengan teks "Rahasia", atur font dan warnanya, dan sejajarkan ke tengah dokumen.
## Langkah 3: Tambahkan Tanda Air Gambar
Jika Anda lebih suka menggunakan gambar sebagai tanda air, GroupDocs.Watermark memudahkannya.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 Dalam contoh ini, kami membuat`ImageWatermark` objek, atur dimensinya, dan sejajarkan ke sudut kanan atas dokumen.
## Langkah 4: Simpan Dokumen
Setelah menambahkan watermark yang diinginkan, langkah terakhir adalah menyimpan dokumen yang telah diubah.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Ini akan menyimpan dokumen yang diberi watermark ke jalur yang ditentukan dan melepaskan sumber daya apa pun yang digunakan olehnya`Watermarker` contoh.
## Langkah 5: Dapatkan Format File yang Didukung
Untuk melihat format file apa saja yang didukung oleh GroupDocs.Watermark, Anda dapat menggunakan cuplikan kode berikut:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Ini akan mencetak semua jenis file yang dapat ditangani GroupDocs.Watermark, memberi Anda gambaran komprehensif tentang kemampuannya.
## Kesimpulan
Memberi watermark pada dokumen Anda dengan GroupDocs. Watermark untuk .NET sangatlah mudah dan efisien. Dengan mengikuti tutorial ini, Anda telah mempelajari cara menginisialisasi mesin watermarking, menambahkan watermark teks dan gambar, menyimpan dokumen yang diberi watermark, dan membuat daftar format file yang didukung. Dengan alat ini, Anda dapat melindungi dokumen Anda dengan percaya diri.
 Jika Anda memiliki pertanyaan atau memerlukan bantuan lebih lanjut, jangan ragu untuk mengunjungi[Forum dukungan GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Bagaimana cara menginstal GroupDocs.Watermark untuk .NET?
 Anda dapat mengunduhnya dari[halaman rilis](https://releases.groupdocs.com/Watermark/net/) dan tambahkan DLL ke proyek Anda.
### Bisakah saya mencoba GroupDocs.Watermark secara gratis?
 Ya, Anda dapat meminta a[uji coba gratis](https://releases.groupdocs.com/) untuk mengevaluasi perangkat lunak sebelum membeli.
### Format file apa yang didukung oleh GroupDocs.Watermark?
Anda dapat menggunakan cuplikan kode yang disediakan untuk mencantumkan semua format file yang didukung.
### Bagaimana saya bisa membeli lisensi untuk GroupDocs.Watermark?
 Lisensi dapat dibeli langsung dari[halaman pembelian](https://purchase.groupdocs.com/buy).
### Apakah ada dokumentasi yang tersedia untuk GroupDocs.Watermark?
 Ya, dokumentasi lengkap tersedia[Di Sini](https://reference.groupdocs.com/Watermark/net/).