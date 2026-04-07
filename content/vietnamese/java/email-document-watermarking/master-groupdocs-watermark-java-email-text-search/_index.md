---
date: '2026-04-07'
description: Học cách tìm kiếm nội dung email bằng Java sử dụng GroupDocs.Watermark,
  bao gồm cách tìm kiếm nhiều từ khóa trong email và cách xóa các watermark của email.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Tìm kiếm nội dung email trong Java bằng GroupDocs.Watermark: Hướng dẫn toàn
  diện'
type: docs
url: /vi/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Tìm kiếm nội dung email Java với GroupDocs.Watermark

Nếu bạn cần **search email body java** nhanh chóng và đáng tin cậy, bạn đã đến đúng nơi. Trong hướng dẫn này, chúng tôi sẽ trình bày cách GroupDocs.Watermark cho Java cho phép bạn xác định văn bản cụ thể trong tiêu đề email, phần thân HTML và phần thân dạng văn bản thuần, và cách bạn có thể loại bỏ các watermark không mong muốn sau đó. Khi kết thúc, bạn sẽ có thể triển khai một giải pháp mạnh mẽ hoạt động với một hoặc nhiều từ khóa và thậm chí loại bỏ watermark của email khi cần.

## Câu trả lời nhanh
- **What does “search email body java” mean?** Nó đề cập đến việc sử dụng mã Java (với GroupDocs.Watermark) để tìm văn bản trong nội dung của email.  
- **Can I search multiple keywords email at once?** Có – tạo các đối tượng `SearchCriteria` riêng biệt và kết hợp chúng.  
- **How to remove email watermarks?** Sử dụng phương thức `PossibleWatermarkCollection.clear()` sau khi tìm kiếm.  
- **Do I need a license?** Bản dùng thử miễn phí đủ cho việc kiểm tra; cần có giấy phép vĩnh viễn cho môi trường sản xuất.  
- **Which IDE works best?** IntelliJ IDEA hoặc Eclipse đều được hỗ trợ đầy đủ.

## Những gì bạn sẽ học
- Cài đặt và cấu hình GroupDocs.Watermark cho Java.  
- Thiết lập tiêu chí tìm kiếm để **search email body java** trên tiêu đề và nội dung email.  
- Kỹ thuật cho **search multiple keywords email** trong một lần chạy.  
- Các bước chính xác **how to remove email watermarks** sau khi xác định chúng.  

## Tại sao lại tìm kiếm nội dung email Java với GroupDocs.Watermark?
GroupDocs.Watermark cung cấp một API cấp cao giúp trừu tượng hoá các phức tạp khi phân tích tệp .msg, xử lý các định dạng thân khác nhau và quản lý watermark. Điều này giúp bạn tiết kiệm thời gian so với việc xây dựng bộ phân tích tùy chỉnh và đảm bảo kết quả nhất quán trên các lô email lớn.

## Yêu cầu trước
- Java Development Kit (JDK) 8 hoặc mới hơn.  
- Maven (hoặc khả năng thêm các tệp JAR thủ công).  
- Kiến thức cơ bản về Java và các định dạng tệp email (.msg, .eml).  

## Cài đặt GroupDocs.Watermark cho Java
GroupDocs.Watermark cho Java đơn giản hoá việc chèn watermark và tìm kiếm văn bản trong tài liệu, bao gồm email. Dưới đây là hai cách phổ biến nhất để thêm thư viện vào dự án của bạn.

### Cấu hình Maven
Thêm đoạn sau vào tệp `pom.xml` của bạn để thêm GroupDocs.Watermark làm phụ thuộc:
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

### Tải xuống trực tiếp
Ngoài ra, bạn có thể tải phiên bản mới nhất trực tiếp từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Các bước lấy giấy phép
- **Free Trial:** Bắt đầu với bản dùng thử miễn phí để kiểm tra các chức năng cơ bản.  
- **Temporary License:** Nhận giấy phép tạm thời để truy cập mở rộng và thử nghiệm.  
- **Purchase:** Xem xét mua nếu GroupDocs.Watermark đáp ứng nhu cầu của bạn.

#### Khởi tạo cơ bản
Khởi tạo lớp `Watermarker` như dưới đây:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Hướng dẫn triển khai

### Tính năng 1: Tìm kiếm văn bản trong nội dung email
Tính năng này cho phép tìm kiếm văn bản cụ thể trong tiêu đề và nội dung của email.

#### Tổng quan
Chúng tôi sẽ trình bày cách cấu hình GroupDocs.Watermark để tìm kiếm qua các phần khác nhau của một tin nhắn email bằng mã Java.

##### Bước 1: Xác định đường dẫn tài liệu
Thiết lập các đường dẫn đầu vào và đầu ra để xử lý email:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Bước 2: Thiết lập tùy chọn tải và Watermarker
Khởi tạo `EmailLoadOptions` và `Watermarker` để làm việc với tài liệu email của bạn.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Bước 3: Tạo tiêu chí tìm kiếm
Xác định tiêu chí để tìm kiếm văn bản. Chúng tôi sẽ sử dụng tìm kiếm không phân biệt chữ hoa chữ thường cho từ khóa **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Bước 4: Chỉ định vị trí tìm kiếm
Cấu hình tìm kiếm để bao phủ cả tiêu đề và nội dung của email:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Bước 5: Thực hiện tìm kiếm và xóa watermark
Thực hiện tìm kiếm và loại bỏ bất kỳ watermark nào được tìm thấy:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Bước 6: Lưu thay đổi
Sau khi xử lý, lưu các thay đổi của bạn vào một tài liệu mới:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Mẹo khắc phục sự cố
- **Common Issue:** Nếu kết quả tìm kiếm rỗng, hãy đảm bảo văn bản có trong thân hoặc tiêu đề email.  
- **Performance Tip:** Tối ưu hoá bằng cách giới hạn tìm kiếm chỉ trong các phần bạn thực sự cần.

### Tính năng 2: Tùy chọn tải tài liệu email
Phần này thảo luận cách bạn có thể thiết lập các tùy chọn bổ sung khi tải tài liệu email để xử lý bằng GroupDocs.Watermark.

#### Tổng quan
Cấu hình các tùy chọn tải cho phép kiểm soát tốt hơn cách tài liệu được xử lý, chẳng hạn như chỉ định bảo vệ bằng mật khẩu hoặc cài đặt mã hoá.

##### Bước 1: Cấu hình tùy chọn tải
Đây là một cấu hình cơ bản cho `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Các tùy chọn cấu hình chính
- **Password Protection:** Chỉ định mật khẩu nếu email của bạn được mã hoá.  
- **Encoding Settings:** Xác định các loại mã hoá cụ thể khi cần.

## Cách tìm kiếm nhiều từ khóa trong email
Nếu bạn cần xác định nhiều thuật ngữ trong một lần, tạo nhiều đối tượng `SearchCriteria` và kết hợp chúng bằng các toán tử logic **OR** hoặc **AND**. API cho phép bạn nối chuỗi các tiêu chí, vì vậy bạn có thể tìm kiếm “invoice” **or** “receipt” mà không cần chạy các vòng lặp riêng.

## Cách loại bỏ watermark của email
Sau khi bạn xác định được watermark (hoặc bất kỳ văn bản nào phù hợp với tiêu chí), phương thức `PossibleWatermarkCollection.clear()` sẽ loại bỏ chúng khỏi tài liệu email. Đây là bước chính xác mà chúng tôi đã sử dụng ở **Step 5** ở trên, và nó hoạt động cho bất kỳ số lượng kết quả nào.

## Ứng dụng thực tiễn

### Trường hợp sử dụng 1: Xử lý email tự động
Tự động hoá việc lọc và xử lý dữ liệu email hàng loạt để tìm nội dung cụ thể một cách hiệu quả.

### Trường hợp sử dụng 2: Kiểm tra tuân thủ pháp lý
Đảm bảo tuân thủ bằng cách tìm kiếm thông tin nhạy cảm trong email doanh nghiệp.

### Trường hợp sử dụng 3: Tự động hoá hỗ trợ khách hàng
Tối ưu hoá quy trình hỗ trợ bằng cách nhanh chóng xác định các từ khóa hoặc cụm từ trong yêu cầu của khách hàng.

## Các yếu tố cân nhắc về hiệu năng
Khi sử dụng GroupDocs.Watermark, hãy cân nhắc các yếu tố sau để tối ưu hoá hiệu năng:
- **Resource Management:** Quản lý bộ nhớ và tài nguyên xử lý một cách hiệu quả để xử lý các bộ dữ liệu email lớn.  
- **Java Memory Management Best Practices:** Thường xuyên giám sát việc sử dụng tài nguyên và giải phóng chúng kịp thời.

## Câu hỏi thường gặp

**Q:** Làm thế nào tôi có thể xử lý email được mã hoá với GroupDocs.Watermark?  
**A:** Sử dụng `EmailLoadOptions` để chỉ định mật khẩu khi khởi tạo `Watermarker`.

**Q:** Tôi có thể tìm kiếm nhiều từ khóa cùng lúc không?  
**A:** Có, tạo các thể hiện `SearchCriteria` riêng biệt và kết hợp chúng bằng các phép toán logic.

**Q:** GroupDocs.Watermark Java có miễn phí để sử dụng không?  
**A:** Có bản dùng thử miễn phí; hãy xem xét mua giấy phép để có các tính năng mở rộng.

**Q:** Làm sao tôi có thể xử lý một khối lượng lớn email một cách hiệu quả?  
**A:** Tối ưu hoá các tìm kiếm của bạn bằng cách nhắm mục tiêu vào các phần cụ thể của email và quản lý tài nguyên một cách hiệu quả.

**Q:** Tôi có thể tìm trợ giúp hoặc hỗ trợ bổ sung ở đâu?  
**A:** Truy cập [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) để nhận hỗ trợ cộng đồng hoặc liên hệ kênh hỗ trợ miễn phí của họ.

## Tài nguyên
- **Documentation:** Khám phá các hướng dẫn chi tiết tại [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Truy cập chi tiết kỹ thuật tại [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Cập nhật lần cuối:** 2026-04-07  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs