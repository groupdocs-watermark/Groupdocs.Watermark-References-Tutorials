---
date: '2026-02-13'
description: Pelajari cara mengekstrak bentuk dan mengekstrak gambar dari bentuk dengan
  GroupDocs.Watermark untuk Java, serta mengambil informasi diagram yang terperinci
  secara efisien.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Cara Mengekstrak Bentuk dari Diagram Menggunakan GroupDocs.Watermark dalam
  Java
type: docs
url: /id/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Cara Mengekstrak Bentuk dari Diagram Menggunakan GroupDocs.Watermark di Java

Ketika Anda perlu **cara mengekstrak bentuk** dari diagram bergaya Visio secara programatik, pustaka GroupDocs.Watermark memberikan cara yang bersih dan berfokus pada Java untuk mengambil setiap detail—dimensi, posisi, gambar yang disematkan, dan bahkan teks di dalam setiap bentuk. Dalam tutorial ini Anda akan melihat **cara mengekstrak bentuk**, mengapa hal itu penting, dan kode langkah‑demi‑langkah yang dapat Anda salin ke dalam proyek Anda.

## Jawaban Cepat
- **Pustaka apa yang menangani ekstraksi bentuk?** GroupDocs.Watermark untuk Java  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi  
- **Apakah saya dapat mendapatkan data gambar dari sebuah bentuk?** Ya – gunakan `shape.getImage()`  
- **Apakah teks di dalam bentuk dapat diakses?** Tentu saja, melalui `shape.getText()`  
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi GroupDocs.Watermark yang valid diperlukan  

## Pendahuluan

Mengelola diagram yang kompleks sering memerlukan akses ke informasi terperinci tentang komponennya, seperti bentuk dan gambar. Jika Anda pernah perlu secara programatik mengambil data seperti dimensi, posisi, atau teks yang terkait dengan bentuk diagram menggunakan Java, tutorial ini untuk Anda. Memanfaatkan kekuatan pustaka GroupDocs.Watermark dapat menyederhanakan proses ini dalam aplikasi Java. Dalam panduan ini, kami akan membahas **cara mengekstrak bentuk** dari file diagram serta menunjukkan **cara mengekstrak gambar dari bentuk** dan **cara mengekstrak teks dari bentuk**.

## Apa itu “cara mengekstrak bentuk”?

Mengekstrak bentuk berarti membaca objek internal diagram (halaman, bentuk, gambar, teks) sehingga Anda dapat menganalisis, mengubah, atau menggunakan kembali mereka dalam aplikasi lain—sempurna untuk otomatisasi, pelaporan, atau integrasi dengan alat CAD.

## Mengapa menggunakan GroupDocs.Watermark untuk ekstraksi bentuk?

- **Dukungan format lengkap** – bekerja dengan VSDX, VDX, dan banyak tipe diagram lainnya.  
- **Model objek yang kaya** – memberikan akses langsung ke geometri bentuk, gambar, dan teks.  
- **Tanpa ketergantungan eksternal** – murni Java, mudah disematkan dalam proyek Maven.  

## Prasyarat

- **GroupDocs.Watermark untuk Java** (versi 24.11 atau lebih baru)  
- Java Development Kit (JDK) 8 atau lebih tinggi  
- Maven untuk manajemen dependensi  
- IDE seperti IntelliJ IDEA atau Eclipse  

## Menyiapkan GroupDocs.Watermark untuk Java

Tambahkan pustaka ke `pom.xml` Maven Anda:

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

Anda juga dapat mengunduh biner terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Langkah-Langkah Akuisisi Lisensi
- **Uji Coba Gratis:** Unduh paket percobaan untuk mengevaluasi API.  
- **Lisensi Sementara:** Minta kunci sementara untuk pengujian yang diperpanjang.  
- **Pembelian:** Dapatkan lisensi penuh untuk penggunaan produksi.

### Inisialisasi dan Pengaturan Dasar

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Cara Mengekstrak Bentuk – Panduan Implementasi

### Memuat dan Mengambil Konten

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Mengiterasi Bentuk-Bentuk

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

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

### Cara mengekstrak gambar dari bentuk

Pemanggilan `shape.getImage()` mengembalikan objek yang berisi bitmap mentah, dimensinya, dan array byte. Gunakan properti yang ditunjukkan di atas untuk menyimpan gambar ke disk atau mengirimnya ke pipeline pemrosesan lain.

### Cara mengekstrak teks dari bentuk

Metode `shape.getText()` mengembalikan teks polos di dalam bentuk. Jika bentuk tidak mengandung teks, metode ini mengembalikan `null`. Loop contoh sudah mencetak teks, dan Anda dapat memanipulasinya lebih lanjut—misalnya, membangun indeks semua label bentuk.

## Tips Pemecahan Masalah
- Verifikasi jalur file dan izin baca.  
- Pastikan Anda menggunakan format diagram yang didukung (VSDX, VDX, dll.).  
- Jika sebuah bentuk muncul tanpa data yang diharapkan, periksa catatan rilis pustaka untuk keanehan spesifik format.

## Aplikasi Praktis

1. **Analisis Diagram:** Secara otomatis mengaudit diagram untuk kepatuhan dengan memeriksa ukuran bentuk atau label yang hilang.  
2. **Visualisasi Data:** Masukkan dimensi yang diekstrak ke dalam dasbor pelaporan untuk memvisualisasikan kepadatan tata letak.  
3. **Integrasi CAD:** Gabungkan data bentuk dengan API CAD untuk menyinkronkan spesifikasi desain antar alat.  

## Pertimbangan Kinerja

- **Tutup sumber daya:** Panggil `watermarker.close()` setelah selesai untuk membebaskan sumber daya native.  
- **Manajemen memori:** Diagram besar dapat mengonsumsi heap yang signifikan; pantau memori dan tingkatkan `-Xmx` bila diperlukan.  
- **Pemrosesan batch:** Proses file secara batch dan gunakan kembali satu instance `Watermarker` bila memungkinkan.

## Kesimpulan

Dengan mengikuti panduan ini Anda kini mengetahui **cara mengekstrak bentuk**, cara **mengekstrak gambar dari bentuk**, dan cara **mengekstrak teks dari bentuk** menggunakan GroupDocs.Watermark untuk Java. Teknik-teknik ini membuka pintu bagi analisis diagram otomatis, pelaporan, dan integrasi dengan sistem teknik lainnya. Langkah selanjutnya, jelajahi API lengkap dengan memeriksa [dokumentasinya](https://docs.groupdocs.com/watermark/java/) dan coba menggabungkan ekstraksi bentuk dengan logika bisnis khusus Anda.

## Bagian FAQ

1. **Apa itu GroupDocs.Watermark?**  
   - Sebuah pustaka Java komprehensif yang dirancang untuk watermarking dan mengekstrak informasi dari berbagai format dokumen, termasuk diagram.  

2. **Apakah saya dapat menggunakan pustaka ini untuk memproses semua jenis file diagram?**  
   - Ya, tetapi pastikan format file didukung dengan memeriksa [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Bagaimana cara mengekstrak dimensi dan posisi bentuk dari diagram menggunakan Java dan GroupDocs.Watermark?**  
   - Muat diagram, akses `DiagramContent`, lalu iterasi bentuk untuk mendapatkan properti seperti lebar, tinggi, X, dan Y.  

4. **Apakah GroupDocs.Watermark dapat mengekstrak gambar yang disematkan dalam bentuk diagram dengan Java?**  
   - Ya, pustaka ini menyediakan metode untuk mengakses data gambar dalam bentuk, termasuk ukuran dan data piksel, yang berguna untuk analisis atau modifikasi.  

5. **Apa saja prasyarat untuk mengekstrak informasi bentuk diagram di Java?**  
   - Java JDK 8+, pengaturan Maven, pustaka GroupDocs.Watermark (24.11+), dan pengetahuan dasar Java diperlukan untuk implementasi.  

---

**Terakhir Diperbarui:** 2026-02-13  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs