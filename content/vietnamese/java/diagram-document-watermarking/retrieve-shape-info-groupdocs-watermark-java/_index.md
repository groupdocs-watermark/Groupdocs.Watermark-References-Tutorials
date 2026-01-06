---
date: '2025-12-20'
description: Tìm hiểu cách trích xuất thông tin hình dạng bằng Java với GroupDocs.Watermark
  cho Java. Truy xuất kích thước, vị trí và văn bản từ các tệp sơ đồ một cách hiệu
  quả.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 'Trích xuất thông tin hình dạng Java: Sử dụng GroupDocs.Watermark cho sơ đồ'
type: docs
url: /vi/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Trích xuất thông tin hình dạng Java sử dụng GroupDocs.Watermark trong Diagram

Khi bạn cần **extract shape information java** từ các tệp diagram phức tạp, việc thực hiện thủ công nhanh chóng trở nên không thực tế. Hướng dẫn này cho bạn cách sử dụng GroupDocs.Watermark cho Java để lập trình lấy các chi tiết như kích thước, vị trí, góc quay, hình ảnh nhúng và văn bản từ mỗi hình dạng. Khi kết thúc, bạn sẽ có một mẫu rõ ràng, có thể tái sử dụng mà bạn có thể đưa vào bất kỳ dự án Java nào làm việc với các diagram kiểu Visio‑style.

## Giới thiệu

Quản lý các diagram phức tạp thường yêu cầu truy cập thông tin chi tiết về các thành phần của chúng, chẳng hạn như hình dạng và hình ảnh. Nếu bạn đã từng cần lấy dữ liệu như kích thước, vị trí hoặc văn bản liên quan đến các hình dạng trong diagram bằng Java, hướng dẫn này dành cho bạn. Tận dụng sức mạnh của thư viện GroupDocs.Watermark có thể giúp đơn giản hoá quá trình này trong một ứng dụng Java. Trong hướng dẫn này, chúng ta sẽ đi qua cách sử dụng GroupDocs.Watermark để **extract shape information java** từ một tệp diagram.

## Câu trả lời nhanh
- **Thư viện nào nên dùng?** GroupDocs.Watermark cho Java (v24.11+).  
- **Các định dạng tệp nào được hỗ trợ?** Visio (.vsdx, .vsd) và các loại diagram khác được liệt kê trong tài liệu API.  
- **Có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho phát triển; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Có thể lấy dữ liệu hình ảnh từ các hình dạng không?** Có – API cung cấp chiều rộng, chiều cao và dữ liệu byte thô của hình ảnh.  
- **Có bắt buộc dùng Maven không?** Maven là cách được khuyến nghị để quản lý phụ thuộc GroupDocs.Watermark.

## “extract shape information java” là gì?

**extract shape information java** có nghĩa là đọc một tệp diagram một cách lập trình và trích xuất các thuộc tính của từng hình dạng — kích thước, vị trí, góc quay, văn bản và bất kỳ hình ảnh nhúng nào — bằng mã Java. Điều này cho phép tự động hoá phân tích, báo cáo hoặc tích hợp với các hệ thống khác như công cụ CAD hoặc quy trình trực quan hoá dữ liệu.

## Tại sao nên dùng GroupDocs.Watermark cho nhiệm vụ này?

GroupDocs.Watermark cung cấp một lớp trừu tượng cao‑cấp cho các định dạng diagram, xử lý việc phân tích cấp thấp cho bạn. Nó cho phép bạn tập trung vào logic nghiệp vụ thay vì phải làm việc với XML hay các đặc tả nhị phân, và hoạt động nhất quán trên các loại diagram được hỗ trợ.

## Yêu cầu trước

- **GroupDocs.Watermark cho Java** (phiên bản 24.11 trở lên)  
- Java Development Kit (JDK) 8 hoặc cao hơn  
- Maven để quản lý phụ thuộc  
- Một IDE như IntelliJ IDEA hoặc Eclipse  

## Cài đặt GroupDocs.Watermark cho Java

Thêm kho và phụ thuộc vào file `pom.xml` của Maven:

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

Hoặc bạn có thể tải trực tiếp phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Các bước lấy giấy phép
- **Dùng thử miễn phí:** Tải gói dùng thử để kiểm tra thư viện.  
- **Giấy phép tạm thời:** Nhận khóa tạm thời để đánh giá kéo dài.  
- **Mua bản đầy đủ:** Mua giấy phép đầy đủ cho môi trường sản xuất.

### Khởi tạo cơ bản

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Hướng dẫn triển khai

Bây giờ chúng ta sẽ đi qua các bước chính để **extract shape information java** từ một tài liệu diagram.

### Tải và lấy nội dung

#### Tổng quan
Đầu tiên chúng ta tải tệp diagram và lấy một đối tượng `DiagramContent`, đối tượng này cho phép truy cập các trang và hình dạng.

#### Các bước

**Tải tài liệu Diagram**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **Lý do:** Điều này khởi tạo đối tượng `Watermarker`, cho phép truy cập nội dung của tài liệu.

**Truy cập nội dung Diagram**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **Lý do:** Lớp `DiagramContent` cung cấp các phương thức để tương tác với các khía cạnh khác nhau của diagram, chẳng hạn như các trang và hình dạng.

### Duyệt qua các hình dạng

#### Tổng quan
Với `DiagramContent` trong tay, chúng ta lặp qua từng trang và sau đó là từng hình dạng để lấy các thuộc tính cần thiết.

#### Các bước

**Duyệt qua các trang**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **Lý do:** Các diagram được cấu thành từ nhiều trang; chúng ta cần kiểm tra từng trang để lấy các hình dạng.

**Trích xuất thông tin hình dạng**

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

- **Lý do:** Vòng lặp này trích xuất và in ra các thuộc tính của mỗi hình dạng, bao gồm kích thước, vị trí, góc quay và bất kỳ hình ảnh hoặc văn bản nhúng nào. Những thuộc tính này rất quan trọng để hiểu cách các hình dạng được cấu hình trong diagram.

### Mẹo khắc phục sự cố
- Kiểm tra đường dẫn tệp có đúng và trỏ tới một tệp `.vsdx` (hoặc định dạng được hỗ trợ) có thể đọc được.  
- Đảm bảo ứng dụng có quyền đọc tệp diagram.  
- Nếu gặp lỗi “Unsupported format”, xác nhận rằng phiên bản GroupDocs.Watermark của bạn hỗ trợ loại diagram cụ thể đó.

## Ứng dụng thực tiễn

Với khả năng **extract shape information java**, bạn có thể triển khai nhiều kịch bản thực tế:

1. **Phân tích Diagram:** Tự động tạo báo cáo liệt kê kích thước, vị trí và văn bản của mỗi hình dạng — hữu ích cho các cuộc kiểm tra chất lượng.  
2. **Trực quan hoá dữ liệu:** Đưa các chỉ số hình dạng vào bảng điều khiển để hiển thị mật độ bố cục hoặc xác định các yếu tố quá lớn.  
3. **Tích hợp CAD:** Kết nối dữ liệu diagram vào quy trình CAD, cho phép tự động thiết kế lại hoặc các bước xác thực.

## Cân nhắc về hiệu năng

Khi xử lý các diagram lớn, hãy lưu ý các thực hành tốt sau:

- **Đóng tài nguyên kịp thời:** Gọi `watermarker.close()` (hoặc sử dụng try‑with‑resources) để giải phóng bộ nhớ.  
- **Giám sát sử dụng heap:** Các diagram lớn có thể tiêu tốn nhiều bộ nhớ; điều chỉnh heap JVM (`-Xmx`) cho phù hợp.  
- **Xử lý theo lô:** Xử lý các tệp theo lô thay vì tải đồng thời nhiều tệp.

## Kết luận

Sau khi làm theo hướng dẫn này, bạn đã biết cách **extract shape information java** bằng GroupDocs.Watermark cho Java. Bạn có thể lấy kích thước, vị trí, góc quay, hình ảnh nhúng và văn bản từ bất kỳ tệp diagram nào được hỗ trợ, mở ra cơ hội cho việc phân tích tự động, báo cáo và tích hợp với các hệ thống lớn hơn. Sẵn sàng cho bước tiếp theo? Khám phá đầy đủ khả năng của thư viện trong [tài liệu chính thức](https://docs.groupdocs.com/watermark/java/) và thử nghiệm các tính năng như watermarking, redaction, hoặc tùy chỉnh thao tác hình dạng.

## Câu hỏi thường gặp

**Q: GroupDocs.Watermark là gì?**  
A: Một thư viện Java toàn diện được thiết kế để chèn watermark và trích xuất thông tin từ nhiều định dạng tài liệu, bao gồm cả diagram.

**Q: Tôi có thể dùng thư viện này để xử lý mọi loại tệp diagram không?**  
A: Có, nhưng hãy chắc chắn rằng định dạng tệp được liệt kê là được hỗ trợ trong [API Reference](https://reference.groupdocs.com/watermark/java/).

**Q: Làm sao để trích xuất kích thước và vị trí của hình dạng trong diagram bằng Java và GroupDocs.Watermark?**  
A: Tải diagram, lấy `DiagramContent`, sau đó duyệt qua mỗi `DiagramShape` để đọc các thuộc tính như width, height, X và Y.

**Q: GroupDocs.Watermark có thể trích xuất hình ảnh nhúng trong các hình dạng diagram bằng Java không?**  
A: Có, nó cung cấp các phương thức để truy cập dữ liệu hình ảnh trong các hình dạng, bao gồm kích thước và mảng byte thô, bạn có thể dùng để phân tích hoặc chỉnh sửa.

**Q: Những yêu cầu trước nào cần có để trích xuất thông tin hình dạng diagram trong Java?**  
A: Java JDK 8+, cấu hình Maven, thư viện GroupDocs.Watermark (24.11+), và kiến thức cơ bản về lập trình Java.

---

**Cập nhật lần cuối:** 2025-12-20  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs