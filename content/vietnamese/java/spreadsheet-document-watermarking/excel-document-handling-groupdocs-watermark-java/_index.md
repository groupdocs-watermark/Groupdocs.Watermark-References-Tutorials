---
date: '2026-04-01'
description: Tìm hiểu cách thêm watermark vào tệp Excel bằng GroupDocs.Watermark cho
  Java. Hướng dẫn này bao gồm cài đặt, tải file, trích xuất hình ảnh từ Excel và các
  ứng dụng thực tế.
keywords:
- how to watermark excel
- extract images from excel
- GroupDocs.Watermark Java
- Excel document handling
title: Cách Đánh Dấu Nước cho Tài liệu Excel bằng GroupDocs.Watermark Java
type: docs
url: /vi/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/
weight: 1
---

# Cách Đánh Dấu Nước cho Tài liệu Excel bằng GroupDocs.Watermark Java

## Giới thiệu
Trong hướng dẫn này, bạn sẽ học **cách đánh dấu nước Excel** bằng cách sử dụng thư viện GroupDocs.Watermark cho Java. Quản lý và xử lý tài liệu Excel một cách hiệu quả là rất quan trọng cho các nhiệm vụ như áp dụng dấu nước hoặc trích xuất nội dung. Bài học này trình bày cách tận dụng thư viện **GroupDocs.Watermark** trong Java để tối ưu hoá các quy trình này.

## Câu trả lời nhanh
- **What library can I use to watermark Excel?** Thư viện nào tôi có thể dùng để đánh dấu nước Excel?  
  GroupDocs.Watermark for Java.  
- **Can I extract images from Excel with the same API?** Tôi có thể trích xuất hình ảnh từ Excel bằng cùng API không?  
  Yes – you can read shape images directly.  
- **Do I need a license for production use?** Tôi có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?  
  A commercial license is required; a free trial is available.  
- **Which Java version is supported?** Phiên bản Java nào được hỗ trợ?  
  JDK 8 or higher.  
- **Is Maven the only way to add the library?** Maven có phải là cách duy nhất để thêm thư viện không?  
  No, you can also download the JAR manually.

## “Cách đánh dấu nước Excel” là gì?
Đánh dấu nước Excel có nghĩa là thêm một lớp văn bản, hình ảnh hoặc hình dạng lên một workbook Excel một cách lập trình, sao cho dấu nước xuất hiện trên mỗi sheet được in hoặc xem. Điều này bảo vệ quyền sở hữu trí tuệ và cho biết trạng thái tài liệu (ví dụ: bản nháp, bí mật).

## Tại sao nên sử dụng GroupDocs.Watermark cho Excel?
- **Full‑featured API** – hoạt động với .xlsx, .xls và ngay cả các định dạng cũ hơn.  
- **No Microsoft Office dependency** – chạy trên bất kỳ môi trường Java phía server nào.  
- **Built‑in shape handling** – cho phép bạn đọc, sửa đổi hoặc trích xuất hình ảnh từ các worksheet của Excel.  
- **Performance‑optimized** – xử lý các workbook lớn với mức tiêu thụ bộ nhớ tối thiểu.

## Yêu cầu trước
- JDK 8 hoặc mới hơn đã được cài đặt.  
- Maven (hoặc xử lý JAR thủ công) để quản lý phụ thuộc.  
- Kiến thức cơ bản về lập trình Java.  

### Thư viện và phụ thuộc cần thiết
Bao gồm GroupDocs.Watermark như một phụ thuộc trong dự án của bạn. Bạn có thể thêm nó qua Maven hoặc tải trực tiếp:

**Maven**  
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
**Tải trực tiếp**  
Alternatively, download the latest version from [Phiên bản GroupDocs.Watermark cho Java](https://releases.groupdocs.com/watermark/java/).

### Yêu cầu thiết lập môi trường
- Đảm bảo JDK 8 hoặc cao hơn đã được cài đặt và cấu hình.  
- Maven nên được thiết lập nếu bạn muốn quản lý phụ thuộc.

### Kiến thức tiên quyết
- Kiến thức cơ bản về lập trình Java.  
- Quen thuộc với việc xử lý tệp trong Java.

## Cài đặt GroupDocs.Watermark cho Java
Để bắt đầu, bạn phải cài đặt thư viện qua Maven hoặc tải trực tiếp từ trang chính thức. GroupDocs cung cấp phiên bản dùng thử miễn phí để thử nghiệm các tính năng, và giấy phép có sẵn cho việc sử dụng lâu dài:

- **Free Trial** – khả năng hạn chế, phù hợp cho việc đánh giá.  
- **Temporary License** – mở khóa tất cả tính năng trong một thời gian ngắn.  
- **Purchase License** – cần thiết cho triển khai thương mại.

Sau khi cài đặt, khởi tạo nó như sau để làm việc với tài liệu Excel:

## Cách Đánh Dấu Nước Excel
Phần này hướng dẫn cách tải một bảng tính, trích xuất hình ảnh (hoặc bất kỳ hình dạng nào), và chuẩn bị cho việc đánh dấu nước.

### Tính năng 1: Tải và Truy cập Nội dung Bảng tính

#### Bước 1: Định nghĩa tùy chọn tải cho Bảng tính
```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
```
- **Purpose**: Cấu hình các tùy chọn cụ thể cần thiết khi tải bảng tính.

#### Bước 2: Khởi tạo Watermarker với Đường dẫn Tài liệu của Bạn  
Thay thế `"YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx"` bằng đường dẫn thực tế tới tệp của bạn.
```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```
- **Explanation**: Tạo một thể hiện `Watermarker` cho phép bạn kiểm soát toàn bộ workbook.

#### Bước 3: Truy cập Nội dung Bảng tính
```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```
- **Functionality**: Lấy mô hình đối tượng phong phú đại diện cho các worksheet, ô và hình dạng.

### Tính năng 2: Trích xuất Hình ảnh từ Excel (Hình dạng)  

#### Tổng quan
Excel lưu trữ hình ảnh, biểu đồ và hộp văn bản dưới dạng *shapes*. Đoạn mã dưới đây trích xuất các shape đó, cho phép bạn **trích xuất hình ảnh từ Excel** hoặc kiểm tra thuộc tính của chúng trước khi áp dụng dấu nước.

#### Bước 4: Duyệt qua từng Worksheet
```java
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
```
- **Purpose**: Lặp qua tất cả các worksheet để truy cập các shape riêng lẻ.

#### Bước 5: Duyệt qua từng Shape trong một Worksheet
```java
for (SpreadsheetShape shape : worksheet.getShapes()) {
    // Display various properties of the shape
    System.out.println(shape.getAutoShapeType());
    System.out.println(shape.getMsoDrawingType());
    System.out.println(shape.getText());

    if (shape.getImage() != null) {
        System.out.println(shape.getImage().getWidth());
        System.out.println(shape.getImage().getHeight());
        System.out.println(shape.getImage().getBytes().length);
    }

    // Display other properties of the shape
    System.out.println(shape.getId());
    System.out.println(shape.getAlternativeText());
    System.out.println(shape.getX());
    System.out.println(shape.getY());
    System.out.println(shape.getWidth());
    System.out.println(shape.getHeight());
    System.out.println(shape.getRotateAngle());
    System.out.println(shape.isWordArt());
    System.out.println(shape.getName());
}
```
- **Explanation**: Trích xuất thông tin chi tiết về shape, bao gồm loại, nội dung văn bản và thuộc tính hình ảnh nếu có. Đây là nơi bạn có thể **trích xuất hình ảnh từ Excel** để xử lý hoặc lưu trữ thêm.

#### Bước 6: Đóng thể hiện Watermarker
```java
watermarker.close();
```
- **Significance**: Giải phóng tài nguyên bằng cách đóng thể hiện `Watermarker` sau khi các thao tác hoàn tất.

## Ứng dụng Thực tiễn
Các tính năng này có thể được áp dụng trong các kịch bản thực tế:

1. **Document Automation** – Tự động trích xuất và xử lý dữ liệu từ báo cáo Excel để tối ưu hoá quy trình làm việc.  
2. **Data Integrity Checks** – Xác thực các shape và hình ảnh nhúng trong bảng tính tài chính để tuân thủ.  
3. **Integration with BI Tools** – Cung cấp dữ liệu shape đã trích xuất vào các nền tảng Business Intelligence để phân tích sâu hơn.  

## Các cân nhắc về hiệu năng
Khi làm việc với các tệp Excel lớn:

- Chỉ xử lý các sheet hoặc shape cần thiết để giảm mức tiêu thụ bộ nhớ.  
- Nếu bạn chỉ cần **trích xuất hình ảnh từ Excel**, bỏ qua các ô và công thức.  
- Kiểm tra trong điều kiện tải thực tế và phân tích mã để xác định các điểm nghẽn.

## Kết luận
Bằng cách nắm vững các chức năng này của GroupDocs.Watermark cho Java, bạn có thể hiệu quả **đánh dấu nước Excel** các workbook, trích xuất hình ảnh nhúng, và tích hợp việc xử lý Excel vào các pipeline tự động lớn hơn. Khám phá các tính năng bổ sung như thêm dấu nước văn bản, xoay dấu nước, hoặc áp dụng chúng có điều kiện dựa trên nội dung worksheet.

### Các bước tiếp theo
- Tìm hiểu sâu API đánh dấu nước để thêm dấu nước văn bản hoặc hình ảnh tùy chỉnh.  
- Kết hợp việc trích xuất shape với OCR để đọc văn bản trong hình ảnh.  
- Khám phá GroupDocs SDK cho PDF, Word và các định dạng hình ảnh để xây dựng giải pháp xử lý tài liệu thống nhất.

## Phần Câu hỏi thường gặp
1. **GroupDocs.Watermark là gì?**  
   - Một thư viện Java mạnh mẽ để xử lý dấu nước và các nội dung khác trong tài liệu.  
2. **Tôi có thể sử dụng GroupDocs.Watermark với các loại tệp khác không?**  
   - Có, nó hỗ trợ PDF, hình ảnh, tệp Word và nhiều hơn nữa.  
3. **Làm thế nào để khắc phục các vấn đề thường gặp?**  
   - Kiểm tra [diễn đàn GroupDocs](https://forum.groupdocs.com/c/watermark/10) chính thức để được hỗ trợ hoặc tham khảo tài liệu.  
4. **Các thực tiễn tốt nhất khi sử dụng GroupDocs.Watermark là gì?**  
   - Luôn đóng các thể hiện `Watermarker` của bạn, chỉ xử lý các sheet cần thiết, và giám sát bộ nhớ khi làm việc với các tệp lớn.  
5. **Tôi có thể tìm thêm ví dụ ở đâu?**  
   - Kho [kho GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) cung cấp nhiều mẫu mã và dự án.

## Câu hỏi thường gặp
**Q: Làm thế nào để thêm dấu nước văn bản vào mỗi sheet trong một workbook Excel?**  
A: Sau khi tải workbook, tạo một đối tượng `TextWatermark` và gọi `watermarker.add(watermark, new SpreadsheetWatermarkOptions())` cho mỗi worksheet.

**Q: Tôi có thể chỉ trích xuất các hình ảnh PNG từ tệp Excel không?**  
A: Có. Kiểm tra `shape.getImage().getBytes()` và xác định định dạng hình ảnh qua `shape.getImage().getImageFormat()` trước khi xử lý.

**Q: Có thể áp dụng dấu nước chỉ cho các sheet chứa một từ khóa cụ thể không?**  
A: Chắc chắn. Duyệt qua `content.getWorksheets()`, kiểm tra giá trị ô, và gọi `watermarker.add(...)` có điều kiện trên các sheet phù hợp.

**Q: Thư viện có hỗ trợ các tệp Excel được bảo vệ bằng mật khẩu không?**  
A: Có. Truyền mật khẩu vào `SpreadsheetLoadOptions` bằng cách sử dụng `setPassword("yourPassword")` trước khi tạo `Watermarker`.

**Q: Phiên bản GroupDocs.Watermark nào được sử dụng trong hướng dẫn này?**  
A: Các ví dụ nhắm tới GroupDocs.Watermark **24.11**.

## Tài nguyên
- **Tài liệu**: [Tài liệu GroupDocs Watermark](https://docs.groupdocs.com/watermark/java/)  
- **Tham chiếu API**: [Tham chiếu API GroupDocs](https://reference.groupdocs.com/watermark/java)  
- **Tải xuống**: [Phiên bản mới nhất](https://releases.groupdocs.com/watermark/java/)

---

**Cập nhật lần cuối:** 2026-04-01  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}