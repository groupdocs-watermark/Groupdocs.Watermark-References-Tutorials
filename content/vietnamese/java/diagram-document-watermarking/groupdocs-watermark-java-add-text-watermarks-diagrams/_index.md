---
date: '2025-12-19'
description: Tìm hiểu cách thêm watermark văn bản vào các sơ đồ bằng GroupDocs.Watermark
  cho Java. Bảo vệ nội dung hình ảnh của bạn một cách hiệu quả và đảm bảo tính toàn
  vẹn của tài liệu.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: Thêm Đánh Dấu Văn Bản vào Sơ Đồ bằng GroupDocs.Watermark cho Java – Hướng Dẫn
  Toàn Diện
type: docs
url: /vi/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Thêm Đánh Dấu Văn Bản vào Sơ Đồ Sử Dụng GroupDocs.Watermark cho Java: Hướng Dẫn Toàn Diện

## Giới thiệu
Bảo vệ các tài liệu sơ đồ khỏi việc sử dụng trái phép là rất quan trọng, và **thêm một dấu watermark văn bản** cung cấp một giải pháp đơn giản nhưng hiệu quả. Trong hướng dẫn này, bạn sẽ khám phá cách tải các tệp sơ đồ, tạo một dấu watermark văn bản có thể tùy chỉnh, và áp dụng nó lên các trang nền hoặc các hình dạng cụ thể bằng **GroupDocs.Watermark cho Java**. Khi kết thúc hướng dẫn, bạn sẽ có thể bảo vệ tài sản hình ảnh của mình đồng thời giữ nguyên giao diện và cảm giác ban đầu.

### Câu trả lời nhanh
- **Thêm dấu watermark văn bản** có nghĩa là gì?  
  Nó có nghĩa là nhúng một lớp văn bản bán trong suốt vào tài liệu để chỉ ra quyền sở hữu hoặc tính bảo mật.  
- **Thư viện nào hỗ trợ đánh dấu watermark cho sơ đồ?**  
  GroupDocs.Watermark for Java cung cấp hỗ trợ gốc cho các định dạng sơ đồ (ví dụ: Visio, VSDX).  
- **Tôi có cần giấy phép không?**  
  Cần một giấy phép tạm thời hoặc đầy đủ cho việc sử dụng trong môi trường sản xuất; bản dùng thử miễn phí có sẵn để đánh giá.  
- **Tôi có thể đặt watermark lên các trang nền không?**  
  Có – sử dụng tùy chọn `DiagramWatermarkPlacementType.SeparateBackgrounds` cho **watermark trang nền**.  
- **Mã có tương thích với Java 8+ không?**  
  Hoàn toàn – thư viện hoạt động với JDK 8 và các phiên bản mới hơn.

## Đánh Dấu Văn Bản là gì cho Sơ Đồ?
Một watermark văn bản là một đoạn văn bản có thể đọc được (thường là bán trong suốt) được hiển thị phía trên hoặc phía sau các thành phần của sơ đồ. Nó có thể được sử dụng cho việc xây dựng thương hiệu, bảo vệ bản quyền, hoặc đánh dấu các bản nháp bảo mật.

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?
- **Broad format support** – hoạt động với Visio, VSDX và nhiều loại sơ đồ khác.  
- **Fine‑grained placement** – chọn watermark cho nền trước, nền sau, hoặc cho hình dạng cụ thể.  
- **Simple API** – tạo và áp dụng watermark chỉ với vài dòng mã Java.  

## Yêu cầu trước
- **GroupDocs.Watermark for Java** (v24.11 hoặc sau)  
- **Java Development Kit (JDK)** 8 hoặc cao hơn  
- Maven (hoặc bao gồm JAR thủ công)  

## Cài đặt GroupDocs.Watermark cho Java
### Cấu hình Maven
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
Tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Đăng ký giấy phép
- **Free Trial** – đánh giá tất cả các tính năng mà không cần khóa giấy phép.  
- **Temporary License** – sử dụng trong quá trình phát triển để mở khóa đầy đủ chức năng.  
- **Purchase** – mua giấy phép sản xuất cho các dự án thương mại.  

### Khởi tạo và Cấu hình Cơ bản
Make sure the following imports are present in your Java class:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Thực hiện từng bước

### Bước 1: Tải tài liệu sơ đồ
First, point the library to your diagram file and initialize load options.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Giải thích*: `DiagramLoadOptions` cho phép bạn kiểm soát cách sơ đồ được phân tích trước khi áp dụng watermark.

### Bước 2: Tạo Watermark Văn Bản
Now create the watermark text and define its visual style.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Giải thích*: Điều này tạo một `TextWatermark` với cụm từ **“Test watermark 1”** sử dụng phông chữ Calibri kích thước 19.

### Bước 3: Cấu hình Vị trí – Watermark Trang Nền
Choose where the watermark should appear. For a **background page watermark**, use the following option:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Giải thích*: `DiagramShapeWatermarkOptions` kiểm soát vị trí chính xác. Đặt loại vị trí thành `SeparateBackgrounds` sẽ thêm watermark vào mỗi trang nền của sơ đồ.

### Bước 4: Áp dụng Watermark và Lưu
Finally, add the watermark to the document, save the result, and release resources.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Giải thích*: Phương thức `add` áp dụng `textWatermark` đã cấu hình bằng các tùy chọn vị trí, sau đó sơ đồ đã chỉnh sửa được lưu vào `outputPath`.

## Ứng dụng Thực tiễn
- **Intellectual Property Protection** – Ngăn chặn đối thủ tái sử dụng các sơ đồ sở hữu.  
- **Brand Reinforcement** – Nhúng tên công ty hoặc logo dưới dạng watermark văn bản trên tất cả các sơ đồ xuất khẩu.  
- **Legal Documentation** – Đánh dấu các bản nháp bảo mật của sơ đồ kỹ thuật.  
- **Academic Submissions** – Thêm mã sinh viên hoặc mã khóa học vào sơ đồ để theo dõi đạo văn.  

## Các yếu tố về hiệu suất
- **Memory Management** – Đóng instance `Watermarker` (`watermarker.close()`) để giải phóng tài nguyên gốc, đặc biệt khi xử lý các tệp lớn.  
- **Batch Processing** – Lặp qua một tập hợp các đường dẫn sơ đồ và tái sử dụng một instance `Watermarker` duy nhất khi có thể để giảm tải.  

## Các vấn đề thường gặp và giải pháp
| Vấn đề | Giải pháp |
|-------|----------|
| **OutOfMemoryError trên các sơ đồ lớn** | Tăng kích thước heap JVM (`-Xmx2g`) và xử lý các tệp từng cái một. |
| **Watermark không hiển thị** | Đảm bảo màu watermark có độ tương phản đủ; đặt độ trong suốt qua `textWatermark.setOpacity(0.5)`. |
| **Định dạng sơ đồ không được hỗ trợ** | Kiểm tra định dạng có được liệt kê trong tài liệu các định dạng được GroupDocs.Watermark hỗ trợ. |

## Câu hỏi thường gặp

**Q: Kích thước phông chữ tốt nhất cho watermark là bao nhiêu?**  
A: Kích thước tối ưu phụ thuộc vào kích thước của sơ đồ; 12‑20 pt thường phù hợp cho hầu hết các trường hợp.

**Q: Tôi có thể tùy chỉnh màu sắc của watermark không?**  
A: Có, sử dụng `textWatermark.setColor(Color.GRAY)` (hoặc bất kỳ `java.awt.Color` nào).

**Q: Làm thế nào để xử lý một loạt tài liệu lớn?**  
A: Tận dụng API batch của thư viện hoặc viết một vòng lặp tái sử dụng các đối tượng `Watermarker` để giảm thiểu tải.

**Q: Có bất kỳ hạn chế nào với GroupDocs.Watermark không?**  
A: Thư viện hỗ trợ hầu hết các định dạng sơ đồ phổ biến, nhưng một số phần mở rộng độc quyền có thể không được hiển thị đầy đủ. Kiểm tra [documentation](https://docs.groupdocs.com/watermark/java/) để biết chi tiết.

**Q: Làm sao tôi có thể nhận hỗ trợ nếu gặp vấn đề?**  
A: Truy cập [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) để được cộng đồng hỗ trợ hoặc liên hệ trực tiếp với bộ phận hỗ trợ của GroupDocs.

## Tài nguyên bổ sung
- **Tài liệu**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Tham chiếu API**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Tải xuống**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **Kho GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Diễn đàn hỗ trợ miễn phí**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Giấy phép tạm thời**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**Cập nhật lần cuối:** 2025-12-19  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs