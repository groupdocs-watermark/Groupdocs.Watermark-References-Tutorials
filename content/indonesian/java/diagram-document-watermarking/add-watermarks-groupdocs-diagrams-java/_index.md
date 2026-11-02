---
date: '2026-02-16'
description: Pelajari cara menambahkan watermark pada halaman diagram tertentu dengan
  GroupDocs.Watermark untuk Java, termasuk cara menambahkan watermark gambar di Java
  dan melindungi file Anda.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: Menandai Halaman Diagram Tertentu dengan GroupDocs.Watermark untuk Java
type: docs
url: /id/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# Menandai Halaman Diagram Spesifik Menggunakan GroupDocs.Watermark untuk Java

Melindungi diagram Anda sangat penting, terutama ketika Anda perlu **watermark specific diagram page** untuk keamanan hak kekayaan intelektual atau atribusi merek. Dalam tutorial ini Anda akan mempelajari langkah demi langkah cara menambahkan watermark teks dan gambar ke halaman yang dipilih dari file diagram menggunakan **GroupDocs.Watermark for Java**. Pada akhir tutorial, Anda akan siap mengamankan diagram Anda dan mengontrol tepat di mana setiap watermark muncul.

## Jawaban Cepat
- **What is the primary purpose?** Tambahkan watermark ke halaman diagram yang dipilih.  
- **Which library is required?** GroupDocs.Watermark for Java (Maven atau unduhan langsung).  
- **Can I add an image watermark java?** Ya – gunakan `ImageWatermark` dengan opsi khusus halaman.  
- **Do I need a license?** Lisensi percobaan sementara dapat digunakan untuk pengujian; lisensi penuh diperlukan untuk produksi.  
- **How many lines of code?** Kurang dari 30 baris untuk alur kerja watermark teks + gambar lengkap.

## Apa itu “watermark specific diagram page”?
A **watermark specific diagram page** berarti menerapkan penanda visual—teks atau gambar—hanya pada halaman yang Anda pilih di dalam diagram multi‑halaman (misalnya, Visio . vsdx). Ini memberi Anda kontrol detail atas branding, pemberitahuan kerahasiaan, atau pernyataan hak cipta tanpa memengaruhi seluruh dokumen.

## Mengapa Menggunakan GroupDocs.Watermark untuk Java?
- **Full page control** – target indeks halaman mana pun yang Anda butuhkan.  
- **Rich styling** – font, warna, opasitas, rotasi, dan skala gambar semuanya dapat dikonfigurasi.  
- **Performance‑optimized** – memproses diagram besar secara efisien dan terintegrasi mulus dengan build Maven.  
- **Cross‑format support** – bekerja dengan Visio, SVG, dan banyak format diagram lainnya.

## Prasyarat
- **GroupDocs.Watermark for Java** versi perpustakaan 24.11 atau lebih baru.  
- Maven atau unduhan JAR langsung.  
- Pengaturan pengembangan Java dasar (JDK 8+ disarankan).

## Menyiapkan GroupDocs.Watermark untuk Java
### Menggunakan Maven groupdocs watermark
Sertakan GroupDocs.Watermark dalam proyek Anda melalui Maven dengan menambahkan ini ke `pom.xml` Anda:

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
Sebagai alternatif, unduh versi terbaru secara langsung dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Akuisisi Lisensi
Mulailah dengan percobaan gratis dengan mengunduh lisensi sementara. Opsi pembelian tersedia di situs resmi mereka jika Anda memilih untuk terus menggunakan GroupDocs.Watermark.

### Inisialisasi dan Penyiapan Dasar
Setelah terpasang, inisialisasi kelas `Watermarker` untuk operasi penandaan:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Panduan Implementasi
### Menambahkan Watermark Teks ke Halaman Spesifik
Untuk menambahkan watermark teks, buat dan konfigurasikan terlebih dahulu sebelum menentukan halaman target.

#### Buat Watermark Teks
Definisikan watermark teks Anda dengan konten yang dapat disesuaikan, gaya font, ukuran, dll.:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### Atur Indeks Halaman untuk Watermark
Tentukan halaman diagram mana yang akan menampilkan watermark menggunakan `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### Tambahkan Watermark Teks
Tambahkan watermark yang telah dikonfigurasi ke diagram:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### Menambahkan Watermark Gambar ke Halaman Spesifik
Ikuti langkah serupa untuk watermark gambar menggunakan objek `ImageWatermark`.

#### Buat Watermark Gambar
Buat instance `ImageWatermark` dengan jalur gambar watermark yang diinginkan:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### Atur Indeks Halaman untuk Watermark
Tentukan halaman mana yang harus menampilkan watermark gambar:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### Tambahkan Watermark Gambar
Tambahkan gambar ke halaman diagram yang Anda tentukan:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### Simpan dan Tutup Sumber Daya
Ingat untuk menyimpan perubahan dan menutup sumber daya untuk mencegah kebocoran:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Aplikasi Praktis
- **Document Security** – Terapkan watermark rahasia hanya pada halaman yang berisi skematik sensitif.  
- **Branding** – Letakkan logo perusahaan Anda pada halaman sampul sementara halaman interior tetap bersih.  
- **Copyright Protection** – Tambahkan pernyataan hak cipta pada halaman terakhir dari paket diagram teknis.

## Pertimbangan Kinerja
- **Memory Management** – Tutup setiap objek watermark setelah menyimpan untuk membebaskan sumber daya native.  
- **Image Optimization** – Gunakan file PNG/JPEG berukuran tepat untuk menjaga proses tetap cepat.  
- **Batch Processing** – Saat menangani banyak diagram, gunakan kembali satu instance `Watermarker` bila memungkinkan.

## Masalah Umum dan Solusinya
| Gejala | Penyebab Kemungkinan | Solusi |
|---------|--------------|-----|
| Watermark tidak terlihat | `pageIndex` salah (berbasis nol) | Verifikasi bahwa indeks cocok dengan halaman yang dimaksud. |
| Gambar terlihat terdistorsi | Gambar sumber beresolusi tinggi | Ubah ukuran gambar sebelum membuat `ImageWatermark`. |
| Kesalahan lisensi pada produksi | Menggunakan lisensi percobaan setelah kedaluwarsa | Terapkan file lisensi penuh melalui `License.setLicense("path/to/license.json")`. |

## Pertanyaan yang Sering Diajukan

**Q1: Bisakah saya menambahkan beberapa watermark ke satu halaman diagram?**  
A1: Ya, cukup panggil `watermarker.add()` dengan objek watermark yang berbeda untuk indeks halaman yang sama.

**Q2: Format file apa yang didukung oleh GroupDocs.Watermark untuk Java?**  
A2: Ini mendukung berbagai format diagram dan gambar. Periksa [API documentation](https://reference.groupdocs.com/watermark/java) untuk daftar lengkap.

**Q3: Bagaimana cara menangani masalah lisensi saat menggunakan versi percobaan?**  
A3: Mulailah dengan lisensi sementara gratis dari GroupDocs. Beli lisensi penuh untuk membuka semua fitur pada produksi.

**Q4: Apa saja tips pemecahan masalah umum jika watermark tidak muncul seperti yang diharapkan?**  
A4: Pastikan indeks halaman benar dan periksa kembali jalur file untuk sumber gambar. Juga pastikan opasitas watermark tidak disetel ke 0.

**Q5: Bagaimana saya dapat menyesuaikan tampilan watermark lebih lanjut?**  
A5: Sesuaikan ukuran font, opasitas, rotasi, dan posisi menggunakan metode yang tersedia pada `TextWatermark` atau `ImageWatermark`.

## Sumber Daya
- [Dokumentasi GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)
- [Panduan Referensi API](https://reference.groupdocs.com/watermark/java)
- [Unduh Perpustakaan](https://releases.groupdocs.com/watermark/java/)
- [Repositori GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/watermark/10)
- [Informasi Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

Jelajahi sumber daya ini untuk memperdalam pemahaman dan kemampuan Anda dengan GroupDocs.Watermark untuk Java. Selamat menandai!

---

**Terakhir Diperbarui:** 2026-02-16  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs