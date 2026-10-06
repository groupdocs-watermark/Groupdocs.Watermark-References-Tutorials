---
date: '2026-07-30'
description: Pelajari cara mengatur lisensi untuk GroupDocs.Watermark di Java, lindungi
  dokumen Anda secara efektif, dan kelola penggunaan dengan efisien.
keywords:
- how to set license
- GroupDocs Watermark Java
- metered licensing Java
lastmod: '2026-07-30'
og_description: Cara mengatur lisensi untuk GroupDocs.Watermark di Java. Panduan ini
  memandu Anda melalui pemasangan SDK, memperoleh kunci bermeter, dan mengonfigurasi
  lisensi untuk mengamankan dokumen Anda.
og_image_alt: 'Guide: Set license for GroupDocs Watermark in Java'
og_title: Cara Mengatur Lisensi untuk GroupDocs Watermark di Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  headline: How to Set License for GroupDocs Watermark in Java
  type: TechArticle
- description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  name: How to Set License for GroupDocs Watermark in Java
  steps:
  - name: Define the public and private keys
    text: Enter the keys you received after registering for a temporary license. `Metered`
      is the GroupDocs.Watermark class that handles metered licensing and usage tracking.
      *Place your keys in a secure location (environment variables, encrypted config,
      etc.) before using them in code.*
  - name: Create an instance of the Metered class
    text: Instantiate the `Metered` object with your keys. This object will be passed
      to the watermark engine during initialization.
  - name: Set the metered license using the provided keys
    text: Call the `setLicense` method (or the equivalent API call) with your public
      and private keys. Once set, all subsequent watermark operations will be billed
      according to your usage. > **Pro tip:** Keep the keys out of source control.
      Use a secrets manager or encrypted properties file to avoid accidenta
  type: HowTo
- questions:
  - answer: A temporary license is time‑limited and ideal for evaluation, while a
      perpetual license provides unlimited use without recurring fees.
    question: What is the difference between a temporary and a perpetual license?
  - answer: Yes—replace the metered key initialization with a call to `engine.setLicense("path/to/license/file")`.
    question: Can I switch from a metered license to a perpetual one without code
      changes?
  - answer: The SDK falls back to offline mode; watermarking continues but usage won’t
      be reported until connectivity is restored.
    question: What happens if the metered service is unreachable?
  - answer: The SDK can handle files up to 1 GB; larger files should be split or processed
      in streaming mode.
    question: Are there file‑size limits for watermarking?
  - answer: It works on any platform that supports Java 8+, including Windows, Linux,
      and macOS.
    question: Does the metered license work on all operating systems?
  type: FAQPage
tags:
- set license
- GroupDocs Watermark
- Java licensing
- metered license
- document security
title: Cara Mengatur Lisensi untuk GroupDocs Watermark di Java
type: docs
url: /id/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Cara Mengatur Lisensi untuk GroupDocs Watermark di Java

Melindungi kekayaan intelektual adalah prioritas utama bagi aplikasi modern, dan watermark adalah cara terbukti untuk mencegah distribusi tidak sah. Jika Anda menggunakan **GroupDocs.Watermark for Java**, Anda memerlukan lisensi yang dapat melacak penggunaan dan skalabel dengan permintaan. Tutorial ini menjelaskan **cara mengatur lisensi** untuk GroupDocs.Watermark di Java, mulai dari menginstal SDK hingga mengonfigurasi kunci bermeter yang melaporkan konsumsi kembali ke layanan.

## Jawaban Cepat
- **Apa itu lisensi bermeter?** Ini adalah lisensi berbasis penggunaan yang mencatat setiap panggilan API, memungkinkan Anda membayar hanya untuk apa yang Anda konsumsi.  
- **Apakah saya perlu percobaan terlebih dahulu?** Ya, Anda dapat meminta lisensi sementara dari situs GroupDocs untuk mengevaluasi produk.  
- **Versi Java apa yang diperlukan?** Java 8 atau lebih baru; SDK dikompilasi untuk JDK 8+.  
- **Bisakah saya beralih ke lisensi permanen nanti?** Tentu – cukup ganti kunci bermeter dengan file lisensi permanen.  
- **Apakah pengaturan kompatibel dengan Maven?** Ya, koordinat Maven disediakan untuk manajemen dependensi yang mulus.

## Apa itu lisensi bermeter untuk GroupDocs Watermark?
Lisensi bermeter adalah hak penggunaan berbasis cloud yang disediakan oleh GroupDocs yang mencatat setiap operasi watermark yang dilakukan oleh SDK. Setiap panggilan API dicatat pada server lisensi GroupDocs, memungkinkan penagihan pay‑as‑you‑go berdasarkan penggunaan aktual. Model ini memberi pengembang wawasan waktu nyata tentang konsumsi dan membantu mengontrol biaya sambil memastikan akses penuh ke semua fitur.

## Mengapa menggunakan lisensi bermeter dengan GroupDocs Watermark?
GroupDocs.Watermark mendukung lebih dari lima puluh format input dan output—termasuk PDF, DOCX, PPTX, dan berbagai jenis gambar—dan dapat memproses file hingga 1 GB tanpa memuat seluruh dokumen ke memori, yang menjaga kinerja. Dengan menggunakan lisensi bermeter Anda hanya membayar untuk operasi yang benar‑benar dijalankan, memungkinkan solusi skalabel secara biaya sambil mempertahankan akses penuh ke semua fitur.

## Prasyarat
- Versi **GroupDocs.Watermark for Java** 24.11 atau lebih baru.  
- Java Development Kit (JDK) 8 atau lebih baru yang terpasang dan dikonfigurasi.  
- Familiaritas dasar dengan Maven atau manajemen JAR manual.  
- Kunci lisensi sementara atau permanen dari portal GroupDocs.

## Cara mengatur lisensi bermeter untuk GroupDocs Watermark di Java?

Muat kunci publik dan pribadi Anda, buat instance `Metered`, dan terapkan lisensi—semua dalam tiga langkah singkat. Pendekatan ini menjamin setiap permintaan watermark dihitung terhadap akun Anda, memberi Anda visibilitas penuh terhadap konsumsi.

### Langkah 1: Tentukan kunci publik dan pribadi
Masukkan kunci yang Anda terima setelah mendaftar untuk lisensi sementara.

`Metered` adalah kelas GroupDocs.Watermark yang menangani lisensi bermeter dan pelacakan penggunaan.  
*Letakkan kunci Anda di lokasi yang aman (variabel lingkungan, konfigurasi terenkripsi, dll.) sebelum menggunakannya dalam kode.*

### Langkah 2: Buat instance dari kelas Metered
Instansiasi objek `Metered` dengan kunci Anda. Objek ini akan diteruskan ke mesin watermark selama inisialisasi.

```text
Metered metered = new Metered(System.getenv("GROUPDOCS_PUBLIC_KEY"),
                               System.getenv("GROUPDOCS_PRIVATE_KEY"));
```

### Langkah 3: Atur lisensi bermeter menggunakan kunci yang disediakan
Panggil metode `setLicense` (atau panggilan API setara) dengan kunci publik dan pribadi Anda. Setelah diatur, semua operasi watermark berikutnya akan ditagih sesuai penggunaan Anda.

```text
WatermarkEngine engine = new WatermarkEngine();
engine.setMeteredLicense(metered);
```

> **Tips pro:** Simpan kunci di luar kontrol sumber. Gunakan manajer rahasia atau file properti terenkripsi untuk menghindari paparan tidak sengaja.

## Menyiapkan GroupDocs.Watermark untuk Java

### Informasi Instalasi

Integrasikan GroupDocs.Watermark ke dalam proyek Anda menggunakan Maven atau dengan mengunduh JAR secara langsung.

**Pengaturan Maven:**  
Tambahkan konfigurasi berikut dalam file `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>watermark</artifactId>
    <version>24.11</version>
</dependency>
```

**Unduhan Langsung:**  
Unduh versi terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Akuisisi Lisensi

Untuk membuka semua fungsi, dapatkan percobaan gratis atau lisensi sementara:

- Daftar di [situs GroupDocs](https://purchase.groupdocs.com/temporary-license/) untuk memulai.  
- Setelah memperoleh kunci Anda, integrasikan ke dalam proyek Anda seperti yang ditunjukkan dalam panduan implementasi.

### Inisialisasi dan Pengaturan Dasar

Setelah SDK ditambahkan ke proyek Anda, impor namespace yang diperlukan dan buat instance mesin watermark seperti yang ditunjukkan dalam cuplikan kode di atas.

## Tips Pemecahan Masalah
- **Kunci tidak valid:** Periksa kembali bahwa kunci publik dan pribadi cocok persis; satu typo saja akan mencegah aktivasi.  
- **Kesalahan jalur file lisensi:** Jika Anda lebih suka lisensi berbasis file, pastikan jalur file bersifat absolut atau terresolusi dengan benar relatif terhadap direktori kerja.  
- **Masalah jaringan:** Lisensi bermeter memerlukan panggilan HTTPS keluar; verifikasi bahwa firewall Anda mengizinkan lalu lintas ke `api.groupdocs.com`.

## Aplikasi Praktis
1. **Keamanan Dokumen:** Tambahkan watermark terlihat atau tidak terlihat pada PDF, dokumen Word, dan gambar untuk melindungi data perusahaan yang sensitif.  
2. **Pelacakan Penggunaan:** Hasilkan laporan tentang berapa banyak dokumen yang telah diberi watermark per hari, berguna untuk penganggaran dan kepatuhan.  
3. **Integrasi CMS:** Otomatiskan penyisipan watermark selama alur kerja penerbitan konten, dengan lisensi yang secara otomatis ditegakkan.

## Pertimbangan Kinerja

**Mengoptimalkan Kinerja:**  
- Terapkan watermark hanya bila diperlukan; lewati pemrosesan untuk file yang sudah dilindungi.  
- Untuk batch besar, gunakan kembali instance `WatermarkEngine` yang sama untuk menghindari overhead inisialisasi berulang.  

**Praktik Terbaik:**  
- Pantau penggunaan heap JVM saat memproses PDF beratus halaman; pertimbangkan API streaming jika memori menjadi kendala.  
- Aktifkan logging pada level `INFO` untuk menangkap panggilan lisensi tanpa membanjiri konsol.

## Kesimpulan

Dalam panduan ini kami membahas **cara mengatur lisensi** untuk GroupDocs.Watermark di Java, mulai dari instalasi Maven hingga konfigurasi kunci bermeter. Dengan mengikuti langkah‑langkah tersebut, Anda memperoleh pelacakan penggunaan yang tepat, penagihan fleksibel, dan perlindungan dokumen yang kuat—semua tanpa mengorbankan kinerja.

**Langkah Selanjutnya:**  
- Bereksperimen dengan berbagai gaya watermark (teks, gambar, diagonal).  
- Jelajahi fitur lanjutan seperti watermark bersyarat berdasarkan peran pengguna.  
- Tinjau dasbor analitik GroupDocs untuk memantau tren konsumsi.

Siap mengamankan dokumen Anda? Implementasikan solusi hari ini dan nikmati ketenangan pikiran mengetahui aset Anda terlindungi dan biaya lisensi Anda transparan.

## Pertanyaan yang Sering Diajukan

**T: Apa perbedaan antara lisensi sementara dan lisensi permanen?**  
A: Lisensi sementara bersifat terbatas waktu dan ideal untuk evaluasi, sementara lisensi permanen memberikan penggunaan tak terbatas tanpa biaya berulang.

**T: Bisakah saya beralih dari lisensi bermeter ke lisensi permanen tanpa perubahan kode?**  
A: Ya—ganti inisialisasi kunci bermeter dengan panggilan ke `engine.setLicense("path/to/license/file")`.

**T: Apa yang terjadi jika layanan bermeter tidak dapat dijangkau?**  
A: SDK beralih ke mode offline; watermarking tetap berlanjut tetapi penggunaan tidak akan dilaporkan sampai konektivitas dipulihkan.

**T: Apakah ada batas ukuran file untuk watermarking?**  
A: SDK dapat menangani file hingga 1 GB; file yang lebih besar harus dipisah atau diproses dalam mode streaming.

**T: Apakah lisensi bermeter bekerja di semua sistem operasi?**  
A: Ini bekerja di platform apa pun yang mendukung Java 8+, termasuk Windows, Linux, dan macOS.

---

**Last Updated:** 2026-07-30  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Sumber Daya**

- [Dokumentasi](https://docs.groupdocs.com/watermark/java/)
- [Referensi API](https://reference.groupdocs.com/watermark/java)
- [Unduh](https://releases.groupdocs.com/watermark/java/)
- [Repositori GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/watermark/10)
- [Akuisisi Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

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
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```

```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```

```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```

## Tutorial Terkait

- [Tutorial Lisensi dan Konfigurasi GroupDocs.Watermark untuk Java](/watermark/java/licensing-configuration/)
- [Cara Menyiapkan Lisensi GroupDocs.Watermark di Java: Panduan Lengkap](/watermark/java/licensing-configuration/groupdocs-watermark-licensing-java-guide/)
- [Panduan Watermarking Java: Amankan Dokumen dengan API GroupDocs.Watermark](/watermark/java/getting-started/java-watermark-groupdocs-guide/)