---
date: '2025-12-31'
description: Tìm hiểu cách tìm kiếm văn bản email bằng GroupDocs.Watermark cho Java,
  quản lý nội dung, tiêu đề và tệp đính kèm một cách hiệu quả.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Cách Tìm Kiếm Văn Bản Email với GroupDocs.Watermark Java – Hướng Dẫn Toàn Diện
type: docs
url: /vi/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Cách Tìm Kiếm Văn Bản Email với GroupDocs.Watermark Java

Việc tìm một cụm từ cụ thể trong tiêu đề, nội dung hoặc tệp đính kèm của email có thể gây đau đầu—đặc biệt khi bạn phải xử lý hàng chục hoặc hàng trăm tin nhắn. Trong hướng dẫn này, bạn sẽ khám phá **cách tìm kiếm email** nhanh chóng và chính xác bằng **GroupDocs.Watermark for Java**. Chúng tôi sẽ hướng dẫn qua việc cài đặt, mã nguồn và các mẹo thực tiễn để bạn có thể tích hợp tìm kiếm văn bản email vào ứng dụng của mình một cách tự tin.

## Câu trả lời nhanh
- **Thư viện nào cho phép tôi tìm kiếm văn bản email trong Java?** GroupDocs.Watermark for Java.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho việc kiểm tra; giấy phép trả phí cần thiết cho môi trường sản xuất.  
- **Tôi có thể tìm kiếm cả tiêu đề và nội dung không?** Có—cấu hình `EmailSearchableObjects` để bao gồm Subject, HtmlBody và PlainTextBody.  
- **API có phân biệt chữ hoa/thường không?** Bạn có thể chọn tìm kiếm không phân biệt chữ hoa/thường bằng cách đặt cờ thích hợp trong `TextSearchCriteria`.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 hoặc cao hơn; Maven được khuyến nghị để quản lý phụ thuộc.

## “Cách tìm kiếm email” với GroupDocs.Watermark là gì?
GroupDocs.Watermark cung cấp một API thống nhất để định vị, loại bỏ hoặc chỉnh sửa watermark và văn bản thuần trên nhiều loại tài liệu—bao gồm **tin nhắn email** (`.msg`, `.eml`). Bằng cách tận dụng mô hình đối tượng có thể tìm kiếm của nó, bạn có thể nhắm chính xác các phần của email mà bạn quan tâm, giúp việc xử lý hàng loạt nhanh chóng và đáng tin cậy.

## Tại sao nên sử dụng GroupDocs.Watermark Java cho việc tìm kiếm email?
- **Unified API** – Hoạt động với PDF, hình ảnh, tệp Office và email bằng cùng một mẫu mã.  
- **Performance‑optimized** – Các thao tác tìm kiếm chạy trong bộ nhớ mà không cần dịch vụ bên ngoài.  
- **Robust handling** – Hỗ trợ nội dung HTML và plain‑text, tệp đính kèm, và thậm chí email được bảo vệ bằng mật khẩu.  
- **Easy integration** – Sẵn sàng cho Maven/Gradle, với tài liệu rõ ràng và hỗ trợ tích cực.

## Yêu cầu trước
- **Java Development Kit (JDK)** 8 hoặc mới hơn.  
- **Maven** (hoặc Gradle) để quản lý phụ thuộc.  
- Một IDE như **IntelliJ IDEA** hoặc **Eclipse**.  
- Kiến thức cơ bản về cú pháp Java và định dạng tệp email (`.msg`, `.eml`).

## Cài đặt GroupDocs.Watermark cho Java

### Cài đặt Maven
Thêm kho lưu trữ và phụ thuộc vào file `pom.xml` của bạn:

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
Ngoài ra, bạn có thể tải JAR mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Nhận giấy phép
- **Free Trial:** Kiểm tra các tính năng cốt lõi mà không cần khóa giấy phép.  
- **Temporary License:** Yêu cầu khóa có thời hạn để đánh giá mở rộng.  
- **Paid License:** Mua để sử dụng không giới hạn trong môi trường sản xuất.

#### Khởi tạo cơ bản
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Hướng dẫn triển khai

### Tính năng 1: Tìm kiếm văn bản trong nội dung email

#### Tổng quan
Chúng tôi sẽ cấu hình API để quét **tiêu đề**, **nội dung HTML**, và **nội dung plain‑text** của email cho một từ khóa nhất định.

#### Bước 1: Xác định đường dẫn tài liệu
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Bước 2: Thiết lập Load Options và Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Bước 3: Tạo tiêu chí tìm kiếm
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Bước 4: Chỉ định vị trí tìm kiếm
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Bước 5: Thực thi tìm kiếm và xóa watermark
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Bước 6: Lưu thay đổi
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Mẹo khắc phục sự cố
- **Empty results:** Xác minh rằng từ khóa thực sự xuất hiện trong các phần email đã chọn.  
- **Performance:** Giới hạn các đối tượng có thể tìm kiếm chỉ ở những phần bạn cần (ví dụ: Subject + PlainTextBody) để tăng tốc xử lý các lô lớn.

### Tính năng 2: Tùy chọn tải tài liệu email

#### Tổng quan
`EmailLoadOptions` cho phép bạn kiểm soát cách email được phân tích—hữu ích cho các tin nhắn được mã hoá hoặc mã hoá tùy chỉnh.

#### Bước 1: Cấu hình Load Options
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Các tùy chọn cấu hình chính
- **Password Protection:** Đặt `loadOptions.setPassword("yourPassword")` cho các tệp `.msg` được mã hoá.  
- **Encoding Settings:** Điều chỉnh `loadOptions.setEncoding(Charset.forName("UTF-8"))` khi làm việc với bộ mã ký tự không chuẩn.

## Ứng dụng thực tế
- **Automated Email Processing:** Quét hàng loạt các ticket hỗ trợ đến để tìm từ khóa như “refund” hoặc “error”.  
- **Legal Compliance Checks:** Nhanh chóng xác định các thuật ngữ bí mật (ví dụ: SSN, số thẻ tín dụng) trong kho lưu trữ email của công ty.  
- **Customer Support Automation:** Chuyển hướng email dựa trên các cụm từ được phát hiện tới đội hỗ trợ phù hợp.

## Các lưu ý về hiệu năng
- **Resource Management:** Gọi `watermarker.close()` ngay khi bạn hoàn thành xử lý để giải phóng tài nguyên gốc.  
- **Memory Best Practices:** Khi xử lý hàng nghìn tin nhắn, xử lý chúng theo lô và tái sử dụng đối tượng `Watermarker` khi có thể.

## Kết luận
Bạn giờ đã có một cách tiếp cận vững chắc, sẵn sàng cho môi trường sản xuất để **tìm kiếm nội dung email** bằng GroupDocs.Watermark Java. Tính linh hoạt của API cho phép bạn nhắm mục tiêu các phần cụ thể của email, xóa các watermark không mong muốn, và tích hợp logic này vào các quy trình làm việc lớn hơn.

### Các bước tiếp theo
- Thử nghiệm với **nhiều tiêu chí tìm kiếm** (ví dụ: kết hợp “invoice” + “overdue”).  
- Khám phá **thêm watermark** để đánh dấu các email chứa dữ liệu nhạy cảm.  
- Nghiên cứu các loại tài liệu khác (PDF, DOCX) bằng quy trình Watermarker tương tự.

## Câu hỏi thường gặp

**Q1:** Làm thế nào tôi có thể xử lý email được mã hoá với GroupDocs.Watermark?  
**A1:** Sử dụng `EmailLoadOptions.setPassword("yourPassword")` trước khi tạo đối tượng `Watermarker`.

**Q2:** Tôi có thể tìm kiếm nhiều từ khóa cùng lúc không?  
**A2:** Có—tạo các đối tượng `SearchCriteria` riêng cho mỗi từ khóa và kết hợp chúng bằng các toán tử logic (ví dụ: `OrSearchCriteria`).

**Q3:** GroupDocs.Watermark Java có miễn phí không?  
**A3:** Bản dùng thử miễn phí có sẵn để đánh giá. Đối với môi trường sản xuất, cần giấy phép trả phí.

**Q4:** Làm sao tôi có thể xử lý khối lượng lớn email một cách hiệu quả?  
**A4:** Giới hạn các đối tượng có thể tìm kiếm chỉ ở những phần cần thiết, xử lý email theo lô, và luôn đóng `Watermarker` để giải phóng tài nguyên.

**Q5:** Tôi có thể tìm trợ giúp hoặc hỗ trợ bổ sung ở đâu?  
**A5:** Truy cập [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) để nhận hỗ trợ từ cộng đồng hoặc liên hệ trực tiếp với bộ phận hỗ trợ của GroupDocs.

## Tài nguyên
- **Documentation:** Khám phá các hướng dẫn chi tiết tại [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Truy cập chi tiết kỹ thuật tại [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

**Last Updated:** 2025-12-31  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs