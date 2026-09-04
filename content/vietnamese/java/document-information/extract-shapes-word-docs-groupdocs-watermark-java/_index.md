---
date: '2026-02-05'
description: Tìm hiểu cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark
  cho Java, bao gồm cách tải tài liệu Word trong Java và thao tác dữ liệu hình dạng.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Cách trích xuất các hình dạng từ tài liệu Word bằng GroupDocs.Watermark Java
type: docs
url: /vi/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Cách Trích Xuất Hình Dạng từ Tài Liệu Word Sử Dụng GroupDocs.Watermark trong Java

Trong hướng dẫn này, bạn sẽ khám phá **cách trích xuất hình dạng** từ tài liệu Word bằng thư viện GroupDocs.Watermark cho Java. Dù bạn cần phân tích sơ đồ, lấy ra các hình ảnh nhúng, hay tự động tạo báo cáo, việc trích xuất siêu dữ liệu hình dạng cho phép bạn kiểm soát và xây dựng các quy trình xử lý tài liệu thông minh hơn. Chúng tôi sẽ hướng dẫn cách cài đặt thư viện, tải tài liệu Word và lấy thông tin chi tiết về các hình dạng — tất cả bằng mã Java rõ ràng, từng bước một.

## Câu trả lời nhanh
- **“Trích xuất hình dạng” có nghĩa là gì?** Lấy siêu dữ liệu (loại, kích thước, vị trí, văn bản, hình ảnh) cho mỗi đối tượng vẽ trong tệp Word.  
- **Thư viện nào thực hiện việc này?** GroupDocs.Watermark cho Java.  
- **Có cần giấy phép không?** Bản dùng thử đủ cho việc phát triển; giấy phép đầy đủ sẽ bỏ các giới hạn sử dụng.  
- **Có thể lấy hình ảnh từ các hình dạng không?** Có – API cung cấp byte ảnh cho các hình dạng kiểu picture.  
- **Yêu cầu phiên bản Java nào?** JDK 8 hoặc mới hơn.

## “Cách Trích Xuất Hình Dạng” trong Ngữ Cảnh Tài Liệu Word là gì?
Trích xuất hình dạng có nghĩa là truy cập lập trình vào mọi phần tử vẽ — ảnh, WordArt, auto‑shape, biểu đồ, và ngay cả các hình dạng nhúng trong header hoặc footer. Thông tin này có thể được dùng để kiểm tra, di chuyển, hoặc phân tích nội dung dựa trên dữ liệu.

## Tại sao nên dùng GroupDocs.Watermark cho Java?
GroupDocs.Watermark cung cấp API cấp cao, tiết kiệm bộ nhớ, trừu tượng hoá độ phức tạp của định dạng Office Open XML. Nó cho phép bạn:
- Tải tài liệu nhanh chóng (`WordProcessingLoadOptions`).  
- Duyệt qua các section và shape mà không cần xử lý XML cấp thấp.  
- Lấy dữ liệu ảnh, văn bản, căn chỉnh và góc quay trong một lần gọi.  
- Tích hợp liền mạch vào các dịch vụ Java hiện có hoặc micro‑service.

## Yêu cầu trước
- **Java Development Kit (JDK)** 8 trở lên.  
- **IDE** như IntelliJ IDEA hoặc Eclipse.  
- Kiến thức cơ bản về Java I/O.  
- Truy cập **giấy phép GroupDocs.Watermark cho Java** hoặc bản dùng thử.

## Cài Đặt GroupDocs.Watermark cho Java
Tích hợp thư viện qua Maven hoặc tải trực tiếp.

### Sử dụng Maven
Thêm repository và dependency vào file `pom.xml` của bạn:

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
Hoặc tải JAR mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Mua Giấy Phép
Bản dùng thử miễn phí đủ cho việc thử nghiệm. Đối với môi trường sản xuất, yêu cầu giấy phép vĩnh viễn để mở khóa tất cả tính năng.

## Hướng Dẫn Triển Khai
Chúng ta sẽ chia triển khai thành hai bước rõ ràng: **tải tài liệu Word** và **trích xuất thông tin hình dạng**.

### Bước 1: Tải Tài Liệu Word (load word document java)
Đầu tiên, cấu hình các tùy chọn tải và tạo một thể hiện `Watermarker`. Điều này chuẩn bị tài liệu để kiểm tra tiếp theo.

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

> **Mẹo:** Giữ thể hiện `Watermarker` trong phạm vi hẹp nhất có thể; đóng nó kịp thời sẽ giải phóng tài nguyên gốc và tránh rò rỉ bộ nhớ.

### Bước 2: Trích Xuất Thông Tin Hình Dạng (extract images from shapes)
Bây giờ chúng ta sẽ lấy chi tiết của mọi hình dạng, bao gồm cả các hình ảnh nhúng. Mã sẽ duyệt qua từng section và từng shape, in ra các siêu dữ liệu hữu ích.

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

**Mã này thực hiện:**  
- Lấy **loại** của mỗi shape (ví dụ: picture, WordArt).  
- In **kích thước**, **vị trí**, và giá trị **góc quay**.  
- Hiển thị **văn bản thay thế** và **tên**, hữu ích cho kiểm tra khả năng truy cập.  
- Nếu shape chứa ảnh, in **kích thước pixel** và **kích thước byte** của ảnh — hoàn hảo để trích xuất hình ảnh từ shape.  

### Các Vấn Đề Thường Gặp & Cách Khắc Phục
| Vấn đề | Nguyên nhân | Giải pháp |
|-------|-------------|-----------|
| `FileNotFoundException` | Đường dẫn tệp sai hoặc thiếu quyền | Kiểm tra lại đường dẫn tuyệt đối/định danh và đảm bảo tệp có thể đọc được. |
| Null `shape.getImage()` | Shape không phải là picture (ví dụ: auto‑shape) | Kiểm tra `if (shape.getImage() != null)` như trong mẫu. |
| Sử dụng bộ nhớ cao trên tài liệu lớn | Tải toàn bộ tài liệu một lúc | Xử lý từng section một hoặc tăng heap JVM (`-Xmx`). |
| Thiếu shape trong header/footer | Không kiểm tra `shape.getHeaderFooter()` | Mẫu đã ghi lại khi một shape thuộc header/footer. |

## Ứng Dụng Thực Tiễn
1. **Tự động tạo báo cáo** – Lấy biểu đồ và sơ đồ để nhúng vào PDF downstream.  
2. **Kiểm tra tuân thủ** – Xác minh mọi shape có văn bản thay thế phù hợp cho khả năng truy cập.  
3. **Di chuyển nội dung** – Xuất ảnh nhúng từ các tệp Word cũ vào hệ thống quản lý tài sản kỹ thuật số.  

## Lưu Ý Về Hiệu Suất
- **Giải phóng tài nguyên**: Luôn gọi `watermarker.close()` trong khối `finally` hoặc dùng try‑with‑resources nếu bạn bọc API.  
- **Xử lý theo khối**: Đối với tài liệu lớn hơn 50 MB, cân nhắc xử lý từng section riêng để giảm footprint bộ nhớ.  
- **An toàn đa luồng**: Các thể hiện `Watermarker` không thread‑safe; tạo một thể hiện mới cho mỗi luồng.

## Kết Luận
Bạn đã biết **cách trích xuất hình dạng** từ tài liệu Word bằng GroupDocs.Watermark cho Java, từ việc tải tệp đến đọc mọi siêu dữ liệu shape và dữ liệu ảnh nhúng. Khả năng này mở ra nhiều cơ hội cho phân tích tài liệu nâng cao, pipeline nội dung tự động và kiểm tra khả năng truy cập.

### Các Bước Tiếp Theo
- Thử thay đổi thuộc tính shape (ví dụ: thay đổi kích thước hoặc vị trí).  
- Kết hợp cách này với **GroupDocs.Parser** để trích xuất văn bản xung quanh.  
- Tích hợp logic trích xuất vào dịch vụ REST để xử lý theo yêu cầu.

## Phần Câu Hỏi Thường Gặp
**Hỏi: GroupDocs.Watermark cho Java là gì?**  
Đáp: Đây là thư viện toàn diện được thiết kế để quản lý watermark và nội dung tài liệu trên nhiều định dạng, hỗ trợ các tác vụ như trích xuất shape, lấy ảnh và thao tác văn bản.

**Hỏi: Tôi có thể trích xuất ảnh từ shape mà không có giấy phép không?**  
Đáp: Phiên bản dùng thử cho phép trích xuất, nhưng giấy phép đầy đủ sẽ bỏ các giới hạn sử dụng và cho phép triển khai thương mại.

**Hỏi: Điều này có hoạt động với tệp `.doc` (binary) không?**  
Đáp: Có, API hỗ trợ cả định dạng `.docx` và `.doc` legacy.

**Hỏi: Làm sao xử lý tài liệu được bảo mật bằng mật khẩu?**  
Đáp: Cung cấp mật khẩu qua `WordProcessingLoadOptions.setPassword("yourPassword")` trước khi tạo `Watermarker`.

**Hỏi: Có cách xuất dữ liệu shape đã trích xuất ra JSON không?**  
Đáp: Bạn có thể ánh xạ các giá trị đã in ra thành POJO và dùng bất kỳ thư viện JSON nào (ví dụ: Jackson) để serialize collection.

---

**Cập nhật lần cuối:** 2026-02-05  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs