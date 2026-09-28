---
date: '2025-12-19'
description: Tìm hiểu cách sử dụng GroupDocs Watermark Maven để quản lý watermark
  trong các tệp sơ đồ như .vsdx bằng Java, nâng cao tính toàn vẹn của tài liệu và
  bảo vệ sở hữu trí tuệ.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – Quản lý watermark cho sơ đồ bằng Java
type: docs
url: /vi/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – Quản lý Watermark cho Sơ đồ bằng Java

Quản lý watermark trong tài liệu là cần thiết để bảo vệ sở hữu trí tuệ và duy trì tính toàn vẹn của tài liệu. **Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách sử dụng groupdocs watermark maven để tải, tìm kiếm và xóa watermark một cách hiệu quả từ các tệp sơ đồ như `.vsdx`**. Dù bạn đang xây dựng phần mềm doanh nghiệp hay tự động hoá quy trình tài liệu, việc nắm vững các kỹ thuật này sẽ cho bạn quyền kiểm soát hoàn toàn việc quản lý watermark cho sơ đồ.

## Câu trả lời nhanh
- **Thư viện cần thiết là gì?** GroupDocs.Watermark for Java (có sẵn qua Maven).  
- **Các định dạng sơ đồ nào được hỗ trợ?** `.vsdx`, `.vdx`, và các định dạng Visio khác.  
- **Tôi có thể tìm kiếm cả watermark dạng văn bản và hình ảnh không?** Có – kết hợp các tiêu chí tìm kiếm bằng `or()`.  
- **Cần có giấy phép để triển khai trong môi trường production không?** Cần một giấy phép GroupDocs.Watermark hợp lệ.  
- **Làm thế nào để tích hợp vào Maven?** Thêm repository và dependency như dưới đây.

## groupdocs watermark maven là gì?
`groupdocs watermark maven` đề cập đến việc tích hợp dựa trên Maven của thư viện GroupDocs.Watermark cho Java. Khi khai báo thư viện trong `pom.xml` của bạn, Maven sẽ tự động giải quyết tất cả các binary cần thiết, cho phép bạn tập trung vào mã tải sơ đồ, tìm kiếm watermark và xóa chúng một cách lập trình.

## Tại sao nên sử dụng GroupDocs.Watermark cho việc quản lý watermark trên sơ đồ?
- **API đầy đủ tính năng** – hỗ trợ watermark dạng văn bản, hình ảnh và hình dạng trên nhiều loại sơ đồ.  
- **Xóa chính xác** – loại bỏ watermark mà không làm hỏng bố cục sơ đồ gốc.  
- **Mở rộng** – phù hợp cho xử lý hàng loạt các bộ sưu tập sơ đồ lớn.  
- **Thân thiện với Maven** – quản lý dependency đơn giản, giữ dự án của bạn sạch sẽ.

## Yêu cầu trước
1. **Java Development Kit (JDK) 8+** – đảm bảo tương thích với thư viện.  
2. **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo nào hỗ trợ Java.  
3. **GroupDocs.Watermark for Java** – được thêm qua Maven (được khuyến nghị) hoặc tải trực tiếp JAR.  

### Thư viện và Dependency cần thiết
#### Cấu hình Maven
Add the following configuration to your `pom.xml` file:

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
Hoặc tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Cách lấy giấy phép
- **Dùng thử miễn phí:** Kiểm tra thư viện với giấy phép dùng thử.  
- **Giấy phép tạm thời:** Yêu cầu khóa ngắn hạn để đánh giá.  
- **Mua:** Nhận giấy phép production để sử dụng không giới hạn.

## Sử dụng groupdocs watermark maven để tải tài liệu sơ đồ
Tải tài liệu sơ đồ là bước đầu tiên trước bất kỳ thao tác watermark nào. Dưới đây là một ví dụ tối thiểu tạo một thể hiện `Watermarker` với `DiagramLoadOptions`.

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

- **Tham số:**  
  - `inputFilePath` – đường dẫn tới tệp `.vsdx` của bạn.  
  - `loadOptions` – cho phép bạn kiểm soát cách sơ đồ được phân tích (ví dụ: bảo vệ bằng mật khẩu).

## Tìm kiếm Watermark với groupdocs watermark maven
### Watermark dạng Văn bản
Để xác định watermark dạng văn bản, định nghĩa một `TextSearchCriteria` và truy vấn trang đầu tiên của sơ đồ.

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

- **Phương thức chính:**  
  - `TextSearchCriteria` – chỉ định chính xác văn bản cần tìm.  
  - `PossibleWatermarkCollection` – lưu trữ các kết quả khớp được tìm thấy.

### Watermark dạng Hình ảnh
Nếu sơ đồ của bạn chứa logo hoặc watermark dạng hình ảnh, sử dụng `ImageDctHashSearchCriteria` để so sánh với một hình ảnh tham chiếu.

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

- **Phương thức chính:**  
  - `ImageDctHashSearchCriteria` – tạo một perceptual hash của hình ảnh tham chiếu để so khớp mạnh mẽ.

## Xóa Watermark
Sau khi đã xác định các watermark không mong muốn, bạn có thể xóa chúng và lưu một bản sao sạch của sơ đồ.

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

- **Phương thức chính:** `clear()` xóa mọi watermark được tìm thấy bởi các tiêu chí kết hợp, để lại sơ đồ nguyên vẹn.

## Ứng dụng thực tiễn
1. **Tích hợp phần mềm doanh nghiệp** – Nhúng quản lý watermark vào các ứng dụng kinh doanh để bảo vệ các sơ đồ sở hữu.  
2. **Hệ thống quản lý nội dung (CMS)** – Tự động phát hiện và xóa logo không được phép trước khi xuất bản.  
3. **Quy trình tài liệu pháp lý** – Thêm hoặc loại bỏ watermark ở các giai đoạn khác nhau của quá trình xử lý hợp đồng.  

## Các vấn đề thường gặp & Khắc phục
- **Lỗi giấy phép:** Đảm bảo tệp giấy phép được tham chiếu đúng trước khi tạo `Watermarker`.  
- **Tệp lớn:** Sử dụng API streaming hoặc tăng kích thước heap JVM (`-Xmx2g`) cho các sơ đồ > 100 MB.  
- **Watermark không tìm thấy:** Kiểm tra lại tiêu chí tìm kiếm (các chữ hoa/thường, ngưỡng tương đồng hình ảnh) có khớp với nội dung watermark thực tế.

## Câu hỏi thường gặp

**Q: Tôi có thể tìm kiếm cả văn bản và hình ảnh cùng lúc không?**  
A: Có. Kết hợp các tiêu chí bằng `or()` như trong ví dụ xóa.

**Q: Việc xóa watermark có an toàn mà không làm thay đổi bố cục sơ đồ không?**  
A: Chắc chắn. API nhắm mục tiêu chính xác vào các đối tượng watermark, giữ nguyên mọi thành phần khác của sơ đồ.

**Q: GroupDocs.Watermark hỗ trợ những định dạng sơ đồ nào?**  
A: Nó hỗ trợ các định dạng Visio như `.vsdx`, `.vdx`, cũng như các loại sơ đồ vector khác.

**Q: Làm sao để xử lý hàng trăm sơ đồ một cách hiệu quả?**  
A: Thực hiện vòng lặp batch, tái sử dụng một thể hiện `Watermarker` duy nhất khi có thể, và cân nhắc xử lý song song bằng `ExecutorService` của Java.

**Q: Tôi có thể tích hợp phát hiện watermark vào pipeline CI/CD không?**  
A: Có. Bao gồm các đoạn mã Java trong script build của bạn (ví dụ: plugin Maven hoặc task Gradle) để xác thực sơ đồ trước khi triển khai.

## Kết luận
Bằng cách tận dụng **groupdocs watermark maven**, bạn có được một cách mạnh mẽ, được quản lý bởi Maven để tải, tìm kiếm và xóa watermark từ các tệp sơ đồ bằng Java. Khả năng này tăng cường bảo mật tài liệu, tối ưu hoá quy trình nội dung và mở rộng dễ dàng trên các bộ sưu tập tài liệu lớn.

---

**Cập nhật lần cuối:** 2025-12-19  
**Được kiểm thử với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs