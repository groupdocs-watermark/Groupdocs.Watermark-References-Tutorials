---
date: '2026-02-18'
description: Pelajari cara menambahkan watermark dan cara menghapus watermark pada
  file diagram seperti .vsdx dengan GroupDocs.Watermark untuk Java. Lindungi integritas
  dokumen dengan GroupDocs Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Cara Menambahkan Watermark ke Diagram menggunakan GroupDocs.Watermark untuk
  Java
type: docs
url: /id/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Cara Menambahkan Watermark ke Diagram menggunakan GroupDocs.Watermark untuk Java

Mengelola watermark pada file diagram merupakan bagian penting dalam melindungi kekayaan intelektual dan menjaga dokumen tetap bersih untuk distribusi publik. Dalam panduan ini Anda akan mempelajari **cara menambahkan watermark** ke diagram Visio, serta **cara menghapus watermark** ketika tidak lagi diperlukan, semuanya dengan pustaka **groupdocs watermark java**. Baik Anda membangun pipeline dokumen tingkat perusahaan maupun skrip utilitas cepat, langkah‑langkah ini akan memberi Anda kontrol penuh atas watermark pada diagram.

## Jawaban Cepat
- **Pustaka apa yang menangani watermark diagram di Java?** GroupDocs.Watermark untuk Java.  
- **Apakah saya dapat menambahkan dan menghapus watermark dalam satu proses?** Ya – muat diagram sekali dan terapkan operasi penambahan serta penghapusan.  
- **Format file apa yang didukung?** Format Visio seperti `.vsdx`, `.vdx`, serta tipe diagram lainnya.  
- **Apakah saya memerlukan lisensi?** Lisensi percobaan dapat digunakan untuk pengembangan; lisensi penuh diperlukan untuk produksi.  
- **Versi Java apa yang dibutuhkan?** JDK 8 atau lebih tinggi.

## Apa itu “cara menambahkan watermark” dalam konteks diagram?
Menambahkan watermark berarti menyisipkan penanda yang terlihat atau tidak terlihat—teks, logo, atau gambar—ke dalam file diagram. Penanda ini menyertai file, memudahkan pembuktian kepemilikan atau menandai versi draft.

## Mengapa menggunakan GroupDocs.Watermark untuk Java?
* **Rich API** – Cari, tambahkan, dan hapus watermark teks maupun gambar dengan beberapa baris kode.  
* **Dukungan lintas format** – Berfungsi dengan Visio (`.vsdx`, `.vdx`) dan banyak tipe diagram lainnya.  
* **Berfokus pada performa** – Memuat hanya bagian diagram yang diperlukan untuk operasi watermark, sehingga penggunaan memori tetap rendah.

## Prasyarat
1. **Java Development Kit (JDK) 8+** – Pastikan `java -version` menampilkan 1.8 atau lebih baru.  
2. **IDE** – IntelliJ IDEA, Eclipse, atau editor lain yang Anda sukai.  
3. **GroupDocs.Watermark untuk Java** – Tambahkan ke proyek Anda melalui Maven atau unduhan JAR langsung.  

### Pustaka dan Dependensi yang Diperlukan
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

*Jika Anda lebih memilih tidak menggunakan Maven, Anda dapat mengunduh JAR terbaru dari [rilis GroupDocs.Watermark untuk Java](https://releases.groupdocs.com/watermark/java/).*  

### Akuisisi Lisensi
- **Trial Gratis:** Uji semua fitur tanpa kunci lisensi.  
- **Lisensi Sementara:** Minta kunci berjangka waktu untuk evaluasi.  
- **Lisensi Penuh:** Beli langganan untuk penggunaan produksi tanpa batas.

## Menyiapkan GroupDocs.Watermark untuk Java
1. **Tambahkan pustaka** ke proyek Anda (Maven atau JAR manual).  
2. **Buat instance `Watermarker`** – objek ini menjadi titik masuk untuk memuat diagram, mencari, menambah, dan menghapus watermark.

## Panduan Implementasi

### Memuat Dokumen Diagram
Memuat adalah langkah pertama sebelum Anda dapat **menambahkan watermark** atau **menghapus watermark**. Kode di bawah ini menunjukkan cara membuka file `.vsdx` dengan opsi pemuatan khusus.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Mencari Watermark Teks
Sebelum menambahkan watermark baru, Anda mungkin ingin memverifikasi apakah watermark teks sudah ada. Cuplikan ini mencari frasa “Company Name”.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Mencari Watermark Gambar
Jika Anda perlu menemukan logo atau gambar apa pun yang digunakan sebagai watermark, gunakan `ImageDctHashSearchCriteria`. Ini berguna ketika Anda ingin **menghapus watermark** yang cocok dengan logo yang dikenal.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Menghapus Watermark
Setelah Anda mengidentifikasi watermark—teks, gambar, atau keduanya—Anda dapat menghapusnya dari diagram. Contoh di bawah ini memperlihatkan operasi penghapusan gabungan.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Aplikasi Praktis
1. **Integrasi Perangkat Lunak Enterprise** – Sematkan manajemen watermark ke dalam ERP atau platform pembuatan dokumen Anda untuk menegakkan branding.  
2. **Sistem Manajemen Konten (CMS)** – Secara otomatis pindai diagram yang diunggah untuk logo tidak sah dan hapus secara otomatis.  
3. **Penanganan Dokumen Hukum** – Tambahkan watermark teks “Confidential” selama fase draft dan kemudian **menghapus watermark** sebelum pengarsipan final.

## Masalah Umum dan Solusinya
| Gejala | Penyebab Kemungkinan | Solusi |
|---------|----------------------|--------|
| Tidak ada watermark yang ditemukan | Teks/gambar pencarian tidak cocok persis | Gunakan `or()` untuk menggabungkan kriteria atau sesuaikan pengaturan sensitivitas huruf. |
| `OutOfMemoryError` pada file besar | Diagram dimuat seluruhnya ke memori | Gunakan `DiagramLoadOptions.setLoadPages()` untuk memuat hanya halaman yang diperlukan. |
| File yang disimpan rusak | `watermarker.save()` dipanggil sebelum semua watermark dibersihkan | Pastikan `possibleWatermarks.clear()` selesai dan `watermarker.close()` dipanggil setelah penyimpanan. |

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya mencari teks dan gambar secara bersamaan?**  
J: Ya. Gabungkan `TextSearchCriteria` dan `ImageDctHashSearchCriteria` dengan metode `or()`, seperti yang ditunjukkan pada contoh penghapusan.

**T: Apakah memungkinkan menghapus watermark tanpa merusak diagram?**  
J: Tentu. Pustaka mengisolasi objek watermark, sehingga pemanggilan `clear()` hanya menghapus lapisan watermark sementara konten diagram asli tetap utuh.

**T: Apakah GroupDocs.Watermark mendukung banyak format diagram?**  
J: Ya. Format seperti `.vsdx`, `.vdx`, dan file kompatibel Visio lainnya didukung sepenuhnya.

**T: Bagaimana cara menangani volume dokumen yang besar secara efisien?**  
J: Implementasikan loop pemrosesan batch, gunakan kembali satu instance `Watermarker` bila memungkinkan, dan batasi pemuatan halaman dengan `DiagramLoadOptions`.

**T: Apakah ada cara mengotomatisasi deteksi watermark dalam pipeline CI/CD?**  
J: Anda dapat menyematkan potongan kode Java yang disediakan ke dalam skrip build Anda (misalnya Maven atau Gradle) untuk memvalidasi tidak adanya watermark tidak sah sebelum merilis artefak.

---

**Terakhir Diperbarui:** 2026-02-18  
**Diuji Dengan:** GroupDocs.Watermark 24.11 untuk Java  
**Penulis:** GroupDocs