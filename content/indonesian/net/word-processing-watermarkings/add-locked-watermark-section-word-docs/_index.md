---
title: Tambahkan Tanda Air Terkunci ke Bagian di Dokumen Word
linktitle: Tambahkan Tanda Air Terkunci ke Bagian di Dokumen Word
second_title: GroupDocs.Tanda Air .NET API
description: Pelajari cara menambahkan tanda air terkunci ke bagian tertentu di dokumen Word menggunakan Groupdocs untuk .NET dengan panduan langkah demi langkah yang komprehensif ini.
weight: 13
url: /id/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---

# Tambahkan Tanda Air Terkunci ke Bagian di Dokumen Word

## Perkenalan
Apakah Anda mencari cara efisien untuk menambahkan tanda air terkunci ke bagian di dokumen Word Anda? Tidak perlu mencari lagi! Dengan Groupdocs.Watermark untuk .NET, Anda dapat menyisipkan tanda air dengan lancar ke dalam dokumen Word sambil memastikan tanda air tetap terkunci dan tahan kerusakan. Alat canggih ini menawarkan beragam fitur untuk memenuhi kebutuhan watermarking Anda, baik untuk tujuan branding, kerahasiaan, atau keamanan. Dalam tutorial langkah demi langkah ini, kami akan memandu Anda tentang cara menambahkan tanda air terkunci ke bagian tertentu dari dokumen Word menggunakan Groupdocs.Watermark untuk .NET. Ayo selami!
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  Groupdocs.Watermark untuk .NET: Pastikan Anda telah menginstal perpustakaan Groupdocs.Watermark. Anda dapat mengunduhnya[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Pastikan Anda telah menyiapkan kerangka .NET di lingkungan pengembangan Anda.
3. IDE: Gunakan Lingkungan Pengembangan Terpadu (IDE) seperti Visual Studio.
4. Dokumen: Dokumen Word (.docx) untuk menerapkan tanda air.
## Impor Namespace
Untuk memulai, Anda harus mengimpor namespace yang diperlukan dalam proyek Anda. Berikut cara melakukannya:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen Anda
 Pertama, Anda perlu memuat dokumen yang ingin Anda tambahkan tanda airnya. Langkah ini melibatkan penentuan jalur dokumen Anda dan memuatnya menggunakan`Watermarker` kelas.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kode watermarking Anda akan ditempatkan di sini.
}
```
## Langkah 2: Buat Tanda Air
Selanjutnya, buat tanda air yang ingin Anda tambahkan ke dokumen Anda. Dalam contoh ini, kita akan membuat tanda air teks dengan pengaturan font dan warna tertentu.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Langkah 3: Konfigurasikan Opsi Tanda Air
Sekarang, konfigurasikan opsi tanda air untuk menentukan indeks bagian dan pengaturan kunci. Ini memastikan tanda air ditambahkan ke bagian yang benar dan terkunci.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // Tambahkan ke bagian pertama
options.IsLocked = true; // Kunci tanda air
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Jenis kunci
```
## Langkah 4: Tambahkan Tanda Air ke Dokumen
 Dengan tanda air dan opsi Anda dikonfigurasi, sekarang saatnya menambahkan tanda air ke dokumen menggunakan`Add` metode`Watermarker` kelas.
```csharp
watermarker.Add(watermark, options);
```
## Langkah 5: Simpan Dokumen yang Dimodifikasi
Terakhir, simpan dokumen dengan tanda air tambahan ke lokasi keluaran yang Anda inginkan.
```csharp
watermarker.Save(outputFileName);
```
## Kesimpulan
Menambahkan tanda air terkunci ke bagian tertentu dalam dokumen Word menggunakan Groupdocs untuk .NET adalah proses yang mudah. Dengan mengikuti langkah-langkah ini, Anda dapat meningkatkan keamanan dan integritas dokumen Anda, memastikan bahwa informasi penting terlindungi. Baik Anda melindungi data sensitif atau menambahkan sentuhan profesional pada dokumen Anda, Groupdocs.Watermark for .NET menyediakan alat yang Anda perlukan untuk mencapai tujuan Anda secara efektif.
## FAQ
### Apa itu Groupdocs.Watermark untuk .NET?
Groupdocs.Watermark for .NET adalah perpustakaan canggih yang memungkinkan pengembang menambahkan tanda air ke berbagai jenis dokumen, termasuk Word, PDF, dan gambar, dengan fitur penyesuaian dan keamanan tingkat lanjut.
### Bisakah saya mengunci tanda air dengan kata sandi?
 Ya, Anda dapat melindungi tanda air dengan kata sandi dengan mengatur`options.Password` properti di`WordProcessingWatermarkSectionOptions` kelas.
### Apakah mungkin untuk menerapkan tanda air yang berbeda pada bagian dokumen yang berbeda?
 Sangat! Dengan pengaturan yang berbeda`SectionIndex` nilai-nilai dalam`WordProcessingWatermarkSectionOptions`, Anda dapat menerapkan tanda air unik ke berbagai bagian dokumen.
### Jenis tanda air apa yang dapat saya tambahkan menggunakan Groupdocs.Watermark?
Groupdocs.Watermark mendukung berbagai jenis tanda air, termasuk tanda air teks, gambar, dan bentuk, menawarkan opsi penyesuaian ekstensif untuk setiap jenis.
### Di mana saya dapat menemukan informasi lebih lanjut tentang Groupdocs.Watermark untuk .NET?
 Untuk informasi lebih lanjut, Anda dapat mengunjungi[dokumentasi](https://tutorials.groupdocs.com/Watermark/net/) Dan[forum dukungan](https://forum.groupdocs.com/c/watermark/19).