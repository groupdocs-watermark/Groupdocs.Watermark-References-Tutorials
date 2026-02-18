---
date: '2026-02-18'
description: Tìm hiểu cách thêm watermark vào các sơ đồ bằng GroupDocs.Watermark cho
  Java. Bảo vệ nội dung hình ảnh của bạn một cách hiệu quả và đảm bảo tính toàn vẹn
  của tài liệu.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: 'Cách Thêm Đánh Dấu Nước vào Sơ Đồ bằng GroupDocs.Watermark cho Java: Hướng
  Dẫn Toàn Diện'
type: docs
url: /vi/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Cách Thêm Watermark vào Sơ Đồ Sử Dụng GroupDocs.Watermark cho Java: Hướng Dẫn Toàn Diện  

## Giới thiệu  
Trong hướng dẫn này, bạn sẽ khám phá **cách thêm watermark** vào các tệp sơ đồ của mình để chúng được bảo vệ khỏi việc sử dụng trái phép. Thêm watermark dạng văn bản là một cách đơn giản nhưng mạnh mẽ để đánh dấu quyền sở hữu, thương hiệu tài sản của bạn, hoặc tuân thủ các yêu cầu pháp lý. Hướng dẫn toàn diện này trình bày cách tích hợp watermark dạng văn bản vào sơ đồ bằng **GroupDocs.Watermark cho Java** — một thư viện mạnh mẽ được thiết kế để watermark nhiều định dạng tài liệu khác nhau.  

### Câu trả lời nhanh  
- **Mục đích chính của watermark là gì?** Để nhận dạng quyền sở hữu một cách trực quan và ngăn chặn việc sao chép trái phép.  
- **Thư viện nào hỗ trợ watermark cho sơ đồ trong Java?** GroupDocs.Watermark cho Java.  
- **Có cần Maven để sử dụng thư viện không?** Có, bạn có thể thêm nó qua Maven (xem phần “groupdocs watermark maven”).  
- **Có thể tùy chỉnh phông chữ, kích thước và màu sắc không?** Chắc chắn — sử dụng API `TextWatermark` để cấu hình các thuộc tính này.  
- **Có cần giấy phép cho môi trường production không?** Cần một giấy phép GroupDocs.Watermark hợp lệ cho các triển khai production.  

## “Cách thêm watermark” trong ngữ cảnh sơ đồ là gì?  
Thêm watermark có nghĩa là nhúng một lớp văn bản bán trong suốt vào mỗi trang hoặc hình dạng của tệp sơ đồ (ví dụ: Visio, SVG). Watermark sẽ đi cùng tệp, hiển thị cho bất kỳ ai mở tài liệu, đồng thời không làm ảnh hưởng đáng kể đến thiết kế gốc.  

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?  
- **Hỗ trợ đa định dạng** – Xử lý Visio, SVG và nhiều loại sơ đồ khác.  
- **Tích hợp Maven dễ dàng** – Thực hiện các bước “groupdocs watermark maven” để bắt đầu nhanh chóng.  
- **Đặt vị trí chi tiết** – Kiểm soát chính xác nơi watermark xuất hiện (nền, phía trước, các hình dạng cụ thể).  
- **Tối ưu hiệu năng** – Thiết kế cho các tệp lớn với mức tiêu thụ bộ nhớ tối thiểu.  

## Yêu cầu trước  
- **GroupDocs.Watermark cho Java** (phiên bản 24.11 trở lên)  
- **Java Development Kit (JDK)** 8+  
- Một IDE như IntelliJ IDEA hoặc Eclipse  
- Maven để quản lý phụ thuộc (không bắt buộc nhưng được khuyến nghị)  

## Cài đặt GroupDocs.Watermark cho Java  

### Cấu hình Maven (groupdocs watermark maven)  
Thêm các mục repository và dependency sau vào tệp `pom.xml` của bạn:  

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

**Tải trực tiếp** – Bạn cũng có thể tải JAR mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).  

### Mua giấy phép  
- **Dùng thử miễn phí** – Đánh giá thư viện mà không cần key giấy phép.  
- **Giấy phép tạm thời** – Sử dụng key tạm thời trong quá trình phát triển để mở khóa tất cả tính năng.  
- **Mua bản quyền** – Mua giấy phép production để sử dụng không giới hạn.  

### Khởi tạo và thiết lập cơ bản  
Bao gồm các import cần thiết trong lớp Java của bạn:  

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Cách Thêm Watermark vào Tài liệu Sơ Đồ  

### Bước 1: Tải tài liệu sơ đồ  
Đầu tiên, chỉ định thư viện tới tệp sơ đồ bạn muốn bảo vệ và tạo một thể hiện `Watermarker`.  

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Giải thích*: `DiagramLoadOptions` cho phép bạn tinh chỉnh cách sơ đồ được phân tích (ví dụ: xử lý phông chữ nhúng).  

### Bước 2: Cấu hình Text Watermark (cấu hình watermark dạng văn bản)  
Tạo một đối tượng `TextWatermark` và đặt các thuộc tính hiển thị như phông chữ, kích thước và màu sắc.  

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Giải thích*: Dòng này tạo một watermark có nội dung **“Test watermark 1”** với phông chữ Calibri 19‑point. Bạn có thể tùy chỉnh thêm bằng `setColor()`, `setOpacity()`, v.v.  

### Bước 3: Định nghĩa tùy chọn đặt vị trí cho các hình dạng sơ đồ  
Xác định nơi watermark sẽ xuất hiện trong sơ đồ (nền, phía trước, hoặc các hình dạng cụ thể).  

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Giải thích*: Lớp `DiagramShapeWatermarkOptions` kiểm soát vị trí. Ở đây chúng ta chọn `SeparateBackgrounds` để watermark được vẽ trên mỗi lớp nền.  

### Bước 4: Thêm watermark và lưu tài liệu  
Cuối cùng, áp dụng watermark và ghi tệp đã bảo vệ ra đĩa.  

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Giải thích*: `add()` chèn watermark đã cấu hình theo các tùy chọn đã định, `save()` ghi kết quả, và `close()` giải phóng tài nguyên gốc.  

## Ứng dụng thực tiễn  
- **Bảo vệ sở hữu trí tuệ** – Ngăn đối thủ tái sử dụng các sơ đồ độc quyền.  
- **Thương hiệu** – Hiển thị nhất quán tên công ty hoặc logo trên mọi tài sản xuất khẩu.  
- **Pháp lý & Tuân thủ** – Đánh dấu các sơ đồ bí mật với watermark “Confidential”.  
- **Nộp bài học thuật** – Gắn nhãn công việc sinh viên với các định danh duy nhất để theo dõi đạo văn.  

## Các lưu ý về hiệu năng  
- **Quản lý bộ nhớ** – Tái sử dụng các thể hiện `Watermarker` khi xử lý hàng loạt tệp.  
- **Dọn dẹp tài nguyên** – Luôn gọi `watermarker.close()` trong khối `finally` hoặc dùng try‑with‑resources nếu hỗ trợ.  
- **Tệp lớn** – Đối với sơ đồ đa megabyte, cân nhắc xử lý từng trang riêng biệt để giảm mức tiêu thụ bộ nhớ tối đa.  

## Kết luận  
Bạn đã có một phương pháp hoàn chỉnh, từng bước để **cách thêm watermark** vào tài liệu sơ đồ bằng GroupDocs.Watermark cho Java. Bằng cách tải sơ đồ, cấu hình `TextWatermark`, thiết lập tùy chọn vị trí và lưu kết quả, bạn có thể bảo vệ các tài sản hình ảnh của mình một cách tối thiểu công sức.  

Tiếp theo, hãy thử nghiệm các phông chữ, màu sắc và mức độ trong suốt khác nhau, hoặc khám phá xử lý batch để tự động watermark toàn bộ thư viện sơ đồ.  

## Phần Câu Hỏi Thường Gặp  
**1. Kích thước phông chữ tốt nhất cho watermark là bao nhiêu?**  
Kích thước phông chữ tối ưu phụ thuộc vào loại tài liệu và yêu cầu về độ nhìn thấy.  

**2. Có thể tùy chỉnh màu sắc của watermark không?**  
Có, đặt màu tùy chỉnh bằng phương thức `textWatermark.setColor()`.  

**3. Làm sao xử lý hàng loạt tài liệu lớn?**  
Sử dụng các phương thức API được thiết kế cho xử lý batch để tăng hiệu quả.  

**4. Có bất kỳ hạn chế nào với GroupDocs.Watermark không?**  
Xem lại [documentation](https://docs.groupdocs.com/watermark/java/) để biết chi tiết về hỗ trợ tính năng và lưu ý tương thích.  

**5. Làm sao nhận được hỗ trợ nếu gặp vấn đề?**  
Truy cập [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) để được hỗ trợ và hướng dẫn miễn phí.  

## Các Câu Hỏi Thường Gặp Bổ Sung  

**Q: Có thể thay đổi độ trong suốt của watermark không?**  
A: Có, gọi `textWatermark.setOpacity(0.5)` (giá trị từ 0 – 1).  

**Q: Có thể watermark chỉ các trang được chọn không?**  
A: Sử dụng `DiagramPageWatermarkOptions` để nhắm mục tiêu các trang hoặc hình dạng cụ thể.  

**Q: Thư viện có hỗ trợ sơ đồ SVG không?**  
A: Chắc chắn — GroupDocs.Watermark xử lý SVG, Visio và nhiều định dạng sơ đồ khác.  

**Q: Làm sao áp dụng watermark cho sơ đồ được bảo vệ bằng mật khẩu?**  
A: Cung cấp mật khẩu qua `DiagramLoadOptions.setPassword("yourPassword")` trước khi tải.  

**Q: Yêu cầu phiên bản Java nào?**  
A: Java 8 hoặc mới hơn được hỗ trợ đầy đủ.  

## Tài Nguyên  
- **Tài liệu**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Tham chiếu API**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Tải xuống**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **Kho GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Diễn đàn hỗ trợ miễn phí**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Giấy phép tạm thời**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---  

**Cập nhật lần cuối:** 2026-02-18  
**Kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs  

---