---
title: Muat Dokumen yang Dilindungi Kata Sandi
linktitle: Muat Dokumen yang Dilindungi Kata Sandi
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke dokumen yang dilindungi kata sandi menggunakan Groupdocs untuk .NET dengan panduan langkah demi langkah kami. Amankan dan beri merek file Anda dengan mudah.
weight: 13
url: /id/net/document-loadings/load-password-protected-document/
---

# Muat Dokumen yang Dilindungi Kata Sandi

## Perkenalan
Apakah Anda ingin melindungi dokumen Anda dengan menambahkan tanda air, meskipun dokumen tersebut dilindungi kata sandi? Groupdocs.Watermark untuk .NET adalah alat canggih yang memungkinkan Anda melakukan hal itu. Dalam tutorial ini, kami akan memandu Anda melalui proses memuat dokumen yang dilindungi kata sandi dan menambahkan tanda air ke dalamnya menggunakan Groupdocs.Watermark untuk .NET. Ayo selami!
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki yang berikut ini:
1. Visual Studio: Versi Visual Studio apa pun yang diinstal pada mesin Anda.
2. .NET Framework: Pastikan Anda memiliki .NET Framework 4.6.1 atau lebih baru.
3. Groupdocs.Watermark untuk .NET: Unduh dan instal perpustakaan Groupdocs.Watermark untuk .NET dari[tautan unduhan](https://releases.groupdocs.com/Watermark/net/).
## Impor Namespace
Pertama, kita perlu mengimpor namespace yang diperlukan ke dalam proyek kita. Ini memastikan bahwa kita dapat mengakses semua metode dan properti yang disediakan oleh Groupdocs.Watermark untuk .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Sekarang, mari kita bagi prosesnya menjadi langkah-langkah sederhana dan mudah diikuti.
## Langkah 1: Siapkan Proyek Anda
Untuk memulai, buat Aplikasi Konsol C# baru di Visual Studio. Setelah proyek Anda siap, instal pustaka Groupdocs.Watermark untuk .NET melalui NuGet Package Manager.
1. Buka Visual Studio dan buat Aplikasi Konsol baru (.NET Framework).
2.  Pergi ke`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Pencarian untuk`GroupDocs.Watermark` dan instal paketnya.
## Langkah 2: Tentukan Jalur Dokumen
Selanjutnya, Anda harus menentukan jalur ke dokumen yang dilindungi kata sandi dan jalur file keluaran tempat dokumen yang diberi tanda air akan disimpan.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"` Dan`"Your Document Directory"` dengan jalur sebenarnya di mesin Anda.
## Langkah 3: Tetapkan Opsi Muat dengan Kata Sandi
Untuk membuka dokumen yang dilindungi kata sandi, Anda harus memberikan kata sandi di opsi muat.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Mengganti`"P@$w0rd"` dengan kata sandi sebenarnya dari dokumen Anda.
## Langkah 4: Muat Dokumen
 Sekarang, mari kita memuat dokumen menggunakan`Watermarker` kelas.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda untuk menambahkan tanda air akan ditempatkan di sini
}
```
## Langkah 5: Buat Tanda Air
Kami akan membuat tanda air teks yang dapat kami tambahkan ke dokumen. Anda dapat menyesuaikan teks, font, ukuran, dan properti lainnya sesuai kebutuhan.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Jangan ragu untuk berubah`"Test watermark"`, `"Arial"` , Dan`12` sesuai teks, font, dan ukuran pilihan Anda.
## Langkah 6: Tambahkan Tanda Air
 Tambahkan tanda air ke dokumen menggunakan`Add` metode`Watermarker` kelas.
```csharp
watermarker.Add(watermark);
```
## Langkah 7: Simpan Dokumen yang diberi Watermark
Terakhir, simpan dokumen yang diberi tanda air ke jalur file keluaran yang ditentukan.
```csharp
watermarker.Save(outputFileName);
```
## Kesimpulan
Menambahkan tanda air ke dokumen Anda yang dilindungi kata sandi adalah proses yang mudah dengan Groupdocs untuk .NET. Dengan mengikuti langkah-langkah sederhana ini, Anda dapat memastikan bahwa dokumen Anda dilindungi dan diberi merek sesuai kebutuhan Anda. Baik untuk keamanan, pencitraan merek, atau kepatuhan, memberi tanda air pada dokumen Anda tidak pernah semudah ini.
## FAQ
### Bisakah saya menambahkan tanda air gambar menggunakan Groupdocs.Watermark untuk .NET?
 Ya, Anda dapat menambahkan tanda air teks dan gambar. Cukup gunakan`ImageWatermark` kelas sebagai gantinya`TextWatermark`.
### Apakah mungkin untuk menghilangkan tanda air dari dokumen?
Ya, Groupdocs.Watermark untuk .NET menyediakan metode untuk mencari dan menghapus tanda air.
### Apakah Groupdocs.Watermark untuk .NET mendukung format dokumen lain selain PDF?
Ya, ini mendukung berbagai format termasuk Word, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan tanda air?
Sangat! Anda dapat menyesuaikan font, ukuran, warna, opasitas, dan lainnya.
### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Anda dapat mengunjungi[Forum Dukungan Groupdocs](https://forum.groupdocs.com/c/watermark/19) untuk bantuan dan bimbingan.