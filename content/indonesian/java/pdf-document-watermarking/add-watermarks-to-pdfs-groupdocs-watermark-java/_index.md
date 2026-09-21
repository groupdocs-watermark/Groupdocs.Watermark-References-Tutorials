---
date: '2026-01-23'
description: Pelajari cara menambahkan watermark pada file PDF dengan watermark teks
  dan gambar menggunakan GroupDocs.Watermark untuk Java – panduan lengkap untuk keamanan
  dokumen PDF.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: Cara Menambahkan Watermark pada PDF Menggunakan GroupDocs.Watermark untuk Java
type: docs
url: /id/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Cara Menambahkan Watermark pada PDF Menggunakan GroupDocs.Watermark untuk Java

Di dunia digital saat ini, **cara menambahkan watermark pada PDF** adalah pertanyaan umum bagi siapa saja yang perlu melindungi hak kekayaan intelektual atau aset merek. Menambahkan watermark—baik teks maupun gambar—membantu Anda menegakkan **keamanan dokumen PDF** dan membuat distribusi tidak sah menjadi jauh lebih sulit. Dalam tutorial ini, Anda akan belajar langkah demi langkah cara menggunakan **GroupDocs.Watermark untuk Java** untuk menambahkan watermark teks dan gambar ke dokumen PDF.

## Jawaban Cepat
- **Library apa yang menambahkan watermark ke PDF di Java?** GroupDocs.Watermark for Java.  
- **Apakah saya dapat menambahkan watermark teks dan gambar?** Ya, API mendukung kedua jenis.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk evaluasi; lisensi berbayar menghilangkan batasan.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi.  
- **Apakah Maven didukung?** Tentu – cukup tambahkan repositori dan dependensi.

## Apa itu Watermark PDF dan Mengapa Menggunakannya?
Watermark pada PDF menyisipkan penanda yang terlihat atau tidak terlihat yang mengidentifikasi kepemilikan, kerahasiaan, atau branding. Ini adalah cara yang ringan namun kuat untuk mencegah penyalinan, membuktikan kepengarangan, dan mematuhi kebijakan perusahaan.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

1. **Java Development Kit (JDK) 8+** terpasang di mesin Anda.  
2. **GroupDocs.Watermark untuk Java** (versi terbaru).  
3. **Maven** (atau kemampuan untuk menambahkan JAR secara manual).

### Penyiapan Lingkungan

#### Konfigurasi Maven
Tambahkan repositori GroupDocs dan dependensi watermark ke `pom.xml` Anda:

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

#### Unduhan Langsung
Jika Anda lebih memilih tidak menggunakan Maven, Anda dapat mengunduh JAR secara langsung dari [GroupDocs.Watermark untuk rilis Java](https://releases.groupdocs.com/watermark/java/).

### Akuisisi Lisensi
Untuk memulai dengan percobaan gratis atau mendapatkan lisensi sementara, kunjungi [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Untuk penggunaan produksi, beli langganan untuk membuka semua fitur.

## Menyiapkan GroupDocs.Watermark untuk Java

Impor kelas inti yang mengendalikan semua operasi watermark:

```java
import com.groupdocs.watermark.Watermarker;
```

Impor ini memberi Anda akses ke kelas `Watermarker`, yang merupakan titik masuk untuk menambahkan watermark ke jenis dokumen apa pun yang didukung.

## Implementasi Langkah demi Langkah

Di bawah ini kami membagi proses menjadi bagian logis: membuat watermark teks, membuat watermark gambar, dan akhirnya menerapkannya pada gambar di dalam PDF.

### 1. Menginisialisasi Watermark Teks

**Mengapa watermark teks?** Ini ringan, dapat dicari, dan sempurna untuk menambahkan pemberitahuan hak cipta atau pernyataan kerahasiaan.

#### 1.1 Buat Instance TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Atur Penjajaran
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Putar Watermark
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Konfigurasi Ukuran
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Menginisialisasi Watermark Gambar

**Kapan menggunakan watermark gambar?** Ideal untuk branding dengan logo atau menambahkan pola visual yang kompleks.

#### 2.1 Muat File Gambar
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Atur Penjajaran
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Putar Watermark Gambar
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Konfigurasi Ukuran
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Tambahkan Watermark ke Gambar di Dalam PDF

Sekarang kami akan menggabungkan semuanya: membuka PDF, menemukan setiap gambar, dan menerapkan watermark teks atau gambar berdasarkan ukuran.

#### 3.1 Buka Dokumen PDF
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Ambil Semua Gambar
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Terapkan Watermark Secara Kondisional
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 Lepaskan Sumber Daya Gambar
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Simpan PDF yang Dimodifikasi
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Bersihkan
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Aplikasi Praktis Watermark PDF

| Kasus Penggunaan | Bagaimana Watermark Membantu |
|------------------|------------------------------|
| **Keamanan Dokumen** | Menandai file rahasia, mencegah kebocoran. |
| **Perlindungan Merek** | Menyisipkan logo pada PDF pemasaran, memperkuat identitas merek. |
| **Pernyataan Hak Cipta** | Menambahkan nama penulis atau simbol © untuk menegaskan kepemilikan. |
| **Kontrol Versi** | Menampilkan nomor versi atau tanggal langsung pada halaman. |

## Kesalahan Umum & Tips

- **Pememisah jalur:** Gunakan double backslashes (`\\`) di Windows atau forward slashes (`/`) di Linux/macOS untuk menghindari `FileNotFoundException`.
- **PDF besar:** Proses gambar dalam batch atau tingkatkan ukuran heap JVM (`-Xmx2g`) untuk mencegah error OutOfMemory.
- **Batas lisensi:** Versi percobaan mungkin membatasi jumlah halaman yang diproses; tingkatkan untuk penggunaan tak terbatas.
- **Kebingungan rotasi:** Ingat bahwa `setRotateAngle` mengharapkan nilai dalam derajat; nilai negatif memutar berlawanan arah jarum jam.

## Pertanyaan yang Sering Diaj watermark pada PDF yang dilindungi kata sandi?**  
A: Ya. Buka dokumen format lain seperti DOCX atau PPTX?**  
A: Tentu. GroupDocs.Watermark `water indeks halaman yang diinginkan.

**Q: Bagaimana jika saya perlu menambahkan watermark pada PDF yang disimpan di bucket cloud?**  
A: Muat PDF ke dalam `InputStream` dan berikan ke konstruktor `Watermarker`; setelah diproses, tulis kembali output stream ke cloud.

## Kesimpulan

Anda kini memiliki metode lengkap dan siap produksi untuk **cara menambahkan watermark pada PDF** menggunakan GroupDocs.Watermark untuk Java. Dengan menggabungkan watermark teks dan gambar, Anda dapat mencapai **keamanan dokumen PDF** yang kuat yang memenuhi kebutuhan branding dan kepatuhan. Jelajahi fitur lain dari perpustakaan—seperti penghapusan watermark atau pemrosesan batch—untuk memperluas alur kerja dokumen Anda lebih jauh.

---

**Terakhir Diperbarui:** 2026-01-23  
**Diuji Dengan:** GroupDocs.Watermark 24.11 for Java  
**Penulis:** GroupDocs