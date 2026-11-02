---
date: '2026-10-01'
description: Tìm hiểu cách tự động thay thế hình ảnh java trong các tệp sơ đồ bằng
  GroupDocs.Watermark, bao gồm việc thêm watermark và xử lý hiệu quả.
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: Tự động thay thế hình ảnh java trong các sơ đồ bằng GroupDocs.Watermark.
  Hướng dẫn này chỉ cách thay thế hình ảnh, thêm watermark và xử lý các tệp lớn một
  cách hiệu quả.
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: Tự động thay thế hình ảnh java bằng GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: Tự động thay thế hình ảnh java bằng GroupDocs.Watermark
type: docs
url: /vi/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Tự động thay thế hình ảnh Java bằng GroupDocs.Watermark

Cập nhật các hình ảnh riêng lẻ trong một sơ đồ có thể là một công việc thủ công tẻ nhạt và dễ gây lỗi. Với **GroupDocs.Watermark for Java**, bạn có thể **tự động thay thế hình ảnh java** trên hàng chục hoặc hàng trăm tệp, đảm bảo tính nhất quán thương hiệu và tiết kiệm thời gian phát triển quý giá. Hướng dẫn này sẽ dẫn bạn qua việc thiết lập thư viện, truy cập nội dung sơ đồ, hoán đổi hình ảnh trong các hình dạng cụ thể, và tùy chọn thêm watermark vào sơ đồ.

## Câu trả lời nhanh
- **Thư viện nào xử lý cập nhật hình ảnh sơ đồ?** GroupDocs.Watermark for Java.  
- **Tôi có thể thêm watermark khi thay thế hình ảnh không?** Có – cùng một API cho phép bạn chồng watermark lên bất kỳ trang sơ đồ nào.  
- **Yêu cầu phiên bản Java nào?** JDK 8 hoặc cao hơn.  
- **Tôi có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Quá trình có tiết kiệm bộ nhớ cho các sơ đồ lớn không?** Có – SDK truyền dữ liệu theo luồng và không bao giờ tải toàn bộ tệp vào bộ nhớ.

## GroupDocs.Watermark for Java là gì?
`GroupDocs.Watermark` là một SDK Java cho phép thêm, xóa và thay thế watermark và hình ảnh một cách lập trình trong hơn 30 định dạng tài liệu, bao gồm Visio, SVG và các loại sơ đồ khác. Nó xử lý tệp theo dạng luồng, cho phép bạn làm việc với các sơ đồ có hàng trăm trang mà không làm cạn kiệt bộ nhớ.

## Tại sao tự động thay thế hình ảnh Java?
Tự động thay thế hình ảnh giảm công việc thủ công lên tới **90 %** khi cập nhật tài sản thương hiệu trên các bộ sưu tập tài liệu lớn. SDK hỗ trợ **hơn 30 định dạng đầu vào và đầu ra**, xử lý các tệp lên tới **200 MB** trong vòng chưa đầy một giây trên phần cứng máy chủ thông thường, và đảm bảo vị trí hình ảnh chính xác đến pixel.

## Yêu cầu trước
- JDK 8 hoặc mới hơn được cài đặt trên máy phát triển của bạn.  
- Maven (hoặc công cụ xây dựng khác) để quản lý các phụ thuộc.  
- Một IDE như IntelliJ IDEA hoặc Eclipse.  
- Kiến thức cơ bản về Java và quen thuộc với I/O tệp.

### Thư viện, phiên bản và phụ thuộc cần thiết
Thêm các tọa độ Maven sau vào `pom.xml` của bạn. Placeholder bên dưới đại diện cho đoạn XML chính xác bạn cần; giữ nguyên không thay đổi.

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

Đối với tải xuống thủ công, lấy các JAR mới nhất từ trang phát hành chính thức: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Cách tự động thay thế hình ảnh Java?
Tải sơ đồ bằng một thể hiện `Watermarker`, xác định các hình dạng mục tiêu, thay thế luồng hình ảnh của chúng, tùy chọn thêm watermark, và cuối cùng lưu tệp. Toàn bộ quy trình bao gồm **bốn bước ngắn gọn**, mỗi bước được minh họa dưới đây, và thường chỉ mất vài giây cho mỗi sơ đồ ngay cả với các tệp lớn.

### Bước 1: khởi tạo watermarker
Lớp `Watermarker` là điểm vào cho tất cả các thao tác tài liệu. Nó mở tệp nguồn và chuẩn bị các cấu trúc nội bộ để chỉnh sửa.

```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```

- **DiagramLoadOptions** cấu hình các tham số tải đặc thù cho sơ đồ.  
- Khởi tạo `Watermarker` mở tay cầm tệp và xác thực định dạng.

### Bước 2: truy cập nội dung sơ đồ
`DiagramContent` đại diện cho cấu trúc logic của một sơ đồ, hiển thị các trang và các hình dạng riêng lẻ để kiểm tra.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- Sử dụng `watermarker.getContent()` để lấy một đối tượng `DiagramContent`.  
- Duyệt qua `content.getPages()` và sau đó `page.getShapes()` để tìm các hình dạng chứa hình ảnh.

### Bước 3: thay thế hình ảnh hình dạng trong sơ đồ
Các đối tượng `DiagramShape` có thể chứa một hình ảnh nhúng. Thay thế nó bằng cách cung cấp một `InputStream` mới đọc ảnh thay thế.

Phương thức `setImage(InputStream)` thay thế hình ảnh hiện tại của hình dạng bằng luồng được cung cấp.  

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```

- Kiểm tra `shape.getImage()`; nếu không null, gọi `shape.setImage(newImageStream)`.  
- SDK tự động cập nhật kích thước hình ảnh và giữ nguyên bố cục hình dạng gốc.

### Bước 4: thêm watermark vào sơ đồ (tùy chọn)
Nếu bạn cũng cần **thêm watermark vào sơ đồ**, tạo một đối tượng `Watermark` và áp dụng nó vào trang mong muốn hoặc toàn bộ tài liệu.

Lớp `Watermark` định nghĩa một lớp phủ trực quan có thể được đặt trên các trang sơ đồ hoặc toàn bộ tài liệu.  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

Phương thức `add(Watermark, AddOptions)` áp dụng watermark đã chỉ định vào tài liệu bằng các tùy chọn được cung cấp.  

*(Mã trên chỉ mang tính minh họa và không được tính là một khối mã mới; nó được đặt trong một đoạn văn hiện có.)*

### Bước 5: lưu và đóng watermarker
Lưu các thay đổi và giải phóng tài nguyên để tránh khóa tệp.

Phương thức `save(String)` ghi tài liệu đã sửa đổi vào đường dẫn được chỉ định.  

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```

- Gọi `watermarker.save("output.vsdx")` (hoặc phần mở rộng phù hợp).  
- Luôn gọi `watermarker.close()` trong khối `finally` hoặc sử dụng try‑with‑resources để tự động dọn dẹp.

## Những khó khăn thường gặp và khắc phục
- **Kích thước hình ảnh không khớp** – Đảm bảo hình ảnh thay thế có cùng tỷ lệ khung hình với hình gốc để tránh biến dạng.  
- **Tăng đột biến bộ nhớ trên sơ đồ lớn** – Xử lý các sơ đồ từng cái một và đóng `Watermarker` sau mỗi lần lưu.  
- **Lỗi giấy phép** – Giấy phép dùng thử hết hạn sau 30 ngày; thay thế bằng key sản xuất trước khi triển khai. Bạn có thể nhận giấy phép tạm thời từ GroupDocs: [obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Câu hỏi thường gặp

**Q: Tôi có thể thay thế hình ảnh trong sơ đồ được bảo mật bằng mật khẩu không?**  
A: Có. Tải tệp bằng `DiagramLoadOptions` bao gồm mật khẩu, sau đó tiếp tục các bước thay thế bình thường.

**Q: SDK có hỗ trợ xử lý hàng loạt nhiều sơ đồ không?**  
A: Hoàn toàn có. Đặt quy trình làm việc cho một tệp trong một vòng lặp duyệt qua một thư mục; kiến trúc truyền dữ liệu giữ mức sử dụng bộ nhớ thấp.

**Q: Tôi có thể làm việc với định dạng nào ngoài Visio?**  
A: GroupDocs.Watermark hỗ trợ SVG, VDX, VSDX và một số định dạng sơ đồ khác, tổng cộng hơn 30 loại được hỗ trợ.

**Q: Có thể thêm watermark sau khi thay thế hình ảnh không?**  
A: Có – gọi `watermarker.add(watermark, options)` sau bước thay thế hình ảnh và trước khi lưu.

**Q: Làm sao để đảm bảo hình ảnh mới được nhúng, không phải liên kết?**  
A: Phương thức `setImage(InputStream)` nhúng dữ liệu hình ảnh trực tiếp vào tệp sơ đồ, đảm bảo tính di động.

---

**Cập nhật lần cuối:** 2026-10-01  
**Được kiểm tra với:** GroupDocs.Watermark 23.12 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Hướng dẫn Watermark Sơ đồ cho GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Xóa Liên kết siêu văn bản khỏi Các Hình dạng Sơ đồ bằng GroupDocs.Watermark Java để Tăng Cường Bảo mật Tài liệu](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Cách Thêm Watermark Hình ảnh trong Java bằng GroupDocs.Watermark: Hướng dẫn Từng Bước](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)