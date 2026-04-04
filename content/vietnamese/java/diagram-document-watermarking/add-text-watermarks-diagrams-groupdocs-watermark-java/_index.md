---
date: '2026-04-04'
description: Tìm hiểu cách tạo dấu watermark văn bản trên các sơ đồ Visio bằng GroupDocs.Watermark
  cho Java. Bao gồm cài đặt, mã nguồn và các trường hợp sử dụng thực tế.
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: Tạo Đánh Dấu Văn Bản trên Sơ Đồ bằng GroupDocs.Watermark Java
type: docs
url: /vi/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Tạo Đánh Dấu Văn Bản trên Sơ Đồ với GroupDocs.Watermark Java

Bảo vệ các sơ đồ của bạn khỏi việc sử dụng trái phép là điều cần thiết trong môi trường cộng tác ngày nay. Trong hướng dẫn này, bạn sẽ **tạo đánh dấu văn bản** trên các sơ đồ kiểu Visio bằng **GroupDocs.Watermark for Java**. Chúng tôi sẽ hướng dẫn từ cài đặt Maven đến việc lưu tệp đã được đánh dấu, để bạn có thể tự tin thêm thương hiệu hoặc dấu bảo mật vào mỗi trang sơ đồ.

## Câu trả lời nhanh
- **Thư viện tôi cần là gì?** GroupDocs.Watermark for Java (Maven artifact `groupdocs-watermark`).
- **Các loại tệp nào được hỗ trợ?** Visio (`.vsdx`, `.vsd`), as well as many other diagram formats.
- **Tôi có cần giấy phép không?** Giấy phép dùng thử tạm thời hoạt động cho việc phát triển; một giấy phép đầy đủ là bắt buộc cho môi trường sản xuất.
- **Tôi có thể tùy chỉnh phông chữ, màu sắc và góc quay không?** Có – lớp `TextWatermark` cho phép bạn thiết lập tất cả các thuộc tính đó.
- **Quá trình mất bao lâu?** Thêm đánh dấu văn bản vào một sơ đồ thông thường mất dưới một giây trên phần cứng hiện đại.

## Hoạt động “tạo đánh dấu văn bản” là gì?
Tạo một đánh dấu văn bản có nghĩa là chồng lên một cách lập trình văn bản bán trong suốt lên một trang tài liệu. Đánh dấu có thể được đặt ở tiền cảnh hoặc hậu cảnh, xoay, đổi màu và định dạng để phù hợp với yêu cầu thương hiệu hoặc bảo mật.

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?
- **Hỗ trợ đa định dạng** – hoạt động với Visio, PDF, Word, Excel và nhiều định dạng khác.
- **Kiểm soát chi tiết** – chọn vị trí, độ mờ, góc quay và việc hiển thị nền/tiền cảnh.
- **Tích hợp dễ dàng** – Cài đặt dựa trên Maven và các lời gọi API đơn giản giúp mã của bạn sạch sẽ.
- **Tối ưu hiệu năng** – các tài nguyên được giải phóng tự động khi bạn đóng `Watermarker`.

## Yêu cầu trước
- Java Development Kit (JDK) 8 hoặc cao hơn.
- Một IDE như IntelliJ IDEA hoặc Eclipse.
- Maven để quản lý phụ thuộc.

## Cài đặt GroupDocs.Watermark cho Java
Thêm kho và phụ thuộc vào tệp `pom.xml` của bạn:

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

Nếu bạn muốn tải xuống thủ công, lấy các tệp nhị phân từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) và thêm chúng vào classpath của dự án.

### Nhận giấy phép
Bắt đầu với giấy phép dùng thử miễn phí từ [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Tải tệp giấy phép trước bất kỳ thao tác đánh dấu nào:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Triển khai theo từng bước

### Bước 1: Tải tệp Sơ Đồ
Sử dụng `DiagramLoadOptions` để mở tệp Visio (hoặc bất kỳ định dạng sơ đồ nào được hỗ trợ).

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Bước 2: Tạo Đánh Dấu Văn Bản
Cấu hình văn bản đánh dấu, phông chữ, màu sắc, cờ nền và góc quay.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### Bước 3: Xác định Vị trí cho Sơ Đồ
Chọn xem đánh dấu xuất hiện ở nền hay tiền cảnh của mỗi trang sơ đồ.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Bước 4: Lưu Sơ Đồ Đã Đánh Dấu
Ghi kết quả vào một tệp mới và giải phóng tài nguyên.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Các vấn đề thường gặp & Giải pháp

| Vấn đề | Giải pháp |
|---------|----------|
| **Không tìm thấy tệp** | Xác minh đường dẫn tuyệt đối/định tương và đảm bảo tệp có thể đọc được bởi tiến trình Java. |
| **Giấy phép không được áp dụng** | Xác nhận đường dẫn tệp giấy phép đúng và tệp không bị hỏng. |
| **Đánh dấu không hiển thị** | Kiểm tra `setBackground(false)` và góc quay; thử màu hoặc độ mờ khác. |
| **Phiên bản sơ đồ không được hỗ trợ** | Sử dụng phiên bản GroupDocs.Watermark mới nhất (24.11) để hỗ trợ các định dạng Visio mới hơn. |

## Các trường hợp sử dụng thực tế
1. **Bảo mật tài liệu** – Ngăn đối thủ tái sử dụng các sơ đồ luồng sở hữu.
2. **Đồng nhất thương hiệu** – Tự động nhúng tên công ty hoặc logo vào tất cả các sơ đồ đã xuất.
3. **Theo dõi hợp tác** – Thêm chữ ký người dùng làm đánh dấu để xác định ai đã chỉnh sửa mỗi sơ đồ.

## Mẹo hiệu năng
- Đóng `Watermarker` ngay khi hoàn thành để giải phóng tài nguyên gốc.
- Đối với xử lý hàng loạt, tái sử dụng một thể hiện `Watermarker` duy nhất khi có thể.
- Giữ văn bản đánh dấu ngắn gọn; phông chữ lớn làm tăng thời gian render.

## Kết luận
Bây giờ bạn đã biết cách **tạo đánh dấu văn bản** trên các sơ đồ Visio bằng GroupDocs.Watermark cho Java. Cách tiếp cận này cho phép bạn kiểm soát toàn diện về giao diện, vị trí và kiểu dáng, giúp bảo vệ và thương hiệu hoá tài sản hình ảnh của bạn một cách hiệu quả.

### Các bước tiếp theo
- Thử nghiệm với đánh dấu hình ảnh (`ImageWatermark`) cho việc thương hiệu hoá logo.
- Khám phá việc đánh dấu trang chọn lọc bằng cách lặp qua `watermarker.getPages()` và áp dụng các tùy chọn có điều kiện.
- Tích hợp logic này vào quy trình CI/CD của bạn để tự động bảo mật các sơ đồ trước khi xuất bản.

## Phần Câu hỏi Thường gặp
1. **Tôi có thể sử dụng GroupDocs.Watermark cho các định dạng tệp khác không?**  
   Có, nó hỗ trợ PDF, tài liệu Word, bảng tính Excel, bản trình bày PowerPoint và nhiều hơn nữa.

2. **Có giới hạn số lượng đánh dấu tôi có thể thêm không?**  
   Không có giới hạn cứng, nhưng việc thêm nhiều đánh dấu phức tạp có thể ảnh hưởng đến hiệu năng.

3. **Làm thế nào để loại bỏ đánh dấu khỏi một sơ đồ?**  
   GroupDocs.Watermark cung cấp API phát hiện và loại bỏ mà bạn có thể gọi tương tự như quy trình thêm.

4. **Có thể thêm đánh dấu văn bản vào tất cả các trang hoặc chỉ một số trang được chọn không?**  
   Bạn có thể cấu hình `DiagramShapeWatermarkOptions` cho mỗi trang hoặc áp dụng bộ lọc trước khi gọi `add`.

5. **Tôi nên làm gì nếu đánh dấu không hiển thị như mong đợi?**  
   Kiểm tra lại cài đặt vị trí, độ tương phản màu và đảm bảo sơ đồ không bị làm phẳng sau khi lưu.

## Câu hỏi Thường gặp

**Q: Thư viện có hoạt động với tệp Visio 2003 (`.vsd`) không?**  
A: Có – `DiagramLoadOptions` hỗ trợ cả định dạng `.vsdx` và `.vsd` legacy.

**Q: Tôi có thể thay đổi độ mờ của đánh dấu văn bản không?**  
A: Chắc chắn. Sử dụng `textWatermark.setOpacity(0.5);` để đặt độ trong suốt 50 %.

**Q: Có thể thêm các đánh dấu khác nhau vào các trang sơ đồ khác nhau không?**  
A: Có. Lặp qua `watermarker.getPages()` và áp dụng các thể hiện `TextWatermark` riêng biệt với các tùy chọn tùy chỉnh cho mỗi trang.

**Q: Có bất kỳ hạn chế giấy phép nào cho việc sử dụng thương mại không?**  
A: Một giấy phép thương mại đầy đủ là bắt buộc cho triển khai sản xuất; giấy phép dùng thử chỉ dành cho đánh giá.

**Q: Làm thế nào để xử lý hàng loạt nhiều sơ đồ trong một lần chạy?**  
A: Đặt các bước trên vào một vòng lặp tải mỗi tệp, áp dụng đánh dấu, lưu và đóng `Watermarker` trước khi chuyển sang tệp tiếp theo.

---

**Cập nhật lần cuối:** 2026-04-04  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs  

## Tài nguyên
- [Tài liệu](https://docs.groupdocs.com/watermark/java/)
- [Tham chiếu API](https://reference.groupdocs.com/watermark/java)
- [Tải phiên bản mới nhất](https://releases.groupdocs.com/watermark/java/)
- [Kho GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Diễn đàn hỗ trợ miễn phí](https://forum.groupdocs.com/c/watermark/10)