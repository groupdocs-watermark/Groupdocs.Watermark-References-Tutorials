---
date: '2026-09-26'
description: Tìm hiểu cách chuyển đổi tài liệu sang hình ảnh và Java tạo thumbnail
  bằng GroupDocs.Watermark. Hướng dẫn từng bước bao gồm cài đặt, luồng preview và
  mẹo hiệu năng.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Tìm hiểu cách chuyển đổi tài liệu sang hình ảnh và Java tạo thumbnail
  bằng GroupDocs.Watermark. Hướng dẫn này sẽ đưa bạn qua quá trình cài đặt, xử lý
  luồng và tối ưu hiệu năng để tạo preview nhanh chóng.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Chuyển đổi tài liệu sang hình ảnh với GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Chuyển đổi tài liệu sang hình ảnh với GroupDocs.Watermark Java
type: docs
url: /vi/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Chuyển đổi tài liệu sang hình ảnh với GroupDocs.Watermark Java

Tạo các bản xem trước hình ảnh nhẹ cho các tài liệu đa trang là một yêu cầu phổ biến cho các cổng thông tin, hệ thống quản lý nội dung và dịch vụ lưu trữ đám mây. Bằng cách **convert document to image** bạn cung cấp cho người dùng cuối một dấu hiệu trực quan nhanh chóng mà không cần tải toàn bộ tệp. Thư viện GroupDocs.Watermark Java không chỉ thêm watermarks mà còn cung cấp một engine xem trước hiệu suất cao có thể **java generate thumbnails** cho mỗi trang trong một lần xử lý.

Trong hướng dẫn này bạn sẽ học cách thiết lập thư viện, tạo luồng trang tùy chỉnh, giải phóng tài nguyên một cách an toàn, và cuối cùng tạo các bản xem trước hình ảnh cho mỗi trang của tài liệu nguồn. Các hướng dẫn được viết cho các nhà phát triển quen thuộc với Java và các khái niệm hướng đối tượng, và chúng bao gồm các mẹo thực tiễn để xử lý các lô tệp lớn.

## Câu trả lời nhanh
- **Bước đầu tiên là gì?** Thêm phụ thuộc Maven của GroupDocs.Watermark và khởi tạo một `Watermarker` với đường dẫn tệp nguồn.  
- **Các hình ảnh xem trước được tạo như thế nào?** Triển khai `ICreatePageStream` để mở một luồng đầu ra cho mỗi trang, sau đó gọi `generatePreview()` với các tùy chọn phù hợp.  
- **Tôi có cần giấy phép không?** Bản dùng thử hoạt động cho các kịch bản cơ bản, nhưng giấy phép đầy đủ sẽ loại bỏ watermarks và mở khóa xử lý hàng loạt.  
- **Tôi có thể xử lý PDF lớn hơn 200 trang không?** Có – thư viện stream các trang, vì vậy việc sử dụng bộ nhớ vẫn thấp ngay cả với các tệp 500 trang.  
- **Các định dạng hình ảnh nào được hỗ trợ?** PNG, JPEG, BMP và TIFF có sẵn ngay từ đầu.

## Convert document to image là gì?
Cụm từ **convert document to image** mô tả quá trình render mỗi trang của tệp nguồn (PDF, DOCX, PPTX, v.v.) thành một hình raster như PNG hoặc JPEG. Việc chuyển đổi này hữu ích cho các bộ sưu tập thumbnail, các ô xem trước và các trình xem tài liệu thân thiện với thiết bị di động.

## Tại sao nên sử dụng GroupDocs.Watermark để tạo xem trước?
GroupDocs.Watermark hỗ trợ **hơn 30 định dạng đầu vào** và có thể tạo xem trước cho tài liệu lên tới **500 trang** mà không cần tải toàn bộ tệp vào bộ nhớ. Nội bộ, nó xử lý các trang một cách tuần tự, giúp việc sử dụng heap Java dưới 50 MB ngay cả với các PDF lớn. Thư viện còn cung cấp tối ưu hoá hình ảnh tích hợp, cho phép bạn chỉ định DPI, độ sâu màu và mức nén, kết quả là các thumbnail thường **nhỏ hơn 70 %** so với việc raster hoá thông thường.

## Yêu cầu trước

- **Java Development Kit (JDK) 11 hoặc mới hơn** – thư viện được biên dịch cho Java 8+, nhưng JDK 11 cung cấp hỗ trợ lâu dài và hiệu năng tốt hơn.  
- **Maven 3.6+** – để quản lý phụ thuộc.  
- **GroupDocs.Watermark for Java phiên bản 24.11** – bản phát hành ổn định mới nhất tại thời điểm viết.  
- **Kiến thức cơ bản về Java I/O streams** – bạn sẽ tạo các đối tượng `FileOutputStream` cho mỗi trang xem trước.  
- **Khóa giấy phép** (tùy chọn cho môi trường production) – bản dùng thử giới hạn kích thước xem trước tối đa 5 MB cho mỗi tài liệu.

## Cách thiết lập GroupDocs.Watermark cho Java

Để thiết lập GroupDocs.Watermark, đầu tiên thêm kho Maven và sau đó bao gồm thư viện như một phụ thuộc trong `pom.xml` của dự án. Điều này đảm bảo Maven có thể tải xuống các artifact đúng và làm cho các lớp có sẵn trên classpath để biên dịch và chạy.

### Thêm phụ thuộc Maven
Thư viện được phân phối qua Maven Central. Thêm đoạn mã sau vào `pom.xml` trong khối `<dependencies>`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Mẹo chuyên nghiệp:** Giữ số phiên bản trong một thuộc tính (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) để bạn có thể nâng cấp dễ dàng.

### Tải trực tiếp (thay thế)
Nếu bạn muốn cài đặt thủ công, bạn có thể tải JAR từ trang phát hành chính thức: [GroupDocs.Watermark cho Java - các bản phát hành](https://releases.groupdocs.com/watermark/java/).

## Cách lấy và áp dụng giấy phép

Áp dụng giấy phép cho GroupDocs.Watermark loại bỏ các giới hạn của bản dùng thử và tắt overlay watermarks mặc định. Đặt tệp giấy phép ở vị trí đã biết và chỉ định API tới nó, hoặc nhúng đường dẫn giấy phép trực tiếp trong mã trước bất kỳ lời gọi nào khác. Khi đã tải, tất cả các thao tác tiếp theo sẽ chạy ở chế độ đầy đủ tính năng.

Bạn có thể:

- **Yêu cầu bản dùng thử miễn phí** từ cổng GroupDocs – nó cung cấp một tệp giấy phép 30 ngày.  
- **Tạo giấy phép tạm thời** qua công cụ tạo giấy phép trực tuyến cho môi trường đánh giá.  
- **Mua giấy phép thương mại** để sử dụng không giới hạn trong sản xuất và nhận hỗ trợ ưu tiên.

Đặt tệp giấy phép (`GroupDocs.Watermark.lic`) trong thư mục gốc của dự án hoặc chỉ định đường dẫn bằng cách lập trình với `Watermarker.setLicense("path/to/license.file")`.

## Cách khởi tạo Watermarker

Khởi tạo `Watermarker` bằng cách cung cấp đường dẫn tới tài liệu nguồn, tùy chọn kèm mật khẩu cho các tệp được bảo vệ. Constructor sẽ xác thực định dạng và chuẩn bị các parser nội bộ, cho phép bạn ngay lập tức gọi các phương thức xem trước hoặc chèn watermark. Sau khi tạo, giữ một tham chiếu để tái sử dụng đối tượng cho nhiều thao tác nếu cần.

Lớp `Watermarker` là đối tượng cốt lõi của GroupDocs.Watermark, chịu trách nhiệm tải tài liệu và cung cấp các thao tác như chèn watermark và tạo xem trước.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – đường dẫn tuyệt đối hoặc tương đối tới tệp nguồn.  
- Constructor xác thực định dạng tệp và chuẩn bị các parser nội bộ.

> **Định nghĩa:** `Watermarker` là điểm vào cho tất cả các hành động xử lý tài liệu trong GroupDocs.Watermark cho Java.

## Cách tạo luồng trang cho việc tạo xem trước

Tạo các luồng trang tùy chỉnh bằng cách triển khai giao diện `ICreatePageStream`, mà thư viện sẽ gọi cho mỗi trang nó render. Việc triển khai của bạn nên tạo một `OutputStream` mới — thường là `FileOutputStream` — trỏ tới một tệp có tên duy nhất dựa trên số trang. Cách tiếp cận này tách biệt đầu ra của mỗi trang và ngăn chặn dữ liệu chồng lấn.

Để **java generate thumbnails**, bạn phải cung cấp một luồng cho mỗi trang nơi hình ảnh render sẽ được ghi. Triển khai giao diện `ICreatePageStream`; thư viện sẽ gọi triển khai của bạn cho mọi trang nó xử lý.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** cho phép bạn nhúng số trang trực tiếp vào tên tệp, giúp việc xử lý hàng loạt trở nên đơn giản.  
- Phương thức trả về một `OutputStream` mới cho mỗi trang, đảm bảo các trang trước không can thiệp vào các lần ghi sau.

> **Định nghĩa:** `ICreatePageStream` là một giao diện callback cho phép bạn định nghĩa cách tạo luồng đầu ra cho mỗi trang xem trước.

## Cách giải phóng luồng trang sau khi tạo xem trước

Sau khi hình ảnh trang đã được ghi, thư viện gọi `IReleasePageStream` để bạn đóng và dọn dẹp luồng đầu ra liên quan. Triển khai callback này để an toàn giải phóng các handle tệp, flush bộ đệm, và thực hiện bất kỳ ghi log bổ sung nào. Việc dọn dẹp đúng cách tránh rò rỉ descriptor và đảm bảo các trang tiếp theo có thể được xử lý mà không bị cản trở.

Việc dọn dẹp tài nguyên đúng cách ngăn rò rỉ handle tệp và giữ JVM không bị cạn descriptor. Triển khai `IReleasePageStream` để đóng luồng khi thư viện thông báo trang đã hoàn thành.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Định nghĩa:** `IReleasePageStream` là một giao diện callback cho phép bạn định nghĩa logic tùy chỉnh để giải phóng các tài nguyên đầu ra riêng cho mỗi trang.

## Cách tạo xem trước tài liệu (convert document to image)

Tạo xem trước bằng cách gọi `generatePreview()` trên đối tượng `Watermarker`, cung cấp một đối tượng `PreviewOptions` xác định độ phân giải, định dạng hình ảnh và phạm vi trang. Phương thức sẽ lặp qua từng trang, sử dụng các trình tạo luồng của bạn để ghi hình raster, và sau đó giải phóng các luồng. Quá trình này tạo ra một tập hợp các tệp hình ảnh đại diện cho các trang của tài liệu.

Với `Watermarker`, `FeatureCreatePageStream` và `FeatureReleasePageStream` đã sẵn sàng, bạn có thể khởi chạy engine xem trước. Phương thức `generatePreview()` lặp qua mỗi trang, gọi các trình tạo luồng của bạn, ghi hình ảnh và cuối cùng giải phóng các luồng.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** kiểm soát DPI; 150 DPI là mức cân bằng tốt cho các thumbnail web.  
- **`ImageFormat`** có thể là PNG, JPEG, BMP hoặc TIFF tùy theo yêu cầu downstream của bạn.  
- Phương thức xử lý các trang một cách tuần tự, vì vậy việc tiêu thụ bộ nhớ vẫn thấp ngay cả với các tài liệu có hàng trăm trang.

> **Định nghĩa:** `generatePreview()` là lời gọi API render mỗi trang của tài liệu đã tải thành hình ảnh bằng các luồng bạn cung cấp.

## Ứng dụng thực tế của convert document to image

Tạo các bản xem trước hình ảnh mở ra nhiều khả năng:

1. **Trình duyệt tài liệu** – Hiển thị lưới thumbnail PNG để người dùng có thể lướt nhanh các PDF lớn mà không cần mở chúng.  
2. **Đoạn trích kết quả tìm kiếm** – Gắn một hình ảnh xem trước vào các mục chỉ mục tìm kiếm để giao diện phong phú hơn.  
3. **Đính kèm email** – Nhúng một preview nhỏ của PDF đính kèm trong nội dung email.  
4. **Ứng dụng di động** – Giảm băng thông bằng cách gửi preview PNG 200 KB thay vì PDF đầy đủ.  
5. **Cổng tuân thủ** – Render các phiên bản có watermark pháp lý của hợp đồng dưới dạng hình ảnh cho các bản ghi audit.

## Các cân nhắc về hiệu năng khi bạn java generate thumbnails

Khi xử lý hàng loạt, hãy nhớ các mẹo tối ưu sau:

- **Buffer luồng** – Bao bọc `FileOutputStream` trong `BufferedOutputStream` để giảm thiểu I/O đĩa.  
- **Thực thi batch song song** – Sử dụng `ForkJoinPool` của Java để xử lý nhiều tài liệu đồng thời; mỗi tác vụ nên tạo một thể hiện `Watermarker` riêng để tránh vấn đề thread‑safety.  
- **Giới hạn DPI cho thumbnail** – 72–150 DPI là đủ cho hầu hết các kịch bản UI; DPI cao hơn nên dành cho preview chuẩn in.  
- **Tái sử dụng đối tượng licence** – Tải tệp licence một lần cho mỗi JVM sẽ giảm overhead.  
- **Giám sát bộ nhớ** – Thư viện chỉ giữ trang hiện tại trong bộ nhớ. Đối với các tệp cực lớn, cân nhắc tăng heap JVM một cách vừa phải (ví dụ, `-Xmx512m`) để đáp ứng các đỉnh tải ngẫu nhiên.

## Những lỗi thường gặp và cách tránh

| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|-------------|---------------------|----------------|
| `OutOfMemoryError` khi tạo xem trước | Sử dụng `ImageFormat.Jpeg` với 300 DPI trên PDF 1000 trang | Giảm DPI hoặc chuyển sang PNG với độ sâu màu thấp hơn |
| Các tệp xem trước rỗng | `FeatureCreatePageStream` trả về cùng một `FileOutputStream` cho mọi trang | Đảm bảo tạo luồng mới cho mỗi `pageNumber` |
| Hình ảnh xem trước bị xoay | PDF nguồn chứa siêu dữ liệu xoay nhưng không được tôn trọng | Gọi `previewOptions.setRotatePages(true)` (nếu có) |
| Cảnh báo giấy phép xuất hiện | Không tìm thấy tệp giấy phép hoặc đường dẫn không đúng | Xác minh `Watermarker.setLicense("path/to/license.file")` được thực thi trước bất kỳ lời gọi API nào khác |

## Câu hỏi thường gặp

**Q: Tôi có thể tạo preview cho các PDF được bảo mật bằng mật khẩu không?**  
A: Có. Chỉ cần truyền mật khẩu vào constructor của `Watermarker`: `new Watermarker("file.pdf", "password")`.

**Q: Các định dạng hình ảnh nào được hỗ trợ cho đầu ra preview?**  
A: PNG, JPEG, BMP và TIFF đều có sẵn. PNG được khuyến nghị cho các thumbnail không mất dữ liệu.

**Q: Có thể xử lý bao nhiêu trang trong một lần gọi?**  
A: Thư viện không đặt giới hạn cứng; bạn có thể preview các tài liệu có hàng ngàn trang, chỉ bị giới hạn bởi không gian lưu trữ và băng thông I/O.

**Q: Tôi có cần một giấy phép riêng cho mỗi instance server không?**  
A: Một tệp giấy phép duy nhất có thể được tái sử dụng trên nhiều instance miễn là tổng mức sử dụng tuân thủ các điều khoản giấy phép.

**Q: Có cách nào để tạo một thumbnail kết hợp duy nhất (ví dụ chỉ trang đầu tiên) không?**  
A: Có. Đặt `previewOptions.setPages(new int[]{1})` để giới hạn việc tạo chỉ trang đầu tiên.

## Kết luận

Bạn đã có một quy trình hoàn chỉnh, sẵn sàng cho sản xuất để **convert document to image** và **java generate thumbnails** bằng GroupDocs.Watermark. Bằng cách cấu hình các handler luồng trang tùy chỉnh, bạn giữ việc sử dụng bộ nhớ ở mức thấp, và bằng cách tinh chỉnh `PreviewOptions` bạn kiểm soát chất lượng hình ảnh và kích thước tệp. Những kỹ thuật này cho phép bạn nhúng các preview nhanh, chất lượng cao vào bất kỳ ứng dụng Java nào — dù là cổng web, client desktop, hay microservice cloud‑native.

**Cập nhật lần cuối:** 2026-09-26  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs

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

## Các hướng dẫn liên quan

- [Cách lấy thông tin tài liệu bằng GroupDocs.Watermark cho Java: Hướng dẫn từng bước](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Các hướng dẫn tính năng Watermark nâng cao cho GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Cách thêm Watermark hình ảnh trong Java bằng GroupDocs.Watermark: Hướng dẫn từng bước](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)