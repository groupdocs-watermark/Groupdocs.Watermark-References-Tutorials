---
title: Tambahkan Tanda Air ke Gambar Anotasi dalam PDF
linktitle: Tambahkan Tanda Air ke Gambar Anotasi dalam PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara melindungi dokumen PDF Anda dengan menambahkan tanda air ke gambar anotasi menggunakan Groupdocs.Watermark untuk .NET.
weight: 17
url: /id/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menambahkan tanda air ke gambar anotasi dalam dokumen PDF menggunakan Groupdocs.Watermark untuk .NET. Pemberian tanda air sangat penting untuk melindungi dokumen Anda dari penggunaan atau distribusi yang tidak sah. Dengan mengikuti panduan langkah demi langkah ini, Anda akan mempelajari cara menerapkan tanda air teks pada gambar anotasi di PDF secara efektif.
## Prasyarat
Sebelum melanjutkan, pastikan Anda memiliki hal berikut:
1. Pemahaman dasar bahasa pemrograman C#.
2. Menginstal Groupdocs.Watermark untuk perpustakaan .NET.
3. Akses ke lingkungan pengembangan seperti Visual Studio.
4. Dokumen PDF dengan gambar anotasi hingga tanda air.

## Mengimpor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke kode C# Anda:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Langkah 2: Dapatkan Konten PDF dan Inisialisasi Tanda Air
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Inisialisasi tanda air gambar atau teks
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Langkah 3: Ulangi Halaman PDF dan Gambar Anotasi
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Tambahkan tanda air ke gambar
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Langkah 4: Simpan Dokumen dengan Tanda Air
```csharp
    watermarker.Save(outputFileName);
}
```
Setelah menjalankan langkah-langkah ini, dokumen PDF Anda akan memiliki tanda air tertentu yang ditambahkan ke gambar anotasi.

## Kesimpulan
Menambahkan tanda air ke gambar anotasi di PDF sangat penting untuk melindungi integritas dokumen Anda dan memastikan dokumen tersebut tidak disalahgunakan. Dengan Groupdocs.Watermark untuk .NET, proses ini menjadi sederhana dan efisien, memungkinkan Anda melindungi file PDF Anda secara efektif.
## FAQ
### Bisakah saya menambahkan beberapa tanda air ke dokumen PDF yang sama?
Ya, Anda dapat menambahkan beberapa tanda air ke dokumen PDF yang sama menggunakan Groupdocs.Watermark untuk .NET.
### Apakah Groupdocs.Watermark mendukung format dokumen lain selain PDF?
Ya, Groupdocs mendukung berbagai format dokumen, termasuk Word, Excel, PowerPoint, dan lainnya.
### Apakah mungkin untuk menyesuaikan tampilan tanda air?
Tentu saja, Anda dapat menyesuaikan teks, font, warna, ukuran, dan posisi tanda air sesuai preferensi Anda.
### Bisakah saya menghapus tanda air dari dokumen PDF menggunakan Groupdocs.Watermark?
Ya, Groupdocs.Watermark menyediakan fungsionalitas untuk menghapus tanda air dari dokumen PDF dengan mudah.
### Apakah ada uji coba gratis yang tersedia untuk Groupdocs.Watermark untuk .NET?
Ya, Anda dapat memanfaatkan uji coba gratis Groupdocs.Watermark untuk .NET dari situs web.