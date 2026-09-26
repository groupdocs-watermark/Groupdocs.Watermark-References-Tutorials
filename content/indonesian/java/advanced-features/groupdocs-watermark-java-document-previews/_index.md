---
date: '2026-09-26'
description: Pelajari cara mengonversi dokumen ke gambar dan menghasilkan thumbnail
  dengan Java menggunakan GroupDocs.Watermark. Panduan langkah demi langkah mencakup
  setup, preview streams, dan performance tips.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Pelajari cara mengonversi dokumen ke gambar dan menghasilkan thumbnail
  dengan Java menggunakan GroupDocs.Watermark. Panduan ini memandu Anda melalui installation,
  stream handling, dan performance optimisation untuk fast preview creation.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Konversi dokumen ke gambar dengan GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Konversi dokumen ke gambar dengan GroupDocs.Watermark Java
type: docs
url: /id/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Mengonversi dokumen ke gambar dengan GroupDocs.Watermark Java

Membuat pratinjau gambar ringan dari dokumen multi‑halaman adalah kebutuhan umum untuk portal, sistem manajemen konten, dan layanan penyimpanan cloud. Dengan **convert document to image** Anda memberikan pengguna akhir petunjuk visual cepat tanpa beban memuat file lengkap. Pustaka GroupDocs.Watermark Java tidak hanya menambahkan watermark tetapi juga menyediakan mesin pratinjau berperforma tinggi yang dapat **java generate thumbnails** untuk setiap halaman dalam satu kali proses.

Dalam tutorial ini Anda akan belajar cara menyiapkan pustaka, membuat aliran halaman khusus, melepaskan sumber daya dengan aman, dan akhirnya menghasilkan pratinjau gambar untuk setiap halaman dokumen sumber. Instruksi ditulis untuk pengembang yang familiar dengan Java dan konsep berorientasi objek, serta mencakup tip praktik terbaik untuk menangani batch file besar.

## Jawaban cepat
- **Apa langkah pertama?** Tambahkan dependensi Maven GroupDocs.Watermark dan inisialisasi `Watermarker` dengan path file sumber.  
- **Bagaimana gambar pratinjau dibuat?** Implementasikan `ICreatePageStream` untuk membuka output stream untuk setiap halaman, kemudian panggil `generatePreview()` dengan opsi yang sesuai.  
- **Apakah saya memerlukan lisensi?** Versi percobaan berfungsi untuk skenario dasar, tetapi lisensi penuh menghapus watermark dan membuka pemrosesan batch.  
- **Bisakah saya memproses PDF lebih besar dari 200 halaman?** Ya – pustaka men‑stream halaman, sehingga penggunaan memori tetap rendah bahkan untuk file 500 halaman.  
- **Format gambar apa yang didukung?** PNG, JPEG, BMP, dan TIFF tersedia secara langsung.

## Apa itu convert document to image?
Frasa **convert document to image** menggambarkan proses merender setiap halaman file sumber (PDF, DOCX, PPTX, dll.) menjadi gambar raster seperti PNG atau JPEG. Konversi ini berguna untuk galeri thumbnail, panel pratinjau, dan penampil dokumen yang ramah seluler.

## Mengapa menggunakan GroupDocs.Watermark untuk pembuatan pratinjau?
GroupDocs.Watermark mendukung **lebih dari 30 format input** dan dapat menghasilkan pratinjau untuk dokumen hingga **500 halaman** tanpa memuat seluruh file ke memori. Secara internal ia memproses halaman secara berurutan, yang menjaga penggunaan heap Java di bawah 50 MB bahkan untuk PDF besar. Pustaka juga menawarkan optimasi gambar bawaan, memungkinkan Anda menentukan DPI, kedalaman warna, dan tingkat kompresi, yang menghasilkan thumbnail biasanya **70 % lebih kecil** dibandingkan rasterisasi sederhana.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki hal‑hal berikut:

- **Java Development Kit (JDK) 11 atau lebih baru** – pustaka dikompilasi untuk Java 8+, tetapi JDK 11 memberikan dukungan jangka panjang dan kinerja yang lebih baik.
- **Maven 3.6+** – untuk manajemen dependensi.
- **GroupDocs.Watermark for Java versi 24.11** – rilis stabil terbaru pada saat penulisan.
- **Pengetahuan dasar tentang Java I/O streams** – Anda akan membuat objek `FileOutputStream` untuk setiap halaman pratinjau.
- **Kunci lisensi** (opsional untuk produksi) – versi percobaan membatasi ukuran pratinjau hingga 5 MB per dokumen.

## Cara menyiapkan GroupDocs.Watermark untuk Java

Untuk menyiapkan GroupDocs.Watermark, pertama tambahkan repositori Maven dan kemudian sertakan pustaka sebagai dependensi di `pom.xml` proyek Anda. Ini memastikan Maven dapat mengunduh artefak yang tepat dan membuat kelas tersedia di classpath untuk kompilasi dan runtime.

### Tambahkan dependensi Maven

Pustaka didistribusikan melalui Maven Central. Tambahkan potongan kode berikut ke `pom.xml` Anda di dalam blok `<dependencies>`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Tip pro:** Simpan nomor versi dalam properti (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) sehingga Anda dapat memperbarui dengan mudah.

### Unduhan langsung (alternatif)

Jika Anda lebih suka instalasi manual, Anda dapat mengunduh JAR dari halaman rilis resmi: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Cara memperoleh dan menerapkan lisensi

Menerapkan lisensi ke GroupDocs.Watermark menghapus batasan percobaan dan menonaktifkan overlay watermark default. Tempatkan file lisensi di lokasi yang diketahui dan arahkan API ke sana, atau sematkan path lisensi langsung dalam kode sebelum panggilan lain. Setelah dimuat, semua operasi selanjutnya berjalan dalam mode fitur penuh.

Anda dapat:

- **Minta percobaan gratis** dari portal GroupDocs – menyediakan file lisensi 30‑hari.
- **Buat lisensi sementara** melalui generator lisensi online untuk lingkungan evaluasi.
- **Beli lisensi komersial** untuk penggunaan produksi tak terbatas dan dukungan prioritas.

Tempatkan file lisensi (`GroupDocs.Watermark.lic`) di root proyek Anda atau tentukan path‑nya secara programatis dengan `Watermarker.setLicense("path/to/license.file")`.

## Cara menginisialisasi Watermarker

Inisialisasi `Watermarker` dengan memberikan path ke dokumen sumber, opsional menyertakan password untuk file yang dilindungi. Konstruktor memvalidasi format dan menyiapkan parser internal, memungkinkan Anda langsung memanggil metode preview atau watermark. Setelah dibuat, simpan referensi untuk menggunakan kembali instance tersebut untuk beberapa operasi jika diperlukan.

Kelas `Watermarker` adalah objek inti GroupDocs.Watermark yang memuat dokumen dan mengekspos operasi seperti penyisipan watermark dan pembuatan pratinjau.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – path absolut atau relatif ke file sumber.
- Konstruktor memvalidasi format file dan menyiapkan parser internal.

> **Definisi anchor:** `Watermarker` adalah titik masuk untuk semua aksi pemrosesan dokumen di GroupDocs.Watermark untuk Java.

## Cara membuat aliran halaman untuk pembuatan pratinjau

Buat aliran halaman khusus dengan mengimplementasikan antarmuka `ICreatePageStream`, yang dipanggil pustaka untuk setiap halaman yang dirender. Implementasi Anda harus menghasilkan `OutputStream` baru—biasanya `FileOutputStream`—yang mengarah ke file dengan nama unik berdasarkan nomor halaman. Pendekatan ini memisahkan output setiap halaman dan mencegah tumpang tindih data.

Untuk **java generate thumbnails**, Anda harus menyediakan aliran untuk setiap halaman tempat gambar yang dirender akan ditulis. Implementasikan antarmuka `ICreatePageStream`; pustaka memanggil implementasi Anda untuk setiap halaman yang diproses.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** memungkinkan Anda menyisipkan nomor halaman langsung ke nama file, memudahkan pemrosesan batch.
- Metode mengembalikan `OutputStream` baru untuk setiap halaman, memastikan halaman sebelumnya tidak mengganggu penulisan selanjutnya.

> **Definisi anchor:** `ICreatePageStream` adalah antarmuka callback yang memungkinkan Anda menentukan cara pembuatan output stream untuk setiap halaman pratinjau.

## Cara melepaskan aliran halaman setelah pembuatan pratinjau

Setelah gambar halaman ditulis, pustaka memanggil `IReleasePageStream` untuk memungkinkan Anda menutup dan membersihkan output stream terkait. Implementasikan callback ini untuk melepaskan handle file dengan aman, mengosongkan buffer, dan melakukan logging tambahan bila diperlukan. Pembersihan yang tepat menghindari kebocoran descriptor dan memastikan halaman berikutnya dapat diproses tanpa gangguan.

Pembersihan sumber daya yang tepat mencegah kebocoran handle file dan menjaga JVM tidak kehabisan descriptor. Implementasikan `IReleasePageStream` untuk menutup stream setelah pustaka memberi sinyal bahwa halaman selesai.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definisi anchor:** `IReleasePageStream` adalah antarmuka callback yang memungkinkan Anda mendefinisikan logika khusus untuk membuang sumber daya output spesifik halaman.

## Cara menghasilkan pratinjau dokumen (convert document to image)

Hasilkan pratinjau dengan memanggil `generatePreview()` pada instance `Watermarker`, menyediakan objek `PreviewOptions` yang menentukan resolusi, format gambar, dan rentang halaman. Metode ini mengiterasi setiap halaman, menggunakan pembuat aliran Anda untuk menulis gambar raster, lalu melepaskan aliran. Proses ini menghasilkan sekumpulan file gambar yang mewakili halaman dokumen.

Dengan `Watermarker`, `FeatureCreatePageStream`, dan `FeatureReleasePageStream` siap, Anda dapat memanggil mesin pratinjau. Metode `generatePreview()` mengiterasi setiap halaman, memanggil pembuat aliran Anda, menulis gambar, dan akhirnya melepaskan aliran.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** mengontrol DPI; 150 DPI adalah keseimbangan yang baik untuk thumbnail web.
- **`ImageFormat`** dapat berupa PNG, JPEG, BMP, atau TIFF tergantung pada kebutuhan downstream Anda.
- Metode memproses halaman secara berurutan, sehingga konsumsi memori tetap rendah bahkan untuk dokumen dengan ratusan halaman.

> **Definisi anchor:** `generatePreview()` adalah panggilan API yang merender setiap halaman dokumen yang dimuat menjadi gambar menggunakan aliran yang Anda sediakan.

## Aplikasi praktis dari convert document to image

Membuat pratinjau gambar membuka banyak kemungkinan:

1. **Penjelajah dokumen** – Tampilkan grid thumbnail PNG sehingga pengguna dapat menelusuri PDF besar tanpa membukanya.
2. **Cuplikan hasil pencarian** – Lampirkan gambar pratinjau ke entri indeks pencarian untuk UI yang lebih kaya.
3. **Lampiran email** – Sisipkan pratinjau kecil PDF terlampir di badan email.
4. **Aplikasi seluler** – Kurangi bandwidth dengan mengirim pratinjau PNG 200 KB alih‑alih PDF lengkap.
5. **Portal kepatuhan** – Render versi kontrak berwatermark yang diwajibkan secara hukum sebagai gambar untuk jejak audit.

## Pertimbangan kinerja saat Anda java generate thumbnails

Saat Anda menangani pemrosesan massal, ingatlah tip optimasi berikut:

- **Buffering aliran** – Bungkus `FileOutputStream` dalam `BufferedOutputStream` untuk meminimalkan I/O disk.
- **Eksekusi batch paralel** – Gunakan `ForkJoinPool` Java untuk memproses beberapa dokumen secara bersamaan; setiap tugas harus membuat instance `Watermarker` sendiri untuk menghindari masalah keamanan thread.
- **Batasi DPI untuk thumbnail** – 72–150 DPI cukup untuk kebanyakan skenario UI; DPI lebih tinggi harus disiapkan untuk pratinjau siap cetak.
- **Gunakan kembali objek lisensi** – Memuat file lisensi sekali per JVM mengurangi overhead.
- **Pantau memori** – Pustaka hanya menyimpan halaman saat ini di memori. Untuk file yang sangat besar, pertimbangkan meningkatkan heap JVM secara moderat (mis., `-Xmx512m`) untuk mengakomodasi lonjakan sesekali.

## Jebakan umum dan cara menghindarinya

| Gejala | Penyebab kemungkinan | Solusi |
|--------|----------------------|--------|
| `OutOfMemoryError` selama pembuatan pratinjau | Menggunakan `ImageFormat.Jpeg` dengan 300 DPI pada PDF 1000‑halaman | Kurangi DPI atau beralih ke PNG dengan kedalaman warna lebih rendah |
| File pratinjau kosong | `FeatureCreatePageStream` mengembalikan `FileOutputStream` yang sama untuk setiap halaman | Pastikan aliran baru dibuat per `pageNumber` |
| Gambar pratinjau terrotasi | PDF sumber berisi metadata rotasi yang tidak dipatuhi | Panggil `previewOptions.setRotatePages(true)` (jika tersedia) |
| Peringatan lisensi muncul | File lisensi tidak ditemukan atau path tidak benar | Verifikasi `Watermarker.setLicense("path/to/license.file")` dijalankan sebelum panggilan API lainnya |

## Pertanyaan yang sering diajukan

**T: Bisakah saya menghasilkan pratinjau untuk PDF yang dilindungi password?**  
J: Ya. Berikan password ke konstruktor `Watermarker`: `new Watermarker("file.pdf", "password")`.

**T: Format gambar apa yang didukung untuk output pratinjau?**  
J: PNG, JPEG, BMP, dan TIFF tersedia. PNG direkomendasikan untuk thumbnail lossless.

**T: Berapa banyak halaman yang dapat diproses dalam satu panggilan?**  
J: Pustaka tidak memberlakukan batas keras; Anda dapat mempratinjau dokumen dengan ribuan halaman, terbatas hanya oleh ruang penyimpanan dan throughput I/O.

**T: Apakah saya memerlukan lisensi terpisah untuk setiap instance server?**  
J: Satu file lisensi dapat digunakan kembali di beberapa instance selama total penggunaan mematuhi ketentuan lisensi.

**T: Apakah ada cara untuk menghasilkan satu thumbnail gabungan (mis., hanya halaman pertama)?**  
J: Ya. Atur `previewOptions.setPages(new int[]{1})` untuk membatasi pembuatan ke halaman pertama.

## Kesimpulan

Anda kini memiliki alur kerja lengkap dan siap produksi untuk **convert document to image** dan **java generate thumbnails** menggunakan GroupDocs.Watermark. Dengan mengonfigurasi penangan aliran halaman khusus, Anda menjaga penggunaan memori tetap rendah, dan dengan menyesuaikan `PreviewOptions` Anda mengontrol kualitas gambar serta ukuran file. Teknik ini memungkinkan Anda menyematkan pratinjau cepat dan berkualitas tinggi ke dalam aplikasi berbasis Java apa pun—baik portal web, klien desktop, atau layanan mikro berbasis cloud.

---

**Terakhir Diperbarui:** 2026-09-26  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## Tutorial Terkait

- [Cara Mengambil Informasi Dokumen Menggunakan GroupDocs.Watermark untuk Java: Panduan Langkah demi Langkah](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Tutorial Fitur Watermark Tingkat Lanjut untuk GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Cara Menambahkan Watermark Gambar di Java menggunakan GroupDocs.Watermark: Panduan Langkah demi Langkah](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)