---
date: '2026-04-07'
description: Pelajari cara mencari isi email dengan Java menggunakan GroupDocs.Watermark,
  termasuk cara mencari beberapa kata kunci dalam email dan cara menghapus watermark
  email.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Mencari Isi Email Java dengan GroupDocs.Watermark: Panduan Komprehensif'
type: docs
url: /id/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Cari Isi Email Java dengan GroupDocs.Watermark

Jika Anda perlu **search email body java** dengan cepat dan andal, Anda berada di tempat yang tepat. Dalam tutorial ini kami akan menjelaskan bagaimana GroupDocs.Watermark untuk Java memungkinkan Anda menemukan teks tertentu di dalam subjek email, isi HTML, dan isi teks biasa, serta bagaimana Anda dapat membersihkan watermark yang tidak diinginkan setelahnya. Pada akhir tutorial, Anda akan dapat mengimplementasikan solusi yang kuat yang bekerja pada satu atau beberapa kata kunci dan bahkan menghapus watermark email bila diperlukan.

## Jawaban Cepat
- **Apa arti “search email body java”?** Ini mengacu pada penggunaan kode Java (dengan GroupDocs.Watermark) untuk menemukan teks di dalam konten email.  
- **Bisakah saya mencari beberapa kata kunci email sekaligus?** Ya – buat objek `SearchCriteria` terpisah dan gabungkan mereka.  
- **Bagaimana cara menghapus watermark email?** Gunakan metode `PossibleWatermarkCollection.clear()` setelah pencarian.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi permanen diperlukan untuk produksi.  
- **IDE mana yang paling cocok?** IntelliJ IDEA atau Eclipse keduanya didukung sepenuhnya.

## Apa yang Akan Anda Pelajari
- Menginstal dan mengkonfigurasi GroupDocs.Watermark untuk Java.  
- Menyiapkan kriteria pencarian untuk **search email body java** di seluruh subjek dan isi.  
- Teknik untuk **search multiple keywords email** dalam satu proses.  
- Langkah tepat **how to remove email watermarks** setelah menemukannya.  

## Mengapa Mencari Isi Email Java dengan GroupDocs.Watermark?
GroupDocs.Watermark menyediakan API tingkat tinggi yang menyederhanakan kompleksitas parsing file .msg, menangani berbagai format isi, dan mengelola watermark. Ini menghemat waktu Anda dibandingkan membangun parser khusus dan memastikan hasil yang konsisten pada kumpulan email yang besar.

## Prasyarat
- Java Development Kit (JDK) 8 atau yang lebih baru.  
- Maven (atau kemampuan menambahkan JAR secara manual).  
- Pemahaman dasar tentang Java dan format file email (.msg, .eml).  

## Menyiapkan GroupDocs.Watermark untuk Java
GroupDocs.Watermark untuk Java menyederhanakan penambahan watermark dan pencarian teks dalam dokumen, termasuk email. Berikut dua cara paling umum untuk menambahkan pustaka ke proyek Anda.

### Pengaturan Maven
Sertakan berikut ini dalam file `pom.xml` Anda untuk menambahkan GroupDocs.Watermark sebagai dependensi:
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
Sebagai alternatif, Anda dapat mengunduh versi terbaru secara langsung dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Langkah-langkah Akuisisi Lisensi
- **Free Trial:** Mulai dengan percobaan gratis untuk menguji fungsionalitas dasar.  
- **Temporary License:** Dapatkan lisensi sementara untuk akses dan pengujian yang lebih lama.  
- **Purchase:** Pertimbangkan untuk membeli jika GroupDocs.Watermark memenuhi kebutuhan Anda.

#### Inisialisasi Dasar
Inisialisasi kelas `Watermarker` seperti ditunjukkan di bawah:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Panduan Implementasi

### Fitur 1: Cari Teks dalam Isi Email
Fitur ini memungkinkan pencarian teks tertentu dalam subjek dan isi email.

#### Gambaran Umum
Kami akan menunjukkan cara mengkonfigurasi GroupDocs.Watermark untuk mencari melalui bagian-bagian berbeda dari pesan email menggunakan kode Java.

##### Langkah 1: Tentukan Jalur Dokumen
Siapkan jalur input dan output Anda untuk menangani email:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Langkah 2: Siapkan Opsi Muat dan Watermarker
Inisialisasi `EmailLoadOptions` dan `Watermarker` untuk bekerja dengan dokumen email Anda.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Langkah 3: Buat Kriteria Pencarian
Tentukan kriteria untuk pencarian teks. Kami akan menggunakan pencarian tidak sensitif huruf besar/kecil untuk kata kunci **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Langkah 4: Tentukan Lokasi Pencarian
Konfigurasikan pencarian untuk mencakup subjek dan isi email:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Langkah 5: Jalankan Pencarian dan Hapus Watermark
Lakukan pencarian dan hapus semua watermark yang ditemukan:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Langkah 6: Simpan Perubahan
Setelah diproses, simpan perubahan Anda ke dokumen baru:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tips Pemecahan Masalah
- **Common Issue:** Jika hasil pencarian kosong, pastikan teks ada di dalam isi atau subjek email.  
- **Performance Tip:** Optimalkan dengan membatasi pencarian hanya pada bagian yang memang Anda butuhkan.

### Fitur 2: Opsi Memuat Dokumen Email
Bagian ini membahas cara menyiapkan opsi tambahan saat memuat dokumen email untuk diproses dengan GroupDocs.Watermark.

#### Gambaran Umum
Mengkonfigurasi opsi muat memberikan kontrol lebih besar atas cara dokumen ditangani, seperti menentukan perlindungan kata sandi atau pengaturan enkoding.

##### Langkah 1: Konfigurasikan Opsi Muat
Berikut contoh konfigurasi dasar untuk `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opsi Konfigurasi Utama
- **Password Protection:** Tentukan kata sandi jika email Anda dienkripsi.  
- **Encoding Settings:** Tentukan jenis enkoding tertentu sesuai kebutuhan.

## Cara Mencari Beberapa Kata Kunci Email
Jika Anda perlu menemukan beberapa istilah dalam satu proses, buat beberapa objek `SearchCriteria` dan gabungkan mereka menggunakan operator logika **OR** atau **AND**. API memungkinkan Anda menggabungkan kriteria, sehingga Anda dapat mencari “invoice” **atau** “receipt” tanpa menjalankan loop terpisah.

## Cara Menghapus Watermark Email
Setelah Anda menemukan watermark (atau teks apa pun yang cocok dengan kriteria Anda), metode `PossibleWatermarkCollection.clear()` menghapusnya dari dokumen email. Ini adalah langkah tepat yang kami gunakan pada **Langkah 5** di atas, dan berfungsi untuk jumlah kecocokan berapa pun.

## Aplikasi Praktis

### Kasus Penggunaan 1: Pemrosesan Email Otomatis
Otomatisasi penyaringan dan pemrosesan data email massal untuk menemukan konten tertentu secara efisien.

### Kasus Penggunaan 2: Pemeriksaan Kepatuhan Hukum
Pastikan kepatuhan dengan mencari informasi sensitif dalam email perusahaan.

### Kasus Penggunaan 3: Otomasi Dukungan Pelanggan
Permudah alur kerja dukungan dengan cepat menemukan kata kunci atau frasa dalam pertanyaan pelanggan.

## Pertimbangan Kinerja
Saat menggunakan GroupDocs.Watermark, pertimbangkan hal berikut untuk mengoptimalkan kinerja:

- **Resource Management:** Kelola memori dan daya pemrosesan secara efisien untuk menangani kumpulan data email yang besar.  
- **Java Memory Management Best Practices:** Secara rutin pantau penggunaan sumber daya dan lepaskan sumber daya dengan cepat.

## Pertanyaan yang Sering Diajukan

**Q:** Bagaimana saya dapat menangani email terenkripsi dengan GroupDocs.Watermark?  
**A:** Gunakan `EmailLoadOptions` untuk menentukan kata sandi saat menginisialisasi `Watermarker`.

**Q:** Bisakah saya mencari beberapa kata kunci sekaligus?  
**A:** Ya, buat instance `SearchCriteria` terpisah dan gabungkan mereka menggunakan operasi logika.

**Q:** Apakah GroupDocs.Watermark Java gratis untuk digunakan?  
**A:** Versi percobaan gratis tersedia; pertimbangkan membeli lisensi untuk fitur tambahan.

**Q:** Bagaimana cara menangani volume email yang besar secara efisien?  
**A:** Optimalkan pencarian Anda dengan menargetkan bagian email tertentu dan mengelola sumber daya secara efektif.

**Q:** Di mana saya dapat menemukan bantuan atau dukungan tambahan?  
**A:** Kunjungi [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) untuk dukungan komunitas atau hubungi saluran dukungan gratis mereka.

## Sumber Daya
- **Documentation:** Jelajahi panduan detail di [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Akses detail teknis di [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Terakhir Diperbarui:** 2026-04-07  
**Diuji Dengan:** GroupDocs.Watermark 24.11 for Java  
**Penulis:** GroupDocs