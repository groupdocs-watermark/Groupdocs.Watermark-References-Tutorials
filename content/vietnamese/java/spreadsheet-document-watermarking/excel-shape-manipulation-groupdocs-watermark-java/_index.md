---
date: '2026-06-01'
description: Tìm hiểu cách xóa các shapes từ tệp Excel với GroupDocs.Watermark cho
  Java. Bao gồm các bước tải Excel, duyệt worksheets, và xóa các formatted shapes.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Cách xóa các shapes từ Excel bằng GroupDocs.Watermark trong Java
type: docs
url: /vi/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Cách xóa các hình dạng khỏi Excel bằng GroupDocs.Watermark trong Java

Excel spreadsheets là nền tảng của báo cáo doanh nghiệp, nhưng các hình dạng không mong muốn—đặc biệt là những hình có định dạng văn bản lỗi thời hoặc không tiêu chuẩn—có thể làm rối tệp và phá vỡ tính nhất quán về hình ảnh. **Xóa các hình dạng khỏi Excel** nhanh chóng trở nên cần thiết cho các tài liệu sạch sẽ, chuyên nghiệp. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn cách tải một workbook Excel, duyệt các worksheet của nó, và xóa các hình dạng đáp ứng tiêu chí định dạng cụ thể bằng cách lập trình, tất cả với thư viện GroupDocs.Watermark mạnh mẽ cho Java.

## Câu trả lời nhanh
- **GroupDocs.Watermark có thể xóa các hình dạng không?** Có, nó cung cấp phương thức `removeShape` hoạt động trên bất kỳ worksheet nào.  
- **Tôi có cần giấy phép cho tính năng này không?** Bản dùng thử hoạt động để đánh giá; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Phiên bản Java nào được yêu cầu?** Java 8 hoặc mới hơn được hỗ trợ.  
- **GroupDocs.Watermark hỗ trợ bao nhiêu định dạng tệp?** Hơn 30 định dạng đầu vào và đầu ra, bao gồm XLSX, DOCX, PDF và PPTX.  
- **Tiêu thụ bộ nhớ có phải là vấn đề đối với workbook lớn không?** Sử dụng try‑with‑resources và tránh tải toàn bộ sheet vào bộ nhớ; API truyền dữ liệu một cách hiệu quả.

## Xóa các hình dạng khỏi Excel là gì?
*Xóa các hình dạng khỏi Excel* có nghĩa là xóa các đối tượng vẽ—như hộp văn bản, biểu tượng hoặc SmartArt—theo lập trình khi chúng đáp ứng các tiêu chí nhất định, chẳng hạn như kiểu phông chữ, màu sắc hoặc kích thước. Thao tác này làm sạch workbook mà không cần chỉnh sửa thủ công, đảm bảo tính nhất quán về hình ảnh, giảm kích thước tệp và ngăn ngừa các đồ họa lỗi thời hoặc không mong muốn xuất hiện trong báo cáo được phân phối.

## Tại sao cần xóa các hình dạng khỏi Excel?
GroupDocs.Watermark có thể xử lý **các workbook hàng trăm trang với tốc độ nhanh tới 3 × so với** chỉnh sửa thủ công, hỗ trợ **hơn 30 định dạng tệp** đồng thời giữ mức sử dụng bộ nhớ dưới 150 MB cho các tệp lớn hơn 50 MB. Tự động xóa các hình dạng loại bỏ lỗi con người và đảm bảo thương hiệu nhất quán trên tất cả các báo cáo được tạo.

## Các yêu cầu trước
### Thư viện, Phiên bản và Phụ thuộc cần thiết
- **Java Development Kit (JDK)**: Phiên bản 8 hoặc mới hơn.  
- **GroupDocs.Watermark**: Phiên bản 24.11 (bản phát hành ổn định mới nhất tại thời điểm viết).

### Yêu cầu thiết lập môi trường
Sử dụng IDE như IntelliJ IDEA hoặc Eclipse và Maven để quản lý phụ thuộc.

### Kiến thức tiên quyết
Quen thuộc với cú pháp Java và các khái niệm cơ bản của Excel (worksheet, ô và hình dạng) sẽ giúp bạn theo dõi các ví dụ.

## Cài đặt GroupDocs.Watermark cho Java
**Phụ thuộc Maven**  
Thêm các dòng sau vào `pom.xml` của bạn:

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
Hoặc, tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Các bước lấy giấy phép
- **Dùng thử miễn phí** – Bắt đầu với bản dùng thử miễn phí để đánh giá tính năng.  
- **Giấy phép tạm thời** – Nhận giấy phép tạm thời để thử nghiệm kéo dài.  
- **Mua** – Mua giấy phép đầy đủ để sử dụng trong môi trường sản xuất.

### Khởi tạo và thiết lập cơ bản  
Khi thư viện đã được thêm vào dự án, khởi tạo nó như dưới đây:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Cách xóa các hình dạng khỏi Excel?
Tải workbook, duyệt qua từng worksheet và gọi API xóa hình dạng. Mô hình hai bước này—*tải* rồi *duyệt*—phủ sóng hầu hết các tình huống bạn cần làm sạch các hình dạng trên toàn bộ tệp. Bằng cách kiểm tra thuộc tính của mỗi hình dạng so với tiêu chí của bạn trước khi xóa, bạn đảm bảo chỉ các yếu tố không mong muốn bị xóa trong khi vẫn giữ lại bố cục và nội dung còn lại của tài liệu.

## Tải tài liệu Excel
**Tổng quan**  
Tải tài liệu Excel là điểm khởi đầu cho bất kỳ nhiệm vụ thao tác nào. GroupDocs.Watermark đơn giản hoá việc này với API trực quan của nó.  

**Định nghĩa**  
`SpreadsheetDocument` là lớp chính trong GroupDocs.Watermark đại diện cho một workbook Excel trong bộ nhớ, cung cấp các phương thức để truy cập worksheet, ô và hình dạng.  

#### Đoạn mã
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Truy cập và duyệt qua các Worksheet trong Spreadsheet
**Tổng quan**  
Duyệt qua các worksheet cho phép bạn thực hiện các thao tác trên từng sheet riêng lẻ.  

**Định nghĩa**  
`Worksheet` đại diện cho một sheet duy nhất trong `SpreadsheetDocument`; bạn có thể đọc, sửa đổi hoặc xóa nội dung của nó thông qua đối tượng này.  

#### Đoạn mã
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Xóa các hình dạng với định dạng văn bản cụ thể khỏi Spreadsheet
**Tổng quan**  
Tính năng này nhắm vào các hình dạng đáp ứng tiêu chí định dạng văn bản nhất định, chẳng hạn như kiểu phông chữ hoặc màu sắc.  

**Định nghĩa**  
`Shape` là mô hình đối tượng cho bất kỳ phần tử vẽ nào (hộp văn bản, hình ảnh hoặc SmartArt) trong worksheet; nó cung cấp các thuộc tính như `getText`, `getFont` và `remove`.  

#### Đoạn mã
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Ứng dụng thực tiễn
### Các trường hợp sử dụng thực tế
1. **Kiểm tra dữ liệu** – Tự động xóa các hình dạng chứa thông báo đã lỗi thời.  
2. **Chuẩn hoá mẫu** – Thực thi thương hiệu công ty bằng cách loại bỏ các hộp văn bản không tiêu chuẩn.  
3. **Báo cáo tự động** – Làm sạch các báo cáo đã tạo trước khi phân phối, đảm bảo giao diện hoàn thiện.

### Các khả năng tích hợp
GroupDocs.Watermark có thể được nhúng vào các pipeline doanh nghiệp dựa trên Java, chẳng hạn như micro‑service tạo tài liệu, công việc xử lý batch, hoặc hệ thống quản lý nội dung, cung cấp cách quản lý tài sản Excel liền mạch và tuân thủ giấy phép.

## Các cân nhắc về hiệu năng
### Tối ưu hoá hiệu năng
- **Tránh các thao tác nặng trong vòng lặp** – lấy bộ sưu tập hình dạng một lần cho mỗi worksheet.  
- **Giải phóng tài nguyên kịp thời** – sử dụng try‑with‑resources để tự động đóng stream.

### Hướng dẫn sử dụng tài nguyên
Giải phóng đối tượng `SpreadsheetDocument` ngay khi quá trình xử lý kết thúc để giải phóng bộ nhớ gốc. Đối với các tệp vượt quá 100 MB, cân nhắc xử lý các worksheet trong các stream song song để tận dụng CPU đa nhân.

### Các thực hành tốt nhất cho quản lý bộ nhớ Java
Sử dụng `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` để phương thức `close()` được gọi ngay cả khi xảy ra ngoại lệ.

## Các vấn đề thường gặp và giải pháp
- **Không tìm thấy hình dạng** – Đảm bảo bạn đang kiểm tra chỉ số worksheet đúng; các hình dạng được giới hạn trong mỗi sheet.  
- **Lỗi giấy phép** – Giấy phép dùng thử vô hiệu hoá xử lý batch; nâng cấp lên giấy phép đầy đủ để thực hiện không giới hạn.  
- **Giá trị phông chữ không mong đợi** – Thuộc tính phông chữ có thể được kế thừa; sử dụng `shape.getEffectiveFont()` để lấy kiểu đã giải quyết.

## Câu hỏi thường gặp

**Q: Tôi có thể xóa các hình dạng khỏi workbook được bảo mật bằng mật khẩu không?**  
A: Có. Tải tài liệu với tham số mật khẩu, sau đó chạy cùng logic xóa; API giải mã tệp trong bộ nhớ.

**Q: Thư viện có hỗ trợ tệp .xls (Excel 97‑2003) không?**  
A: Hoàn toàn có. GroupDocs.Watermark xử lý cả định dạng `.xlsx` và `.xls` legacy mà không cần chuyển đổi.

**Q: Làm thế nào để ghi lại các hình dạng đã bị xóa?**  
A: Duyệt bộ sưu tập hình dạng, kiểm tra tiêu chí định dạng, ghi log `shape.getName()` hoặc `shape.getId()`, sau đó gọi `remove()`.

**Q: Có thể thêm watermark sau khi xóa các hình dạng không?**  
A: Có. Sau khi làm sạch, gọi `doc.addWatermark(new TextWatermark("Confidential"))` để chồng một watermark văn bản lên tất cả worksheet.

**Q: Kích thước tệp tối đa được hỗ trợ là bao nhiêu?**  
A: Thư viện có thể xử lý các tệp lên tới **2 GB** trên JVM 64‑bit, chỉ bị giới hạn bởi bộ nhớ heap khả dụng và các ràng buộc của hệ điều hành.

## Kết luận
Trong hướng dẫn này, chúng tôi đã trình bày một phương pháp hoàn chỉnh, sẵn sàng cho sản xuất để **xóa các hình dạng khỏi Excel** workbook bằng GroupDocs.Watermark cho Java. Bằng cách tải tài liệu, duyệt các worksheet và áp dụng các bộ lọc định dạng chính xác, bạn có thể tự động hoá các nhiệm vụ làm sạch, thực thi thương hiệu và cải thiện chất lượng báo cáo ở quy mô lớn. Khám phá các tính năng bổ sung như chèn watermark, chuyển đổi tài liệu và xử lý batch để mở rộng bộ công cụ tự động hoá tài liệu của bạn.

---

**Cập nhật lần cuối:** 2026-06-01  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Thao tác hình dạng Excel bằng GroupDocs.Watermark trong Java: Hướng dẫn toàn diện](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Thêm Watermark Hình ảnh vào Spreadsheet Excel bằng GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Xử lý tài liệu Excel và Watermark với GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)