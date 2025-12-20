---
date: '2025-12-20'
description: Pelajari cara mengekstrak gambar dari dokumen Word dan mengekstrak bentuk
  menggunakan GroupDocs.Watermark untuk Java, sempurna untuk otomatisasi dan manipulasi
  dokumen.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Cara Mengekstrak Gambar dari Dokumen Word Menggunakan GroupDocs.Watermark di
  Java
type: docs
url: /id/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Cara Mengekstrak Gambar dari Dokumen Word Menggunakan GroupDocs.Watermark di Java

Dalam aplikasi pemrosesan dokumen modern, **mengekstrak gambar dari word** dokumen adalah kebutuhan yang sering—baik Anda perlu menggunakan kembali grafik, menjalankan OCR, atau sekadar mengaudit konten. Tutorial ini, langkah demi langkah, cara memuat dokumen Word di Java dengan GroupDocs.Watermark dan kemudian **mengekstrak gambar dari word** file sambil juga mendemonstrasikan **cara mengekstrak bentuk**. Pada akhir, Anda akan memiliki potongan kode yang dapat digunakan kembali dan cocok untuk pipeline otomatisasi Anda.

## Jawaban Cepat
- **Perpustakaan apa yang menangani ekstraksi gambar?** GroupDocs.Watermark untuk Java  
- **Apakah saya dapat mengekstrak baik gambar maupun bentuk vektor?** Ya – API menyediakan akses ke gambar dan metadata bentuk.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi.  
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi komersial disarankan; percobaan gratis dapat digunakan untuk evaluasi.  
- **Apakah proses ini efisien memori untuk file besar?** Ya, Anda dapat melepaskan sumber daya dengan cepat dan memproses bagian secara bertahap.

## Apa Itu “Mengekstrak Gambar dari Word”?
Mengekstrak gambar dari Word berarti secara programatis menemukan setiap gambar, gambar gambar, atau grafik tersemat di dalam file `.docx` dan mengambil data biner atau metadata-nya. Hal ini memungkinkan tugas-tugas selanjutnya seperti analisis gambar, migrasi konten, atau pembuatan laporan dinamis.

## Mengapa Menggunakan GroupDocs.Watermark untuk Tugas Ini?
GroupDocs.Watermark menawarkan API tingkat tinggi yang menyederhanakan kompleksitas format OpenXML. Ini memungkinkan Anda **memuat dokumen word java** proyek dengan hanya beberapa baris kode, sekaligus menampilkan informasi bentuk yang detail—sempurna bagi pengembang yang membutuhkan baik ekstraksi gambar maupun analisis bentuk.

## Prasyarat
- **Java Development Kit (JDK)** 8 atau lebih baru  
- **IDE** – IntelliJ IDEA, Eclipse, atau editor Java‑compatible apa pun  
- Pengetahuan dasar I/O Java  
- Akses ke lisensi GroupDocs.Watermark (percobaan dapat digunakan untuk pengujian)

## Menyiapkan GroupDocs.Watermark untuk Java
Integrasikan perpustakaan melalui Maven atau unduhan langsung.

### Menggunakan Maven
Add the repository and dependency to your `pom.xml`:

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

### Unduhan Langsung
Sebagai alternatif, unduh JAR terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Akuisisi Lisensi
Untuk fungsionalitas penuh, dapatkan kunci lisensi dari portal GroupDocs. Lisensi percobaan sementara dapat diminta untuk menjelajahi semua fitur tanpa batasan.

## Panduan Implementasi
Kami akan membagi implementasi menjadi dua bagian logis:

1. **Cara memuat dokumen Word di Java**  
2. **Cara mengekstrak bentuk dan gambar (yaitu, mengekstrak gambar dari word)**

### Memuat Dokumen Word
Pertama, konfigurasikan opsi pemuatan dan buat instance `Watermarker`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Tip Pro:** Ganti `"YOUR_DOCUMENT_DIRECTORY/document.docx"` dengan jalur absolut atau relatif yang mengarah ke file yang ingin Anda proses.

### Mengekstrak Informasi Bentuk dan Gambar
Setelah dokumen dimuat, Anda dapat mengiterasi setiap bagian dan setiap bentuk, mengambil data bentuk vektor serta detail gambar tersemat.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Mengapa ini penting:** Pemanggilan `shape.getImage()` memberi Anda akses langsung ke representasi biner setiap gambar, memungkinkan Anda menyimpannya ke disk, mengirimnya melalui jaringan, atau memasukkannya ke dalam perpustakaan pemrosesan gambar.

## Masalah Umum dan Solusinya
| Problem | Solution |
|---------|----------|
| **FileNotFoundException** – wrong path | Verifikasi jalur file dan pastikan aplikasi memiliki izin baca. |
| **OutOfMemoryError** on large docs | Proses bagian satu per satu dan panggil `watermarker.close()` segera setelah Anda menyelesaikan satu batch. |
| Shapes return `null` for `getImage()` | Tidak semua bentuk adalah gambar; beberapa adalah objek gambar. Periksa `shape.getShapeType()` sebelum mengakses gambar. |
| License not applied | Tambahkan `License.setLicense("path/to/license/file.lic");` sebelum membuat `Watermarker`. |

## Aplikasi Praktis
- **Pembuatan Laporan Otomatis:** Tarik diagram dan logo dari templat untuk digunakan kembali di dasbor.  
- **Audit Konten:** Pindai dokumen perusahaan untuk grafik yang dilarang.  
- **Proyek Migrasi:** Ekspor gambar tersemat sebelum memindahkan konten ke CMS baru.

## Pertimbangan Kinerja
- Lepaskan instance `Watermarker` dengan cepat (`watermarker.close()`).  
- Untuk file besar (>50 MB), pertimbangkan streaming bagian alih-alih memuat seluruh dokumen ke memori.  
- Gunakan versi GroupDocs.Watermark terbaru untuk peningkatan kinerja.

## Kesimpulan
Anda kini memiliki pendekatan lengkap dan siap produksi untuk **mengekstrak gambar dari word** dokumen dan mengambil metadata bentuk menggunakan GroupDocs.Watermark untuk Java. Kemampuan ini membuka skenario otomatisasi yang kuat, mulai dari menghasilkan laporan dinamis hingga melakukan audit dokumen berskala besar.

### Langkah Selanjutnya
- Bereksperimen dengan menyimpan gambar yang diekstrak ke disk (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Jelajahi API tambahan seperti penghapusan atau penambahan watermark.  
- Integrasikan logika ini ke dalam alur kerja manajemen dokumen Anda yang sudah ada.

## Bagian FAQ
**Q: Apa itu GroupDocs.Watermark untuk Java?**  
A: Ini adalah perpustakaan komprehensif yang dirancang untuk mengelola watermark dan mengekstrak elemen visual di berbagai format dokumen, meningkatkan otomatisasi tugas manipulasi dokumen.

**Q: Bisakah saya mengekstrak gambar dari file Word yang dilindungi kata sandi?**  
A: Ya. Muat dokumen dengan `WordProcessingLoadOptions` yang menyertakan kata sandi, kemudian lanjutkan dengan logika ekstraksi yang sama.

**Q: Apakah API mendukung file .doc (biner) juga?**  
A: Perpustakaan ini terutama menargetkan format OpenXML `.docx`, tetapi juga dapat membuka file `.doc` lama setelah konversi.

**Q: Bagaimana cara menyimpan gambar yang diekstrak ke sistem file?**  
A: Gunakan `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` di dalam loop di mana `shape.getImage()` tidak null.

**Q: Apakah ada batasan jumlah bentuk yang dapat saya proses?**  
A: Tidak ada batasan keras, tetapi konsumsi memori meningkat seiring ukuran dokumen; proses bagian secara berurutan untuk file yang sangat besar.

---  

**Terakhir Diperbarui:** 2025-12-20  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs