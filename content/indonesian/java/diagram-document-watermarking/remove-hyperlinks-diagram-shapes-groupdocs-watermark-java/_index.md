---
date: '2026-04-04'
description: Pelajari cara menghapus tautan dari bentuk diagram dengan GroupDocs.Watermark
  Java, memastikan keamanan dan kejelasan dokumen.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Cara Menghapus Tautan dari Bentuk Diagram dengan GroupDocs.Watermark Java
type: docs
url: /id/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cara Menghapus Tautan dari Bentuk Diagram menggunakan GroupDocs.Watermark Java

Mengelola dokumen digital sering melibatkan penyuntingan diagram, terutama ketika Anda perlu **cara menghapus tautan** untuk keamanan atau kejelasan. Dalam tutorial ini Anda akan mempelajari cara sederhana, langkah demi langkah untuk menghapus hyperlink yang tidak diinginkan dari bentuk diagram menggunakan pustaka **GroupDocs.Watermark** yang kuat untuk Java. Pada akhirnya, Anda akan memiliki diagram bersih tanpa tautan yang aman untuk dibagikan.

## Jawaban Cepat
- **Apa arti “cara menghapus tautan”?** Ini merujuk pada penghapusan objek hyperlink yang tertanam dalam bentuk diagram.  
- **Pustaka mana yang menangani ini?** GroupDocs.Watermark untuk Java (versi 24.11 atau lebih baru).  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi yang valid diperlukan untuk produksi.  
- **Bisakah saya memproses banyak file sekaligus?** Ya – bungkus kode dalam loop atau pekerjaan batch.  
- **Apakah pendekatan ini spesifik bahasa?** Contohnya menggunakan Java, tetapi konsep yang sama berlaku untuk API .NET/Java lainnya.

## Apa itu “cara menghapus tautan” dalam penyuntingan diagram?
Menghapus tautan berarti menemukan objek hyperlink yang terlampir pada bentuk di dalam diagram (mis., Visio *.vsdx) dan menghapusnya. Ini menghilangkan URL eksternal yang dapat mengungkap informasi sensitif atau mengganggu alur presentasi.

## Mengapa menggunakan GroupDocs.Watermark untuk Java?
- **Precision** – Akses langsung ke objek bentuk dan koleksi hyperlink mereka.  
- **Performance** – Dioptimalkan untuk diagram besar tanpa memuat seluruh dokumen ke memori.  
- **Cross‑format support** – Berfungsi dengan banyak format diagram (Visio, Draw.io, dll.).  

## Prasyarat
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (atau penyertaan JAR manual).  
- Java JDK 8 atau lebih baru.  
- IDE seperti IntelliJ IDEA atau Eclipse.

## Menyiapkan GroupDocs.Watermark untuk Java
### Pengaturan Maven
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
Jika Anda lebih memilih tidak menggunakan Maven, unduh JAR terbaru dari situs resmi:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Langkah-langkah Akuisisi Lisensi
- Mulai dengan mengunduh versi percobaan gratis.  
- Untuk produksi, dapatkan lisensi sementara atau penuh dari portal GroupDocs.

#### Inisialisasi dan Penyiapan Dasar
Buat instance `Watermarker` yang menunjuk ke folder yang berisi diagram Anda:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cara Menghapus Tautan dari Bentuk Diagram
Berikut adalah proses singkat empat langkah yang menunjukkan **remove hyperlinks java** dalam aksi.

### Langkah 1: Muat File Diagram
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Mengapa?* Memuat file memberi Anda akses programatik ke halaman, bentuk, dan koleksi hyperlinknya.

### Langkah 2: Akses Konten Bentuk
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Mengapa?* Anda memerlukan referensi ke bentuk spesifik yang mungkin berisi hyperlink.

### Langkah 3: Iterasi dan Hapus Hyperlink
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Mengapa?* Iterasi secara terbalik mencegah masalah pergeseran indeks saat menghapus item dari koleksi.

### Langkah 4: Simpan dan Tutup
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Mengapa?* Menyimpan menuliskan diagram yang telah dibersihkan ke disk, dan menutup melepaskan handle file untuk menghindari kebocoran memori.

## Aplikasi Praktis Menghapus Tautan
1. **Keamanan** – Hapus URL eksternal yang dapat menyebabkan phishing atau kebocoran data.  
2. **Kepatuhan** – Pastikan diagram memenuhi kebijakan internal sebelum distribusi.  
3. **Kebersihan Presentasi** – Hilangkan area yang dapat diklik tidak perlu yang mengalihkan perhatian penonton.

## Pertimbangan Kinerja
- **Efisiensi Loop** – Gunakan pola iterasi terbalik yang ditunjukkan di atas.  
- **Manajemen Sumber Daya** – Lebih baik gunakan `try‑with‑resources` atau pemanggilan `close()` secara eksplisit.  
- **File Besar** – Pantau CPU/memori; pertimbangkan memproses halaman secara batch.

## Masalah Umum dan Solusinya
- **Tidak ada hyperlink ditemukan** – Pastikan diagram memang berisi objek hyperlink; beberapa format menyimpannya secara berbeda.  
- **IndexOutOfBoundsException** – Selalu iterasi secara terbalik saat menghapus item dari koleksi.  
- **Kesalahan lisensi** – Pastikan file lisensi Anda ditempatkan dengan benar atau diteruskan ke konstruktor `Watermarker`.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana saya menangani banyak bentuk pada banyak halaman?**  
A: Loop melalui `content.getPages()` dan kemudian melalui koleksi `getShapes()` setiap halaman, menerapkan logika penghapusan yang sama pada setiap bentuk.

**Q: Bisakah saya memfilter tautan berdasarkan domain bukan URL lengkap?**  
A: Ya – ubah pemeriksaan `contains` untuk mencari string domain (mis., `"example.com"`).

**Q: Apakah ada cara untuk mencatat tautan mana yang dihapus?**  
A: Di dalam loop, ambil `shape.getHyperlinks().get_Item(i).getAddress()` sebelum dihapus dan tulis ke file log.

**Q: Apakah ini bekerja dengan diagram PDF yang disematkan dalam dokumen lain?**  
A: GroupDocs.Watermark mendukung banyak format; pastikan tipe file dikenali sebagai diagram (Visio, VDX, dll.).

**Q: Lisensi apa yang diperlukan untuk pemrosesan batch?**  
A: Lisensi produksi penuh diperlukan untuk operasi non‑percobaan dengan volume tinggi.

## Kesimpulan
Anda kini memiliki metode lengkap dan siap produksi untuk **cara menghapus tautan** dari bentuk diagram menggunakan GroupDocs.Watermark untuk Java. Gabungkan ini ke dalam alur pemrosesan dokumen Anda untuk meningkatkan keamanan, kepatuhan, dan kualitas visual.

### Langkah Selanjutnya
- Jelajahi fitur manipulasi lain seperti menambahkan watermark atau menstempel teks.  
- Gabungkan rutinitas ini dengan layanan pemantau file untuk secara otomatis membersihkan diagram saat diunggah.

---

**Terakhir Diperbarui:** 2026-04-04  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs  

## Sumber Daya
- [Dokumentasi](https://docs.groupdocs.com/watermark/java/)
- [Referensi API](https://reference.groupdocs.com/watermark/java)
- [Unduh](https://releases.groupdocs.com/watermark/java/)
- [Repositori GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/watermark/10)
- [Akuisisi Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)