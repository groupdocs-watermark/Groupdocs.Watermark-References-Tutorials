---
date: '2026-03-20'
description: Tìm hiểu cách thêm watermark bằng cách sử dụng GroupDocs.Watermark Java
  SDK để chèn watermark hình ảnh vào bảng tính Excel, hoàn hảo cho việc xây dựng thương
  hiệu và bảo mật tài liệu.
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'Cách Thêm Đánh Dấu Nước: Đánh Dấu Nước Hình Ảnh vào Bảng Tính Excel Sử Dụng
  GroupDocs.Watermark Java SDK'
type: docs
url: /vi/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# Cách Thêm Watermark vào Bảng Tính Excel Sử Dụng GroupDocs.Watermark Java SDK

Bảo vệ các tệp Excel của bạn khỏi việc phân phối trái phép hoặc đơn giản là củng cố nhận diện thương hiệu có thể đạt được bằng cách thêm một dấu hiệu trực quan luôn hiển thị bất kể tệp được xem như thế nào. Trong hướng dẫn này, bạn sẽ học **cách thêm watermark** — cụ thể là watermark hình ảnh — vào phần header hoặc footer của một bảng tính Excel bằng **GroupDocs.Watermark Java SDK**. Khi kết thúc, bạn sẽ có thể nhúng logo, huy hiệu bảo mật, hoặc bất kỳ hình ảnh tùy chỉnh nào trực tiếp vào workbook mà không làm thay đổi dữ liệu ô.

## Câu Hỏi Nhanh
- **“cách thêm watermark” đề cập đến gì?** Thêm một lớp phủ hình ảnh (hoặc văn bản) xuất hiện trên mỗi trang được in hoặc trên các phần cụ thể như header/footer.  
- **Thư viện nào hỗ trợ điều này trong Java?** `GroupDocs.Watermark` Java SDK (phiên bản mới nhất).  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho phát triển; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Tôi có thể thêm logo vào header không?** Có – sử dụng watermark hình ảnh và đặt tùy chọn header (`add logo to header`).  
- **Có thể xử lý nhiều sheet cùng lúc không?** Lặp qua các chỉ số worksheet và áp dụng cùng một watermark cho mỗi sheet.

## Yêu Cầu Trước

Để làm theo, hãy chắc chắn rằng bạn có:

- **GroupDocs.Watermark for Java SDK** (phiên bản 24.11 trở lên).  
- **Java Development Kit (JDK)** 8 hoặc cao hơn.  
- Kiến thức cơ bản về Java và cấu trúc tệp Excel.  

## Cài Đặt GroupDocs.Watermark cho Java SDK

Đầu tiên, thêm các phụ thuộc Maven cần thiết để SDK có sẵn trên classpath của bạn.

### Cấu Hình Maven

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

### Tải Trực Tiếp

Nếu bạn không muốn dùng Maven, tải JAR mới nhất từ trang phát hành chính thức: [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

**Mua Giấy Phép**  
- Nhận bản dùng thử miễn phí hoặc khóa giấy phép tạm thời để đánh giá toàn bộ tính năng.  
- Mua giấy phép đầy đủ cho các triển khai thương mại.

### Khởi Tạo và Cấu Hình

Tạo một thể hiện `Watermarker` sẽ tải tệp Excel và là điểm vào cho mọi thao tác watermark.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## Cách Thêm Watermark vào Header/Footer của Spreadsheet

Dưới đây là quy trình từng bước thể hiện chức năng **java add image watermark** và cũng cho thấy cách **add logo to header**.

### Bước 1: Cấu Hình Tùy Chọn Tải

Chúng ta bắt đầu bằng việc định nghĩa các tùy chọn tải và khởi tạo lại `Watermarker`. Điều này đảm bảo SDK đọc workbook đúng cách.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### Bước 2: Tạo và Cấu Hình Image Watermark

Tạo một đối tượng `ImageWatermark` trỏ tới hình ảnh bạn muốn nhúng (ví dụ: logo hoặc huy hiệu “CONFIDENTIAL”). Điều chỉnh căn chỉnh và tỉ lệ sao cho phù hợp trong khu vực header/footer.

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### Bước 3: Cấu Hình Tùy Chọn Header/Footer

Cho SDK biết worksheet nào và phần nào (header hoặc footer) sẽ nhận watermark. Đây là nơi bạn có thể **add logo to header** hoặc chọn footer thay thế.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### Bước 4: Thêm Watermark

Bây giờ gắn watermark hình ảnh đã chuẩn bị vào vị trí header/footer đã chọn.

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### Bước 5: Lưu và Đóng

Lưu các thay đổi vào một tệp mới để workbook gốc không bị thay đổi, sau đó giải phóng tài nguyên.

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### Mẹo Khắc Phục Sự Cố

- Kiểm tra lại đường dẫn hình ảnh; đường dẫn sai sẽ gây ra `FileNotFoundException`.  
- Chỉ số worksheet bắt đầu từ 0; đảm bảo chỉ số bạn đặt thực sự tồn tại.  
- Nếu watermark bị biến dạng, điều chỉnh `setScaleFactor` hoặc chuyển `SizingType` sang `StretchToParentDimensions`.

## Tại Sao Nên Sử Dụng GroupDocs.Watermark Java SDK?

- **Hỗ trợ đa định dạng** – hoạt động với Excel, Word, PowerPoint, PDF và hình ảnh.  
- **Chỉnh sửa không mất dữ liệu** – dữ liệu ô gốc vẫn nguyên vẹn.  
- **Tối ưu hiệu năng** – phù hợp cho workbook lớn và xử lý hàng loạt.  

## Các Trường Hợp Sử Dụng Thực Tế

| Kịch bản | Watermark giúp gì |
|----------|-------------------|
| **Báo cáo bảo mật** | Thêm hình ảnh “CONFIDENTIAL” vào mỗi trang được in. |
| **Củng cố thương hiệu** | Đặt logo công ty vào header của hóa đơn. |
| **Theo dõi phiên bản** | Nhúng huy hiệu số phiên bản tự động cập nhật. |
| **Tuân thủ pháp lý** | Đánh dấu các spreadsheet được quy định bằng con dấu tuân thủ. |

## Các Yếu Tố Về Hiệu Suất

- **Tiêu thụ bộ nhớ** – Giám sát heap JVM khi xử lý các spreadsheet rất lớn.  
- **Xử lý batch** – Xử lý tệp theo nhóm để giữ dung lượng bộ nhớ thấp.  
- **Tái sử dụng đối tượng** – Tái sử dụng một thể hiện `Watermarker` duy nhất cho nhiều tệp giảm tải overhead.

## Câu Hỏi Thường Gặp

**Hỏi: Tôi có thể thêm nhiều watermark vào một tài liệu duy nhất không?**  
Đáp: Có, bằng cách tạo thêm các thể hiện `ImageWatermark` và cấu hình mỗi cái trước khi gọi `watermarker.add()`.

**Hỏi: Làm sao để xóa watermark hiện có khỏi một spreadsheet?**  
Đáp: Hiện tại, GroupDocs.Watermark tập trung vào việc thêm watermark. Để xóa, bạn cần tạo lại workbook mà không có watermark hoặc dùng công cụ hỗ trợ trích xuất watermark.

**Hỏi: Các định dạng hình ảnh nào được hỗ trợ cho watermark?**  
Đáp: Các định dạng phổ biến như PNG và JPEG được hỗ trợ, nhưng hãy kiểm tra [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/) để biết danh sách đầy đủ các định dạng tương thích.

**Hỏi: Có thể watermark các spreadsheet được bảo mật bằng mật khẩu không?**  
Đáp: Có, miễn là bạn cung cấp mật khẩu cần thiết khi mở tệp.

**Hỏi: Làm sao áp dụng watermark cho tất cả worksheets trong một tài liệu?**  
Đáp: Lặp qua mỗi chỉ số worksheet và lặp lại các bước watermark, đặt `headerFooterOptions.setWorksheetIndex(i)` cho mỗi vòng lặp.

## Kết Luận

Bạn đã có một phương pháp hoàn chỉnh, sẵn sàng cho môi trường production để **java add excel watermark**—cụ thể là watermark hình ảnh—bằng **GroupDocs.Watermark Java SDK**. Cách tiếp cận này thêm thương hiệu, thông báo bảo mật, hoặc bất kỳ dấu hiệu trực quan nào vào header hoặc footer của tệp Excel trong khi giữ nguyên dữ liệu nền. Hãy tự do khám phá các loại watermark khác (văn bản, hình dạng) và kết hợp chúng để tăng cường bảo vệ tài liệu.

---

**Cập nhật lần cuối:** 2026-03-20  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs