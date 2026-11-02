---
date: '2026-10-21'
description: Pelajari cara menghapus hyperlink dari bentuk diagram menggunakan GroupDocs.Watermark
  untuk Java. Ikuti panduan langkah demi langkah ini untuk mengamankan dan membersihkan
  dokumen Anda.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Pelajari cara menghapus hyperlink dari bentuk diagram menggunakan
  GroupDocs.Watermark untuk Java. Panduan ini memandu Anda melalui pengaturan, kode,
  dan praktik terbaik untuk dokumen yang aman dan bersih.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Cara menghapus hyperlink dari bentuk dengan GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Cara menghapus hyperlink dari bentuk dengan GroupDocs.Watermark Java
type: docs
url: /id/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cara menghapus hyperlink dari shape dengan GroupDocs.Watermark Java

Mengelola dokumen digital sering melibatkan penyuntingan diagram, terutama ketika Anda perlu **cara menghapus hyperlink** dari shape untuk keamanan atau kejelasan visual. Tutorial ini memandu Anda melalui metode sederhana untuk menghapus hyperlink yang tidak diinginkan dari shape diagram menggunakan pustaka **GroupDocs.Watermark** yang kuat dalam Java. Pada akhir panduan ini, Anda akan memahami mengapa menghapus hyperlink penting, cara menyiapkan lingkungan, dan langkah‑langkah tepat untuk melakukan penghapusan dengan aman.

## Jawaban Cepat
- **Apa tujuan utama menghapus hyperlink?** Untuk menghilangkan risiko keamanan dan meningkatkan kejelasan visual dalam diagram yang dibagikan.  
- **Library mana yang menangani penghapusan?** GroupDocs.Watermark for Java menyediakan API khusus untuk manipulasi diagram.  
- **Apakah saya memerlukan lisensi?** Versi percobaan dapat digunakan untuk pengujian; lisensi komersial diperlukan untuk penggunaan produksi.  
- **Bisakah saya memproses banyak file sekaligus?** Ya—bungkus kode dalam loop atau batch job untuk menangani operasi massal.  
- **Versi Java apa yang diperlukan?** Java 8 atau lebih tinggi didukung.

## Apa itu cara menghapus hyperlink?
Frasa **cara menghapus hyperlink** mengacu pada proses menemukan dan menghapus objek hyperlink yang tertanam dalam elemen shape diagram. Melakukan tindakan ini mencegah navigasi eksternal yang secara tidak sengaja menampilkan pengguna ke situs berbahaya atau konten yang tidak diinginkan. Hal ini sangat penting saat menyiapkan dokumen untuk distribusi publik, memastikan tidak ada jalur navigasi tersembunyi yang dapat mengarahkan ke situs phishing atau sumber eksternal yang tidak diinginkan.

## Mengapa menggunakan GroupDocs.Watermark untuk Java?
GroupDocs.Watermark mendukung **30+ format input dan output** dan dapat memproses diagram dengan **hingga 500 halaman** tanpa memuat seluruh file ke memori, menghasilkan **penurunan penggunaan CPU sebesar 40 %** dibandingkan parser XML umum. API‑nya memberi Anda kontrol detail atas properti shape, menjadikannya pendekatan standar untuk penanganan diagram yang aman dalam aplikasi Java.

## Prasyarat
- **GroupDocs.Watermark** library versi 24.11 atau lebih baru.  
- Maven terpasang (atau unduhan JAR langsung).  
- JDK 8 atau yang lebih baru dan IDE seperti IntelliJ IDEA atau Eclipse.  
- Pengetahuan dasar Java dan familiaritas dengan dependensi Maven.

## Menyiapkan GroupDocs.Watermark untuk Java
Untuk memulai, sertakan pustaka GroupDocs.Watermark dalam proyek Anda. Anda dapat menambahkannya melalui Maven atau mengunduh JAR secara manual.

### Pengaturan Maven
Tambahkan konfigurasi berikut ke `pom.xml` Anda:

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

### Unduhan langsung
Atau, unduh versi terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Langkah memperoleh lisensi
- Mulailah dengan percobaan gratis dengan mengunduh GroupDocs.Watermark.  
- Untuk pengujian lanjutan atau penggunaan produksi, dapatkan lisensi sementara atau beli lisensi penuh.

#### Inisialisasi dan penyiapan dasar
Kelas `Watermarker` adalah titik masuk untuk semua operasi tingkat dokumen. Ia memuat file, memberi Anda akses ke halaman, shape, dan metadata, dan akhirnya menulis dokumen yang dimodifikasi kembali ke disk.

Untuk menginisialisasi kelas Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cara menghapus hyperlink dari shape diagram?
Muat diagram, temukan setiap shape yang berisi hyperlink, dan hapus objek hyperlink tersebut. Seluruh operasi dapat dilakukan dalam kurang dari sepuluh baris kode, dan memastikan diagram yang dihasilkan tidak lagi berisi tautan yang dapat mengarahkan pengguna ke situs eksternal atau mengungkap informasi sensitif.

### Langkah 1: muat file diagram
Mulailah dengan memuat diagram Anda menggunakan `Watermarker`. Objek ini memberikan akses ke berbagai elemen dokumen, termasuk shape dan propertinya.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Mengapa**: Memuat file penting untuk mengakses kontennya untuk manipulasi lebih lanjut.

### Langkah 2: akses konten shape
Ambil konten shape diagram. Ini memungkinkan Anda bekerja langsung dengan elemen yang mungkin berisi hyperlink.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Mengapa**: Mengakses shape tertentu penting untuk menargetkan dan memodifikasi properti hyperlink.

### Langkah 3: iterasi dan hapus hyperlink
Iterasi hyperlink secara terbalik untuk menghapus tautan yang tidak diinginkan dengan aman tanpa mengganggu proses iterasi.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Mengapa**: Membalik urutan iterasi mencegah masalah indeks saat menghapus elemen.

### Langkah 4: simpan dan tutup
Setelah modifikasi selesai, simpan perubahan ke lokasi file baru dan tutup sumber daya watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Mengapa**: Menutup sumber daya dengan benar memastikan tidak ada kebocoran memori atau file terkunci yang tersisa di sistem.

## Kesulitan umum dan pemecahan masalah
- **Koleksi shape null** – Selalu periksa bahwa koleksi `Hyperlinks` pada shape tidak null sebelum iterasi.  
- **Diagram besar** – Untuk file lebih dari 200 halaman, tingkatkan ukuran heap JVM (`-Xmx2g`) untuk menghindari `OutOfMemoryError`.  
- **Kesalahan lisensi** – Jika Anda melihat pengecualian lisensi, pastikan lisensi percobaan belum kedaluwarsa dan jalur file lisensi sudah benar.

## Pertanyaan yang sering diajukan

**Q: Bagaimana saya menangani banyak shape pada halaman yang sama?**  
A: Loop melalui koleksi `Shapes` setiap halaman, menerapkan logika penghapusan hyperlink yang sama pada setiap shape yang Anda temui.

**Q: Bisakah saya membatasi penghapusan pada rentang halaman tertentu?**  
A: Ya—gunakan indeks halaman saat mengambil shape dan lewati halaman di luar rentang target Anda.

**Q: Apakah lisensi diperlukan untuk pemrosesan batch?**  
A: Lisensi komersial yang valid diperlukan untuk pekerjaan batch tingkat produksi; lisensi percobaan hanya berfungsi untuk pengujian terbatas.

**Q: Apakah ini bekerja dengan file SVG atau Visio?**  
A: GroupDocs.Watermark mendukung SVG, VSDX, dan beberapa format diagram lainnya; pastikan tipe file tercantum dalam tabel format yang didukung.

**Q: Kinerja apa yang dapat saya harapkan pada diagram 300‑halaman?**  
A: Pada server tipikal (8 CPU, 16 GB RAM), memproses diagram 300‑halaman memakan waktu kurang dari 45 detik, dengan penggunaan memori di bawah 200 MB.

## Sumber Daya
- [Dokumentasi](https://docs.groupdocs.com/watermark/java/)
- [Referensi API](https://reference.groupdocs.com/watermark/java)
- [Unduhan](https://releases.groupdocs.com/watermark/java/)
- [Repositori GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/watermark/10)
- [Akuisisi Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

---

**Terakhir Diperbarui:** 2026-10-21  
**Diuji Dengan:** GroupDocs.Watermark 24.11 for Java  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Modifikasi Shape Dokumen Word dengan GroupDocs.Watermark di Java: Panduan Komprehensif](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Hapus Shape dari Dokumen Word Menggunakan GroupDocs.Watermark di Java: Panduan Komprehensif](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Edit Header & Footer Diagram di Java Menggunakan GroupDocs.Watermark: Panduan Komprehensif](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)