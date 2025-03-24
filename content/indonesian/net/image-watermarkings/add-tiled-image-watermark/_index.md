---
title: Tambahkan Tanda Air Gambar Berubin
linktitle: Tambahkan Tanda Air Gambar Berubin
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air gambar bersusun ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET. Mudah, efisien, dan dapat disesuaikan.
weight: 10
url: /id/net/image-watermarkings/add-tiled-image-watermark/
---
## Perkenalan
GroupDocs.Watermark for .NET adalah API canggih yang memungkinkan pengembang menambahkan, menghapus, dan mencari tanda air dalam berbagai format dokumen secara terprogram. Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan tanda air gambar ubin ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
- Pengetahuan dasar bahasa pemrograman C#.
- Visual Studio diinstal pada sistem Anda.
- GroupDocs.Watermark untuk perpustakaan .NET ditambahkan ke proyek Anda. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).

## Impor Namespace
Pastikan untuk mengimpor namespace yang diperlukan di awal file C# Anda:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Langkah 1: Tetapkan Jalur Dokumen dan Direktori Keluaran
Tentukan jalur dokumen masukan Anda dan direktori tempat Anda ingin menyimpan dokumen keluaran:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Mengganti`"Your Document Path"` dengan jalur absolut atau relatif ke dokumen masukan Anda.
## Langkah 2: Inisialisasi Objek Watermarker
Buat objek Watermarker menggunakan jalur dokumen masukan:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Tambahkan tanda air di sini
}
```
## Langkah 3: Tambahkan Tanda Air Gambar Berubin
Buat instance objek ImageWatermark dengan jalur ke file gambar yang ingin Anda gunakan sebagai tanda air:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Konfigurasikan opsi ubin
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Tambahkan tanda air ke dokumen
    watermarker.Add(watermark);
    // Simpan dokumen yang diubah
    watermarker.Save(outputFileName);
}
```
 Mengganti`"Path to Your Image"` dengan jalur sebenarnya ke file gambar tanda air Anda.

## Kesimpulan
Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah menambahkan tanda air gambar ubin ke dokumen Anda menggunakan GroupDocs.Watermark untuk .NET. Bereksperimenlah dengan berbagai opsi dan konfigurasi untuk mencapai hasil yang diinginkan.
## FAQ
### Bisakah saya menambahkan beberapa tanda air ke satu dokumen?
Ya, Anda dapat menambahkan beberapa tanda air dari jenis yang berbeda ke dokumen menggunakan GroupDocs.Watermark untuk .NET.
### Apakah GroupDocs.Watermark mendukung semua format dokumen?
GroupDocs.Watermark mendukung berbagai format dokumen, termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Watermark?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bisakah saya menyesuaikan tampilan tanda air?
Ya, Anda dapat menyesuaikan berbagai aspek tanda air, seperti posisi, ukuran, rotasi, transparansi, dll.
### Apakah GroupDocs.Watermark menawarkan dukungan teknis?
 Ya, Anda bisa mendapatkan dukungan teknis dari forum GroupDocs.Watermark[Di Sini](https://forum.groupdocs.com/c/watermark/19).