---
title: Rasterisasi Halaman PDF
linktitle: Rasterisasi Halaman PDF
second_title: GroupDocs.Tanda Air .NET API
description: Tingkatkan keamanan dokumen dengan GroupDocs untuk .NET. Tambahkan tanda air ke PDF dan format lainnya dengan lancar.
type: docs
weight: 28
url: /id/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## Perkenalan
GroupDocs.Watermark for .NET adalah API canggih yang memungkinkan pengembang menambahkan tanda air dengan lancar ke berbagai format dokumen, termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi. Dengan antarmuka intuitif dan fitur ekstensif, GroupDocs.Watermark menyederhanakan proses penambahan tanda air teks atau gambar ke dokumen, memungkinkan pengguna melindungi kekayaan intelektual mereka dan meningkatkan keamanan dokumen dengan mudah.
## Prasyarat
Sebelum mulai menggunakan GroupDocs.Watermark untuk .NET, pastikan Anda memiliki prasyarat berikut:
1. Instalasi: Unduh dan instal GroupDocs.Watermark untuk .NET dari[Unduh Halaman](https://releases.groupdocs.com/Watermark/net/).
2.  Lisensi: Dapatkan lisensi untuk GroupDocs.Watermark untuk .NET. Anda dapat memperoleh lisensi sementara untuk tujuan evaluasi dari[Di Sini](https://purchase.groupdocs.com/temporary-license/) , atau beli lisensi penuh dari[halaman pembelian](https://purchase.groupdocs.com/buy).
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework di mesin pengembangan Anda.
4. Dokumen: Siapkan dokumen yang ingin Anda tambahkan tanda air.

## Impor Namespace
Untuk mulai menggunakan GroupDocs.Watermark untuk .NET, impor namespace yang diperlukan ke dalam proyek Anda:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode Anda ada di sini
}
```
## Langkah 2: Inisialisasi Tanda Air
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Langkah 3: Tambahkan Tanda Air
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Langkah 4: Rasterisasi Halaman
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Langkah 5: Simpan Dokumen
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Kesimpulannya, GroupDocs.Watermark untuk .NET menawarkan solusi sempurna untuk menambahkan tanda air ke PDF dan format dokumen lainnya. Dengan mengikuti panduan langkah demi langkah yang diuraikan di atas, pengembang dapat melakukan rasterisasi halaman PDF secara efisien dan meningkatkan keamanan dokumen dengan mudah.
## FAQ
### Apakah GroupDocs.Watermark kompatibel dengan format dokumen lain selain PDF?
Ya, GroupDocs.Watermark mendukung berbagai format dokumen, termasuk Word, Excel, PowerPoint, Visio, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan tanda air yang ditambahkan ke dokumen?
Sangat! GroupDocs.Watermark menyediakan opsi penyesuaian ekstensif untuk tanda air teks dan gambar, memungkinkan pengguna menyesuaikan font, ukuran, warna, opacity, dan posisi sesuai dengan preferensi mereka.
### Apakah GroupDocs.Watermark cocok untuk penggunaan pribadi dan komersial?
Ya, GroupDocs.Watermark menawarkan opsi lisensi yang fleksibel untuk memenuhi kebutuhan individu dan perusahaan, sehingga cocok untuk proyek pribadi serta aplikasi komersial skala besar.
### Apakah GroupDocs.Watermark menawarkan dukungan teknis untuk pengembang?
Ya, pengembang dapat mengakses dukungan teknis yang komprehensif melalui forum GroupDocs.Watermark, tempat mereka dapat mencari bantuan, berbagi pengalaman, dan berinteraksi dengan sesama pengembang.
### Bisakah saya mencoba GroupDocs.Watermark sebelum melakukan pembelian?
Tentu! Anda dapat memanfaatkan versi uji coba gratis GroupDocs.Watermark dari[halaman rilis](https://releases.groupdocs.com/), memungkinkan Anda menjelajahi fitur dan fungsinya sebelum melakukan pembelian.