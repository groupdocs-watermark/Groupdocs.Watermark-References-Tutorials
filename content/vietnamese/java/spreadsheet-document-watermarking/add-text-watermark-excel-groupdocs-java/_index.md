---
date: '2026-03-20'
description: Tìm hiểu cách thêm watermark vào bảng tính Excel bằng GroupDocs.Watermark
  cho Java, bao gồm các kỹ thuật thêm watermark văn bản vào Excel và thêm watermark
  vào Excel bằng Java.
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: Cách thêm watermark vào Excel bằng GroupDocs.Watermark Java
type: docs
url: /vi/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# Cách Thêm Đánh Dấu Nước vào Bảng Tính Excel Sử Dụng GroupDocs.Watermark cho Java

Thêm khả năng **thêm đánh dấu nước** vào các tệp Excel là cách thực tiễn để bảo vệ dữ liệu nhạy cảm và khẳng định quyền sở hữu. Trong hướng dẫn từng bước này, bạn sẽ học cách thêm đánh dấu nước vào bảng tính Excel, tùy chỉnh giao diện của nó và đặt nó vào phần đầu trang hoặc chân trang — tất cả đều thực hiện bằng GroupDocs.Watermark cho Java.

## Trả Lời Nhanh
- **Thư viện cần thiết là gì?** GroupDocs.Watermark cho Java (phiên bản 24.11 trở lên).  
- **Có thể tùy chỉnh phông chữ và màu sắc không?** Có, sử dụng các lớp `Font` và `Color`.  
- **Đánh dấu nước sẽ xuất hiện ở đâu?** Trong phần đầu trang hoặc chân trang của worksheet đã chọn.  
- **Cần giấy phép cho môi trường sản xuất không?** Cần giấy phép GroupDocs hợp lệ cho việc sử dụng không phải thử nghiệm.  
- **Có hoạt động tốt với các workbook lớn không?** Có, nhưng hãy đóng đối tượng `Watermarker` để giải phóng tài nguyên.

## Giới Thiệu

Bạn có muốn tăng cường bảo mật cho các bảng tính Excel bằng cách thêm đánh dấu nước dạng văn bản không? Dù là để bảo vệ dữ liệu bí mật hay khẳng định quyền sở hữu, việc nhúng đánh dấu nước vào phần đầu hoặc chân trang của bảng tính có thể vô cùng hữu ích. Trong tutorial này, chúng tôi sẽ hướng dẫn bạn cách triển khai tính năng này bằng GroupDocs.Watermark cho Java.

**Bạn sẽ học được**
- Cách thêm đánh dấu nước dạng văn bản vào bảng tính Excel  
- Cấu hình đánh dấu nước với phông chữ và màu sắc tùy chỉnh  
- Đặt căn chỉnh đầu/trang hoặc chân/trang trong tài liệu  

Với những kỹ năng này, bạn sẽ sẵn sàng bảo vệ các bảng tính của mình một cách hiệu quả. Bây giờ, hãy cùng khám phá các yêu cầu tiên quyết để bắt đầu.

## “how to add watermark” trong Excel là gì?

Đánh dấu nước là một đoạn văn bản hoặc hình ảnh mờ, bán trong suốt xuất hiện phía sau (hoặc phía trước) nội dung chính. Trong Excel, đánh dấu nước thường được đặt trong khu vực đầu trang hoặc chân trang để chúng xuất hiện trên mỗi trang in mà không làm cản trở dữ liệu ô.

## Tại sao nên dùng GroupDocs.Watermark cho Java?

- **Đa nền tảng**: Hoạt động trên mọi hệ điều hành hỗ trợ Java.  
- **Kiểm soát đầy đủ**: Tùy chỉnh phông chữ, kích thước, màu sắc và căn chỉnh.  
- **Tối ưu hiệu năng**: Xử lý hiệu quả các workbook lớn.  

## Yêu Cầu Tiên Quyết

- **GroupDocs.Watermark cho Java** (phiên bản 24.11 trở lên)  
- **Java Development Kit (JDK)** đã được cài đặt và cấu hình  
- IDE như IntelliJ IDEA hoặc Eclipse  
- Maven (nếu bạn muốn quản lý phụ thuộc)  

### Thư Viện Cần Thiết

- **GroupDocs.Watermark cho Java** – cung cấp API đánh dấu nước.  

### Kiến Thức Tiên Quyết

- Lập trình Java cơ bản  
- Quen thuộc với Maven hoặc cách xử lý JAR thủ công  

## Cài Đặt GroupDocs.Watermark cho Java

Bạn có thể cài đặt thư viện qua Maven hoặc tải JAR trực tiếp.

**Cài Đặt qua Maven**

Thêm cấu hình sau vào file `pom.xml` của bạn:

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

**Tải Trực Tiếp**  
Ngoài ra, bạn có thể tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Mua Giấy Phép
- **Dùng Thử Miễn Phí** – khám phá API không tốn phí.  
- **Giấy Phép Tạm Thời** – thời gian đánh giá kéo dài.  
- **Mua Bản Quyền** – đầy đủ tính năng, không giới hạn sử dụng.

Để khởi tạo GroupDocs.Watermark, thêm câu lệnh import:

```java
import com.groupdocs.watermark.Watermarker;
```

## Cách Thêm Đánh Dấu Nước vào Bảng Tính Excel

Dưới đây là đoạn mã hoàn chỉnh, có thể chạy được, được chia thành các bước rõ ràng. Mỗi bước đi kèm với một giải thích ngắn gọn trước khối mã, để bạn không bao giờ thấy đoạn mã mà không có ngữ cảnh.

### Bước 1: Tải Bảng Tính

Đầu tiên, tải workbook với các tùy chọn tải phù hợp.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**Giải thích**: Đoạn mã này tạo một thể hiện `Watermarker` gắn với tệp Excel của bạn, sẵn sàng cho các thao tác đánh dấu nước.

### Bước 2: Tạo Đánh Dấu Nước Dạng Văn Bản

Cấu hình giao diện hiển thị của đánh dấu nước.

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**Giải thích**: Chúng ta đặt nội dung đánh dấu nước, chọn phông chữ **Segoe UI** in đậm, và áp dụng màu nền và màu chữ tương phản.

### Bước 3: Cấu Hình Vị Trí Đánh Dấu Nước

Xác định worksheet nào và phần nào của trang (đầu/trang hoặc chân/trang) sẽ nhận được đánh dấu nước.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**Giải thích**: Đối tượng `SpreadsheetWatermarkHeaderFooterOptions` cho API biết áp dụng đánh dấu nước vào đầu/trang hoặc chân/trang của sheet đầu tiên.

### Bước 4: Thêm Đánh Dấu Nước và Lưu

Áp dụng đánh dấu nước và ghi kết quả vào tệp mới.

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**Giải thích**: Phương thức `add` chèn đánh dấu nước, `save` ghi workbook đã chỉnh sửa, và `close` giải phóng tài nguyên.

## Thêm Đánh Dấu Nước Văn Bản cho Excel – Mẹo Nâng Cao

- **Nhiều Worksheet**: Duyệt qua các chỉ số worksheet và gọi `options.setWorksheetIndex(i)` cho mỗi worksheet.  
- **Văn Bản Động**: Lấy nội dung đánh dấu nước từ cơ sở dữ liệu hoặc tệp cấu hình để cá nhân hoá từng tài liệu.  
- **Kiểm Soát Độ Mờ**: Dùng `watermark.setOpacity(0.5)` để làm cho đánh dấu nước nhẹ nhàng hơn.  

## Các Vấn Đề Thường Gặp và Giải Pháp

| Vấn Đề | Giải Pháp |
|-------|----------|
| **File Không Tìm Thấy** | Kiểm tra lại các chuỗi đường dẫn (`YOUR_DOCUMENT_DIRECTORY/...`) xem có đúng không và dùng đường dẫn tuyệt đối trong quá trình thử nghiệm. |
| **Không Tìm Thấy Giấy Phép** | Đặt tệp `GroupDocs.Watermark.lic` ở thư mục gốc dự án hoặc thiết lập giấy phép bằng mã: `License license = new License(); license.setLicense("path/to/license.lic");`. |
| **Định Dạng Không Hỗ Trợ** | Đảm bảo workbook được lưu dưới dạng `.xlsx` hoặc `.xls`. Các định dạng cũ hơn có thể cần chuyển đổi trước. |
| **Độ Trễ Khi Xử Lý Tập Tin Lớn** | Xử lý một worksheet mỗi lần và gọi `watermarker.close()` ngay khi hoàn thành mỗi tệp. |

## Ứng Dụng Thực Tiễn

1. **Bảo Vệ Dữ Liệu Bảo Mật** – Ngăn chặn sao chép trái phép bằng cách đánh dấu mỗi trang in một cách rõ ràng.  
2. **Khẳng Định Quyền Sở Hữu** – Nhúng tên công ty hoặc logo dưới dạng đánh dấu nước để chứng minh nguồn gốc tài liệu.  
3. **Theo Dõi Tài Liệu** – Bao gồm các định danh duy nhất trong đánh dấu nước để truy vết đường truyền tài liệu.  

## Lưu Ý Về Hiệu Năng

- Giảm thiểu số lượng đánh dấu nước trong mỗi phiên làm việc.  
- Đóng đối tượng `Watermarker` ngay sau khi hoàn thành để giải phóng các handle tệp.  
- Đối với workbook rất lớn, cân nhắc tăng kích thước heap JVM (`-Xmx2g`).  

## Câu Hỏi Thường Gặp

**Hỏi: Tôi có thể thay đổi kiểu phông chữ của đánh dấu nước không?**  
Đáp: Có, bạn có thể tùy chỉnh đối tượng `Font` với bất kỳ họ phông chữ nào đã cài đặt, kích thước và `FontStyle` (Bold, Italic, …).

**Hỏi: Có thể thêm đánh dấu nước vào nhiều sheet không?**  
Đáp: Chắc chắn. Duyệt qua các chỉ số worksheet và áp dụng cùng một `SpreadsheetWatermarkHeaderFooterOptions` cho mỗi sheet.

**Hỏi: GroupDocs.Watermark hỗ trợ những định dạng file nào cho Excel?**  
Đáp: Định dạng XLS, XLSX và các định dạng Office Open XML spreadsheet khác đều được hỗ trợ đầy đủ.

**Hỏi: Làm sao xử lý tài liệu rất lớn một cách hiệu quả?**  
Đáp: Xử lý một workbook mỗi lần, đóng `Watermarker` sau khi lưu, và theo dõi việc sử dụng bộ nhớ JVM.

**Hỏi: Có thể gỡ bỏ đánh dấu nước sau này không?**  
Đáp: Việc gỡ bỏ trực tiếp không được cung cấp, nhưng bạn có thể tạo lại file gốc mà không áp dụng đánh dấu nước hoặc giữ một bản sao không có đánh dấu để sử dụng sau này.

## Tài Nguyên

- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)  

---

**Cập Nhật Lần Cuối:** 2026-03-20  
**Đã Kiểm Tra Với:** GroupDocs.Watermark 24.11 cho Java  
**Tác Giả:** GroupDocs  

---