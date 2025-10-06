---
title: Tambahkan Tanda Air ke PDF
linktitle: Tambahkan Tanda Air ke PDF
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air teks dan gambar ke PDF Anda menggunakan GroupDocs.Watermark untuk .NET dengan panduan langkah demi langkah komprehensif kami.
weight: 14
url: /id/net/pdf-watermarking-attachments/add-watermarks-pdf/
type: docs
---
# Tambahkan Tanda Air ke PDF

## Perkenalan
Apakah Anda ingin menambahkan tanda air ke PDF untuk melindungi dokumen Anda atau memberi merek dengan logo Anda? Tidak perlu mencari lagi! Dalam tutorial ini, kita akan mendalami proses penggunaan GroupDocs.Watermark untuk .NET guna menambahkan tanda air teks dan gambar ke file PDF Anda. Baik Anda seorang pengembang berpengalaman atau baru memulai, panduan ini akan memandu Anda melalui setiap langkah, memastikan Anda dapat menerapkan tanda air dengan mudah dan tepat.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki semua yang perlu Anda ikuti bersama dengan tutorial ini:
-  GroupDocs.Watermark untuk .NET: Pastikan Anda menginstal versi terbaru. Kamu bisa[Unduh di sini](https://releases.groupdocs.com/Watermark/net/).
- Lingkungan Pengembangan .NET: Visual Studio atau IDE lain yang mendukung .NET.
- Pengetahuan Dasar C#: Memahami dasar-dasar pemrograman C# akan membantu Anda mengikuti langkah-langkah dengan mudah.
- Dokumen PDF: Siapkan contoh dokumen PDF untuk diberi tanda air.
- Gambar untuk Tanda Air: Jika Anda menambahkan tanda air gambar, siapkan file gambar Anda.
## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda. Ini akan memungkinkan Anda mengakses fungsionalitas GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Sekarang, mari kita bagi prosesnya menjadi langkah-langkah yang dapat dikelola.
## Langkah 1: Muat Dokumen PDF Anda
Langkah pertama adalah memuat dokumen PDF Anda ke dalam watermarker. Inilah cara Anda melakukannya:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Langkah lebih lanjut akan ditambahkan di sini
}
```
## Langkah 2: Tambahkan Tanda Air Teks ke Halaman Pertama
Selanjutnya, kami akan menambahkan tanda air teks ke halaman pertama PDF Anda. Ikuti petunjuk berikut:
```csharp
// Tambahkan tanda air teks ke halaman pertama
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Menambahkan tanda air teks dapat membantu melindungi dokumen Anda dari penggunaan tidak sah atau sekadar memberi merek pada dokumen tersebut. Bayangkan mencap dokumen Anda dengan segel keaslian yang tidak terlihat.
## Langkah 3: Tambahkan Tanda Air Gambar ke Halaman Kedua
Sekarang, mari tambahkan watermark gambar ke halaman kedua. Ini sangat berguna untuk logo atau tanda air grafis apa pun.
```csharp
// Tambahkan tanda air gambar ke halaman kedua
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Tanda air gambar dapat membuat dokumen Anda terlihat profesional dan memastikan merek Anda selalu terlihat. Ini seperti menambahkan tanda tangan Anda ke setiap halaman.
## Langkah 4: Simpan PDF yang diberi Watermark
Setelah menambahkan watermark, langkah terakhir adalah menyimpan PDF yang diberi watermark ke lokasi yang Anda inginkan.
```csharp
watermarker.Save(outputFileName);
```
Menyimpan dokumen akan menyelesaikan semua perubahan yang Anda buat. Inilah saatnya upaya Anda dipadatkan menjadi hasil nyata, siap digunakan atau didistribusikan.
## Kesimpulan
Selamat! Anda telah berhasil menambahkan tanda air teks dan gambar ke PDF Anda menggunakan GroupDocs.Watermark untuk .NET. Proses ini tidak hanya mudah tetapi juga sangat dapat disesuaikan agar sesuai dengan kebutuhan spesifik Anda. Baik Anda melindungi dokumen atau memberi merek pada dokumen, tanda air adalah alat ampuh yang dapat Anda gunakan.
## FAQ
### Bisakah saya menambahkan beberapa tanda air ke halaman yang sama?
 Ya, Anda dapat menambahkan beberapa tanda air ke halaman yang sama dengan memanggil`Add` metode beberapa kali dengan objek tanda air yang berbeda.
### Bagaimana cara menyesuaikan tampilan tanda air teks?
 Anda dapat menyesuaikan tanda air teks dengan menyesuaikan properti seperti font, ukuran, warna, dan opacity menggunakan`TextWatermark` obyek.
### Apakah mungkin untuk memberi tanda air hanya pada halaman tertentu dari PDF?
 Ya, Anda dapat menentukan halaman mana yang akan diberi tanda air dengan mengatur`PageIndex` properti di`PdfArtifactWatermarkOptions`.
### Bisakah saya menghapus tanda air dari PDF?
Ya, GroupDocs.Watermark menyediakan fungsionalitas untuk mencari dan menghapus tanda air dari dokumen PDF.
### Bagaimana cara mendapatkan lisensi sementara untuk GroupDocs.Watermark?
Anda bisa mendapatkan lisensi sementara dengan mengunjungi[halaman lisensi sementara](https://purchase.groupdocs.com/temporary-license/).