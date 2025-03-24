---
title: Tambahkan Tanda Air ke Artefak Gambar di PDF
linktitle: Tambahkan Tanda Air ke Artefak Gambar di PDF
second_title: GroupDocs.Tanda Air .NET API
description: Lindungi file PDF Anda dengan tanda air yang dipersonalisasi menggunakan GroupDocs.Watermark untuk .NET. Tambahkan tanda air teks atau gambar dengan mudah ke artefak gambar di dokumen PDF.
weight: 18
url: /id/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---

# Tambahkan Tanda Air ke Artefak Gambar di PDF

## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan tanda air ke artefak gambar dalam dokumen PDF menggunakan GroupDocs.Watermark untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat melindungi file PDF Anda secara efisien dengan tanda air yang dipersonalisasi.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Watermark for .NET: Unduh dan instal pustaka GroupDocs.Watermark for .NET dari[Di Sini](https://releases.groupdocs.com/Watermark/net/).
2. Jalur Dokumen: Memiliki jalur ke dokumen PDF tempat Anda ingin menambahkan tanda air.
3. Direktori Output: Buat direktori tempat dokumen yang diberi watermark akan disimpan.

## Impor Namespace
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Langkah 1: Muat Dokumen dan Inisialisasi Watermarker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Langkah 2: Dapatkan Konten PDF dan Tambahkan Tanda Air
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Inisialisasi tanda air gambar atau teks
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Tambahkan tanda air ke gambar
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Langkah 3: Simpan Dokumen yang diberi Watermark
```csharp
	watermarker.Save(outputFileName);
}
```

## Kesimpulan
Dengan GroupDocs.Watermark untuk .NET, menambahkan tanda air ke artefak gambar dalam dokumen PDF menjadi proses yang lancar. Dengan mengikuti tutorial ini, Anda dapat secara efisien melindungi file PDF Anda dengan tanda air yang disesuaikan, memastikan keamanan dan keasliannya.
## FAQ
### Bisakah saya menambahkan tanda air gambar dan teks ke dokumen PDF saya?
Ya, GroupDocs.Watermark untuk .NET mendukung penambahan tanda air gambar dan teks secara bersamaan.
### Apakah ada batasan jumlah tanda air yang dapat saya tambahkan ke dokumen?
Tidak, Anda dapat menambahkan beberapa tanda air ke dokumen tanpa batasan apa pun.
### Bisakah saya menyesuaikan tampilan dan posisi tanda air?
Tentu saja, Anda memiliki kendali penuh atas tampilan, posisi, dan properti tanda air.
### Apakah GroupDocs.Watermark untuk .NET mendukung format dokumen lain selain PDF?
Ya, ini mendukung berbagai format dokumen termasuk Word, Excel, PowerPoint, dan lainnya.
### Apakah ada cara untuk menghilangkan tanda air dari dokumen?
Ya, GroupDocs.Watermark untuk .NET menyediakan metode untuk menghapus tanda air dari dokumen jika diperlukan.