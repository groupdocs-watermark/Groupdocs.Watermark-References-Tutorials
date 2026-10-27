---
date: '2026-10-27'
description: Tìm hiểu cách xóa watermark văn bản khỏi các tệp sơ đồ bằng GroupDocs.Watermark
  for Java và phát hiện watermark hình ảnh một cách hiệu quả. Hướng dẫn chi tiết từng
  bước cho nhà phát triển.
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: Xóa watermark văn bản khỏi các tệp sơ đồ bằng GroupDocs.Watermark
  for Java. Tìm hiểu cách phát hiện watermark hình ảnh, tìm kiếm và loại bỏ watermark
  bằng các đoạn mã mẫu.
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: Xóa watermark văn bản trong các tệp sơ đồ bằng Java nhanh chóng
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: Cách xóa watermark văn bản trong sơ đồ bằng Java
type: docs
url: /vi/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Cách xóa watermark văn bản trong sơ đồ bằng Java

Quản lý watermark trong tài liệu là điều cần thiết để bảo vệ sở hữu trí tuệ và duy trì tính toàn vẹn của tài liệu. Trong hướng dẫn này, bạn sẽ học cách **xóa watermark văn bản** khỏi các tệp sơ đồ như `.vsdx` bằng GroupDocs.Watermark cho Java, và cách **phát hiện watermark hình ảnh** khi cần. Dù bạn đang xây dựng một quy trình tài liệu cấp doanh nghiệp hay tự động hoá một công việc batch đơn giản, những kỹ thuật này sẽ cho bạn khả năng kiểm soát chi tiết watermark trong sơ đồ.

**Bạn sẽ học được**
- Cài đặt thư viện GroupDocs.Watermark
- Tải tài liệu sơ đồ với các tùy chọn cụ thể
- Tìm kiếm và xóa watermark văn bản
- Phát hiện watermark hình ảnh và loại bỏ chúng
- Các mẹo thực hành tốt cho xử lý quy mô lớn

Sẵn sàng bắt đầu? Hãy chuẩn bị môi trường của bạn trước.

## Câu trả lời nhanh
- **Có thể xóa đồng thời cả watermark văn bản và hình ảnh không?** Có – kết hợp `TextSearchCriteria` và `ImageDctHashSearchCriteria` với điều kiện `or()`.  
- **Thư viện có tải toàn bộ sơ đồ vào bộ nhớ không?** Không – nó stream các trang, cho phép xử lý các tệp lên tới 500 MB mà không tiêu tốn toàn bộ bộ nhớ.  
- **Các định dạng sơ đồ nào được hỗ trợ?** Hơn 20 định dạng, bao gồm `.vsdx`, `.vdx` và `.drawio`.  
- **Cần giấy phép để sử dụng trong môi trường production không?** Cần một giấy phép GroupDocs.Watermark hợp lệ cho việc sử dụng không phải bản trial.  
- **Có thể chạy trong pipeline CI/CD không?** Hoàn toàn có thể – API chạy ở chế độ headless và hỗ trợ Windows, Linux và macOS.

## Delete text watermark là gì?
Delete text watermark có nghĩa là loại bỏ các đối tượng phủ lên dạng văn bản đã được thêm vào tài liệu để chỉ ra quyền sở hữu, tính bảo mật hoặc trạng thái bản nháp. Trong GroupDocs.Watermark, thao tác này được thực hiện bằng cách xác định các đối tượng watermark bằng tiêu chí tìm kiếm và sau đó gọi `clear()` trên tập hợp kết quả.

## Tại sao cần phát hiện watermark hình ảnh?
Detect image watermark cho phép bạn xác định các logo hoặc con dấu đồ họa đã được nhúng vào sơ đồ. Điều này quan trọng cho việc kiểm tra tuân thủ, bảo vệ thương hiệu và tự động hoá kiểm duyệt nội dung. GroupDocs.Watermark sử dụng hàm băm nhận thức (DCT) để so sánh hình ảnh một cách nhanh chóng và chính xác.

## Yêu cầu trước
Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:
1. **Java Development Kit (JDK)** 8 hoặc cao hơn.  
2. **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo nào bạn thích.  
3. **GroupDocs.Watermark for Java** – các file JAR của thư viện phải có trong classpath của bạn.  

### Thư viện và phụ thuộc cần thiết
Bạn có thể thêm thư viện qua Maven hoặc tải các JAR thủ công.

#### Cấu hình Maven
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

#### Tải trực tiếp
Hoặc tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Mua giấy phép
- **Dùng thử miễn phí** – thử tất cả các tính năng mà không cần key giấy phép.  
- **Giấy phép tạm thời** – yêu cầu key có thời hạn để đánh giá.  
- **Mua bản quyền** – nhận giấy phép vĩnh viễn hoặc theo thuê bao cho môi trường production.

## Cài đặt GroupDocs.Watermark cho Java
1. **Cài đặt thư viện** – đảm bảo repository Maven và các mục dependency đã được thêm, hoặc đặt các file JAR vào thư mục `libs/` và thêm chúng vào đường dẫn build của dự án.  
2. **Khởi tạo API** – tạo một thể hiện `Watermarker`; đối tượng này là điểm vào để tải sơ đồ và thực hiện các thao tác watermark.

## Cách xóa watermark văn bản trong sơ đồ bằng Java
Để xóa watermark văn bản, tải sơ đồ bằng `Watermarker`, tạo một `TextSearchCriteria` khớp với nội dung watermark, lấy `PossibleWatermarkCollection` phù hợp, và gọi `clear()` trên nó. Thao tác này chỉ loại bỏ các lớp phủ văn bản được chỉ định mà không ảnh hưởng đến các phần còn lại của sơ đồ.

Lớp `Watermarker` đại diện cho một tài liệu duy nhất trong bộ nhớ và cung cấp các phương thức để tải, tìm kiếm và chỉnh sửa watermark.

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
  - `inputFilePath`: Đường dẫn tới tệp `.vsdx` của bạn.  
  - `loadOptions`: Cấu hình cách tài liệu được tải (ví dụ: phạm vi trang, mật khẩu).

## Cách phát hiện watermark hình ảnh trong tệp sơ đồ?
Phát hiện watermark hình ảnh bao gồm việc tạo một `ImageDctHashSearchCriteria` với hình ảnh tham chiếu, sau đó dùng `Watermarker` để tìm kiếm trong sơ đồ. API sẽ tạo một hàm băm nhận thức cho mỗi hình ảnh nhúng và so sánh với hình tham chiếu, trả về các kết quả khớp kèm theo điểm tương đồng để bạn có thể xác định và loại bỏ các logo hoặc con dấu không mong muốn.

`ImageDctHashSearchCriteria` tạo hàm băm cho hình ảnh tham chiếu và so sánh với các hình ảnh nhúng trong sơ đồ, trả về các khớp kèm điểm tương đồng.

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
- **Các phương thức chính:**  
  - `TextSearchCriteria` – tạo tiêu chí cho watermark dạng văn bản.  
  - `PossibleWatermarkCollection` – chứa kết quả của bất kỳ thao tác tìm kiếm nào.

## Cách loại bỏ watermark sau khi đã tìm thấy?
Sau khi xác định được watermark, bạn có thể loại bỏ chúng bằng cách gọi phương thức `clear()` trên `PossibleWatermarkCollection` trả về từ quá trình tìm kiếm. Thao tác này xóa các đối tượng watermark trong khi giữ nguyên tất cả các thành phần khác của sơ đồ, đảm bảo nội dung gốc không bị thay đổi.

`clear()` xóa mọi watermark trong collection đồng thời bảo toàn phần còn lại của nội dung sơ đồ.

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
- **Phương thức chính:** `clear()` – xóa tất cả watermark trong collection được cung cấp mà không làm thay đổi các yếu tố khác của sơ đồ.

## Ứng dụng thực tiễn
1. **Tích hợp phần mềm doanh nghiệp** – nhúng quản lý watermark vào các ứng dụng kinh doanh tập trung vào tài liệu để bảo vệ các sơ đồ sở hữu.  
2. **Hệ thống quản lý nội dung (CMS)** – tự động phát hiện logo không được phép trước khi công bố các sơ đồ do người dùng tạo.  
3. **Xử lý tài liệu pháp lý** – thêm hoặc xóa watermark ở các giai đoạn khác nhau của quy trình hồ sơ vụ án, đảm bảo tuân thủ chính sách bảo mật.

## Những lỗi thường gặp và cách khắc phục
- **Tệp lớn** – tăng giá trị `maxMemory` trong `LoadOptions` nếu gặp `OutOfMemoryError`.  
- **Sơ đồ được bảo vệ bằng mật khẩu** – cung cấp mật khẩu trong `LoadOptions` để mở tệp.  
- **Không tìm thấy khớp băm hình ảnh** – đảm bảo hình ảnh tham chiếu có độ phân giải đủ; hình ảnh độ phân giải thấp có thể tạo ra băm yếu.

## Câu hỏi thường gặp

**H: Có thể tìm kiếm đồng thời cả văn bản và hình ảnh không?**  
Đ: Có – kết hợp `TextSearchCriteria` và `ImageDctHashSearchCriteria` với toán tử `or()` để xác định cả hai loại trong một lần quét.

**H: Có thể xóa watermark mà không làm hỏng sơ đồ không?**  
Đ: Hoàn toàn có thể. API tách riêng các đối tượng watermark và loại bỏ chúng, để lại cấu trúc sơ đồ gốc không thay đổi.

**H: GroupDocs.Watermark có hỗ trợ nhiều định dạng sơ đồ không?**  
Đ: Có – hỗ trợ hơn 20 định dạng, bao gồm `.vsdx`, `.vdx`, `.drawio` và `.svg`, giúp quản lý sơ đồ đa dạng.

**H: Làm sao xử lý khối lượng tài liệu lớn một cách hiệu quả?**  
Đ: Sử dụng vòng lặp batch, tái sử dụng một thể hiện `Watermarker` duy nhất khi có thể, và tinh chỉnh `LoadOptions` để stream các trang thay vì tải toàn bộ tệp.

**H: Có thể tích hợp phát hiện watermark vào pipeline CI/CD không?**  
Đ: Có – thư viện chạy ở chế độ headless và có thể được gọi từ Maven, Gradle hoặc bất kỳ script build nào để tự động kiểm tra tài sản sơ đồ.

---

**Last Updated:** 2026-10-27  
**Tested With:** GroupDocs.Watermark 23.6 for Java  
**Author:** GroupDocs

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

## Các hướng dẫn liên quan

- [Cách Thêm Watermark Văn Bản vào Sơ Đồ Sử Dụng GroupDocs.Watermark trong Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [Hướng Dẫn Thêm Watermark vào Sơ Đồ Sử Dụng GroupDocs.Watermark cho Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [Cách Lấy Thông Tin Tài Liệu Sử Dụng GroupDocs.Watermark cho Java: Hướng Dẫn Từng Bước](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)