---
date: '2026-03-22'
description: Tìm hiểu cách tạo watermark cho tệp Excel bằng cách thêm watermark văn
  bản sử dụng GroupDocs.Watermark cho Java. Bảo vệ bảng tính của bạn và tăng cường
  nhận diện thương hiệu.
keywords:
- text watermark Excel
- GroupDocs.Watermark Java
- Excel document security
title: Cách Đánh Dấu Nước Văn Bản lên Các Trang Excel bằng GroupDocs.Watermark cho
  Java
type: docs
url: /vi/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-watermark-java/
weight: 1
---

# Cách Thêm Đánh Dấu Nước Văn Bản Văn Bản Excel Bằng Văn Bản Sử Dụng GroupDocs.Watermark cho Java

Khi bạn cần **cách đánh dấu nước Excel** cho các workbook—đặc biệt là những file chứa dữ liệu nhạy cảm—việc thêm một dấu nước văn bản rõ ràng, chuyên nghiệp là một trong những cách hiệu quả nhất để bảo vệ nội dung và củng cố nhận diện thương hiệu. Trong hướng dẫn này, chúng tôi sẽ trình bày chi tiết các bước **thêm dấu nước văn bản Excel** bằng thư viện GroupDocs.Watermark cho Java, bao gồm mọi thứ từ thiết lập dự án đến lưu workbook đã được bảo vệ cuối cùng.

## Câu trả lời nhanh
- **Nên dùng thư viện nào?** GroupDocs.Watermark cho Java.  
- **Có thể thêm dấu nước văn bản cho mọi sheet không?** Có – lặp qua từng worksheet và áp dụng cùng một dấu nước.  
- **Cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép vĩnh viễn cần cho môi trường sản xuất.  
- **Phiên bản Java nào được hỗ trợ?** JDK 8 hoặc mới hơn.  
- **Dấu nước có ảnh hưởng tới dữ liệu ô không?** Không, nó chỉ phủ lên các hình ảnh trong worksheet.

## Đánh dấu nước Excel là gì?
Đánh dấu nước Excel có nghĩa là nhúng một dấu nhận dạng có thể nhìn thấy—văn bản hoặc hình ảnh—trực tiếp lên các thành phần hiển thị của worksheet (như hình ảnh) để bất kỳ ai mở file đều thấy thông báo sở hữu hoặc bảo mật. Kỹ thuật này giúp ngăn ngừa việc phân phối trái phép và tạo vẻ chuyên nghiệp cho báo cáo của bạn.

## Tại sao nên thêm dấu nước văn bản Excel bằng Java?
- **Bảo mật** – Rõ ràng chỉ ra thông tin bí mật hoặc sở hữu.  
- **Nhất quán thương hiệu** – Củng cố nhận diện thương hiệu công ty trên mọi bảng tính được chia sẻ.  
- **Tự động hoá** – Java cho phép bạn nhúng dấu nước một cách lập trình, tiết kiệm thời gian chỉnh sửa thủ công.  
- **Hỗ trợ đa định dạng** – Hoạt động với cả file `.xlsx` và file legacy `.xls`.

## Yêu cầu trước
- **Java Development Kit (JDK)** 8 hoặc mới hơn.  
- **Maven** để quản lý phụ thuộc.  
- Kiến thức cơ bản về cú pháp Java và các khái niệm hướng đối tượng.

## Cài đặt GroupDocs.Watermark cho Java
Để bắt đầu, thêm phụ thuộc GroupDocs.Watermark vào dự án Maven của bạn.

### Sử dụng Maven
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

**Mua giấy phép**
- **Bản dùng thử** – Khám phá mọi tính năng mà không tốn phí.  
- **Giấy phép tạm thời** – Dùng cho việc thử nghiệm ngắn hạn.  
- **Mua bản quyền** – Mở khóa đầy đủ khả năng sản xuất.

### Khởi tạo cơ bản
```java
import com.groupdocs.watermark.Watermarker;
// Initialize watermarker instance for your document
Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx");
```

## Hướng dẫn triển khai

### Tính năng 1: Tạo dấu nước văn bản và cấu hình các thuộc tính
Việc tạo và tùy chỉnh dấu nước bao gồm việc đặt văn bản, phông chữ, căn chỉnh, góc xoay và tỷ lệ.  

#### Tổng quan từng bước
**Xác định Dấu Nước của Bạn**
```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a new TextWatermark object
text watermark = new TextWatermark("Protected image", new Font("Arial", 8));

// Configure the watermark properties
text watermark.setHorizontalAlignment(HorizontalAlignment.Center);
text watermark.setVerticalAlignment(VerticalAlignment.Center);
text watermark.setRotateAngle(45); // Set rotation angle
text watermark.setSizingType(SizingType.ScaleToParentDimensions);
text watermark.setScaleFactor(1); // Maintain original size scale factor
```
- **Văn bản và Phông chữ** – Chọn thông điệp rõ ràng và phông chữ dễ đọc.  
- **Căn chỉnh** – Căn giữa thường phù hợp với hầu hết các hình ảnh.  
- **Xoay & Tỷ lệ** – Góc nghiêng 45° giúp dấu nước nổi bật mà không che khuất hình ảnh.

### Tính năng 2: Tải tài liệu bảng tính để đánh dấu nước
Tải workbook với các tùy chọn phù hợp để GroupDocs có thể truy cập các hình ảnh bên trong.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
// Load your Excel spreadsheet
documentLoadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", documentLoadOptions);
```

### Tính năng 3: Thêm dấu nước văn bản vào hình ảnh trong một Worksheet
Lặp qua các hình ảnh trên worksheet đầu tiên và áp dụng dấu nước đã cấu hình.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.WatermarkableImageCollection;

// Access content from your loaded document
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
WatermarkableImageCollection images = content.getWorksheets().get_Item(0).findImages();

for (com.groupdocs.watermark.contents.WatermarkableImage image : images) {
    // Add the configured watermark to each image in the worksheet
    image.add(watermark);
}
```

### Tính năng 4: Lưu và đóng tài liệu bảng tính đã được đánh dấu nước
Ghi lại các thay đổi vào một file mới và giải phóng tài nguyên.

```java
// Save the changes to a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx");
// Close the watermarker instance to free resources
watermarker.close();
```

## Ứng dụng thực tiễn
- **Bảo mật tài liệu** – Bảo vệ các mô hình tài chính hoặc dữ liệu nhân sự nhạy cảm.  
- **Thương hiệu** – Chèn khẩu hiệu công ty hoặc thông báo pháp lý trên mọi báo cáo được chia sẻ.  
- **Bảo vệ bản quyền** – Ngăn chặn sao chép bằng cách đánh dấu mỗi hình ảnh xuất ra.

## Các lưu ý về hiệu suất
- Giữ GroupDocs.Watermark luôn cập nhật để tận dụng các cải tiến về hiệu suất mới nhất.  
- Giải phóng nhanh đối tượng `Watermarker` (`close()`) để giải bộ nhớ.  
- Đối với workbook rất lớn, xử lý các worksheet theo lô để tránh tiêu thụ bộ nhớ quá mức.

## Các vấn đề thường gặp và giải pháp
| Vấn đề | Giải pháp |
|-------|----------|
| Dấu nước không hiển thị | Kiểm tra worksheet có thực sự chứa hình ảnh; API chỉ đánh dấu nước trên hình ảnh, không phải trên ô. |
| Dấu nước lệch | Điều chỉnh `HorizontalAlignment` / `VerticalAlignment` hoặc thay đổi `RotateAngle`. |
| Lỗi hết bộ nhớ khi xử lý file lớn | Tăng kích thước heap JVM (`-Xmx`) hoặc xử lý từng worksheet riêng biệt. |
| Lỗi giấy phép | Đảm bảo file giấy phép dùng thử hoặc vĩnh viễn được tham chiếu đúng trong dự án. |

## Câu hỏi thường gặp

**H: Có thể dùng trên mọi phiên bản Excel không?**  
Đ: Có, GroupDocs hỗ trợ cả định dạng `.xlsx` và `.xls`.

**H: Nếu dấu nước không xuất hiện đúng cách thì sao?**  
Đ: Kiểm tra lại cài đặt căn chỉnh và đảm bảo kích thước hình ảnh phù hợp với hệ số tỷ lệ đã chọn.

**H: Làm sao để tùy chỉnh kiểu phông chữ sâu hơn?**  
Đ: Sử dụng lớp `Font` để đặt in đậm, nghiêng, màu sắc hoặc các thuộc tính typographic khác.

**H: Có thể thêm dấu nước cho tất cả các sheet trong một workbook không?**  
Đ: Chắc chắn—lặp qua `content.getWorksheets()` và áp dụng logic `image.add(watermark)` cho mỗi sheet.

**H: Làm sao xử lý các file Excel lớn một cách hiệu quả?**  
Đ: Xử lý các worksheet theo từng phần, đóng mỗi `Watermarker` sau khi lưu, và cân nhắc tăng kích thước heap JVM.

## Tài nguyên
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/) 

Bằng cách tích hợp các bước này vào dự án Java của bạn, bạn có thể **java add watermark excel** file nhanh chóng, đảm bảo cả bảo mật và tính nhất quán thương hiệu.

---

**Cập nhật lần cuối:** 2026-03-22  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs  

---