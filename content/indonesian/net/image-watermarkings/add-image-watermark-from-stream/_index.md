---
title: Tambahkan Tanda Air Gambar dari Aliran
linktitle: Tambahkan Tanda Air Gambar dari Aliran
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air gambar ke dokumen menggunakan GroupDocs.Watermark untuk .NET. Ikuti panduan langkah demi langkah kami untuk integrasi tanda air yang lancar.
weight: 12
url: /id/net/image-watermarkings/add-image-watermark-from-stream/
type: docs
---
# Tambahkan Tanda Air Gambar dari Aliran

## Perkenalan
Dalam bidang manajemen dan keamanan dokumen, memasukkan tanda air ke dalam file sangatlah penting. Baik itu soal branding, perlindungan hak cipta, atau menjaga integritas dokumen, tanda air memainkan peran penting. Untungnya, GroupDocs.Watermark untuk .NET memberikan solusi tangguh untuk menambah, menghapus, dan mencari tanda air dalam berbagai format dokumen.
## Prasyarat
Sebelum mendalami penerapan tanda air menggunakan GroupDocs.Watermark untuk .NET, pastikan prasyarat berikut terpenuhi:
1.  Instal GroupDocs.Watermark untuk .NET: Unduh dan instal perpustakaan GroupDocs.Watermark untuk .NET dari[tautan unduhan](https://releases.groupdocs.com/Watermark/net/).
2. Akses ke Dokumen: Memiliki akses ke dokumen yang ingin Anda tambahkan atau hapus tanda airnya.
3. Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# diperlukan untuk memahami dan mengimplementasikan cuplikan kode yang disediakan.

## Impor Namespace
Sebelum melanjutkan dengan menambahkan tanda air gambar dari aliran, impor namespace yang diperlukan:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Langkah 1: Tentukan Jalur Dokumen dan Direktori Keluaran
Pertama, tentukan jalur dokumen tempat Anda ingin menambahkan tanda air dan tentukan direktori keluaran untuk dokumen yang diproses.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Langkah 2: Buka Aliran Tanda Air
 Buka file gambar watermark sebagai aliran menggunakan`File.OpenRead` metode.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // Logika pemrosesan tanda air akan ada di sini
}
```
## Langkah 3: Tambahkan Tanda Air ke Dokumen
 Inisialisasi a`Watermarker` objek dengan jalur dokumen, lalu buat`ImageWatermark` objek dengan aliran tanda air yang diperoleh pada Langkah 2. Tambahkan tanda air ke dokumen menggunakan`Add` metode`Watermarker` obyek.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Tambahkan tanda air ke dokumen
        watermarker.Add(watermark);
        // Simpan dokumen dengan tanda air
        watermarker.Save(outputFileName);
    }
}
```

## Kesimpulan
GroupDocs.Watermark untuk .NET memberikan solusi sempurna untuk menambahkan tanda air ke dokumen, memastikan identitas merek, perlindungan hak cipta, dan integritas dokumen. Dengan mengikuti langkah-langkah yang diuraikan dan memanfaatkan cuplikan kode yang disediakan, pengguna dapat dengan mudah memasukkan tanda air ke dalam dokumen mereka.
## FAQ
### Apakah GroupDocs.Watermark kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Watermark mendukung berbagai format dokumen termasuk dokumen Word, spreadsheet Excel, presentasi PowerPoint, PDF, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan dan posisi tanda air?
Tentu saja, GroupDocs.Watermark menawarkan opsi ekstensif untuk menyesuaikan tampilan tanda air, posisi, transparansi, rotasi, dan lainnya untuk memenuhi kebutuhan spesifik.
### Apakah GroupDocs.Watermark menyediakan API untuk menghapus tanda air yang ada?
Ya, GroupDocs.Watermark memungkinkan pengguna tidak hanya menambahkan tanda air tetapi juga menghapus tanda air yang ada dari dokumen dengan mudah.
### Apakah dukungan teknis tersedia untuk pengguna GroupDocs.Watermark?
 Ya, pengguna dapat memanfaatkan dukungan teknis dan bantuan melalui layanan khusus[Forum GroupDocs.Tanda Air](https://forum.groupdocs.com/c/watermark/19).
### Bisakah saya mengevaluasi GroupDocs.Watermark sebelum membeli?
Tentu saja, pengguna dapat memilih uji coba gratis GroupDocs.Watermark untuk menjelajahi fitur dan fungsinya sebelum membuat keputusan pembelian.