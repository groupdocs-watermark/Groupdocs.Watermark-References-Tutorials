---
date: '2026-01-23'
description: Tìm hiểu cách đánh dấu bản quyền cho các tệp PDF bằng văn bản và hình
  ảnh sử dụng GroupDocs.Watermark cho Java – hướng dẫn đầy đủ về bảo mật tài liệu
  PDF.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: Cách Thêm Watermark vào PDF bằng GroupDocs.Watermark cho Java
type: docs
url: /vi/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

ánh Dấu Nước PDF Bằng GroupDocs.Watermark cho Java

Trong thế giới kỹ thuật số ngày nay, **cách đánh dấu nước PDF** là một câu hỏi phổ biến đối với bất kỳ ai cần bảo vệ tài sản trí tuệ hoặc thương hiệu. Thêm dấu nước—dù là văn bản hay hình này, bạn sẽ học từng bước cách sử dụng **GroupDocs.Watermark for Java** để thêm cả dấu nước văn bản và hình ảnh vào tài liệu PDF.

## Câu trả lời nhanh
- **Thư viện nào.Watermark for Java.  
- **Tôi có thể thêm cả dấu nước văn bản và hình ảnh không?** Có, API hỗ trợ cả hai loại.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho việc đánh giá; giấy phép trả phí loại bỏ các giới hạn.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 trở lên.  
- **Maven có được hỗ trợ không?** Hoàn toàn—chỉ cần thêm kho và phụ thuộc.

## Đánh dấu nước PDF là gì và tại sao nên sử dụng?
Đánh dấu nước một PDF nhúng một dấu hiệu có thể nhìn thấy hoặc ẩn, xác định quyền sở hữu, tính bảo mật hoặc thương hiệu. Đây là cách nhẹ nhưng mạnh mẽ để ngăn chặn sao chép, chứng minh quyền tác giả và tuân thủ các chính sách công ty.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

1. **Java Development Kit (JDK) 8+** đã được cài đặt trên máy của bạn.  
2. ** Cài đặt môi trường

#### Cấu hình Maven
Thêm kho GroupDocs và phụ thuộc watermark vào tệp `pom.xml` của bạn:

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

#### Tải trực tiếp
Nếu bạn không muốn sử dụng Maven, bạn có thể tải JAR trực tiếp từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Nhận giấy phép
Để bắt đầu với bản dùng thử miễn phí hoặc lấy giấy phép tạm thời, truy cập [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Đối với sử dụng trong môi trường sản xuất, mua gói đăng ký để mở khóa tất cả tính năng.

## Cài đặt GroupDocs.Watermark cho Java

Nhập lớp cốt lõi điều khiển tất cả các thao tác dấu nước:

```java
import com.groupdocs.watermark.Watermarker;
```

Lệnh nhập này cung cấp cho bạn quyền truy cập vào lớp `Watermarker`, là điểm khởi đầu để thêm dấu nước vào bất kỳ loại tài liệu nào được hỗ trợ.

## Triển khai từng bước

Dưới đây chúng tôi chia quá trình thành các phần logic: tạo dấu nước văn bản, tạo dấu nước hình ảnh, và cuối cùng áp dụng chúng lên các hình ảnh trong PDF.

### 1. Khởi tạo Dấu nước Văn bản

**Tại sao lại dùng dấu nước văn bản?** Nó nhẹ, có thể tìm kiếm và hoàn hảo cho việc thêm thông báo bản quyền hoặc tuyên bố bảo mật.

#### 1.1 Tạo đối tượng TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Đặt căn chỉnh
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Xoay dấu nước
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Cấu hình kích thước
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Khởi tạo Dấu nước Hình ảnh

**Khi nào nên dùng dấu nước hình ảnh?** Thích hợp cho việc xây dựng thương hiệu với logo hoặc thêm các mẫu hình ảnh phức tạp.

#### 2.1 Tải tệp hình ảnh
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Đặt căn chỉnh
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Xoay dấu nước hình ảnh
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Cấu hình kích thước
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Thêm Dấu nước vào Hình ảnh trong PDF

Bây giờ chúng ta sẽ kết hợp mọi thứ: mở một PDF, xác định mọi hình ảnh, và áp dụng dấu nước văn bản hoặc hình ảnh dựa trên kích thước.

#### 3.1 Mở tài liệu PDF
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Lấy tất cả hình ảnh
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Áp dụng dấu nước có điều kiện
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 Giải phóng tài nguyên hình ảnh
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Lưu PDF đã chỉnh sửa
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Dọn dẹp
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Ứng dụng thực tế của Đánh dấu nước PDF

| Trường hợp sử dụng | Cách Dấu nước Giúp |
|--------------------|--------------------|
| **Bảo mật tài liệu** | Đánh dấu các tệp tin bí mật, **Bảo vệ thương hiệu** | Nhúng logo vào PDF marketing, chéo (`/`) trên Linux/macOS để để ngăn lỗi OutOfMemory.  
- **Giới hạn giấy phép:** Phiên bản dùng thử có thể giới hạn số giới hạn.  
- **Nhầm lẫn về xoay:** Nhớ rằng `setRotateAngle` nhận giá trị độ; giá trị âm sẽ xoay ngược chiều kim đồng hồ.  

## Câu hỏi thường gặp

**Hỏi: Tôi có thể đánh dấu nước PDF có mật khẩu không?**  
**Đáp:** Có. Mở tài liệu bằng mật khẩu sử dụng hàm tạo `Watermarker` chấp nhận một chuỗi mật khẩu.

**Hỏi: Thư viện có hỗ trợ các định dạng khác như DOCX hoặc PPTX không?**  
**Đáp:** Chắc chắn của dấu nước?**  
**Đáp:** Sử dụng `setOpacity(float opacity)` trên đối tượng dấu nước (giá trị từ 0.0 đến 1.0).

**Hỏi: Có thể thêm dấu nước chỉ vào trang đầu tiên không?**  
**Đáp:** Lấy bộ sưu tập trang bằng `watermarker.getPages()` và áp dụng dấu nước vào chỉ mục trang mong muốn.

**Hỏi: Nếu tôi cần đánh dấu nước một PDF lưu trong bucket đám mây thì sao?**  
**Đáp:** Tải PDF vào một `InputStream` và truyền nó vào hàm tạo `Watermarker`; sau khi xử lý, ghi luồng đầu ra trở lại đám mây.

## Kết luận

Bây giờ bạn đã có một phương pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **cách đánh dấu nước PDF** bằng GroupDocs.Watermark cho Java. Bằng cách kết hợp thủ. Khám phá các tính năng khác của thư viện—như loại bỏ dấu nước hoặc xử lý hàng loạt—đ