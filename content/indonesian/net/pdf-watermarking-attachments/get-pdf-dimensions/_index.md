---
title: Dapatkan Dimensi PDF
linktitle: Dapatkan Dimensi PDF
second_title: GroupDocs.Tanda Air .NET API
description: Lindungi dokumen Anda dengan mudah menggunakan Groupdocs.Watermark untuk .NET. Tambahkan tanda air, stempel, dan anotasi dengan mudah.
weight: 26
url: /id/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# Dapatkan Dimensi PDF

## Perkenalan
Di era digital saat ini, menjaga keamanan dokumen Anda adalah hal yang terpenting. Baik Anda seorang profesional bisnis, pakar hukum, atau seniman kreatif, melindungi kekayaan intelektual Anda sangatlah penting. Groupdocs.Watermark untuk .NET menawarkan solusi tangguh untuk menambahkan tanda air, stempel, dan anotasi ke dokumen Anda, memastikan keamanan dan keasliannya.
## Prasyarat
Sebelum mendalami dunia Groupdocs.Watermark untuk .NET, pastikan Anda memiliki prasyarat berikut:
1.  Instalasi Groupdocs.Watermark untuk .NET: Unduh dan instal Groupdocs.Watermark untuk .NET dari[tautan unduhan](https://releases.groupdocs.com/Watermark/net/).
2.  Kunci Lisensi (Opsional): Meskipun Groupdocs.Watermark untuk .NET menawarkan uji coba gratis, Anda dapat memilih lisensi sementara atau membeli lisensi penuh dari[Di Sini](https://purchase.groupdocs.com/buy) untuk fungsionalitas yang diperluas.
3. Keakraban dengan C#: Pengetahuan dasar bahasa pemrograman C# disarankan untuk memahami dan menerapkan contoh yang diberikan.
4. Dokumen untuk Dilindungi: Siapkan contoh dokumen (misalnya PDF, Word, Excel) di mesin lokal Anda untuk bereksperimen.

## Impor Namespace
Untuk mulai bekerja dengan Groupdocs.Watermark untuk .NET, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Langkah 1: Deklarasikan Variabel
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Langkah 2: Muat Dokumen
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Langkah 3: Dapatkan Konten PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Langkah 4: Ambil Dimensi
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Kesimpulan
Kesimpulannya, Groupdocs.Watermark untuk .NET menawarkan solusi komprehensif untuk melindungi dokumen Anda dari penggunaan dan distribusi yang tidak sah. Dengan mengikuti langkah-langkah yang diuraikan di atas dan memanfaatkan kekuatan Groupdocs.Watermark untuk .NET, Anda dapat memastikan keamanan dan integritas aset digital Anda yang berharga.
## FAQ
### Bisakah saya menggunakan Groupdocs.Watermark untuk .NET secara gratis?
Ya, Groupdocs.Watermark untuk .NET menawarkan versi uji coba gratis untuk tujuan evaluasi. Namun, untuk fungsionalitas yang lebih luas, Anda dapat mempertimbangkan untuk membeli lisensi penuh.
### Apakah Groupdocs.Watermark mendukung berbagai format dokumen?
Ya, Groupdocs. Watermark mendukung berbagai format dokumen termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menyesuaikan tanda air dan stempel dengan Groupdocs.Watermark?
Sangat! Groupdocs.Watermark menyediakan opsi penyesuaian ekstensif untuk tanda air, stempel, dan anotasi agar sesuai dengan kebutuhan spesifik Anda.
### Apakah dukungan teknis tersedia untuk pengguna Groupdocs.Watermark?
 Ya, Anda bisa mendapatkan bantuan teknis dan terlibat dengan komunitas Groupdocs melalui[forum dukungan](https://forum.groupdocs.com/c/watermark/19).
### Bagaimana saya bisa mendapatkan lisensi sementara untuk Groupdocs.Watermark?
 Anda dapat memperoleh lisensi sementara untuk Groupdocs.Watermark dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).