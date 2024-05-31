---
title: Tambahkan Tanda Air ke XObjects di PDF
linktitle: Tambahkan Tanda Air ke XObjects di PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air ke XObjects di PDF menggunakan Groupdocs.Watermark untuk .NET. Ikuti panduan langkah demi langkah kami untuk kemudahan penerapan.
type: docs
weight: 20
url: /id/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Perkenalan
Memberi tanda air pada PDF adalah langkah penting untuk memastikan dokumen Anda terlindungi dari penggunaan yang tidak sah. Dengan Groupdocs.Watermark untuk .NET, menambahkan tanda air ke XObjects dalam PDF Anda tidak pernah semudah ini. Dalam tutorial ini, kami akan memandu Anda melalui proses langkah demi langkah, memastikan Anda dapat dengan percaya diri menerapkan tanda air ke dokumen PDF Anda. Mari kita mulai!
## Prasyarat
Sebelum masuk ke tutorial, pastikan Anda memiliki semua yang perlu Anda ikuti dengan lancar:
-  Groupdocs.Watermark untuk .NET: Unduh dan instal versi terbaru dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Pastikan Anda telah menginstal .NET Framework di mesin pengembangan Anda.
- Lingkungan Pengembangan: Gunakan Visual Studio atau IDE lain yang mendukung pengembangan .NET.
-  Lisensi Sementara: Mendapatkan a[izin sementara](https://purchase.groupdocs.com/temporary-license/) jika Anda mengevaluasi produk.
Setelah Anda memiliki prasyarat ini, Anda siap untuk mulai memberi tanda air pada PDF Anda.
## Impor Namespace
Pertama, Anda harus mengimpor namespace yang diperlukan dalam proyek Anda. Buka proyek C# Anda dan tambahkan arahan penggunaan berikut:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Siapkan Jalur Dokumen Anda
Langkah pertama melibatkan pengaturan jalur untuk dokumen Anda. Tentukan jalur di mana PDF Anda berada dan di mana Anda ingin menyimpan PDF yang diberi tanda air.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"` Dan`"Your Document Directory"` dengan jalur sebenarnya di mesin Anda.
## Langkah 2: Inisialisasi Opsi Pemuatan PDF
Selanjutnya, Anda harus menginisialisasi opsi pemuatan PDF. Ini penting untuk memuat konten PDF dengan benar.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Langkah 3: Muat Dokumen PDF
Menggunakan opsi muat, muat dokumen PDF dengan`Watermarker` kelas.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Langkah 4: Buat Tanda Air
Sekarang, Anda perlu membuat tanda air yang akan ditambahkan ke PDF. Untuk tutorial ini, kita akan membuat tanda air teks.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Langkah 5: Tambahkan Tanda Air ke XObjects
Ulangi setiap halaman dan setiap XObject dalam PDF untuk menerapkan tanda air.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Tambahkan tanda air ke gambar
            xObject.Image.Add(watermark);
        }
    }
}
```
## Langkah 6: Simpan PDF yang diberi Watermark
Terakhir, simpan PDF yang diberi tanda air ke file keluaran yang ditentukan.
```csharp
    watermarker.Save(outputFileName);
}
```
Dan itu dia! PDF Anda sekarang berisi tanda air di semua XObjects-nya.
## Kesimpulan
 Menambahkan tanda air ke dokumen PDF Anda menggunakan Groupdocs untuk .NET adalah proses sederhana yang memberikan lapisan keamanan tambahan. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat memastikan bahwa dokumen Anda terlindungi dari penggunaan yang tidak sah. Ingat, Anda selalu dapat merujuk ke[dokumentasi](https://reference.groupdocs.com/Watermark/net/) untuk informasi lebih detail dan fitur lanjutan.
## FAQ
### Bisakah saya menggunakan gambar sebagai tanda air dan bukan teks?
Ya, Groupdocs.Watermark untuk .NET mendukung tanda air teks dan gambar.
### Bagaimana saya bisa menguji Groupdocs.Watermark tanpa membelinya?
 Anda dapat menggunakan a[izin sementara](https://purchase.groupdocs.com/temporary-license/) untuk mengevaluasi produk.
### Apakah mungkin untuk menyesuaikan tampilan tanda air?
Sangat! Anda dapat menyesuaikan font, ukuran, sudut rotasi, dan lainnya.
### Apakah Groupdocs.Watermark mendukung format dokumen lain?
Ya, ini mendukung berbagai format, termasuk Word, Excel, dan PowerPoint.
### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Anda bisa mendapatkan dukungan dari[Forum Grupdocs](https://forum.groupdocs.com/c/watermark/19).