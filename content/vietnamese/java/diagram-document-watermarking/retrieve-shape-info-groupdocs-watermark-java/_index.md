---
date: '2026-02-13'
description: Tìm hiểu cách trích xuất các hình dạng và lấy hình ảnh từ hình dạng bằng
  GroupDocs.Watermark cho Java, đồng thời truy xuất thông tin chi tiết của sơ đồ một
  cách hiệu quả.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Cách Trích Xuất Các Hình Dạng Từ Sơ Đồ Sử Dụng GroupDocs.Watermark Trong Java
type: docs
url: /vi/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

 any code blocks placeholders: CODE_BLOCK_0,1,2,3,4,5.

Also ensure we keep markdown formatting.

Now produce final content.# Cách Trích Xuất Các Hình Dạng Từ Sơ Đồ Sử Dụng GroupDocs.Watermark trong Java

Khi bạn cần **cách trích xuất các hình dạng** từ một sơ đồ kiểu Visio một cách lập trình, thư viện GroupDocs.Watermark cung cấp cho bạn một cách tiếp cận sạch sẽ, ưu tiên Java để lấy mọi chi tiết—kích thước, vị trí, hình ảnh nhúng, và thậm chí cả văn bản bên trong mỗi hình dạng. Trong hướng dẫn này, bạn sẽ thấy chính xác **cách trích xuất các hình dạng**, lý do tại sao nó quan trọng, và mã từng bước mà bạn có thể sao chép vào dự án của mình.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc trích xuất hình dạng?** GroupDocs.Watermark for Java  
- **Phiên bản Java nào được yêu cầu?** JDK 8 hoặc cao hơn  
- **Tôi có thể lấy dữ liệu hình ảnh từ một hình dạng không?** Có – sử dụng `shape.getImage()`  
- **Văn bản bên trong một hình dạng có thể truy cập được không?** Hoàn toàn có thể, thông qua `shape.getText()`  
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép GroupDocs.Watermark hợp lệ  

## Giới thiệu

Quản lý các sơ đồ phức tạp thường đòi hỏi việc truy cập thông tin chi tiết về các thành phần của chúng, chẳng hạn như hình dạng và hình ảnh. Nếu bạn từng cần lấy dữ liệu như kích thước, vị trí, hoặc văn bản liên quan đến các hình dạng trong sơ đồ bằng Java một cách lập trình, hướng dẫn này dành cho bạn. Tận dụng sức mạnh của thư viện GroupDocs.Watermark có thể giúp tối ưu hoá quy trình này trong một ứng dụng Java. Trong hướng dẫn này, chúng tôi sẽ trình bày **cách trích xuất các hình dạng** từ một tệp sơ đồ và cũng sẽ chỉ cho bạn cách **trích xuất hình ảnh từ hình dạng** và **trích xuất văn bản từ hình dạng**.

## “Cách trích xuất các hình dạng” là gì?

Việc trích xuất các hình dạng có nghĩa là đọc các đối tượng nội bộ của sơ đồ (trang, hình dạng, hình ảnh, văn bản) để bạn có thể phân tích, chuyển đổi, hoặc tái sử dụng chúng trong các ứng dụng khác—lý tưởng cho tự động hoá, báo cáo, hoặc tích hợp với các công cụ CAD.

## Tại sao nên sử dụng GroupDocs.Watermark để trích xuất hình dạng?

- **Hỗ trợ đầy đủ các định dạng** – hoạt động với VSDX, VDX và nhiều loại sơ đồ khác.  
- **Mô hình đối tượng phong phú** – cung cấp truy cập trực tiếp tới hình học của hình dạng, hình ảnh và văn bản.  
- **Không phụ thuộc bên ngoài** – thuần Java, dễ nhúng vào các dự án Maven.  

## Yêu cầu trước

- **GroupDocs.Watermark for Java** (phiên bản 24.11 hoặc mới hơn)  
- Java Development Kit (JDK) 8 hoặc cao hơn  
- Maven để quản lý phụ thuộc  
- Một IDE như IntelliJ IDEA hoặc Eclipse  

## Cài đặt GroupDocs.Watermark cho Java

Thêm thư viện vào `pom.xml` Maven của bạn:

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

Bạn cũng có thể tải xuống các binary mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Các bước lấy giấy phép

- **Dùng thử miễn phí:** Tải gói dùng thử để đánh giá API.  
- **Giấy phép tạm thời:** Yêu cầu một khóa tạm thời để thử nghiệm kéo dài.  
- **Mua:** Nhận giấy phép đầy đủ để sử dụng trong môi trường sản xuất.  

### Khởi tạo và Cấu hình Cơ bản

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Cách Trích Xuất Các Hình Dạng – Hướng Dẫn Triển Khai

### Tải và Lấy Nội Dung

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Duyệt Qua Các Hình Dạng

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Cách trích xuất hình ảnh từ hình dạng

Lệnh `shape.getImage()` trả về một đối tượng chứa bitmap thô, kích thước của nó và mảng byte. Sử dụng các thuộc tính được hiển thị ở trên để lưu hình ảnh vào đĩa hoặc đưa nó vào một pipeline xử lý khác.

### Cách trích xuất văn bản từ hình dạng

Phương thức `shape.getText()` trả về văn bản thuần bên trong hình dạng. Nếu hình dạng không chứa văn bản, phương thức sẽ trả về `null`. Vòng lặp mẫu đã in ra văn bản, và bạn có thể thao tác thêm—ví dụ, xây dựng một chỉ mục của tất cả nhãn hình dạng.

## Mẹo Khắc Phục Sự Cố

- Xác minh đường dẫn tệp và quyền đọc.  
- Đảm bảo bạn đang sử dụng định dạng sơ đồ được hỗ trợ (VSDX, VDX, v.v.).  
- Nếu một hình dạng xuất hiện mà không có dữ liệu mong đợi, kiểm tra ghi chú phát hành của thư viện để biết các quirks đặc thù của định dạng.  

## Ứng Dụng Thực Tiễn

1. **Phân tích sơ đồ:** Tự động kiểm tra sơ đồ để tuân thủ bằng cách kiểm tra kích thước hình dạng hoặc nhãn bị thiếu.  
2. **Trực quan hoá dữ liệu:** Đưa các kích thước đã trích xuất vào bảng điều khiển báo cáo để hiển thị mật độ bố cục.  
3. **Tích hợp CAD:** Kết hợp dữ liệu hình dạng với các API CAD để đồng bộ thông số thiết kế giữa các công cụ.  

## Các Yếu Tố Hiệu Suất

- **Đóng tài nguyên:** Gọi `watermarker.close()` khi hoàn thành để giải phóng tài nguyên gốc.  
- **Quản lý bộ nhớ:** Các sơ đồ lớn có thể tiêu tốn heap đáng kể; giám sát bộ nhớ và tăng `-Xmx` nếu cần.  
- **Xử lý hàng loạt:** Xử lý các tệp theo lô và tái sử dụng một thể hiện `Watermarker` duy nhất khi có thể.  

## Kết luận

Bằng cách làm theo hướng dẫn này, bạn hiện đã biết **cách trích xuất các hình dạng**, cách **trích xuất hình ảnh từ hình dạng**, và cách **trích xuất văn bản từ hình dạng** bằng GroupDocs.Watermark cho Java. Những kỹ thuật này mở ra cánh cửa cho việc phân tích sơ đồ tự động, báo cáo và tích hợp với các hệ thống kỹ thuật khác. Bước tiếp theo, khám phá toàn bộ API bằng cách xem [tài liệu](https://docs.groupdocs.com/watermark/java/) và thử kết hợp việc trích xuất hình dạng với logic kinh doanh tùy chỉnh.

## Phần Câu Hỏi Thường Gặp

1. **GroupDocs.Watermark là gì?**  
   - Một thư viện Java toàn diện được thiết kế để đánh dấu bản quyền và trích xuất thông tin từ nhiều định dạng tài liệu, bao gồm cả sơ đồ.  

2. **Tôi có thể sử dụng thư viện này để xử lý mọi loại tệp sơ đồ không?**  
   - Có, nhưng hãy đảm bảo định dạng tệp được hỗ trợ bằng cách kiểm tra [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Làm thế nào để trích xuất kích thước và vị trí của hình dạng từ một sơ đồ bằng Java và GroupDocs.Watermark?**  
   - Tải sơ đồ, truy cập `DiagramContent`, sau đó duyệt các hình dạng để lấy các thuộc tính như chiều rộng, chiều cao, X và Y.  

4. **GroupDocs.Watermark có thể trích xuất hình ảnh nhúng trong các hình dạng sơ đồ bằng Java không?**  
   - Có, nó cung cấp các phương thức để truy cập dữ liệu hình ảnh trong các hình dạng, bao gồm kích thước và dữ liệu pixel, hữu ích cho việc phân tích hoặc chỉnh sửa.  

5. **Các yêu cầu trước khi trích xuất thông tin hình dạng sơ đồ trong Java là gì?**  
   - Java JDK 8+, cấu hình Maven, thư viện GroupDocs.Watermark (24.11+), và kiến thức Java cơ bản là cần thiết cho việc triển khai.  

---

**Cập nhật lần cuối:** 2026-02-13  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs