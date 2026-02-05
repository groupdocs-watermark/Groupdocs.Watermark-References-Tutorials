---
date: '2026-02-05'
description: Pelajari cara mengekstrak bentuk dari dokumen Word menggunakan GroupDocs.Watermark
  untuk Java, termasuk cara memuat dokumen Word di Java dan memanipulasi data bentuk.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Cara Mengekstrak Bentuk dari Dokumen Word Menggunakan GroupDocs.Watermark Java
type: docs
url: /id/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Cara Mengekstrak Bentuk dari Dokumen Word Menggunakan GroupDocs.Watermark di Java

Dalam tutorial ini Anda akan menemukan **cara mengekstrak bentuk** dari dokumen Word dengan pustaka GroupDocs.Watermark Java. Apakah Anda perlu menganalisis diagram, mengambil gambar yang disematkan, atau mengotomatisasi pembuatan laporan, mengekstrak metadata bentuk memberi Anda kontrol untuk membangun pipeline pemrosesan dokumen yang lebih cerdas. Kami akan memandu Anda melalui penyiapan pustaka, memuat dokumen Word, dan mengambil informasi bentuk secara detail—semua dalam kode Java yang jelas langkah demi langkah.

## Jawaban Cepat
- **Apa arti “mengekstrak bentuk”?** Mengambil metadata (tipe, ukuran, posisi, teks, gambar) untuk setiap objek gambar dalam file Word.  
- **Pustaka mana yang menangani ini?** GroupDocs.Watermark untuk Java.  
- **Apakah saya memerlukan lisensi?** Versi percobaan cukup untuk pengembangan; lisensi penuh menghapus batas penggunaan.  
- **Bisakah saya juga mendapatkan gambar dari bentuk?** Ya – API menyediakan byte gambar untuk bentuk gambar.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih baru.

## Apa Itu “Cara Mengekstrak Bentuk” dalam Konteks Dokumen Word?
Mengekstrak bentuk berarti mengakses secara programatik setiap elemen gambar—gambar, WordArt, auto‑shape, diagram, dan bahkan bentuk yang disematkan di header atau footer. Informasi ini dapat digunakan untuk validasi, migrasi, atau analitik berbasis konten.

## Mengapa Menggunakan GroupDocs.Watermark untuk Java?
GroupDocs.Watermark menyediakan API tingkat tinggi yang efisien dalam memori yang mengabstraksi kompleksitas format Office Open XML yang mendasarinya. Ini memungkinkan Anda untuk:
- Memuat dokumen dengan cepat (`WordProcessingLoadOptions`).  
- Iterasi melalui bagian dan bentuk tanpa harus berurusan dengan XML tingkat rendah.  
- Mengambil data gambar, teks, perataan, dan rotasi dalam satu panggilan.  
- Mengintegrasikan secara mulus ke dalam layanan Java yang ada atau mikro‑service.

## Prasyarat
- **Java Development Kit (JDK)** 8 atau lebih tinggi.  
- **IDE** seperti IntelliJ IDEA atau Eclipse.  
- Pengetahuan dasar Java I/O.  
- Akses ke lisensi **GroupDocs.Watermark untuk Java** atau percobaan.

## Menyiapkan GroupDocs.Watermark untuk Java
Integrasikan pustaka melalui Maven atau unduhan langsung.

### Menggunakan Maven
Tambahkan repositori dan dependensi ke `pom.xml` Anda:

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
Versi percobaan gratis sudah cukup untuk pengujian. Untuk produksi, minta lisensi permanen untuk membuka semua fitur.

## Panduan Implementasi
Kami akan membagi implementasi menjadi dua langkah jelas: **memuat dokumen Word** dan **mengekstrak informasi bentuk**.

### Langkah 1: Memuat Dokumen Word (load word document java)
Pertama, konfigurasikan opsi pemuatan dan buat instance `Watermarker`. Ini menyiapkan dokumen untuk inspeksi lebih lanjut.

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

> **Pro tip:** Jaga agar instance `Watermarker` memiliki ruang lingkup yang sempit; menutupnya segera membebaskan sumber daya native dan menghindari kebocoran memori.

### Langkah 2: Mengekstrak Informasi Bentuk (extract images from shapes)
Sekarang kami akan mengambil detail setiap bentuk, termasuk gambar yang disematkan. Kode ini mengiterasi setiap bagian dan setiap bentuk, mencetak metadata yang berguna.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

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

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
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

**Apa yang dilakukan kode ini:**  
- Mengambil **tipe** setiap bentuk (mis., picture, WordArt).  
- Mencetak nilai **ukuran**, **posisi**, dan **rotasi**.  
- Menampilkan **teks alternatif** dan **nama**, yang berguna untuk pemeriksaan aksesibilitas.  
- Jika bentuk berisi gambar, mencetak **dimensi piksel** gambar dan **ukuran byte**—sempurna untuk mengekstrak gambar dari bentuk.  

### Kesalahan Umum & Cara Memperbaikinya
| Masalah | Penyebab | Solusi |
|-------|-------|----------|
| `FileNotFoundException` | Path file salah atau izin tidak mencukupi | Verifikasi path absolut/relatif dan pastikan file dapat dibaca. |
| Null `shape.getImage()` | Bentuk bukan gambar (mis., auto‑shape) | Gunakan pengecekan `if (shape.getImage() != null)` seperti yang ditunjukkan. |
| Penggunaan memori tinggi pada dokumen besar | Memuat seluruh dokumen sekaligus | Proses bagian satu per satu atau tingkatkan heap JVM (`-Xmx`). |
| Bentuk header/footer tidak terdeteksi | Tidak memeriksa `shape.getHeaderFooter()` | Contoh sudah mencatat ketika sebuah bentuk berada di header/footer. |

## Aplikasi Praktis
1. **Pembuatan Laporan Otomatis** – Mengambil diagram dan grafik untuk disematkan dalam PDF selanjutnya.  
2. **Audit Kepatuhan** – Memverifikasi bahwa semua bentuk memiliki teks alternatif yang sesuai untuk aksesibilitas.  
3. **Migrasi Konten** – Mengekspor gambar yang disematkan dari file Word lama ke sistem manajemen aset digital.  

## Pertimbangan Kinerja
- **Lepaskan sumber daya**: Selalu panggil `watermarker.close()` dalam blok `finally` atau gunakan try‑with‑resources jika Anda membungkus API.  
- **Pemrosesan chunk**: Untuk dokumen yang melebihi 50 MB, pertimbangkan memproses setiap bagian secara terpisah untuk menjaga jejak memori tetap rendah.  
- **Keamanan thread**: Instance `Watermarker` tidak thread‑safe; buat instance baru per thread.

## Kesimpulan
Anda kini tahu **cara mengekstrak bentuk** dari dokumen Word menggunakan GroupDocs.Watermark untuk Java, mulai dari memuat file hingga membaca metadata setiap bentuk dan data gambar yang disematkan. Kemampuan ini membuka peluang untuk analitik dokumen tingkat lanjut, pipeline konten otomatis, dan validasi aksesibilitas.

### Langkah Selanjutnya
- Bereksperimen dengan memodifikasi properti bentuk (mis., mengubah ukuran atau memindahkan posisi).  
- Gabungkan pendekatan ini dengan **GroupDocs.Parser** untuk mengekstrak teks di sekitarnya.  
- Integrasikan logika ekstraksi ke dalam layanan REST untuk pemrosesan sesuai permintaan.

## Bagian FAQ
**Q: Apa itu GroupDocs.Watermark untuk Java?**  
A: Ini adalah pustaka komprehensif yang dirancang untuk mengelola watermark dan konten dokumen di berbagai format, memungkinkan tugas seperti ekstraksi bentuk, pengambilan gambar, dan manipulasi teks.

**Q: Bisakah saya mengekstrak gambar dari bentuk tanpa lisensi?**  
A: Versi percobaan memungkinkan ekstraksi, tetapi lisensi penuh menghapus batas penggunaan dan memungkinkan penerapan komersial.

**Q: Apakah ini bekerja dengan file `.doc` (biner)?**  
A: Ya, API mendukung format `.docx` dan format legacy `.doc`.

**Q: Bagaimana cara menangani dokumen yang dilindungi kata sandi?**  
A: Berikan kata sandi melalui `WordProcessingLoadOptions.setPassword("yourPassword")` sebelum membuat `Watermarker`.

**Q: Apakah ada cara mengekspor data bentuk yang diekstrak ke JSON?**  
A: Anda dapat memetakan nilai yang dicetak ke POJO dan menggunakan pustaka JSON apa pun (mis., Jackson) untuk menyerialisasi koleksi.

---

**Terakhir Diperbarui:** 2026-02-05  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs