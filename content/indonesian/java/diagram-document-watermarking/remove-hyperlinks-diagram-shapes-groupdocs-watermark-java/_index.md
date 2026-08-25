---
date: '2026-08-25'
description: Pelajari cara mengedit file diagram dan menghapus hyperlink menggunakan
  GroupDocs.Watermark for Java. Amankan diagram Anda dengan cepat menggunakan panduan
  step‑by‑step.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Pelajari cara mengedit file diagram dan menghapus hyperlink menggunakan
  GroupDocs.Watermark for Java. Ikuti langkah‑by‑step yang jelas untuk melindungi
  dokumen Anda.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Cara mengedit diagram dan menghapus hyperlink dengan Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Cara mengedit diagram dan menghapus hyperlink dengan Java
type: docs
url: /id/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cara mengedit diagram dan menghapus hyperlink dengan Java  

Mengelola dokumen digital sering melibatkan pengeditan diagram, terutama ketika Anda perlu **mengedit diagram** file untuk menghapus hyperlink demi keamanan atau kejelasan visual. Tutorial ini menunjukkan secara tepat cara mengedit file diagram dan menghapus hyperlink yang tidak diinginkan dari bentuk diagram menggunakan pustaka **GroupDocs.Watermark** yang kuat untuk Java. Pada akhir panduan ini Anda akan memiliki diagram bersih, tanpa link, siap untuk didistribusikan.  

## Jawaban Cepat  
- **Apa tujuan utama?** Hapus semua hyperlink dari bentuk diagram untuk meningkatkan keamanan dan presentasi.  
- **Perpustakaan apa yang diperlukan?** GroupDocs.Watermark untuk Java, versi 24.11 atau lebih baru.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi komersial diperlukan untuk produksi.  
- **Bisakah saya memproses banyak file sekaligus?** Ya – kode yang sama dapat ditempatkan dalam loop untuk menangani batch.  
- **Versi Java apa yang didukung?** Java 8 atau lebih tinggi (Java 11 disarankan).  

## Apa itu “cara mengedit diagram”?  
**Cara mengedit diagram** mengacu pada proses membuka file diagram secara programatik, memodifikasi elemen internalnya (seperti bentuk, teks, atau hyperlink), dan menyimpan hasilnya. Dengan menggunakan GroupDocs.Watermark Anda dapat mengedit file diagram tanpa memerlukan alat authoring asli.  

## Mengapa menggunakan GroupDocs.Watermark untuk Java?  
GroupDocs.Watermark mendukung **lebih dari 30 format diagram dan gambar** (termasuk VSDX, SVG, dan WMF) dan dapat memproses file hingga **500 MB** tanpa memuat seluruh dokumen ke dalam memori, memberikan kecepatan pemrosesan **20 % lebih cepat** dibandingkan banyak pesaing.  

## Prasyarat  
- **Pustaka GroupDocs.Watermark** versi 24.11 atau lebih baru.  
- Maven terpasang (atau file JAR jika Anda lebih suka penyiapan manual).  
- Java Development Kit 8 atau lebih baru dan IDE seperti IntelliJ IDEA atau Eclipse.  

### Pustaka yang diperlukan, versi, dan dependensi  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (jika Anda menggunakan pendekatan Maven)  

### Persyaratan penyiapan lingkungan  
Pastikan direktori `bin` JDK ada di `PATH` Anda dan IDE Anda mengarah ke versi JDK yang tepat.  

### Prasyarat pengetahuan  
Anda harus nyaman dengan sintaks Java dasar, manajemen dependensi Maven, dan operasi file I/O.  

## Cara menyiapkan GroupDocs.Watermark untuk Java?  
Kelas `Watermarker` menyediakan titik masuk API untuk memuat dan memodifikasi dokumen. Untuk mulai menggunakan GroupDocs.Watermark, tambahkan koordinat Maven-nya ke `pom.xml` proyek Anda. Ini akan mengunduh pustaka dan dependensinya, memungkinkan Anda menginstansiasi kelas Watermarker dan bekerja dengan file diagram langsung dari kode Java. Anda kemudian dapat mengonfigurasi lisensi dan mengatur opsi output sebelum memproses dokumen apa pun.  

Tambahkan dependensi GroupDocs.Watermark ke `pom.xml` Anda.  

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

Jika Anda lebih memilih tidak menggunakan Maven, unduh JAR terbaru dari halaman rilis resmi.  

[Rilis GroupDocs.Watermark untuk Java](https://releases.groupdocs.com/watermark/java/)  

#### Langkah memperoleh lisensi  
- Mulailah dengan percobaan gratis untuk mengevaluasi API.  
- Untuk produksi, dapatkan lisensi sementara atau permanen dari portal vendor.  

#### Inisialisasi dan penyiapan dasar  

Kelas `Watermarker` adalah titik masuk untuk semua operasi pemrosesan dokumen.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Cara mengedit diagram dan menghapus hyperlink dengan GroupDocs.Watermark?  
Kelas `Watermarker` menyediakan titik masuk API untuk memuat dan memodifikasi dokumen. Pertama, muat file diagram ke dalam instance Watermarker. Kemudian ambil koleksi bentuk, identifikasi yang berisi objek hyperlink, dan iterasi melalui mereka dalam urutan terbalik untuk menghapus setiap link secara aman tanpa memengaruhi indeks koleksi. Ini memastikan semua URL yang tertanam dihapus sambil mempertahankan integritas visual diagram.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Mengapa langkah ini penting**: Memuat file memberi Anda akses programatik ke setiap bentuk dan properti terkait.  

## Cara mengakses konten bentuk dalam diagram?  
Objek `DiagramShape` mewakili sebuah bentuk individual dalam diagram, menampilkan properti dan metadata yang terlampir. Setelah memuat diagram, panggil `getShapes()` pada Watermarker untuk mendapatkan daftar objek `DiagramShape`. Setiap bentuk dapat diperiksa untuk koleksi hyperlink, memungkinkan penargetan tepat link untuk dihapus atau dimodifikasi. Anda juga dapat membaca teks bentuk, warna, dan geometri jika diperlukan penyesuaian lebih lanjut.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Mengapa langkah ini penting**: Menargetkan bentuk yang tepat memastikan Anda hanya menghapus link yang tidak diinginkan tanpa memengaruhi elemen visual lainnya.  

## Cara mengiterasi dan menghapus hyperlink dengan aman?  
Metode `removeHyperlink(int index)` menghapus hyperlink pada posisi yang ditentukan dalam koleksi hyperlink sebuah bentuk. Iterasi daftar hyperlink dari indeks terakhir hingga nol. Loop terbalik ini mencegah pergeseran indeks yang terjadi saat item dihapus, memastikan setiap hyperlink diproses tanpa terlewat. Setelah penghapusan, Anda dapat menyegarkan status bentuk atau melanjutkan ke bentuk berikutnya dalam diagram.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Mengapa langkah ini penting**: Loop terbalik menjamin semua hyperlink dihapus tanpa melewatkan entri apa pun.  

## Cara menyimpan diagram yang telah diedit dan melepaskan sumber daya?  
Metode `save(String path)` menulis dokumen yang dimodifikasi ke lokasi file yang ditentukan, menyelesaikan semua perubahan. Setelah semua hyperlink dihapus, panggil metode `save` pada instance Watermarker, berikan nama file baru untuk menghindari menimpa file asli. Kemudian panggil `close()` untuk melepaskan handle file dan membebaskan memori, yang penting untuk proses batch yang berjalan lama. Ini memastikan file ditutup dengan benar dan siap untuk penggunaan selanjutnya.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Mengapa langkah ini penting**: Menutup sumber daya dengan benar menghindari kebocoran memori dan masalah penguncian file di server.  

## Aplikasi Praktis  

Menghapus hyperlink dari bentuk diagram dapat bermanfaat dalam beberapa skenario dunia nyata:  

1. **Keamanan** – Mencegah link eksternal yang dapat mengarahkan ke situs berbahaya.  
2. **Kepatuhan** – Memenuhi kebijakan perusahaan yang melarang URL tertanam dalam aset yang dibagikan.  
3. **Kejelasan** – Menghasilkan presentasi yang lebih bersih di mana link dapat mengganggu.  

Anda dapat menyematkan logika ini ke dalam pipeline otomasi yang lebih besar, seperti pekerjaan batch malam yang membersihkan semua diagram sebelum dipublikasikan ke intranet.  

## Pertimbangan Kinerja  

### Mengoptimalkan kinerja  
- Gunakan satu instance `Watermarker` per file untuk mengurangi overhead.  
- Lebih suka iterasi terbalik (seperti yang ditunjukkan) untuk menghindari re‑indeksasi daftar yang mahal.  

### Pedoman penggunaan sumber daya  
- Untuk diagram lebih besar dari 200 MB, pantau penggunaan heap dan pertimbangkan meningkatkan flag JVM `-Xmx`.  
- Alat profiling seperti VisualVM dapat membantu mengidentifikasi bottleneck dalam batch berskala besar.  

### Praktik terbaik untuk manajemen memori Java  
- Deklarasikan objek dalam ruang lingkup sekecil mungkin.  
- Gunakan try‑with‑resources saat bekerja dengan stream untuk memastikan penutupan otomatis.  

## Pertanyaan yang Sering Diajukan  

**Q: Bagaimana cara menangani diagram yang berisi ribuan bentuk?**  
A: Proses diagram halaman per halaman dan lepaskan sumber daya setiap halaman sebelum beralih ke berikutnya untuk menjaga penggunaan memori tetap rendah.  

**Q: Bisakah saya membatasi penghapusan hyperlink hanya pada halaman tertentu?**  
A: Ya – ambil indeks halaman yang diinginkan, kemudian terapkan loop penghapusan hanya pada bentuk di halaman tersebut.  

**Q: Apakah lisensi komersial wajib untuk pemrosesan batch?**  
A: Lisensi yang valid diperlukan untuk setiap penerapan tingkat produksi; percobaan gratis terbatas pada 30 hari dan 5 dokumen.  

**Q: Apakah GroupDocs.Watermark mendukung diagram SVG?**  
A: Tentu – SVG termasuk dalam lebih dari 30 format yang didukung, dan hyperlink dapat dihapus menggunakan panggilan API yang sama.  

**Q: Bagaimana jika sebuah bentuk memiliki banyak hyperlink?**  
A: Loop iterasi terbalik menghapus setiap entri hyperlink secara individual, memastikan semua link dihapus.  

## Sumber Daya  

- [Dokumentasi](https://docs.groupdocs.com/watermark/java/)  
- [Referensi API](https://reference.groupdocs.com/watermark/java)  
- [Unduhan](https://releases.groupdocs.com/watermark/java/)  
- [Repositori GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/watermark/10)  
- [Perolehan Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)  

---  

**Terakhir Diperbarui:** 2026-08-25  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs  

## Tutorial Terkait

- [Tutorial Watermark Diagram untuk GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Edit Header & Footer Diagram di Java Menggunakan GroupDocs.Watermark: Panduan Komprehensif](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Menghapus Bentuk dari Diagram Secara Efisien Menggunakan GroupDocs.Watermark untuk Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)