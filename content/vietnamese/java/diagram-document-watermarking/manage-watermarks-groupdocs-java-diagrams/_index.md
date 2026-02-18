---
date: '2026-02-18'
description: Học cách thêm watermark và cách xóa watermark trong các tệp diagram như
  .vsdx bằng GroupDocs.Watermark cho Java. Bảo vệ tính toàn vẹn của tài liệu với GroupDocs
  Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Cách thêm watermark vào sơ đồ bằng GroupDocs.Watermark cho Java
type: docs
url: /vi/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Cách Thêm Watermark vào Sơ Đồ bằng GroupDocs.Watermark cho Java

Quản lý watermark trong các tệp sơ đồ là một phần cốt lõi để bảo vệ sở hữu trí tuệ và giữ cho tài liệu sạch sẽ khi phân phối công cộng. Trong hướng dẫn này, bạn sẽ học **cách thêm watermark** vào sơ đồ Visio, cũng như **cách xóa watermark** khi không còn cần thiết, tất cả bằng thư viện **groupdocs watermark java**. Dù bạn đang xây dựng một pipeline tài liệu cấp doanh nghiệp hay một script tiện ích nhanh, các bước này sẽ cho bạn kiểm soát đầy đủ việc watermark sơ đồ.

## Quick Answers
- **Thư viện nào xử lý watermark cho sơ đồ trong Java?** GroupDocs.Watermark for Java.  
- **Tôi có thể thêm và xóa watermark trong cùng một lần chạy không?** Có – tải sơ đồ một lần và thực hiện cả hai thao tác thêm và xóa.  
- **Các định dạng tệp nào được hỗ trợ?** Các định dạng Visio như `.vsdx`, `.vdx`, cùng các loại sơ đồ khác.  
- **Tôi có cần giấy phép không?** Giấy phép dùng thử hoạt động cho phát triển; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Yêu cầu phiên bản Java nào?** JDK 8 trở lên.

## What is “how to add watermark” in the context of diagrams?
Thêm watermark có nghĩa là nhúng một dấu hiệu có thể nhìn thấy hoặc ẩn—văn bản, logo hoặc hình ảnh—vào tệp sơ đồ. Dấu hiệu này đi kèm với tệp, giúp dễ dàng chứng minh quyền sở hữu hoặc đánh dấu phiên bản nháp.

## Why use GroupDocs.Watermark for Java?
* **Rich API** – Tìm kiếm, thêm và xóa cả watermark văn bản và hình ảnh chỉ với vài dòng code.  
* **Hỗ trợ đa định dạng** – Hoạt động với Visio (`.vsdx`, `.vdx`) và nhiều loại sơ đồ khác.  
* **Tập trung vào hiệu năng** – Chỉ tải các phần của sơ đồ cần thiết cho các thao tác watermark, giảm mức sử dụng bộ nhớ.

## Prerequisites
1. **Java Development Kit (JDK) 8+** – Đảm bảo `java -version` trả về 1.8 hoặc mới hơn.  
2. **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình chỉnh sửa nào bạn thích.  
3. **GroupDocs.Watermark for Java** – Thêm vào dự án của bạn qua Maven hoặc tải JAR trực tiếp.  

### Required Libraries and Dependencies
Add the repository and dependency to your `pom.xml`:

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

*Nếu bạn không muốn dùng Maven, bạn có thể tải JAR mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### License Acquisition
- **Dùng thử miễn phí:** Kiểm tra tất cả tính năng mà không cần key giấy phép.  
- **Giấy phép tạm thời:** Yêu cầu key có thời hạn để đánh giá.  
- **Giấy phép đầy đủ:** Mua gói đăng ký để sử dụng không giới hạn trong môi trường sản xuất.

## Setting Up GroupDocs.Watermark for Java
1. **Thêm thư viện** vào dự án của bạn (Maven hoặc JAR thủ công).  
2. **Tạo một thể hiện `Watermarker`** – đối tượng này là điểm vào để tải sơ đồ, tìm kiếm, thêm và xóa watermark.

## Implementation Guide

### Loading a Diagram Document
Việc tải là bước đầu tiên trước khi bạn có thể **thêm watermark** hoặc **xóa watermark**. Đoạn code dưới đây cho thấy cách mở tệp `.vsdx` với các tùy chọn tải tùy chỉnh.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Searching for Text Watermarks
Trước khi thêm watermark mới, bạn có thể muốn kiểm tra xem watermark văn bản đã tồn tại chưa. Đoạn mã này tìm kiếm cụm từ “Company Name”.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Searching for Image Watermarks
Nếu bạn cần xác định logo hoặc bất kỳ hình ảnh nào đã được dùng làm watermark, hãy sử dụng `ImageDctHashSearchCriteria`. Điều này hữu ích khi bạn muốn **xóa watermark** khớp với logo đã biết.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Removing Watermarks
Sau khi đã xác định được các watermark—văn bản, hình ảnh hoặc cả hai—bạn có thể xóa chúng khỏi sơ đồ. Ví dụ dưới đây minh họa một thao tác xóa kết hợp.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Practical Applications
1. **Tích hợp phần mềm doanh nghiệp** – Nhúng quản lý watermark vào ERP hoặc nền tảng tạo tài liệu của bạn để thực thi thương hiệu.  
2. **Hệ thống quản lý nội dung (CMS)** – Tự động quét các sơ đồ được tải lên để phát hiện logo không được phép và loại bỏ chúng.  
3. **Xử lý tài liệu pháp lý** – Thêm watermark văn bản “Confidential” trong giai đoạn nháp và sau đó **xóa watermark** trước khi nộp bản cuối cùng.

## Common Issues and Solutions
| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|------------|---------------------|----------------|
| Không tìm thấy watermark | Văn bản/hình ảnh tìm kiếm không khớp chính xác | Sử dụng `or()` để kết hợp tiêu chí hoặc điều chỉnh cài đặt phân biệt chữ hoa/thường. |
| `OutOfMemoryError` on large files | Sơ đồ được tải toàn bộ vào bộ nhớ | Sử dụng `DiagramLoadOptions.setLoadPages()` để chỉ tải các trang cần thiết. |
| Tệp đã lưu bị hỏng | `watermarker.save()` được gọi trước khi xóa hết watermark | Đảm bảo `possibleWatermarks.clear()` hoàn thành và `watermarker.close()` được gọi sau khi lưu. |

## Frequently Asked Questions

**Q: Tôi có thể tìm kiếm cả văn bản và hình ảnh đồng thời không?**  
A: Có. Kết hợp `TextSearchCriteria` và `ImageDctHashSearchCriteria` bằng phương thức `or()`, như trong ví dụ xóa.

**Q: Có thể xóa watermark mà không làm hỏng sơ đồ không?**  
A: Hoàn toàn có thể. Thư viện tách riêng các đối tượng watermark, vì vậy gọi `clear()` chỉ xóa các lớp watermark mà vẫn giữ nguyên nội dung sơ đồ gốc.

**Q: GroupDocs.Watermark có hỗ trợ nhiều định dạng sơ đồ không?**  
A: Có. Các định dạng như `.vsdx`, `.vdx` và các tệp tương thích Visio khác đều được hỗ trợ đầy đủ.

**Q: Làm thế nào để xử lý khối lượng lớn tài liệu một cách hiệu quả?**  
A: Thực hiện vòng lặp xử lý hàng loạt, tái sử dụng một thể hiện `Watermarker` duy nhất khi có thể, và giới hạn việc tải trang bằng `DiagramLoadOptions`.

**Q: Có cách nào tự động phát hiện watermark trong pipeline CI/CD không?**  
A: Bạn có thể nhúng các đoạn mã Java đã cung cấp vào script build (ví dụ Maven hoặc Gradle) để xác thực không có watermark không được phép trước khi phát hành artifact.

---

**Cập nhật lần cuối:** 2026-02-18  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs