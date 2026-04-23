---
date: '2026-02-03'
description: Pelajari cara menampilkan pratinjau dokumen menggunakan GroupDocs.Watermark
  untuk Java – panduan singkat untuk pengembang Java yang meninjau dokumen.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: Cara Pratinjau Dokumen dengan GroupDocs.Watermark untuk Java
type: docs
url: /id/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

#Membuat fungsi **how to preview documents** sangat penting untuk setiap aplikasi yang menangani sejumlah besar file. Dengan seluruh dokumen ke memori aliran halaman, dan menghasilkan gambar pratinjau untuk setiap halaman dokumen.

## Jawaban Cepat
- **Library apa yang direkomendasikan?** GroupDocs.Watermark for Java (v24.11)  
- **Kata kunci utama apa yang ditargetkan tutorial ini?** *how to preview documents*  
- **Apakah saya memerlukan lisensi?** Trial dapat digunakan untuk evaluasi; lisensi penuh diperlukan untuk produksi.  
- **Bisakah saya menyesuaikan format output?** Ya – Anda dapat mengubah ekstakah kode ini thread‑safe?** Instansi Watermarker tidak thread‑safe; buat instansi terpisah per thread.

## Apa ituumen di gambar ringan (biasanya PNG atau JPEG) yang mewakili satu halaman file. Ini memungkinkan pengguna melihat sekilas isi dengan cepat, meningkatkan UX di penjelajah file, platform CMS, dan layanan penyimpanan cloud.

## Mengapa menggunakan GroupDocs.Watermark untuk pembuatan pratinjau?
- **Berfokus pada kinerja**: Menghasilkan gambar halaman tanpa merender dokumen.  
 **Mend**: Bekerja dan banyak lainnya.  
- **Penanganan aliran bawaan**: Menyediakan antarmuka `ICreatePageStream` dan `IReleasePageStream` untuk manajemen sumber daya yang bersih.  

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

1. **GroupDocs.Watermark Java v24.11** – rilis stabil terbaru.  
2. **JDK 8+** terpasang dan IDE seperti IntelliJ IDEA atau Eclipse.  
3. Pengetahuan dasar Java (file I/O, pemrograman berorientasi objek).  

## Menyiapkan GroupDocs.Watermark untuk Java

Tambahkan pustaka ke proyek Anda menggunakan Maven:

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

Atau unduh JAR langsung dari halaman resmi:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### Akuisisi Lisensi

- **Free Trial** – fungsionalitas terbatas, cocok untuk pengujian.  
- **Temporary License** – semua fitur tersedia untuk periode evaluasi singkat.  
- **Full License** – penggunaan tak terbatas dan dukungan prioritas.  

## Panduan Implementasi

### Inisialisasi Watermarker

Langkah pertama adalah membuat instansi `Watermarker` yang menunjuk ke dokumen sumber.

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

> **Tip:** Ganti `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` dengan jalur sebenarnya dari file yang ingin Anda pratinjau.

### Buat Aliran Halaman untuk Pembuatan Pratinjau

Implementasikan `ICreatePageStream` untuk memberi tahu pustaka di mana dan bagaimana menyimpan setiap gambar halaman.

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

*`page%s.png`* adalah pola **page stream java** yang secara otomatis memberi nama setiap file pratinjau (mis., `page1.png`, `page2.png`).

### Lepaskan Aliran Halaman

Menutup aliran dengan benar mencegah kebocoran memori.

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

### Hasilkan Pratinjau Dokumen

Sekarang gabungkan semuanya dan panggil `generatePreview` dengan **preview options java**.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

- `createPageStream` menangani pembuatan **page stream java** untuk setiap gambar pratinjau.  
- `releasePageStream` memastikan sumber daya dibebaskan setelah setiap halaman ditulis.  

## Aplikasi Praktis

- **PDF Viewer Apps** – menampilkan pratinjau thumbnail sebelum membuka file lengkap.  
- **Content Management Systems** – memungkinkan editor menelusuri isi dokumen dengan cepat.  
- **Cloud Storage Services** – menghasilkan thumbnail secara langsung untukgunaan Memori** al RAMStream` dengan `BufferedOutputStream` jika Anda memproses banyak halaman.  
- **Pemrosesan Batch** – Jalankan pembuatan pratinjau dalam thread paralel, masing‑masing dengan instansi `Watermarker` sendiri.  

## Masalah Umum & Solusi

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **OutOfMemoryError** | Dokumen besar dimuat seluruhnya | Gunakan antarmuka aliran (seperti yang ditunjukkan) untuk memproses halaman per halaman. |
| **ikan bahwa `YOUR_OUTPUT_DIRECTORY` ada dan dapat ditulisi. |
| **Preview images are blank** | Format file tidak didukung | Pastikan tipe dokumen didukung oleh GroupDocs.Watermark (mis., PDF, DOCX, VDX). |

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya menghasilkan pratinjau untuk dokumen yang dilindungi kata sandi?**  
**A:** Ya. Berikan kata sandi ke overload konstruktor `Watermarker` yang menerima gambar PNG adalah default, tetapi Anda dapat mengubah ekstensi file di `FeatureCreatePageStream` menjadi JPEG, BMP, dll.

**Q: Apakah memungkinkan membatasi pratinjau ke halaman tertentu?**  
**A:** Gunakan `PreviewOptions.setPageNumber(int pageNumber)` untuk menghasilkan pratinjau satu halaman.

**Q: Apakah pustaka ini bekerja di Linux/macOS?**  
**A:** Tentu saja. GroupDocs.Watermark bersifat platform‑independen selama runtime Java tersedia.

**Q: Bagaimana cara membersihkan file sementara setelah pemrosesan batch?**  
**A:** Hapus file pratinjau yang dihasilkan secara manual atau implementasikan tugas pembersihan terjadwal.

---

**Terakhir Diperbarui:** 2026-02-03  
**Diuji Dengan:** GroupDocs.Watermark Java 24.11  
**Penulis:** GroupDocs