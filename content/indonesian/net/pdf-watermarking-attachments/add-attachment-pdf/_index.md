---
title: Tambahkan Lampiran ke PDF
linktitle: Tambahkan Lampiran ke PDF
second_title: GroupDocs.Tanda Air .NET API
description: Tingkatkan kemampuan manajemen dokumen .NET Anda dengan GroupDocs.Watermark untuk penanganan tanda air dan lampiran yang lancar.
weight: 12
url: /id/net/pdf-watermarking-attachments/add-attachment-pdf/
---
## Perkenalan
Dalam bidang pengembangan .NET, GroupDocs.Watermark menonjol sebagai alat yang ampuh untuk mengelola tanda air, anotasi, dan lainnya dalam berbagai format dokumen. Baik Anda bekerja dengan PDF, dokumen Word, atau gambar, GroupDocs.Watermark untuk .NET menyediakan integrasi sempurna yang memberdayakan pengembang untuk memanipulasi dokumen dengan mudah.
## Prasyarat
Sebelum mendalami seluk-beluk penggunaan GroupDocs.Watermark untuk .NET, pastikan Anda memiliki prasyarat berikut:
1.  Instalasi: Pastikan Anda telah menginstal GroupDocs.Watermark untuk .NET. Anda dapat mengunduhnya dari[halaman rilis](https://releases.groupdocs.com/Watermark/net/).
2. Persiapan Dokumen: Siapkan dokumen yang ingin Anda beri tanda air atau operasi lainnya.
3. Pengetahuan Dasar C#: Biasakan diri Anda dengan dasar-dasar bahasa pemrograman C# karena kita akan menggunakannya untuk berinteraksi dengan GroupDocs.Watermark API.

## Impor Namespace
Sebelum memulai implementasi, penting untuk mengimpor namespace yang diperlukan untuk mengakses fungsionalitas GroupDocs.Watermark. Di bawah ini adalah namespace yang diperlukan:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Langkah 1: Muat Dokumen
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 Pada langkah ini, kita menentukan jalur ke dokumen yang ingin kita kerjakan dan buat a`PdfLoadOptions` objek untuk memuat dokumen PDF. Kemudian, kami menginisialisasi a`Watermarker` objek dengan jalur dokumen dan opsi pemuatan.
## Langkah 2: Dapatkan Konten PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 Di sini, kami memperoleh konten dokumen PDF menggunakan`GetContent<PdfContent>()` metode.
## Langkah 3: Tambahkan Lampiran
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
Langkah ini melibatkan penambahan lampiran ke dokumen PDF. Anda perlu memberikan byte file lampiran, nama, dan deskripsi.
## Langkah 4: Simpan Perubahan
```csharp
watermarker.Save(outputFileName);
```
Terakhir, kami menyimpan perubahan yang dilakukan pada dokumen dengan lampiran tambahan.

## Kesimpulan
GroupDocs.Watermark untuk .NET menawarkan solusi tangguh untuk mengelola tanda air dan lampiran dokumen dengan lancar. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat dengan mudah mengintegrasikan fungsi watermarking dan lampiran ke dalam aplikasi .NET Anda.
## FAQ
### Apakah GroupDocs.Watermark kompatibel dengan semua kerangka .NET?
Ya, GroupDocs.Watermark mendukung .NET Framework 2.0 dan lebih tinggi.
### Bisakah saya menghapus tanda air yang ditambahkan menggunakan GroupDocs.Watermark?
Ya, GroupDocs.Watermark menyediakan metode untuk menghilangkan tanda air dari dokumen.
### Apakah GroupDocs.Watermark mendukung enkripsi dokumen?
Ya, GroupDocs.Watermark memungkinkan Anda bekerja dengan dokumen terenkripsi.
### Bisakah saya menyesuaikan tampilan tanda air?
Tentu saja, GroupDocs.Watermark menawarkan berbagai opsi penyesuaian untuk tanda air.
### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?
 Ya, Anda dapat mengakses versi uji coba dari[halaman rilis](https://releases.groupdocs.com/).