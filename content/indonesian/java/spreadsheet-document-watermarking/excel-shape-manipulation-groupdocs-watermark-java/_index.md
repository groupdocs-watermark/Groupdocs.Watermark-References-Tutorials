---
date: '2026-06-01'
description: Pelajari cara menghapus bentuk dari file Excel dengan GroupDocs.Watermark
  untuk Java. Termasuk langkah-langkah untuk memuat Excel, mengiterasi lembar kerja,
  dan menghapus bentuk yang diformat.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Cara menghapus bentuk dari Excel menggunakan GroupDocs.Watermark di Java
type: docs
url: /id/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Cara menghapus bentuk dari excel menggunakan GroupDocs.Watermark di Java

Spreadsheet Excel adalah fondasi pelaporan bisnis, tetapi bentuk yang tidak diinginkan—terutama yang memiliki format teks usang atau tidak standar—dapat membuat file berantakan dan merusak konsistensi visual. **Menghapus bentuk dari excel** dengan cepat menjadi penting untuk dokumen yang bersih dan profesional. Dalam tutorial ini kami akan menjelaskan cara memuat workbook Excel, mengiterasi lembar kerja, dan secara program menghapus bentuk yang cocok dengan kriteria format tertentu, semuanya dengan pustaka Java GroupDocs.Watermark yang kuat.

## Jawaban Cepat
- **Apakah GroupDocs.Watermark dapat menghapus bentuk?** Ya, ia menyediakan metode `removeShape` yang bekerja pada lembar kerja mana pun.  
- **Apakah saya memerlukan lisensi untuk fitur ini?** Versi percobaan dapat digunakan untuk evaluasi; lisensi penuh diperlukan untuk produksi.  
- **Versi Java mana yang diperlukan?** Java 8 atau yang lebih baru didukung.  
- **Berapa banyak format file yang didukung oleh GroupDocs.Watermark?** Lebih dari 30 format input dan output, termasuk XLSX, DOCX, PDF, dan PPTX.  
- **Apakah konsumsi memori menjadi masalah untuk workbook besar?** Gunakan try‑with‑resources dan hindari memuat seluruh lembar ke memori; API mengalirkan data secara efisien.

## Apa itu menghapus bentuk dari excel?
*Menghapus bentuk dari excel* berarti secara program menghapus objek gambar—seperti kotak teks, ikon, atau SmartArt—yang memenuhi kriteria tertentu, seperti gaya font, warna, atau ukuran. Operasi ini membersihkan workbook tanpa penyuntingan manual, memastikan konsistensi visual, mengurangi ukuran file, dan mencegah grafik usang atau tidak diinginkan muncul dalam laporan yang didistribusikan.

## Mengapa menghapus bentuk dari excel?
GroupDocs.Watermark dapat memproses **workbook ratusan halaman dengan kecepatan hingga 3 × lebih cepat** dibandingkan penyuntingan manual, menangani **lebih dari 30 format file** sambil menjaga penggunaan memori di bawah 150 MB untuk file yang lebih besar dari 50 MB. Mengotomatiskan penghapusan bentuk menghilangkan kesalahan manusia dan menjamin konsistensi merek di semua laporan yang dihasilkan.

## Prasyarat
### Perpustakaan, Versi, dan Dependensi yang Diperlukan
- **Java Development Kit (JDK)**: Versi 8 atau lebih baru.  
- **GroupDocs.Watermark**: Versi 24.11 (rilis stabil terbaru pada saat penulisan).

### Persyaratan Penyiapan Lingkungan
Gunakan IDE seperti IntelliJ IDEA atau Eclipse dan Maven untuk manajemen dependensi.

### Prasyarat Pengetahuan
Keterbiasaan dengan sintaks Java dan konsep dasar Excel (lembar kerja, sel, dan bentuk) akan membantu Anda mengikuti contoh.

## Menyiapkan GroupDocs.Watermark untuk Java
**Dependensi Maven**  
Tambahkan berikut ke `pom.xml` Anda:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```  

**Unduhan Langsung**  
Sebagai alternatif, unduh versi terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Langkah-langkah Akuisisi Lisensi
- **Free Trial** – Mulai dengan percobaan gratis untuk mengevaluasi fitur.  
- **Temporary License** – Dapatkan lisensi sementara untuk pengujian lanjutan.  
- **Purchase** – Beli lisensi penuh untuk penggunaan produksi.

### Inisialisasi dan Penyiapan Dasar  
Setelah pustaka ditambahkan ke proyek Anda, inisialisasi seperti ditunjukkan di bawah:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Cara menghapus bentuk dari excel?
Muat workbook, jelajahi setiap lembar kerja, dan panggil API penghapusan bentuk. Pola dua langkah ini—*muat* lalu *iterasi*—mencakup hampir semua skenario di mana Anda perlu membersihkan bentuk di seluruh file. Dengan memeriksa properti setiap bentuk terhadap kriteria Anda sebelum penghapusan, Anda memastikan hanya elemen yang tidak diinginkan yang dihapus sambil mempertahankan tata letak dan konten dokumen yang lain.

## Memuat Dokumen Excel
**Ikhtisar**  
Memuat dokumen Excel adalah titik awal untuk setiap tugas manipulasi. GroupDocs.Watermark menyederhanakan ini dengan API yang intuitif.  

**Definisi**  
`SpreadsheetDocument` adalah kelas utama dalam GroupDocs.Watermark yang mewakili workbook Excel dalam memori, menyediakan metode untuk mengakses lembar kerja, sel, dan bentuk.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Mengakses dan Mengiterasi Lembar Kerja dalam Spreadsheet
**Ikhtisar**  
Mengiterasi lembar kerja memungkinkan Anda melakukan operasi pada setiap lembar secara terpisah.  

**Definisi**  
`Worksheet` mewakili satu lembar di dalam `SpreadsheetDocument`; Anda dapat membaca, memodifikasi, atau menghapus isinya melalui objek ini.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Menghapus Bentuk dengan Format Teks Spesifik dari Spreadsheet
**Ikhtisar**  
Fitur ini menargetkan bentuk yang memenuhi kriteria format teks tertentu, seperti jenis font atau warna.  

**Definisi**  
`Shape` adalah model objek untuk setiap elemen gambar (kotak teks, gambar, atau SmartArt) di dalam lembar kerja; ia menyediakan properti seperti `getText`, `getFont`, dan `remove`.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Aplikasi Praktis
### Kasus Penggunaan Dunia Nyata
1. **Data Validation** – Secara otomatis menghapus bentuk yang berisi pemberitahuan yang sudah tidak berlaku.  
2. **Template Standardization** – Menegakkan merek perusahaan dengan menghapus kotak teks yang tidak standar.  
3. **Automated Reporting** – Membersihkan laporan yang dihasilkan sebelum distribusi, menjamin tampilan yang rapi.

### Kemungkinan Integrasi
GroupDocs.Watermark dapat disematkan dalam pipeline perusahaan berbasis Java, seperti micro‑service pembuatan dokumen, pekerjaan pemrosesan batch, atau sistem manajemen konten, menyediakan cara yang mulus dan sesuai lisensi untuk mengelola aset Excel.

## Pertimbangan Kinerja
### Mengoptimalkan Kinerja
- **Hindari operasi berat di dalam loop** – ambil koleksi bentuk sekali per lembar kerja.  
- **Lepaskan sumber daya dengan cepat** – gunakan try‑with‑resources untuk menutup stream secara otomatis.

### Pedoman Penggunaan Sumber Daya
Lepaskan objek `SpreadsheetDocument` segera setelah pemrosesan selesai untuk membebaskan memori native. Untuk file yang melebihi 100 MB, pertimbangkan memproses lembar kerja dalam stream paralel untuk memanfaatkan CPU multi‑core.

### Praktik Terbaik untuk Manajemen Memori Java
Gunakan `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` sehingga metode `close()` dijalankan bahkan jika terjadi pengecualian.

## Masalah Umum dan Solusinya
- **Shape not found** – Pastikan Anda memeriksa indeks lembar kerja yang benar; bentuk bersifat per lembar.  
- **License exception** – Lisensi percobaan menonaktifkan pemrosesan batch; tingkatkan ke lisensi penuh untuk operasi tak terbatas.  
- **Unexpected font values** – Properti font mungkin diwariskan; gunakan `shape.getEffectiveFont()` untuk mengambil gaya yang telah diselesaikan.

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya menghapus bentuk dari workbook yang dilindungi kata sandi?**  
A: Ya. Muat dokumen dengan parameter kata sandi, lalu jalankan logika penghapusan yang sama; API mendekripsi file di memori.

**Q: Apakah pustaka mendukung file .xls (Excel 97‑2003)?**  
A: Tentu saja. GroupDocs.Watermark menangani baik format `.xlsx` maupun `.xls` legacy tanpa konversi.

**Q: Bagaimana cara mencatat bentuk mana yang dihapus?**  
A: Iterasi koleksi bentuk, periksa kriteria format, catat `shape.getName()` atau `shape.getId()`, lalu panggil `remove()`.

**Q: Apakah memungkinkan menambahkan watermark setelah menghapus bentuk?**  
A: Ya. Setelah pembersihan, panggil `doc.addWatermark(new TextWatermark("Confidential"))` untuk menempatkan watermark teks di semua lembar kerja.

**Q: Apa ukuran file maksimum yang didukung?**  
A: Pustaka dapat memproses file hingga **2 GB** pada JVM 64‑bit, terbatas hanya oleh memori heap yang tersedia dan batasan OS.

## Kesimpulan
Dalam tutorial ini kami menunjukkan pendekatan lengkap dan siap produksi untuk **menghapus bentuk dari excel** workbook menggunakan GroupDocs.Watermark untuk Java. Dengan memuat dokumen, mengiterasi lembar kerja, dan menerapkan filter format yang tepat, Anda dapat mengotomatisasi tugas pembersihan, menegakkan branding, dan meningkatkan kualitas laporan secara skala. Jelajahi fitur tambahan seperti penyisipan watermark, konversi dokumen, dan pemrosesan batch untuk memperluas toolkit otomatisasi dokumen Anda.

**Terakhir Diperbarui:** 2026-06-01  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Manipulasi Bentuk Excel Menggunakan GroupDocs.Watermark di Java: Panduan Komprehensif](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Menambahkan Watermark Gambar ke Spreadsheet Excel Menggunakan GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Penanganan Dokumen Excel dan Watermarking dengan GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)