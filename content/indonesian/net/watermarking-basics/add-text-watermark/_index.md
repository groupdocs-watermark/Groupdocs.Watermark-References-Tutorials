---
title: Tambahkan Tanda Air Teks
linktitle: Tambahkan Tanda Air Teks
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air teks ke dokumen Anda menggunakan Groupdocs untuk .NET dengan panduan langkah demi langkah ini.
weight: 11
url: /id/net/watermarking-basics/add-text-watermark/
type: docs
---
# Tambahkan Tanda Air Teks

## Perkenalan
GroupDocs.Watermark untuk .NET adalah perpustakaan canggih yang memungkinkan pengembang menambahkan, mencari, dan menghapus tanda air dari berbagai format dokumen dalam aplikasi .NET. Dalam tutorial ini, kita akan fokus menambahkan tanda air teks ke dokumen menggunakan GroupDocs.Watermark.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1. Pengetahuan dasar bahasa pemrograman C#.
2. Visual Studio diinstal pada sistem Anda.
3.  GroupDocs.Watermark untuk perpustakaan .NET diinstal. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Langkah 1: Tentukan Jalur Dokumen dan Direktori Keluaran
Tentukan jalur ke dokumen masukan Anda dan direktori keluaran tempat dokumen yang diberi tanda air akan disimpan.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"` dengan jalur absolut atau relatif ke dokumen masukan Anda, misalnya:`@"C:\Docs\document.pdf"`. Tentukan juga direktori tempat Anda ingin menyimpan dokumen yang diberi watermark.
## Langkah 2: Tambahkan Tanda Air Teks
 Buat instance`Watermarker` kelas dengan jalur dokumen input. Kemudian, buat a`TextWatermark` objek dengan pengaturan teks dan font yang diinginkan.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan tanda air teks ke dokumen menggunakan GroupDocs.Watermark untuk .NET. Dengan API intuitifnya, pengembang dapat dengan mudah memanipulasi tanda air dalam berbagai format dokumen.
## FAQ
### Apakah GroupDocs.Watermark untuk .NET kompatibel dengan semua format dokumen?
GroupDocs.Watermark mendukung berbagai format dokumen termasuk PDF, Microsoft Word, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan tanda air teks?
Ya, Anda dapat menyesuaikan berbagai properti seperti font, warna, perataan, dan opasitas tanda air teks.
### Apakah GroupDocs.Watermark menyediakan dukungan untuk menghilangkan tanda air dari dokumen?
Ya, GroupDocs.Watermark menawarkan fungsionalitas untuk mencari dan menghapus tanda air dari dokumen.
### Bisakah saya mencoba GroupDocs.Watermark untuk .NET sebelum membeli?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Watermark?
 Anda bisa mendapatkan dukungan teknis dengan mengunjungi[Forum GroupDocs.Tanda Air](https://forum.groupdocs.com/c/watermark/19).