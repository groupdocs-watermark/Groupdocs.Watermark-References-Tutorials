---
title: Tambahkan Tanda Air Terkunci ke Semua Halaman di Dokumen Word
linktitle: Tambahkan Tanda Air Terkunci ke Semua Halaman di Dokumen Word
second_title: GroupDocs.Tanda Air .NET API
description: Amankan dokumen Anda dengan menambahkan tanda air terkunci menggunakan Groupdocs.Watermark untuk .NET. Ikuti panduan langkah demi langkah kami untuk kemudahan penerapan.
weight: 11
url: /id/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---
## Perkenalan
Menambahkan tanda air ke dokumen Anda adalah langkah penting dalam mengamankan dan memberi merek pada konten Anda. Baik Anda mencegah penggunaan tidak sah atau sekadar menambahkan sentuhan profesional, tanda air dapat memiliki banyak tujuan. Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan tanda air terkunci ke semua halaman dokumen Word menggunakan Groupdocs.Watermark untuk .NET.
## Prasyarat
Sebelum kita mendalami panduan langkah demi langkah, pastikan Anda memiliki semua yang Anda butuhkan:
1. Groupdocs.Watermark untuk .NET: Unduh versi terbaru dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework di mesin Anda.
3. Lingkungan Pengembangan: Lingkungan pengembangan seperti Visual Studio.
4.  Lisensi: Anda dapat memilih a[uji coba gratis](https://releases.groupdocs.com/) atau membeli a[izin sementara](https://purchase.groupdocs.com/temporary-license/).
## Impor Namespace
Hal pertama yang pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda. Ini penting untuk mengakses kelas dan metode yang disediakan oleh Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Siapkan Proyek Anda

Buka lingkungan pengembangan Anda dan buat proyek .NET baru. Ini bisa berupa aplikasi konsol atau jenis lainnya yang sesuai dengan kebutuhan Anda.

Anda perlu menambahkan paket Groupdocs.Watermark ke proyek Anda. Ini dapat dilakukan melalui Manajer Paket NuGet. Jalankan perintah berikut di Konsol Manajer Paket NuGet:
```sh
Install-Package GroupDocs.Watermark
```
## Langkah 2: Muat Dokumen Word
### Tentukan Jalur Dokumen
Tentukan jalur ke dokumen Word Anda. Ini akan menjadi dokumen tempat Anda ingin menambahkan tanda air.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Atur Opsi Muat
 Buat sebuah contoh dari`WordProcessingLoadOptions` untuk memuat dokumen Word Anda dengan opsi spesifik.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Langkah 3: Buat Tanda Air
### Inisialisasi Penanda Air
 Menggunakan`Watermarker`kelas, muat dokumen dengan opsi pemuatan yang ditentukan.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Langkah selanjutnya akan ada di dalam blok penggunaan ini
}
```
### Tentukan Properti Tanda Air
 Membuat`TextWatermark` Misalnya dengan teks, font, dan warna yang Anda inginkan.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Langkah 4: Terapkan Tanda Air ke Semua Halaman
### Tetapkan Opsi Tanda Air
 Mendefinisikan`WordProcessingWatermarkPagesOptions` dan atur`IsLocked` properti ke true untuk mengunci tanda air. Hal ini memastikan bahwa tanda air tidak dapat dihilangkan dengan mudah.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Opsional: Tambahkan Perlindungan Kata Sandi
Jika Anda ingin menambahkan lapisan keamanan ekstra, Anda dapat mengatur kata sandi untuk tanda air tersebut.
```csharp
// Untuk melindungi dengan kata sandi
// pilihan.Kata Sandi = "7654321";
```
### Tambahkan Tanda Air
 Menggunakan`Add` metode`Watermarker` kelas untuk menambahkan tanda air ke dokumen dengan opsi yang ditentukan.
```csharp
watermarker.Add(watermark, options);
```
## Langkah 5: Simpan Dokumen
Terakhir, simpan dokumen yang dimodifikasi ke file keluaran yang ditentukan.
```csharp
watermarker.Save(outputFileName);
```

## Kesimpulan
Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah menambahkan tanda air terkunci ke semua halaman dokumen Word Anda menggunakan Groupdocs.Watermark untuk .NET. Ini tidak hanya membantu melindungi dokumen Anda dari penggunaan tidak sah tetapi juga menambahkan sentuhan profesional pada konten Anda. Groupdocs.Watermark menawarkan solusi komprehensif untuk kebutuhan watermarking, memastikan dokumen Anda tetap aman dan bermerek.
## FAQ
### Bisakah saya menggunakan gambar sebagai tanda air dan bukan teks?
 Ya, Groupdocs mendukung tanda air teks dan gambar. Anda bisa menggantinya`TextWatermark` dengan`ImageWatermark` dan tentukan gambar Anda.
### Apakah posisi watermark bisa disesuaikan?
 Sangat! Anda dapat mengatur posisi watermark menggunakan properti seperti`HorizontalAlignment` Dan`VerticalAlignment`.
### Bisakah saya menerapkan tanda air yang berbeda pada halaman dokumen yang berbeda?
 Ya, Anda dapat menyesuaikan tanda air untuk halaman tertentu menggunakan`PageIndex` properti di`WordProcessingWatermarkPagesOptions`.
### Apakah Groupdocs.Watermark mendukung format dokumen lain selain Word?
Ya, Groupdocs mendukung berbagai format termasuk PDF, Excel, PowerPoint, dan lainnya.
### Apa saja persyaratan sistem untuk menggunakan Groupdocs.Watermark?
Anda memerlukan sistem dengan .NET Framework terinstal dan lingkungan pengembangan seperti Visual Studio.