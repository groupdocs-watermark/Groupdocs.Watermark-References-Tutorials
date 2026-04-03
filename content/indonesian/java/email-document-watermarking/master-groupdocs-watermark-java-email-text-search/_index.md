---
date: '2025-12-31'
description: Pelajari cara mencari teks email menggunakan GroupDocs.Watermark untuk
  Java, kelola isi, subjek, dan lampiran secara efisien.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Cara Mencari Teks Email dengan GroupDocs.Watermark Java – Panduan Lengkap
type: docs
url: /id/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Cara Mencari Teks Email dengan GroupDocs.Watermark Java

Menemukan frasa tertentu di dalam subjek, isi, atau lampiran email dapat menjadi sangat merepotkan—terutama ketika Anda menangani puluhan atau ratusan pesan. Pada tutorial ini Anda akan mempelajari **cara mencari teks email** dengan cepat dan akurat menggunakan **GroupDocs.Watermark untuk Java**. Kami akan membahas pengaturan, kode, dan tips praktik terbaik sehingga Anda dapat mengintegrasikan pencarian teks email ke dalam aplikasi Anda dengan percaya diri.

## Jawaban Cepat
- **Perpustakaan apa yang memungkinkan saya mencari teks email di Java?** GroupDocs.Watermark untuk Java.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi berbayar diperlukan untuk produksi.  
- **Bisakah saya mencari di subjek maupun isi?** Ya—konfigurasikan `EmailSearchableObjects` untuk menyertakan Subject, HtmlBody, dan PlainTextBody.  
- **Apakah API sensitif huruf besar/kecil?** Anda dapat memilih pencarian tidak sensitif huruf besar/kecil dengan mengatur flag yang sesuai di `TextSearchCriteria`.  
- **Versi Java apa yang dibutuhkan?** JDK 8 atau lebih tinggi; Maven disarankan untuk manajemen dependensi.

## Apa itu “cara mencari email” dengan GroupDocs.Watermark?
GroupDocs.Watermark menyediakan API terpadu untuk menemukan, menghapus, atau memodifikasi watermark dan teks biasa di berbagai tipe dokumen—termasuk **pesan email** (`.msg`, `.eml`). Dengan memanfaatkan model objek yang dapat dicari, Anda dapat menargetkan bagian email yang tepat, sehingga pemrosesan massal menjadi cepat dan dapat diandalkan.

## Mengapa menggunakan GroupDocs.Watermark Java untuk pencarian email?
- **API terpadu** – Berfungsi dengan PDF, gambar, file Office, dan email menggunakan pola kode yang sama.  
- **Dioptimalkan untuk kinerja** – Operasi pencarian dijalankan di memori tanpa memerlukan layanan eksternal.  
- **Penanganan yang kuat** – Mendukung badan HTML dan teks biasa, lampiran, serta email yang dilindungi kata sandi.  
- **Integrasi mudah** – Siap pakai dengan Maven/Gradle, dilengkapi dokumentasi jelas dan dukungan aktif.

## Prasyarat

- **Java Development Kit (JDK)** 8 atau yang lebih baru.  
- **Maven** (atau Gradle) untuk manajemen dependensi.  
- IDE seperti **IntelliJ IDEA** atau **Eclipse**.  
- Familiaritas dasar dengan sintaks Java dan format file email (`.msg`, `.eml`).

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
Sebagai alternatif, Anda dapat mengunduh JAR terbaru dari [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Akuisisi Lisensi
- **Percobaan Gratis:** Uji fitur inti tanpa kunci lisensi.  
- **Lisensi Sementara:** Minta kunci berjangka waktu untuk evaluasi lebih lama.  
- **Lisensi Berbayar:** Beli untuk penggunaan produksi tanpa batas.

#### Inisialisasi Dasar
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Panduan Implementasi

### Fitur 1: Mencari Teks di Isi Email

#### Gambaran Umum
Kami akan mengonfigurasi API untuk memindai **subjek**, **badan HTML**, dan **badan teks biasa** email demi menemukan kata kunci tertentu.

#### Langkah 1: Tentukan Jalur Dokumen
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Langkah 2: Siapkan Load Options dan Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Langkah 3: Buat Kriteria Pencarian
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Langkah 4: Tentukan Lokasi Pencarian
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Langkah 5: Jalankan Pencarian dan Hapus Watermark
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Langkah 6: Simpan Perubahan
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tips Pemecahan Masalah
- **Hasil kosong:** Pastikan kata kunci memang muncul di bagian email yang dipilih.  
- **Kinerja:** Batasi objek yang dapat dicari hanya pada yang Anda perlukan (misalnya Subject + PlainTextBody) untuk mempercepat pemrosesan batch besar.

### Fitur 2: Opsi Memuat Dokumen Email

#### Gambaran Umum
`EmailLoadOptions` memungkinkan Anda mengontrol cara email diparse—berguna untuk pesan terenkripsi atau enkoding khusus.

#### Langkah 1: Konfigurasikan Load Options
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opsi Konfigurasi Utama
- **Proteksi Kata Sandi:** Setel `loadOptions.setPassword("yourPassword")` untuk file `.msg` yang terenkripsi.  
- **Pengaturan Enkoding:** Sesuaikan `loadOptions.setEncoding(Charset.forName("UTF-8"))` saat berurusan dengan set karakter non‑standar.

## Aplikasi Praktis

- **Pemrosesan Email Otomatis:** Pindai massal tiket dukungan masuk untuk kata kunci seperti “refund” atau “error”.  
- **Pemeriksaan Kepatuhan Hukum:** Cepat temukan istilah rahasia (misalnya SSN, nomor kartu kredit) di arsip email perusahaan.  
- **Otomatisasi Dukungan Pelanggan:** Arahkan email berdasarkan frasa yang terdeteksi ke tim dukungan yang tepat.

## Pertimbangan Kinerja
- **Manajemen Sumber Daya:** Panggil `watermarker.close()` segera setelah selesai memproses untuk membebaskan sumber daya native.  
- **Praktik Memori Terbaik:** Saat menangani ribuan pesan, proses dalam batch dan gunakan kembali instance `Watermarker` bila memungkinkan.

## Kesimpulan
Anda kini memiliki pendekatan siap produksi untuk **cara mencari teks email** menggunakan GroupDocs.Watermark Java. Fleksibilitas API memungkinkan Anda menargetkan bagian spesifik email, menghapus watermark yang tidak diinginkan, dan mengintegrasikan logika ini ke dalam alur kerja yang lebih besar.

### Langkah Selanjutnya
- Bereksperimen dengan **kriteria pencarian ganda** (misalnya gabungkan “invoice” + “overdue”).  
- Jelajahi **penambahan watermark** untuk menandai email yang berisi data sensitif.  
- Selami tipe dokumen lain (PDF, DOCX) dengan alur kerja Watermarker yang sama.

## Pertanyaan yang Sering Diajukan

**T1:** Bagaimana cara menangani email terenkripsi dengan GroupDocs.Watermark?  
**J1:** Gunakan `EmailLoadOptions.setPassword("yourPassword")` sebelum membuat instance `Watermarker`.

**T2:** Bisakah saya mencari beberapa kata kunci sekaligus?  
**J2:** Ya—buat objek `SearchCriteria` terpisah untuk tiap kata kunci dan gabungkan dengan operator logika (misalnya `OrSearchCriteria`).

**T3:** Apakah GroupDocs.Watermark Java gratis untuk digunakan?  
**J3:** Versi percobaan gratis tersedia untuk evaluasi. Untuk penggunaan produksi, lisensi berbayar diperlukan.

**T4:** Bagaimana cara menangani volume email yang besar secara efisien?  
**J4:** Batasi objek yang dapat dicari hanya pada yang diperlukan, proses email dalam batch, dan selalu tutup `Watermarker` untuk melepaskan sumber daya.

**T5:** Di mana saya dapat menemukan bantuan atau dukungan tambahan?  
**J5:** Kunjungi [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) untuk bantuan komunitas atau hubungi dukungan GroupDocs secara langsung.

## Sumber Daya
- **Dokumentasi:** Jelajahi panduan lengkap di [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **Referensi API:** Akses detail teknis di [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Terakhir Diperbarui:** 2025-12-31  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs  

---