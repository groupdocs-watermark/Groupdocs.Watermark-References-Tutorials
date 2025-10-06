---
title: Simpan Dokumen ke Lokasi Tertentu
linktitle: Simpan Dokumen ke Lokasi Tertentu
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air dengan mudah ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET dengan panduan langkah demi langkah ini. Meningkatkan keamanan dokumen.
weight: 11
url: /id/net/document-savings/save-document-specified-location/
type: docs
---
# Simpan Dokumen ke Lokasi Tertentu

## Perkenalan
Di era digital, pengamanan dokumen menjadi lebih penting dari sebelumnya. Watermarking adalah cara efektif untuk melindungi dokumen Anda dari penggunaan yang tidak sah. GroupDocs.Watermark untuk .NET menawarkan solusi tangguh untuk menambahkan tanda air ke dokumen Anda. Baik Anda seorang pengembang yang ingin mengintegrasikan watermarking ke dalam aplikasi Anda atau seseorang yang tertarik untuk melindungi dokumen Anda, tutorial ini akan memandu Anda melalui proses langkah demi langkah.
## Prasyarat
Sebelum masuk ke tutorial, pastikan Anda memiliki prasyarat berikut:
- Lingkungan Pengembangan .NET: Pastikan Anda telah menginstal Visual Studio atau lingkungan pengembangan .NET lainnya.
-  GroupDocs.Watermark untuk .NET Library: Unduh dan referensikan perpustakaan di proyek Anda.[Unduh GroupDocs.Watermark untuk .NET](https://releases.groupdocs.com/Watermark/net/)
- Pengetahuan Dasar Pemrograman C#: Memahami konsep dasar pemrograman C# akan sangat membantu.
- Dokumen ke Tanda Air: Siapkan contoh dokumen yang ingin Anda beri tanda air.
## Impor Namespace
Sebelum kita mulai dengan contohnya, Anda perlu mengimpor namespace yang diperlukan. Tambahkan pernyataan penggunaan berikut di bagian atas file kode Anda:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Mari kita uraikan proses menambahkan tanda air ke dokumen menggunakan GroupDocs.Watermark untuk .NET menjadi langkah-langkah yang dapat dikelola. Ikuti langkah-langkah berikut agar berhasil menerapkan tanda air dan menyimpan dokumen Anda ke lokasi tertentu.
## Langkah 1: Siapkan Proyek Anda
Mulailah dengan membuat proyek .NET baru di Visual Studio. Anda dapat memilih Aplikasi Konsol untuk kesederhanaan.
1. Buka Visual Studio.
2.  Pilih`File` >`New` >`Project`.
3.  Memilih`Console App (.NET Core)` atau`Console App (.NET Framework)`.
4.  Beri nama proyek Anda dan klik`Create`.

## Langkah 2: Siapkan Dokumen dan Teks Tanda Air Anda
### Tentukan Jalur Dokumen
Tentukan jalur dokumen yang ingin Anda beri tanda air. Untuk contoh ini, mari kita gunakan jalur placeholder.
```csharp
string documentPath = "Your Document Path";
```
### Tentukan Jalur Keluaran
Siapkan jalur keluaran tempat Anda ingin menyimpan dokumen yang diberi tanda air.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Langkah 3: Muat Dokumen
 Menggunakan`Watermarker` kelas untuk memuat dokumen Anda. Kelas ini menyediakan metode untuk menambah, menghapus, dan mengedit tanda air.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Tambahkan logika watermarking di sini
}
```
## Langkah 4: Buat dan Tambahkan Tanda Air

### Buat Tanda Air Teks
 Buat contoh a`TextWatermark` objek dengan properti teks dan font yang Anda inginkan.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Tambahkan Tanda Air ke Dokumen
 Tambahkan tanda air yang dibuat ke dokumen Anda menggunakan`Add` metode`Watermarker` kelas.
```csharp
watermarker.Add(watermark);
```
## Langkah 5: Simpan Dokumen
Terakhir, simpan dokumen yang diberi watermark ke lokasi yang ditentukan.
```csharp
watermarker.Save(outputFileName);
```
## Kesimpulan
Memberi watermark pada dokumen Anda menggunakan GroupDocs. Watermark untuk .NET adalah proses sederhana yang dapat meningkatkan keamanan dokumen Anda secara signifikan. Dengan mengikuti panduan langkah demi langkah ini, Anda dapat dengan mudah menambahkan tanda air ke dokumen Anda dan menyimpannya ke lokasi yang Anda inginkan. Baik Anda melindungi kekayaan intelektual, memastikan keaslian dokumen, atau sekadar menambahkan sentuhan profesional, GroupDocs.Watermark untuk .NET menyediakan alat yang Anda perlukan.
## FAQ
### Bisakah saya menggunakan gambar sebagai tanda air dengan GroupDocs.Watermark untuk .NET?
Ya, Anda dapat menggunakan tanda air teks dan gambar dengan GroupDocs untuk .NET. Perpustakaan mendukung berbagai jenis tanda air sesuai kebutuhan Anda.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Watermark untuk .NET?
 Ya, Anda dapat mengunduh uji coba gratis dari[situs web](https://releases.groupdocs.com/).
### Bagaimana cara membeli lisensi GroupDocs.Watermark untuk .NET?
 Anda dapat membeli lisensi dari[halaman pembelian](https://purchase.groupdocs.com/buy).
### Apakah GroupDocs.Watermark untuk .NET mendukung watermarking batch?
Ya, Anda dapat memberi tanda air pada beberapa dokumen dalam proses batch dengan mengulangi daftar dokumen dan menerapkan tanda air.
### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Watermark untuk .NET?
 Dukungan tersedia di[Forum Grup Dokumen](https://forum.groupdocs.com/c/watermark/19).