---
date: '2026-04-04'
description: Học cách trích xuất tệp đính kèm Excel và trích xuất các đối tượng nhúng
  bằng GroupDocs.Watermark cho Java. Tối ưu hoá việc quản lý tài liệu của bạn một
  cách hiệu quả.
keywords:
- how to extract excel
- extract embedded objects
- java attachment extraction
title: Cách trích xuất tệp đính kèm Excel bằng GroupDocs Watermark Java
type: docs
url: /vi/java/email-document-watermarking/extract-attachments-excel-groupdocs-watermark-java/
weight: 1
---

# Cách Trích Xuất Tệp Đính Kèm Excel bằng GroupDocs.Watermark Java

Việc trích xuất các tệp được nhúng từ một sổ làm việc Excel có thể là một nút thắt thực sự khi bạn tự động hoá các pipeline dữ liệu hoặc xây dựng các giải pháp lưu trữ. Trong hướng dẫn này, bạn sẽ học **cách trích xuất Excel** các tệp đính kèm một cách nhanh chóng và đáng tin cậy bằng thư viện GroupDocs.Watermark cho Java. Chúng tôi sẽ hướng dẫn qua việc thiết lập môi trường, xem xét mã nguồn, và các mẹo thực tiễn để bạn có thể tích hợp khả năng này vào ứng dụng của mình ngay lập tức.

## Câu trả lời nhanh
- **Thư viện nào xử lý tệp đính kèm Excel?** GroupDocs.Watermark for Java  
- **Phương thức chính được sử dụng?** `Watermarker` với `SpreadsheetLoadOptions`  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho phát triển; cần giấy phép đầy đủ cho môi trường sản xuất  
- **Phiên bản Java được hỗ trợ?** Java 8 hoặc cao hơn  
- **Tôi có thể trích xuất hình ảnh xem trước không?** Có, thông qua `getPreviewImageContent()`  

## “Cách trích xuất excel” là gì trong bối cảnh tự động hoá tài liệu?
Khi chúng ta nói *cách trích xuất excel* chúng ta đề cập đến việc lập trình để lấy ra bất kỳ đối tượng nhúng nào—như PDF, hình ảnh, hoặc các bảng tính khác—được lưu trong tệp `.xlsx`. Điều này cho phép các quy trình hạ nguồn như phân tích dữ liệu, lưu trữ tuân thủ, hoặc tạo báo cáo động mà không cần sự tương tác thủ công của người dùng.

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?
GroupDocs.Watermark cung cấp một API cấp cao trừu tượng hoá việc xử lý OpenXML cấp thấp, mang lại cho bạn:
- **Mô hình đối tượng đơn giản** cho các worksheet, tệp đính kèm và siêu dữ liệu  
- **Trích xuất xem trước tích hợp** để kiểm tra nhanh bằng hình ảnh  
- **Giấy phép mạnh mẽ** mở rộng từ bản dùng thử đến doanh nghiệp  

## Yêu cầu trước
- **Java Development Kit (JDK) 8+** – đã cài đặt và thêm vào `PATH` của bạn  
- **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo nào bạn thích  
- **Maven** – để quản lý phụ thuộc (hoặc bạn có thể tải JAR về)  

### Thư viện và phụ thuộc cần thiết
Bạn sẽ cần thư viện GroupDocs.Watermark cho Java. Hướng dẫn này sử dụng phiên bản 24.11, bạn có thể lấy từ Maven Central hoặc kho chính thức của GroupDocs.

### Liên kết tải xuống trực tiếp (giữ nguyên)
Hoặc tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Cài đặt GroupDocs.Watermark cho Java

### Cấu hình Maven
Thêm cấu hình sau vào tệp `pom.xml` của bạn:

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

### Các bước lấy giấy phép
- **Bản dùng thử miễn phí:** Bắt đầu với bản dùng thử để khám phá các khả năng của thư viện.  
- **Giấy phép tạm thời:** Nhận giấy phép tạm thời cho việc phát triển kéo dài.  
- **Mua:** Nâng cấp lên giấy phép đầy đủ cho triển khai sản xuất.  

### Khởi tạo và thiết lập cơ bản
```java
import com.groupdocs.watermark.Watermarker;

public class DocumentSetup {
    public static void main(String[] args) {
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        Watermarker watermarker = new Watermarker(filePath);
        
        // Your code to manipulate the document goes here
        
        watermarker.close();
    }
}
```

## Cách Trích Xuất Tệp Đính Kèm Excel bằng GroupDocs.Watermark

### Tải và chuẩn bị bảng tính
**Tổng quan:** Tải sổ làm việc của bạn bằng `SpreadsheetLoadOptions` để kiểm soát việc sử dụng bộ nhớ và hành vi tải.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.Watermarker;

public class ExtractAttachments {
    public static void extract() {
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### Truy cập nội dung bảng tính
**Tổng quan:** Lấy mô hình nội dung cấp cao cho phép bạn truy cập vào các worksheet và các đối tượng nhúng.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;

// Get the content of the spreadsheet.
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```

### Duyệt qua các Worksheet
**Tổng quan:** Lặp qua từng worksheet và sau đó từng tệp đính kèm để xử lý chúng riêng lẻ.

```java
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
```

### Trích xuất chi tiết tệp đính kèm
**Tổng quan:** Đối với mỗi tệp đính kèm, lấy ra siêu dữ liệu hữu ích như văn bản thay thế, vị trí, kích thước và byte dữ liệu thực tế của tệp.

```java
import com.groupdocs.watermark.contents.SpreadsheetAttachment;

// Display alternative text and frame details of each attachment.
System.out.println("Alternative text: " + attachment.getAlternativeText());
System.out.println("Attachment frame x-coordinate: " + attachment.getX());
System.out.println("Attachment frame y-coordinate: " + attachment.getY());
System.out.println("Attachment frame width: " + attachment.getWidth());
System.out.println("Attachment frame height: " + attachment.getHeight());

// Check if a preview image is available and display its size.
int imageSize = (attachment.getPreviewImageContent() != null) ? attachment.getPreviewImageContent().length : 0;
System.out.println("Preview image size: " + imageSize);

if (attachment.isLink()) {
    System.out.println("Full path to the attached file: " + attachment.getSourceFullName());
} else {
    System.out.println("File type: " + attachment.getDocumentInfo().getFileType());
    System.out.println("Name of the source file: " + attachment.getSourceFullName());
    System.out.println("File size: " + attachment.getContent().length);
}
```

### Đóng tài nguyên
**Tổng quan:** Luôn đóng đối tượng `Watermarker` để giải phóng tài nguyên gốc và tránh rò rỉ bộ nhớ.

```java
// Close the Watermarker to release resources.
watermarker.close();
```

## Ứng dụng thực tiễn (Tại sao điều này quan trọng)

1. **Hợp nhất dữ liệu tự động** – Lấy mọi PDF hoặc hình ảnh đính kèm từ một loạt báo cáo để thực hiện một lần phân tích duy nhất.  
2. **Lưu trữ tuân thủ** – Lưu các tệp đã trích xuất cùng với sổ làm việc gốc để đáp ứng yêu cầu kiểm toán.  
3. **Tạo báo cáo động** – Tái sử dụng các biểu đồ hoặc tài liệu nhúng như các tài sản riêng trong công cụ báo cáo tùy chỉnh.  

## Các cân nhắc về hiệu năng
- **Quản lý bộ nhớ:** Đóng `Watermarker` ngay khi bạn hoàn thành xử lý mỗi tệp.  
- **Xử lý batch:** Xử lý các sổ làm việc theo từng khối (ví dụ, 10‑20 tệp mỗi luồng) để duy trì mức sử dụng CPU ổn định.  
- **Tinh chỉnh tùy chọn tải:** Sử dụng `SpreadsheetLoadOptions` để giới hạn số hàng/cột được tải khi bạn chỉ cần các tệp đính kèm.  

## Các vấn đề thường gặp và giải pháp
| Issue | Solution |
|-------|----------|
| **`NullPointerException` trên `getPreviewImageContent()`** | Xác minh rằng tệp đính kèm thực sự chứa bản xem trước; không phải tất cả các loại tệp đều tạo ra bản xem trước. |
| **Các tệp Excel lớn gây OutOfMemoryError** | Tăng kích thước heap JVM (`-Xmx2g`) hoặc xử lý các tệp tuần tự với việc gọi `close()` rõ ràng sau mỗi tệp. |
| **LicenseException trong môi trường sản xuất** | Đảm bảo bạn đã áp dụng tệp giấy phép đầy đủ hợp lệ bằng `License.setLicense("path/to/license.json")`. |

## Câu hỏi thường gặp

**Q: Tôi có thể trích xuất tệp đính kèm từ các tệp Excel được bảo mật bằng mật khẩu không?**  
A: Có. Tải sổ làm việc bằng `SpreadsheetLoadOptions` bao gồm mật khẩu, sau đó tiếp tục như đã trình bày.

**Q: API có hỗ trợ trích xuất biểu đồ nhúng dưới dạng hình ảnh không?**  
A: Biểu đồ được coi là các đối tượng riêng; bạn có thể lấy hình ảnh xem trước của chúng qua `getPreviewImageContent()`.

**Q: Những định dạng tệp nào có thể được trích xuất dưới dạng tệp đính kèm?**  
A: Bất kỳ loại tệp nào được nhúng trong sổ làm việc—PDF, DOCX, PNG, JPG, v.v.—có thể truy cập qua API `SpreadsheetAttachment`.

**Q: Có cách nào để tự động lưu các tệp đã trích xuất không?**  
A: Bạn có thể ghi `attachment.getContent()` vào một `FileOutputStream` mà bạn chọn. Hướng dẫn này tập trung vào việc in siêu dữ liệu, nhưng cùng một mảng byte có thể được lưu lại.

**Q: Tôi có cần xử lý công thức Excel khi trích xuất tệp đính kèm không?**  
A: Không. Các tệp đính kèm độc lập với công thức ô; chúng được lưu dưới dạng đối tượng OLE trong sổ làm việc.

## Kết luận
Bạn đã có một hướng dẫn đầy đủ, sẵn sàng cho môi trường sản xuất về **cách trích xuất Excel** các tệp đính kèm bằng GroupDocs.Watermark cho Java. Bằng cách tích hợp các bước này vào các pipeline tự động của bạn, bạn có thể tối ưu hoá việc thu thập dữ liệu, cải thiện tuân thủ và mở ra các khả năng báo cáo mới. Khám phá các tính năng khác của thư viện—như đánh dấu watermark hoặc xóa nhạy cảm—để nâng cao quy trình xử lý tài liệu của bạn hơn nữa.

---

**Cập nhật lần cuối:** 2026-04-04  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs