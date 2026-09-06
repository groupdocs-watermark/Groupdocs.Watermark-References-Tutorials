---
date: '2026-09-06'
description: Tìm hiểu cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark
  cho Java, cho phép tự động hoá và phân tích tài liệu mạnh mẽ.
keywords:
- how to extract shapes
- GroupDocs.Watermark Java
- Word document shape extraction
lastmod: '2026-09-06'
og_description: Cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark
  cho Java. Hãy làm theo hướng dẫn từng bước này để tải, phân tích và xử lý các hình
  dạng một cách hiệu quả.
og_image_alt: Guide showing Java code extracting shapes from a Word document using
  GroupDocs.Watermark
og_title: Cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark
  trong Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract shapes from Word documents with GroupDocs.Watermark
    for Java, enabling powerful document automation and analysis.
  headline: How to extract shapes from Word documents using GroupDocs.Watermark in
    Java
  type: TechArticle
- questions:
  - answer: GroupDocs.Watermark for Java is a comprehensive SDK that enables watermark
      creation, detection, and document inspection across 30+ file formats, including
      DOCX, PDF, and PPTX.
    question: What is GroupDocs.Watermark for Java?
  - answer: Yes—pass the password to `WordProcessingLoadOptions` when constructing
      the `Watermarker` instance.
    question: Can I extract shapes from password‑protected Word files?
  - answer: Absolutely; GroupDocs.Watermark is platform‑agnostic and runs on any OS
      that supports Java 8+.
    question: Does the library work on Linux servers?
  - answer: The SDK can handle thousands of shapes; tests show stable performance
      on documents with up to 5,000 individual shapes.
    question: How many shapes can be processed in a single document?
  - answer: No, shape extraction is included in the standard GroupDocs.Watermark license.
    question: Is a separate license needed for shape extraction?
  type: FAQPage
tags:
- extract shapes
- GroupDocs.Watermark
- Java document processing
title: Cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark trong
  Java
type: docs
url: /vi/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark trong Java

Trong các ứng dụng hiện đại tập trung vào tài liệu, **cách trích xuất các hình dạng** từ tệp Word là một thách thức phổ biến. Cho dù bạn cần kiểm tra việc sử dụng sơ đồ, chuyển đổi đồ họa thành hình ảnh, hoặc hỗ trợ báo cáo động, khả năng lấy siêu dữ liệu hình dạng một cách lập trình sẽ tiết kiệm vô số giờ làm thủ công. Hướng dẫn này sẽ chỉ cho bạn cách sử dụng GroupDocs.Watermark cho Java để tải một DOCX, liệt kê mọi hình dạng và lấy các thuộc tính của chúng như loại, kích thước và vị trí.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc trích xuất hình dạng?** GroupDocs.Watermark for Java.  
- **Phiên bản Java tối thiểu?** JDK 8 hoặc cao hơn.  
- **Tôi có cần giấy phép cho việc phát triển không?** Một giấy phép dùng thử miễn phí hoạt động cho việc thử nghiệm; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Tôi có thể xử lý tài liệu lớn không?** Có—xử lý các phần một cách tăng dần để giữ mức sử dụng bộ nhớ thấp.  
- **Maven có phải là phương pháp thiết lập ưu tiên không?** Maven đơn giản hoá quản lý phụ thuộc và được khuyến nghị cho hầu hết các dự án.

## Trích xuất hình dạng trong tài liệu Word là gì?
Trích xuất hình dạng là quá trình đọc một tệp Word một cách lập trình và lấy chi tiết về mỗi đối tượng đồ họa—hình ảnh, bản vẽ, SmartArt, biểu đồ hoặc hộp văn bản—để bạn có thể phân tích hoặc thao tác chúng trong mã. Siêu dữ liệu được trích xuất bao gồm loại hình dạng, kích thước, vị trí và bất kỳ văn bản liên quan nào, cho phép xử lý tiếp như chuyển đổi hoặc phân tích.

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?
GroupDocs.Watermark hỗ trợ **hơn 30 định dạng tài liệu** và có thể xử lý **các tệp hàng trăm trang** mà không cần tải toàn bộ tệp vào bộ nhớ, nhờ API streaming của nó. Thư viện xử lý siêu dữ liệu hình dạng trong thời gian dưới **200 ms cho mỗi tài liệu 100 trang** trên một máy chủ tiêu chuẩn, mang lại kết quả nhanh chóng và đáng tin cậy cho các thao tác batch.

## Yêu cầu trước
- **Java Development Kit (JDK)** 8 hoặc cao hơn.  
- **IDE** như IntelliJ IDEA hoặc Eclipse.  
- Kiến thức cơ bản về Java I/O và Maven.  

Chúng ta sẽ sử dụng GroupDocs.Watermark cho Java, một SDK mạnh mẽ tập trung vào việc chèn watermark nhưng cũng cung cấp khả năng kiểm tra tài liệu sâu.

## Cài đặt GroupDocs.Watermark cho Java
Tích hợp SDK qua Maven hoặc tải trực tiếp.

### Sử dụng Maven
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

### Tải trực tiếp
Hoặc tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Nhận giấy phép
Giấy phép dùng thử miễn phí cho phép bạn khám phá tất cả các tính năng. Đối với môi trường sản xuất, hãy lấy khóa giấy phép vĩnh viễn từ cổng thông tin GroupDocs.

## Hướng dẫn triển khai
Chúng ta sẽ chia việc triển khai thành hai phần logic: tải tài liệu và trích xuất thông tin hình dạng.

## Cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark?
`Watermarker` là lớp chính trong GroupDocs.Watermark dùng để tải tài liệu và cung cấp quyền truy cập vào nội dung của nó. Tải DOCX bằng một thể hiện `Watermarker`, sau đó lặp qua mỗi phần và hình dạng để đọc các thuộc tính của chúng. Mô hình hai bước—khởi tạo, rồi liệt kê—bao phủ **tất cả hơn 30 loại hình dạng được hỗ trợ** và hoạt động cho các tài liệu lên tới 500 trang mà không tiêu tốn quá nhiều bộ nhớ. Nó stream tài liệu một cách hiệu quả, cho phép bạn làm việc với các tệp lớn mà không cần bộ nhớ cao.

### Bước 1: cấu hình tùy chọn tải
`WordProcessingLoadOptions` cho phép bạn tinh chỉnh cách tệp được phân tích (ví dụ: bỏ qua header, bật chế độ nhanh).  
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```  
Đoạn mã tạo một `Watermarker` giữ tài liệu trong bộ nhớ và chuẩn bị nó để kiểm tra.

### Bước 2: truy cập nội dung xử lý Word
Lặp qua các phần và hình dạng, in ra các chi tiết chính như loại, kích thước, căn chỉnh và liệu hình dạng có nằm trong header/footer hay không.  
```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```  
Vòng lặp này bao phủ mọi đối tượng hình dạng, đảm bảo bạn không bỏ lỡ các đồ họa ẩn được nhúng trong header hoặc footer.

## Các vấn đề thường gặp và giải pháp
- **File not found** – kiểm tra lại đường dẫn tuyệt đối hoặc tương đối; sử dụng `Paths.get(...).toAbsolutePath()` để rõ ràng.  
- **Performance bottlenecks** – đối với tài liệu lớn hơn 300 trang, xử lý từng phần một và gọi `watermarker.close()` sau mỗi lô để giải phóng bộ nhớ.  
- **Unsupported shape type** – hiện tại GroupDocs.Watermark hỗ trợ 25 danh mục hình dạng gốc; đối với các đối tượng OfficeArt tùy chỉnh, hãy cân nhắc sử dụng OpenXML SDK như một giải pháp dự phòng.

## Ứng dụng thực tiễn
1. **Automated report generation** – trích xuất biểu đồ để nhúng vào bảng điều khiển.  
2. **Compliance auditing** – xác minh rằng không có đồ họa bị cấm xuất hiện trong tài liệu được quy định.  
3. **Migration pipelines** – chuyển đổi hình dạng sang SVG trước khi di chuyển nội dung tới các nền tảng xuất bản dựa trên web.

## Các cân nhắc về hiệu năng
- Giải phóng đối tượng `Watermarker` ngay lập tức bằng `watermarker.close()` để giải phóng tài nguyên gốc.  
- Bật cờ `fastLoad` trong `WordProcessingLoadOptions` khi bạn chỉ cần siêu dữ liệu hình dạng, không cần render toàn bộ nội dung.  
- Xử lý tài liệu trong parallel streams chỉ khi máy chủ của bạn có đủ lõi CPU; tránh các đối tượng chia sẻ không an toàn với thread.

## Kết luận
Bây giờ bạn đã biết **cách trích xuất các hình dạng** từ tài liệu Word bằng GroupDocs.Watermark cho Java. Bằng cách tải tài liệu với `Watermarker`, cấu hình tùy chọn tải và lặp qua mỗi hình dạng, bạn có thể xây dựng các quy trình tự động mạnh mẽ xử lý ngay cả những tệp phức tạp nhất.

### Các bước tiếp theo
- Thử nghiệm phương thức `getImageData()` của đối tượng `Shape` để xuất hình ảnh dưới dạng PNG.  
- Khám phá các tính năng khác của GroupDocs.Watermark như phát hiện và loại bỏ watermark.  
- Kết hợp việc trích xuất hình dạng với thư viện GroupDocs.Parser để lấy văn bản xung quanh cho phân tích sâu hơn.

## Câu hỏi thường gặp

**Q: GroupDocs.Watermark cho Java là gì?**  
A: GroupDocs.Watermark cho Java là một SDK toàn diện cho phép tạo, phát hiện watermark và kiểm tra tài liệu trên hơn 30 định dạng tệp, bao gồm DOCX, PDF và PPTX.

**Q: Tôi có thể trích xuất hình dạng từ các tệp Word được bảo vệ bằng mật khẩu không?**  
A: Có—cung cấp mật khẩu cho `WordProcessingLoadOptions` khi khởi tạo thể hiện `Watermarker`.

**Q: Thư viện có hoạt động trên máy chủ Linux không?**  
A: Hoàn toàn; GroupDocs.Watermark không phụ thuộc vào nền tảng và chạy trên bất kỳ hệ điều hành nào hỗ trợ Java 8+.

**Q: Có thể xử lý bao nhiêu hình dạng trong một tài liệu duy nhất?**  
A: SDK có thể xử lý hàng nghìn hình dạng; các thử nghiệm cho thấy hiệu năng ổn định trên tài liệu có tới 5.000 hình dạng riêng lẻ.

**Q: Cần giấy phép riêng cho việc trích xuất hình dạng không?**  
A: Không, việc trích xuất hình dạng đã được bao gồm trong giấy phép tiêu chuẩn của GroupDocs.Watermark.

---

**Cập nhật lần cuối:** 2026-09-06  
**Kiểm tra với:** GroupDocs.Watermark 23.12 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Trích xuất thông tin hình dạng từ sơ đồ bằng GroupDocs.Watermark trong Java](/watermark/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/)
- [Xóa các hình dạng khỏi tài liệu Word bằng GroupDocs.Watermark trong Java&#58; Hướng dẫn toàn diện](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}