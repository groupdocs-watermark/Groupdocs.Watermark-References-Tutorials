---
date: '2025-12-19'
description: Pelajari cara menggunakan GroupDocs Watermark Maven untuk mengelola watermark
  pada file diagram seperti .vsdx dengan Java, meningkatkan integritas dokumen dan
  melindungi hak kekayaan intelektual.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – Kelola Watermark Diagram dengan Java
type: docs
url: /id/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – Kelola Watermark Diagram dengan Java

Mengelola watermark dalam dokumen penting untuk melindungi hak kekayaan intelektual dan menjaga integritas dokumen. **Dalam tutorial ini kami akan menunjukkan cara menggunakan groupdocs watermark maven untuk memuat, mencari, dan menghapus watermark secara efisien dari file diagram seperti `.vsdx`**. Baik Anda membangun perangkat lunak perusahaan atau mengotomatisasi alur kerja dokumen, menguasai teknik ini akan memberi Anda kontrol penuh atas manajemen watermark diagram.

## Jawaban Cepat
- **Library apa yang dibutuhkan?** GroupDocs.Watermark for Java (tersedia via Maven).  
- **Format diagram apa yang didukung?** `.vsdx`, `.vdx`, dan format Visio lainnya.  
- **Bisakah saya mencari watermark teks dan gambar sekaligus?** Ya – gabungkan kriteria pencarian dengan `or()`.  
- **Apakah lisensi diperlukan untuk produksi?** Lisensi GroupDocs.Watermark yang valid diperlukan.  
- **Bagaimana cara mengintegrasikannya ke Maven?** Tambahkan repositori dan dependensi yang ditunjukkan di bawah.

## Apa itu groupdocs watermark maven?
`groupdocs watermark maven` mengacu pada integrasi berbasis Maven dari pustaka GroupDocs.Watermark untuk Java. Dengan mendeklarasikan pustaka di `pom.xml` Anda, Maven secara otomatis menyelesaikan semua binari yang diperlukan, memungkinkan Anda fokus pada kode yang memuat diagram, mencari watermark, dan menghapusnya secara programatis.

## Mengapa menggunakan GroupDocs.Watermark untuk manajemen watermark diagram?
- **API lengkap** – mendukung watermark teks, gambar, dan bentuk pada banyak tipe diagram.  
- **Penghapusan presisi** – menghilangkan watermark tanpa merusak tata letak diagram asli.  
- **Skalabel** – cocok untuk pemrosesan batch koleksi diagram yang besar.  
- **Maven friendly** – manajemen dependensi yang sederhana, menjaga proyek Anda tetap bersih.

## Prasyarat
1. **Java Development Kit (JDK) 8+** – memastikan kompatibilitas dengan pustaka.  
2. **IDE** – IntelliJ IDEA, Eclipse, atau editor kompatibel Java apa pun.  
3. **GroupDocs.Watermark for Java** – ditambahkan via Maven (direkomendasikan) atau unduhan JAR langsung.  

### Pustaka dan Dependensi yang Diperlukan
#### Pengaturan Maven
Add the following configuration to your `pom.xml` file:

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
Alternatively, download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Akuisisi Lisensi
- **Free Trial:** Uji pustaka dengan lisensi percobaan.  
- **Temporary License:** Minta kunci jangka pendek untuk evaluasi.  
- **Purchase:** Dapatkan lisensi produksi untuk penggunaan tak terbatas.

## Menggunakan groupdocs watermark maven untuk Memuat Dokumen Diagram
Memuat dokumen diagram adalah langkah pertama sebelum operasi watermark apa pun. Di bawah ini contoh minimal yang membuat instance `Watermarker` dengan `DiagramLoadOptions`.

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

- **Parameter:**  
  - `inputFilePath` – path ke file `.vsdx` Anda.  
  - `loadOptions` – memungkinkan Anda mengontrol bagaimana diagram diparsing (misalnya, proteksi password).

## Mencari Watermark dengan groupdocs watermark maven
### Watermark Teks
To locate text‑based watermarks, define a `TextSearchCriteria` and query the first page of the diagram.

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

- **Metode Kunci:**  
  - `TextSearchCriteria` – menentukan teks tepat yang dicari.  
  - `PossibleWatermarkCollection` – menyimpan semua kecocokan yang ditemukan.

### Watermark Gambar
If your diagram contains logo or picture watermarks, use `ImageDctHashSearchCriteria` to compare against a reference image.

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

- **Metode Kunci:**  
  - `ImageDctHashSearchCriteria` – membuat hash perseptual dari gambar referensi untuk pencocokan yang kuat.

## Menghapus Watermark
Once you’ve identified unwanted watermarks, you can clear them and save a clean copy of the diagram.

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

- **Metode Kunci:** `clear()` menghapus semua watermark yang ditemukan oleh kriteria gabungan, meninggalkan diagram tetap utuh.

## Aplikasi Praktis
1. **Integrasi Perangkat Lunak Perusahaan** – Menyematkan manajemen watermark ke dalam aplikasi bisnis untuk melindungi diagram kepemilikan.  
2. **Sistem Manajemen Konten (CMS)** – Mengotomatiskan deteksi dan penghapusan logo tidak sah sebelum dipublikasikan.  
3. **Alur Kerja Dokumen Hukum** – Menambahkan atau menghapus watermark pada berbagai tahap proses kontrak.  

## Masalah Umum & Pemecahan Masalah
- **Kesalahan lisensi:** Pastikan file lisensi direferensikan dengan benar sebelum membuat `Watermarker`.  
- **File besar:** Gunakan API streaming atau tingkatkan ukuran heap JVM (`-Xmx2g`) untuk diagram > 100 MB.  
- **Watermark tidak ditemukan:** Verifikasi bahwa kriteria pencarian (case teks, ambang kesamaan gambar) cocok dengan konten watermark sebenarnya.

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya mencari teks dan gambar secara bersamaan?**  
A: Ya. Gabungkan kriteria dengan `or()` seperti yang ditunjukkan pada contoh penghapusan.

**Q: Apakah aman menghapus watermark tanpa mengubah tata letak diagram?**  
A: Tentu saja. API secara tepat menargetkan objek watermark, menjaga semua elemen diagram lainnya.

**Q: Format diagram apa yang didukung oleh GroupDocs.Watermark?**  
A: Mendukung format Visio seperti `.vsdx`, `.vdx`, serta tipe diagram vektor lainnya.

**Q: Bagaimana saya dapat memproses ratusan diagram secara efisien?**  
A: Implementasikan loop batch, gunakan kembali satu instance `Watermarker` bila memungkinkan, dan pertimbangkan pemrosesan paralel dengan `ExecutorService` Java.

**Q: Bisakah saya mengintegrasikan deteksi watermark ke dalam pipeline CI/CD?**  
A: Ya. Sertakan potongan kode Java dalam skrip build Anda (mis., plugin Maven atau tugas Gradle) untuk memvalidasi diagram sebelum deployment.

## Kesimpulan
Dengan memanfaatkan **groupdocs watermark maven**, Anda mendapatkan cara yang kuat dan dikelola Maven untuk memuat, mencari, dan menghapus watermark dari file diagram menggunakan Java. Kemampuan ini memperkuat keamanan dokumen, menyederhanakan alur kerja konten, dan dapat diskalakan dengan mudah pada koleksi dokumen yang besar.

---

**Terakhir Diperbarui:** 2025-12-19  
**Diuji Dengan:** GroupDocs.Watermark 24.11 for Java  
**Penulis:** GroupDocs