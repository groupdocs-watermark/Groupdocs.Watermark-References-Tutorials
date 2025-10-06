---
title: Tambahkan Tanda Air ke Semua Lampiran di PDF
linktitle: Tambahkan Tanda Air ke Semua Lampiran di PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke lampiran PDF menggunakan GroupDocs.Watermark untuk .NET. Amankan dokumen Anda dengan tanda air khusus dengan mudah.
weight: 16
url: /id/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
type: docs
---
# Tambahkan Tanda Air ke Semua Lampiran di PDF

## Perkenalan
Menambahkan tanda air ke lampiran PDF bisa menjadi langkah penting dalam pengelolaan dokumen, terutama saat memastikan keamanan atau branding. GroupDocs.Watermark untuk .NET menawarkan solusi komprehensif untuk menyematkan tanda air ke dalam file PDF dengan lancar. Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan tanda air ke semua lampiran dalam dokumen PDF menggunakan GroupDocs.Watermark untuk .NET.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Watermark for .NET: Jika Anda belum melakukannya, unduh dan instal GroupDocs.Watermark for .NET dari[situs web](https://releases.groupdocs.com/Watermark/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai dengan Visual Studio atau IDE lain yang kompatibel dengan .NET.
3. Dokumen PDF: Siapkan dokumen PDF yang ingin Anda tambahkan watermark, beserta lampiran yang ingin Anda beri watermark.

## Mengimpor Namespace
Sebelum mendalami kode, pastikan untuk mengimpor namespace yang diperlukan untuk mengakses GroupDocs.Watermark untuk fungsi .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Tentukan Jalur Dokumen dan Direktori Keluaran
Pertama, tentukan jalur ke dokumen PDF masukan Anda dan direktori tempat dokumen yang diberi tanda air akan disimpan:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Langkah 2: Inisialisasi Opsi Muat dan Tanda Air
Selanjutnya, inisialisasi opsi pemuatan dokumen PDF dan buat tanda air teks:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Langkah 3: Muat Dokumen dan Lampiran
Muat dokumen PDF dan ulangi lampirannya:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Langkah 4: Periksa Dukungan Lampiran
Periksa apakah file terlampir didukung oleh GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Langkah 5: Tambahkan Tanda Air ke Lampiran
Muat dokumen terlampir dan tambahkan tanda air:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Langkah 6: Simpan Perubahan
Terakhir, simpan perubahan pada dokumen PDF yang diberi watermark:
```csharp
    watermarker.Save(outputFileName);
}
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan tanda air ke semua lampiran dalam dokumen PDF menggunakan GroupDocs.Watermark untuk .NET. Dengan mengikuti panduan langkah demi langkah, Anda dapat dengan mudah mengintegrasikan tanda air ke dalam file PDF Anda, memastikan keamanan dan branding dokumen.
## FAQ
### Bisakah saya menyesuaikan tampilan tanda air?
Ya, Anda dapat menyesuaikan berbagai aspek seperti teks, font, ukuran, warna, dan posisi watermark sesuai kebutuhan Anda.
### Apakah GroupDocs.Watermark mendukung format dokumen lain selain PDF?
Ya, GroupDocs.Watermark mendukung berbagai format dokumen termasuk Microsoft Word, Excel, PowerPoint, Visio, Outlook, dan Gambar.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark?
Ya, Anda dapat menjelajahi fitur GroupDocs.Watermark dengan mengunduh versi uji coba gratis dari situs web.
### Bisakah saya menambahkan beberapa tanda air ke satu dokumen?
Tentu saja, GroupDocs.Watermark memungkinkan Anda menambahkan beberapa tanda air termasuk teks, gambar, dan anotasi secara bersamaan untuk meningkatkan keamanan dan pencitraan merek dokumen.
### Apakah dukungan teknis tersedia untuk pengguna GroupDocs.Watermark?
Ya, GroupDocs menyediakan dukungan teknis komprehensif melalui forum dan saluran dukungan khusus untuk membantu pengguna dengan pertanyaan atau masalah apa pun yang mungkin mereka temui.