---
date: '2025-12-20'
description: Pelajari cara mengekstrak informasi bentuk dengan GroupDocs.Watermark
  untuk Java. Dapatkan dimensi, posisi, dan teks dari file diagram secara efisien.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 'Ekstrak Informasi Bentuk Java: Menggunakan GroupDocs.Watermark untuk Diagram'
type: docs
url: /id/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Ekstrak Informasi Bentuk Java Menggunakan GroupDocs.Watermark dalam Diagram

Ketika Anda perlu **mengekstrak informasi bentuk java** dari file diagram yang kompleks, melakukannya secara manual dengan cepat menjadi tidak praktis. Tutorial ini menunjukkan cara memanfaatkan GroupDocs.Watermark untuk Java agar dapat secara programatis mengambil detail seperti dimensi, posisi, sudut rotasi, gambar tersemat, dan teks dari setiap bentuk. Pada akhir tutorial, Anda akan memiliki pola yang jelas dan dapat digunakan kembali yang dapat Anda masukkan ke dalam proyek Java apa pun yang bekerja dengan diagram bergaya Visio.

## Pendahuluan

Mengelola diagram yang kompleks sering kali memerlukan akses ke informasi terperinci tentang komponennya, seperti bentuk dan gambar. Jika Anda pernah perlu secara programatis mengambil data seperti dimensi, posisi, atau teks yang terkait dengan bentuk diagram menggunakan Java, tutorial ini untuk Anda. Memanfaatkan kekuatan pustaka GroupDocs.Watermark dapat menyederhanakan proses ini dalam aplikasi Java. Dalam panduan ini, kami akan menjelaskan cara menggunakan GroupDocs.Watermark untuk **mengekstrak informasi bentuk java** dari file diagram.

## Jawaban Cepat
- **Pustaka apa yang harus saya gunakan?** GroupDocs.Watermark untuk Java (v24.11+).  
- **Format file apa yang didukung?** Visio (.vsdx, .vsd) dan tipe diagram lain yang tercantum dalam dokumentasi API.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengembangan; lisensi komersial diperlukan untuk produksi.  
- **Bisakah saya mendapatkan data gambar dari bentuk?** Ya – API menyediakan lebar gambar, tinggi, dan data byte mentah.  
- **Apakah Maven diperlukan?** Maven adalah cara yang direkomendasikan untuk mengelola dependensi GroupDocs.Watermark.

## Apa itu “ekstrak informasi bentuk java”?

**Ekstrak informasi bentuk java** berarti membaca file diagram secara programatis dan mengambil properti setiap bentuk—ukuran, lokasi, rotasi, teks, dan gambar tersemat—menggunakan kode Java. Hal ini memungkinkan analisis otomatis, pelaporan, atau integrasi dengan sistem lain seperti alat CAD atau pipeline visualisasi data.

## Mengapa menggunakan GroupDocs.Watermark untuk tugas ini?

GroupDocs.Watermark menyediakan abstraksi tingkat tinggi atas format diagram, menangani parsing tingkat rendah untuk Anda. Ini memungkinkan Anda fokus pada logika bisnis alih-alih berurusan dengan spesifikasi XML atau biner, dan bekerja secara konsisten di semua tipe diagram yang didukung.

## Prasyarat

- **GroupDocs.Watermark untuk Java** (versi 24.11 atau lebih baru)  
- Java Development Kit (JDK) 8 atau lebih tinggi  
- Maven untuk manajemen dependensi  
- IDE seperti IntelliJ IDEA atau Eclipse  

## Menyiapkan GroupDocs.Watermark untuk Java

Tambahkan repositori dan dependensi ke `pom.xml` Maven Anda:

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

Sebagai alternatif, Anda dapat langsung mengunduh versi terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Langkah-langkah Akuisisi Lisensi
- **Percobaan Gratis:** Unduh paket percobaan untuk menguji pustaka.  
- **Lisensi Sementara:** Dapatkan kunci sementara untuk evaluasi yang diperpanjang.  
- **Pembelian:** Dapatkan lisensi penuh untuk penggunaan produksi.

### Inisialisasi Dasar

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Panduan Implementasi

Sekarang mari kita bahas langkah‑langkah tepat untuk **mengekstrak informasi bentuk java** dari dokumen diagram.

### Memuat dan Mengambil Konten

#### Gambaran Umum
Pertama kami memuat file diagram dan memperoleh objek `DiagramContent`, yang memberi akses ke halaman dan bentuk.

#### Langkah-langkah

**Memuat Dokumen Diagram**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **Mengapa:** Ini menginisialisasi objek `Watermarker`, memungkinkan akses ke konten dokumen.

**Mengakses Konten Diagram**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **Mengapa:** Kelas `DiagramContent` menyediakan metode untuk berinteraksi dengan berbagai aspek diagram, seperti halaman dan bentuk.

### Mengiterasi Bentuk

#### Gambaran Umum
Dengan `DiagramContent` di tangan, kami melakukan loop melalui setiap halaman dan kemudian setiap bentuk untuk mengambil properti yang diperlukan.

#### Langkah-langkah

**Mengiterasi Halaman**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **Mengapa:** Diagram terdiri dari beberapa halaman; kami perlu memeriksa masing‑masing untuk menemukan bentuk‑bentuknya.

**Mengekstrak Informasi Bentuk**

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

- **Mengapa:** Loop ini mengekstrak dan mencetak properti setiap bentuk, termasuk dimensi, posisi, rotasi, serta gambar atau teks yang tersemat. Atribut‑atribut ini penting untuk memahami cara bentuk‑bentuk dikonfigurasi dalam diagram.

### Tips Pemecahan Masalah
- Pastikan jalur file benar dan mengarah ke file `.vsdx` (atau yang didukung) yang dapat dibaca.  
- Pastikan aplikasi memiliki izin baca untuk file diagram.  
- Jika Anda menemukan error “Unsupported format”, pastikan versi GroupDocs.Watermark Anda mendukung tipe diagram spesifik tersebut.

## Aplikasi Praktis

Dengan kemampuan **mengekstrak informasi bentuk java**, Anda dapat mendukung berbagai skenario dunia nyata:

1. **Analisis Diagram:** Secara otomatis menghasilkan laporan yang mencantumkan ukuran, lokasi, dan teks setiap bentuk—berguna untuk audit jaminan kualitas.  
2. **Visualisasi Data:** Salurkan metrik bentuk ke dasbor untuk memvisualisasikan kepadatan tata letak atau mengidentifikasi elemen yang terlalu besar.  
3. **Integrasi CAD:** Jembatani data diagram ke pipeline CAD, memungkinkan redesain atau langkah validasi otomatis.

## Pertimbangan Kinerja

Saat memproses diagram berukuran besar, perhatikan praktik terbaik berikut:

- **Tutup Sumber Daya Segera:** Panggil `watermarker.close()` (atau gunakan try‑with‑resources) untuk membebaskan memori.  
- **Pantau Penggunaan Heap:** Diagram besar dapat mengonsumsi memori signifikan; sesuaikan heap JVM (`-Xmx`) sesuai kebutuhan.  
- **Pemrosesan Batch:** Proses file secara batch daripada memuat puluhan sekaligus.

## Kesimpulan

Dengan mengikuti panduan ini, Anda kini tahu cara **mengekstrak informasi bentuk java** menggunakan GroupDocs.Watermark untuk Java. Anda dapat mengambil dimensi, posisi, sudut rotasi, gambar tersemat, dan teks dari file diagram apa pun yang didukung, membuka pintu bagi analisis otomatis, pelaporan, dan integrasi dengan sistem yang lebih besar. Siap melangkah ke tahap berikutnya? Jelajahi kemampuan lengkap pustaka dalam [dokumentasi resmi](https://docs.groupdocs.com/watermark/java/) dan bereksperimen dengan watermarking, redaksi, atau manipulasi bentuk khusus.

## Pertanyaan yang Sering Diajukan

**T: Apa itu GroupDocs.Watermark?**  
J: Sebuah pustaka Java komprehensif yang dirancang untuk watermarking dan mengekstrak informasi dari berbagai format dokumen, termasuk diagram.

**T: Bisakah saya menggunakan pustaka ini untuk memproses semua tipe file diagram?**  
J: Ya, tetapi pastikan format file tercantum sebagai didukung dalam [API Reference](https://reference.groupdocs.com/watermark/java/).

**T: Bagaimana cara mengekstrak dimensi dan posisi bentuk dari diagram menggunakan Java dan GroupDocs.Watermark?**  
J: Muat diagram, peroleh `DiagramContent`, lalu iterasi setiap `DiagramShape` untuk membaca properti seperti lebar, tinggi, X, dan Y.

**T: Apakah GroupDocs.Watermark dapat mengekstrak gambar yang tersemat dalam bentuk diagram dengan Java?**  
J: Ya, pustaka menyediakan metode untuk mengakses data gambar dalam bentuk, termasuk ukuran dan array byte mentah, yang dapat Anda gunakan untuk analisis atau modifikasi.

**T: Apa saja prasyarat untuk mengekstrak informasi bentuk diagram di Java?**  
J: Java JDK 8+, pengaturan Maven, pustaka GroupDocs.Watermark (24.11+), dan pengetahuan dasar pemrograman Java.

---

**Terakhir Diperbarui:** 2025-12-20  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs  

---