---
date: '2026-02-16'
description: Tìm hiểu cách thêm dấu nước vào trang sơ đồ cụ thể bằng GroupDocs.Watermark
  cho Java, bao gồm cách thêm dấu nước hình ảnh trong Java và bảo vệ các tệp của bạn.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: Thêm watermark vào trang sơ đồ cụ thể bằng GroupDocs.Watermark cho Java
type: docs
url: /vi/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# Đánh dấu trang biểu đồ cụ thể bằng GroupDocs.Watermark cho Java

Bảo vệ các biểu đồ của bạn là rất quan trọng, đặc biệt khi bạn cần **watermark specific diagram page** để bảo vệ sở hữu trí tuệ hoặc ghi nhận thương hiệu. Trong hướng dẫn này, bạn sẽ học từng bước cách thêm cả dấu nước dạng văn bản và hình ảnh vào các trang đã chọn của tệp biểu đồ bằng **GroupDocs.Watermark for Java**. Khi kết thúc, bạn sẽ sẵn sàng bảo mật các biểu đồ và kiểm soát chính xác vị trí xuất hiện của mỗi dấu nước.

## Câu trả lời nhanh
- **Mục đích chính là gì?** Thêm dấu nước vào các trang biểu đồ đã chọn.  
- **Thư viện nào được yêu cầu?** GroupDocs.Watermark for Java (Maven hoặc tải trực tiếp).  
- **Tôi có thể thêm dấu nước hình ảnh java không?** Có – sử dụng `ImageWatermark` với các tùy chọn riêng cho trang.  
- **Tôi có cần giấy phép không?** Giấy phép dùng thử tạm thời hoạt động cho việc thử nghiệm; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Có bao nhiêu dòng mã?** Ít hơn 30 dòng cho quy trình dấu nước văn bản + hình ảnh hoàn chỉnh.

## “watermark specific diagram page” là gì?
Một **watermark specific diagram page** có nghĩa là áp dụng một dấu hiệu trực quan—văn bản hoặc hình ảnh—chỉ vào các trang bạn chọn trong một biểu đồ đa trang (ví dụ, Visio . vsdx). Điều này cho phép bạn kiểm soát chi tiết về thương hiệu, thông báo bảo mật, hoặc tuyên bố bản quyền mà không ảnh hưởng đến toàn bộ tài liệu.

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?
- **Full page control** – nhắm mục tiêu bất kỳ chỉ mục trang nào bạn cần.  
- **Rich styling** – phông chữ, màu sắc, độ trong suốt, xoay, và tỉ lệ hình ảnh đều có thể cấu hình.  
- **Performance‑optimized** – xử lý các biểu đồ lớn một cách hiệu quả và tích hợp mượt mà với các dự án Maven.  
- **Cross‑format support** – hoạt động với Visio, SVG và nhiều định dạng biểu đồ khác.

## Yêu cầu trước
- **GroupDocs.Watermark for Java** phiên bản 24.11 hoặc mới hơn.  
- Maven hoặc tải JAR trực tiếp.  
- Môi trường phát triển Java cơ bản (khuyến nghị JDK 8+).

## Cài đặt GroupDocs.Watermark cho Java
### Sử dụng Maven groupdocs watermark
Bao gồm GroupDocs.Watermark vào dự án của bạn qua Maven bằng cách thêm đoạn sau vào `pom.xml` của bạn:

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
Hoặc tải phiên bản mới nhất trực tiếp từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Nhận giấy phép
Bắt đầu với bản dùng thử miễn phí bằng cách tải giấy phép tạm thời. Các tùy chọn mua hàng có sẵn trên trang chính thức nếu bạn muốn tiếp tục sử dụng GroupDocs.Watermark.

### Khởi tạo và Cấu hình Cơ bản
Sau khi cài đặt, khởi tạo lớp `Watermarker` để thực hiện các thao tác đánh dấu:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Hướng dẫn triển khai
### Thêm Dấu nước Văn bản vào Trang Cụ thể
Để thêm dấu nước văn bản, tạo và cấu hình nó trước khi chỉ định trang mục tiêu.

#### Tạo Dấu nước Văn bản
Xác định dấu nước văn bản của bạn với nội dung tùy chỉnh, kiểu phông chữ, kích thước, v.v.:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### Đặt Chỉ mục Trang cho Dấu nước
Xác định trang biểu đồ nào sẽ hiển thị dấu nước bằng cách sử dụng `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### Thêm Dấu nước Văn bản
Thêm dấu nước đã cấu hình vào biểu đồ:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### Thêm Dấu nước Hình ảnh vào Trang Cụ thể
Thực hiện các bước tương tự cho dấu nước hình ảnh bằng cách sử dụng đối tượng `ImageWatermark`.

#### Tạo Dấu nước Hình ảnh
Tạo một thể hiện của `ImageWatermark` với đường dẫn hình ảnh dấu nước mong muốn:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### Đặt Chỉ mục Trang cho Dấu nước
Chỉ định trang nào sẽ hiển thị dấu nước hình ảnh:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### Thêm Dấu nước Hình ảnh
Thêm hình ảnh vào trang biểu đồ đã chỉ định:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### Lưu và Đóng Tài nguyên
Nhớ lưu các thay đổi và đóng tài nguyên để tránh rò rỉ:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Ứng dụng Thực tiễn
- **Document Security** – Áp dụng dấu nước bảo mật chỉ trên các trang chứa sơ đồ nhạy cảm.  
- **Branding** – Đặt logo công ty của bạn trên trang bìa trong khi để các trang bên trong sạch sẽ.  
- **Copyright Protection** – Thêm thông báo bản quyền vào trang cuối cùng của một bộ sơ đồ kỹ thuật.

## Các yếu tố về Hiệu năng
- **Memory Management** – Đóng mỗi đối tượng dấu nước sau khi lưu để giải phóng tài nguyên gốc.  
- **Image Optimization** – Sử dụng các tệp PNG/JPEG có kích thước phù hợp để giữ tốc độ xử lý nhanh.  
- **Batch Processing** – Khi xử lý nhiều biểu đồ, tái sử dụng một thể hiện `Watermarker` duy nhất nếu có thể.

## Các vấn đề thường gặp và Giải pháp
| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|------------|---------------------|----------------|
| Dấu nước không hiển thị | Sai `pageIndex` (đánh số từ 0) | Xác minh chỉ mục khớp với trang mong muốn. |
| Hình ảnh bị biến dạng | Hình ảnh nguồn độ phân giải cao | Thay đổi kích thước hình ảnh trước khi tạo `ImageWatermark`. |
| Lỗi giấy phép trong môi trường sản xuất | Sử dụng giấy phép dùng thử vượt quá thời hạn | Áp dụng tệp giấy phép đầy đủ qua `License.setLicense("path/to/license.json")`. |

## Câu hỏi thường gặp

**Q1: Tôi có thể thêm nhiều dấu nước vào một trang biểu đồ duy nhất không?**  
A1: Có, chỉ cần gọi `watermarker.add()` với các đối tượng dấu nước khác nhau cho cùng một chỉ mục trang.

**Q2: Các định dạng tệp nào được GroupDocs.Watermark cho Java hỗ trợ?**  
A2: Nó hỗ trợ nhiều định dạng biểu đồ và hình ảnh. Kiểm tra [API documentation](https://reference.groupdocs.com/watermark/java) để xem danh sách đầy đủ.

**Q3: Làm thế nào để xử lý các vấn đề giấy phép khi sử dụng phiên bản dùng thử?**  
A3: Bắt đầu với giấy phép tạm thời miễn phí từ GroupDocs. Mua giấy phép đầy đủ để mở khóa tất cả tính năng cho môi trường sản xuất.

**Q4: Một số mẹo khắc phục sự cố thường gặp nếu dấu nước không hiển thị như mong đợi là gì?**  
A4: Đảm bảo chỉ mục trang đúng và kiểm tra lại đường dẫn tệp cho tài nguyên hình ảnh. Ngoài ra, xác nhận độ trong suốt của dấu nước không được đặt là 0.

**Q5: Làm thế nào tôi có thể tùy chỉnh thêm giao diện dấu nước?**  
A5: Điều chỉnh kích thước phông chữ, độ trong suốt, xoay và vị trí bằng các phương thức có sẵn trên `TextWatermark` hoặc `ImageWatermark`.

## Tài nguyên
- [Tài liệu GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)
- [Hướng dẫn Tham chiếu API](https://reference.groupdocs.com/watermark/java)
- [Tải thư viện](https://releases.groupdocs.com/watermark/java/)
- [Kho GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Diễn đàn Hỗ trợ Miễn phí](https://forum.groupdocs.com/c/watermark/10)
- [Thông tin Giấy phép Tạm thời](https://purchase.groupdocs.com/temporary-license/)

Khám phá các tài nguyên này để nâng cao hiểu biết và khả năng của bạn với GroupDocs.Watermark cho Java. Chúc bạn đánh dấu thành công!

---

**Cập nhật lần cuối:** 2026-02-16  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs