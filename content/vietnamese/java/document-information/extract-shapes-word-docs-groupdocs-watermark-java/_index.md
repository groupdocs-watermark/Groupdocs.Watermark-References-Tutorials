---
date: '2025-12-20'
description: Tìm hiểu cách trích xuất hình ảnh từ tài liệu Word và trích xuất các
  hình dạng bằng GroupDocs.Watermark cho Java, hoàn hảo cho tự động hoá và xử lý tài
  liệu.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Cách trích xuất hình ảnh từ tài liệu Word bằng GroupDocs.Watermark trong Java
type: docs
url: /vi/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Cách Trích Xuất Hình Ảnh từ Tài Liệu Word Sử Dụng GroupDocs.Watermark trong Java

Trong các ứng dụng xử lý tài liệu hiện đại, **trích xuất hình ảnh từ word** là một yêu cầu thường gặp — dù bạn cần tái sử dụng đồ họa, chạy OCR, hay chỉ đơn giản là kiểm tra nội dung. Hướng dẫn này sẽ chỉ cho bạn, từng bước, cách tải một tài liệu Word trong Java bằng GroupDocs.Watermark và sau đó **trích xuất hình ảnh từ word** đồng thời minh họa **cách trích xuất các hình dạng**. Khi hoàn thành, bạn sẽ có một đoạn mã có thể tái sử dụng, phù hợp ngay vào quy trình tự động của mình.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc trích xuất hình ảnh?** GroupDocs.Watermark cho Java  
- **Có thể trích xuất cả ảnh và hình vector không?** Có — API cung cấp quyền truy cập vào hình ảnh và siêu dữ liệu hình dạng.  
- **Yêu cầu phiên bản Java nào?** JDK 8 trở lên.  
- **Cần giấy phép cho môi trường production không?** Giấy phép thương mại được khuyến nghị; bản dùng thử miễn phí đủ cho việc đánh giá.  
- **Quá trình có tiết kiệm bộ nhớ cho các tệp lớn không?** Có, bạn có thể giải phóng tài nguyên kịp thời và xử lý các phần một cách tuần tự.

## “Trích xuất hình ảnh từ Word” là gì?
Trích xuất hình ảnh từ Word có nghĩa là lập trình tìm ra mọi ảnh, bản vẽ hoặc đồ họa nhúng bên trong tệp `.docx` và lấy dữ liệu nhị phân hoặc siêu dữ liệu của chúng. Điều này cho phép các tác vụ tiếp theo như phân tích hình ảnh, di chuyển nội dung, hoặc tạo báo cáo động.

## Tại sao nên dùng GroupDocs.Watermark cho nhiệm vụ này?
GroupDocs.Watermark cung cấp một API cấp cao, trừu tượng hoá các phức tạp của định dạng OpenXML. Nó cho phép bạn **load word document java** chỉ với vài dòng mã, đồng thời cung cấp thông tin chi tiết về các hình dạng — lý tưởng cho các nhà phát triển cần cả trích xuất hình ảnh và phân tích hình dạng.

## Điều kiện tiên quyết
- **Java Development Kit (JDK)** 8 hoặc mới hơn  
- **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo Java nào tương thích  
- Kiến thức cơ bản về Java I/O  
- Truy cập giấy phép GroupDocs.Watermark (bản dùng thử đủ cho việc thử nghiệm)

## Cài đặt GroupDocs.Watermark cho Java
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

### Nhận giấy phép
Để sử dụng đầy đủ tính năng, lấy khóa giấy phép từ cổng GroupDocs. Bạn có thể yêu cầu giấy phép dùng thử tạm thời để khám phá mọi tính năng mà không bị giới hạn.

## Hướng dẫn triển khai
Chúng ta sẽ chia việc triển khai thành hai phần logic:

1. **Cách tải tài liệu Word trong Java**  
2. **Cách trích xuất hình dạng và hình ảnh (tức là trích xuất hình ảnh từ word)**

### Tải tài liệu Word
Đầu tiên, cấu hình các tùy chọn tải và khởi tạo đối tượng `Watermarker`.

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

> **Mẹo chuyên nghiệp:** Thay `"YOUR_DOCUMENT_DIRECTORY/document.docx"` bằng đường dẫn tuyệt đối hoặc tương đối trỏ tới tệp bạn muốn xử lý.

### Trích xuất thông tin hình dạng và hình ảnh
Sau khi tài liệu đã được tải, bạn có thể duyệt qua từng phần và từng hình dạng, lấy cả dữ liệu hình vector và chi tiết ảnh nhúng.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

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

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
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

> **Tại sao lại quan trọng:** Lệnh `shape.getImage()` cung cấp truy cập trực tiếp tới biểu diễn nhị phân của mỗi ảnh, cho phép bạn lưu nó ra đĩa, gửi qua mạng, hoặc đưa vào thư viện xử lý ảnh.

## Các vấn đề thường gặp và giải pháp
| Vấn đề | Giải pháp |
|---------|----------|
| **FileNotFoundException** – đường dẫn sai | Kiểm tra lại đường dẫn tệp và đảm bảo ứng dụng có quyền đọc. |
| **OutOfMemoryError** khi tài liệu lớn | Xử lý từng phần một và gọi `watermarker.close()` ngay khi hoàn thành một batch. |
| Hình dạng trả về `null` cho `getImage()` | Không phải mọi hình dạng đều là ảnh; một số là đối tượng vẽ. Kiểm tra `shape.getShapeType()` trước khi truy cập ảnh. |
| Giấy phép chưa được áp dụng | Thêm `License.setLicense("path/to/license/file.lic");` trước khi tạo `Watermarker`. |

## Ứng dụng thực tiễn
- **Tự động tạo báo cáo:** Lấy biểu đồ và logo từ mẫu để tái sử dụng trong dashboard.  
- **Kiểm tra nội dung:** Quét tài liệu công ty để phát hiện đồ họa bị cấm.  
- **Dự án di chuyển:** Xuất ảnh nhúng trước khi chuyển nội dung sang CMS mới.

## Các lưu ý về hiệu năng
- Giải phóng nhanh đối tượng `Watermarker` (`watermarker.close()`).  
- Đối với tệp rất lớn (>50 MB), cân nhắc streaming các phần thay vì tải toàn bộ tài liệu vào bộ nhớ.  
- Sử dụng phiên bản GroupDocs.Watermark mới nhất để được cải thiện hiệu năng.

## Kết luận
Bạn đã có một quy trình hoàn chỉnh, sẵn sàng cho môi trường production để **trích xuất hình ảnh từ word** và lấy siêu dữ liệu hình dạng bằng GroupDocs.Watermark cho Java. Khả năng này mở ra các kịch bản tự động mạnh mẽ, từ tạo báo cáo động đến thực hiện kiểm tra tài liệu quy mô lớn.

### Các bước tiếp theo
- Thử lưu các ảnh đã trích xuất ra đĩa (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Khám phá các API bổ sung như loại bỏ hoặc thêm watermark.  
- Tích hợp logic này vào quy trình quản lý tài liệu hiện có của bạn.

## Phần Câu hỏi thường gặp
**Hỏi: GroupDocs.Watermark cho Java là gì?**  
Đáp: Đây là một thư viện toàn diện được thiết kế để quản lý watermark và trích xuất các yếu tố hình ảnh trên nhiều định dạng tài liệu, hỗ trợ tự động hoá các tác vụ thao tác tài liệu.

**Hỏi: Có thể trích xuất hình ảnh từ các tệp Word được bảo mật bằng mật khẩu không?**  
Đáp: Có. Tải tài liệu bằng `WordProcessingLoadOptions` kèm mật khẩu, sau đó thực hiện quy trình trích xuất như bình thường.

**Hỏi: API có hỗ trợ tệp .doc (binary) không?**  
Đáp: Thư viện chủ yếu nhắm tới định dạng OpenXML `.docx`, nhưng cũng có thể mở các tệp `.doc` cũ sau khi chuyển đổi.

**Hỏi: Làm sao lưu các ảnh đã trích xuất vào hệ thống tập tin?**  
Đáp: Sử dụng `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` trong vòng lặp khi `shape.getImage()` không null.

**Hỏi: Có giới hạn số lượng hình dạng có thể xử lý không?**  
Đáp: Không có giới hạn cứng, nhưng tiêu thụ bộ nhớ tăng theo kích thước tài liệu; nên xử lý các phần tuần tự cho các tệp rất lớn.

---

**Cập nhật lần cuối:** 2025-12-20  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs