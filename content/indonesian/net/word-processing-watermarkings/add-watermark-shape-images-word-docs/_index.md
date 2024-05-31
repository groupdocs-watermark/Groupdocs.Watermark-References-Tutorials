---
title: Tambahkan Tanda Air ke Gambar Bentuk di Dokumen Word
linktitle: Tambahkan Tanda Air ke Gambar Bentuk di Dokumen Word
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air untuk membentuk gambar di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Tingkatkan keamanan dokumen dengan tutorial ini.
type: docs
weight: 17
url: /id/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menambahkan tanda air untuk membentuk gambar dalam dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Watermarking adalah aspek penting dalam perlindungan dokumen, terutama ketika berhubungan dengan informasi sensitif atau rahasia. Dengan menambahkan tanda air untuk membentuk gambar, Anda dapat memastikan integritas dan keamanan dokumen Anda.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Watermark untuk .NET: Unduh dan instal perpustakaan GroupDocs.Watermark dari[Unduh Halaman](https://releases.groupdocs.com/Watermark/net/).
2. Dokumen: Siapkan dokumen Word yang ingin Anda tambahkan tanda airnya.
3. Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET pilihan Anda.
## Impor Namespace
Sebelum menulis kode, pastikan untuk mengimpor namespace yang diperlukan:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
Pertama, tentukan jalur ke dokumen Anda dan tentukan nama file keluaran:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Langkah 2: Inisialisasi Penanda Air
 Buat contoh a`Watermarker` objek dengan menyediakan jalur dokumen dan opsi pemuatan opsional:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tambahkan logika watermarking di sini
}
```
## Langkah 3: Buat Tanda Air Teks
Tentukan tanda air teks dengan properti yang diinginkan seperti teks, font, perataan, rotasi, ukuran, dll.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Langkah 4: Terapkan Tanda Air ke Gambar Bentuk
Ulangi bagian dan bentuk dokumen untuk mengidentifikasi gambar bentuk dan menambahkan tanda air:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Langkah 5: Simpan Dokumen
Simpan dokumen dengan tanda air yang ditambahkan ke file keluaran yang ditentukan:
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan tanda air untuk membentuk gambar di dokumen Word menggunakan GroupDocs.Watermark untuk .NET. Dengan mengikuti panduan langkah demi langkah dan memanfaatkan fitur canggih GroupDocs.Watermark, Anda dapat meningkatkan keamanan dan perlindungan dokumen Anda secara efektif.
## FAQ
### Bisakah saya menyesuaikan tampilan teks tanda air?
Ya, Anda dapat menyesuaikan berbagai properti seperti font, ukuran, warna, sudut rotasi, dan perataan untuk menyesuaikan tanda air sesuai preferensi Anda.
### Apakah GroupDocs.Watermark mendukung format dokumen lain selain Word?
Ya, GroupDocs.Watermark menyediakan dukungan untuk berbagai format dokumen termasuk PDF, Excel, PowerPoint, dan banyak lagi.
### Apakah mungkin menambahkan banyak tanda air ke satu dokumen?
Tentu saja, Anda dapat menambahkan beberapa tanda air dengan konten, gaya, dan posisi berbeda dalam dokumen yang sama.
### Bisakah saya menghapus tanda air dari dokumen menggunakan GroupDocs.Watermark?
Ya, GroupDocs.Watermark menawarkan fitur untuk mendeteksi dan menghapus tanda air dari dokumen secara efisien.
### Apakah GroupDocs.Watermark menyediakan kompatibilitas lintas platform?
Ya, GroupDocs.Watermark kompatibel dengan .NET Framework, .NET Core, dan .NET Standard, memastikan integrasi yang lancar di berbagai platform.