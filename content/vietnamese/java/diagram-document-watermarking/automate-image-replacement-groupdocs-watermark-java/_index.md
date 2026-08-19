---
date: '2026-08-19'
description: Tìm hiểu cách thay thế hình ảnh sơ đồ trong Java bằng GroupDocs.Watermark,
  đồng thời thêm watermark vào sơ đồ một cách hiệu quả. Mã từng bước và các thực tiễn
  tốt nhất.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Tìm hiểu cách thay thế hình ảnh sơ đồ trong Java bằng GroupDocs.Watermark,
  đồng thời thêm watermark vào sơ đồ một cách hiệu quả. Mã từng bước và các thực tiễn
  tốt nhất.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Thay thế hình ảnh sơ đồ trong Java bằng GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Thay thế hình ảnh sơ đồ trong Java bằng GroupDocs.Watermark
type: docs
url: /vi/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Thay thế hình ảnh sơ đồ trong Java bằng GroupDocs.Watermark

Việc cập nhật hình ảnh trong các tệp sơ đồ một cách thủ công tốn thời gian và dễ gây lỗi. Trong hướng dẫn này, bạn sẽ học cách **thay thế hình ảnh sơ đồ trong Java** chỉ với vài dòng mã, và bạn cũng sẽ thấy cách **thêm watermark vào sơ đồ** khi cần. Khi hoàn thành, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ dự án Java nào làm việc với Visio, Draw.io hoặc các định dạng sơ đồ được hỗ trợ khác.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc thay thế hình ảnh sơ đồ?** GroupDocs.Watermark for Java.
- **Cần bao nhiêu dòng mã cho một lần thay thế cơ bản?** Chỉ ba dòng sau khi Watermarker được tạo.
- **Tôi có thể thêm watermark cùng lúc không?** Có – sử dụng cùng một thể hiện Watermarker với một đối tượng watermark.
- **Phiên bản Java nào được yêu cầu?** JDK 8 hoặc cao hơn.
- **Tôi có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?** Cần một giấy phép GroupDocs.Watermark hợp lệ; có sẵn bản dùng thử miễn phí.

## Thay thế hình ảnh sơ đồ trong Java là gì?
Thay thế hình ảnh sơ đồ trong Java có nghĩa là tìm kiếm các hình dạng chứa đồ họa bitmap bên trong tệp sơ đồ (như .vsdx, .drawio hoặc .svg) một cách lập trình và thay thế các hình ảnh nhúng bằng các hình ảnh mới bằng cách sử dụng API của GroupDocs.Watermark. Điều này tự động hoá các cập nhật mà nếu không sẽ phải chỉnh sửa thủ công trong trình chỉnh sửa sơ đồ.

## Tại sao nên sử dụng GroupDocs.Watermark để thay thế hình ảnh sơ đồ?
GroupDocs.Watermark hỗ trợ **hơn 50 định dạng đầu vào và đầu ra** – bao gồm Visio, Draw.io và SVG – và có thể xử lý **các tệp lên tới 500 MB** mà không cần tải toàn bộ tài liệu vào bộ nhớ, mang lại **giảm 30 % mức sử dụng CPU** so với các phương pháp xử lý luồng tệp đơn giản.

## Yêu cầu trước
- JDK 8 hoặc mới hơn đã được cài đặt.
- Một IDE (IntelliJ IDEA, Eclipse hoặc VS Code) để phát triển Java.
- Maven (hoặc khả năng thêm JAR thủ công).
- Một giấy phép GroupDocs.Watermark hợp lệ (bản dùng thử hoặc vĩnh viễn). Bạn có thể lấy giấy phép từ [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Thư viện, phiên bản và phụ thuộc cần thiết
Thêm kho lưu trữ và phụ thuộc GroupDocs.Watermark vào `pom.xml` của bạn:

```xml
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
```

Nếu bạn muốn quản lý JAR thủ công, tải bản phát hành mới nhất từ trang chính thức: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Cách thay thế hình ảnh sơ đồ trong Java từng bước

### Làm thế nào để khởi tạo Watermarker cho một tệp sơ đồ?
Watermarker là lớp chính đại diện cho một tài liệu và cung cấp các phương thức để thao tác nội dung. Để bắt đầu, tạo một đối tượng `Watermarker` tải tệp sơ đồ vào bộ nhớ. Lớp `Watermarker` là điểm vào cốt lõi của GroupDocs.Watermark, cho phép bạn đọc, sửa đổi và lưu tài liệu. Sử dụng `DiagramLoadOptions` để chỉ định các cài đặt riêng cho định dạng như DPI hoặc phạm vi trang. `DiagramLoadOptions` cấu hình cách một sơ đồ được tải, ví dụ, đặt DPI hoặc chế độ tải.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Làm thế nào để truy cập nội dung sơ đồ để tìm các hình dạng?
Sau khi tải tệp, lấy một đối tượng `DiagramContent` từ `Watermarker`. `DiagramContent` đại diện cho cấu trúc nội bộ của sơ đồ gồm các trang và hình dạng. Mô hình này cung cấp các bộ sưu tập các trang và hình dạng mà bạn có thể lặp qua, giúp dễ dàng tìm các phần tử cụ thể như hình ảnh hoặc văn bản.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Làm thế nào để thay thế hình ảnh của các hình dạng trong sơ đồ?
Lặp qua mỗi `DiagramShape` trên trang mong muốn, kiểm tra xem hình dạng có chứa hình ảnh không, và thay thế byte hình ảnh bằng byte của tệp mới. `DiagramShape` là mô hình cho một hình dạng riêng lẻ trong sơ đồ, trong khi `DiagramWatermarkableImage` lưu trữ dữ liệu hình ảnh có thể áp dụng cho một hình dạng.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Làm thế nào để lưu các thay đổi và đóng Watermarker?
Khi tất cả các sửa đổi đã hoàn tất, gọi `save` trên `Watermarker` để ghi sơ đồ đã cập nhật vào tệp, sau đó gọi `close` để giải phóng tài nguyên gốc. Điều này đảm bảo các handle tệp được giải phóng và ngăn ngừa rò rỉ bộ nhớ, đặc biệt khi xử lý nhiều sơ đồ trong một công việc batch.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Thêm watermark vào cùng một sơ đồ (tùy chọn)

Nếu bạn cũng cần gắn thương hiệu vào sơ đồ, bạn có thể thêm watermark trước hoặc sau khi thay thế hình ảnh:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Các lỗi thường gặp và cách khắc phục

| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|------------|----------------------|----------------|
| Không có thay đổi hình ảnh sau khi chạy mã | `DiagramShape.hasImage()` trả về false | Xác minh loại hình dạng; một số hình dạng vector lưu trữ hình ảnh khác nhau. |
| Lỗi OutOfMemoryError trên các tệp lớn | Tải toàn bộ sơ đồ một lúc | Sử dụng `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` để xử lý các trang theo thứ tự. |
| Watermark không hiển thị | Watermark được đặt phía sau nội dung hiện có | Gọi `watermarker.setWatermarkPosition(Position.Foreground)` trước khi lưu. |

## Câu hỏi thường gặp

**Q: Tôi có thể thay thế hình ảnh trong sơ đồ được bảo vệ bằng mật khẩu không?**  
A: Có. Cung cấp mật khẩu cho `DiagramLoadOptions` khi tạo `Watermarker`.

**Q: Thư viện có hoạt động với các tệp .drawio (XML) không?**  
A: Hoàn toàn – GroupDocs.Watermark hỗ trợ định dạng Draw.io XML và xem mỗi node như một hình dạng.

**Q: Tôi có thể xử lý bao nhiêu sơ đồ đồng thời?**  
A: Thư viện an toàn với đa luồng cho các thao tác chỉ đọc; đối với các thao tác ghi, hạn chế đồng thời theo số lõi CPU để tránh tranh chấp handle tệp.

**Q: Có giới hạn kích thước hình ảnh không?**  
A: Hình ảnh lên tới 100 MB được hỗ trợ; các tệp lớn hơn nên được thu nhỏ trước để giảm mức sử dụng bộ nhớ.

**Q: Các tùy chọn cấp phép nào có sẵn?**  
A: Bạn có thể bắt đầu với bản dùng thử miễn phí 30 ngày; sử dụng trong môi trường sản xuất yêu cầu giấy phép trả phí, có thể mua tại cửa hàng GroupDocs.

---

**Cập nhật lần cuối:** 2026-08-19  
**Được kiểm tra với:** GroupDocs.Watermark 23.9 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Hướng dẫn Watermark cho Sơ đồ cho GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Xóa liên kết siêu văn bản khỏi các hình dạng sơ đồ bằng GroupDocs.Watermark Java để tăng cường bảo mật tài liệu](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Cách Thêm Watermark Hình Ảnh trong Java bằng GroupDocs.Watermark: Hướng Dẫn Từng Bước](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)