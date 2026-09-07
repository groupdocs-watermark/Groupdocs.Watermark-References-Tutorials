---
date: '2026-03-17'
description: Tìm hiểu cách lưu hình ảnh biểu đồ PowerPoint và thiết lập nền biểu đồ
  bằng Java và GroupDocs.Watermark. Hãy làm theo hướng dẫn từng bước này để nâng cao
  khả năng trực quan hoá dữ liệu.
keywords:
- set chart background image PowerPoint
- Java GroupDocs.Watermark
- PowerPoint presentation enhancement
title: Lưu hình ảnh biểu đồ PowerPoint bằng Java & GroupDocs.Watermark
type: docs
url: /vi/java/presentation-document-watermarking/set-chart-background-image-powerpoint-java-groupdocs-watermark/
weight: 1
---

 keep markdown formatting.

Now produce final content.# Lưu Hình Ảnh Biểu Đồ PowerPoint Bằng Java & GroupDocs.Watermark

Trong hướng dẫn này, bạn sẽ học **cách lưu hình ảnh biểu đồ PowerPoint** và áp dụng nền tùy chỉnh, giúp bản trình bày của bạn trông chuyên nghiệp, đồng nhất với thương hiệu. Chúng tôi sẽ hướng dẫn toàn bộ quy trình bằng Java và GroupDocs.Watermark, từ việc thiết lập thư viện đến cấu hình độ trong suốt và các tùy chọn lặp lại.

## Câu trả lời nhanh
- **“save PowerPoint chart” có nghĩa là gì?** Nó có nghĩa là xuất biểu đồ dưới dạng một phần của tệp PowerPoint sau khi áp dụng các tùy chỉnh hình ảnh.  
- **Thư viện nào thêm hình nền cho biểu đồ?** GroupDocs.Watermark cho Java cung cấp một API đơn giản để đặt hình nền cho biểu đồ.  
- **Tôi có cần giấy phép không?** Một bản dùng thử miễn phí hoạt động cho việc đánh giá; giấy phép đầy đủ là bắt buộc cho việc sử dụng trong môi trường sản xuất.  
- **Tôi có thể lặp lại hình nền không?** Có – sử dụng phương thức `setTileAsTexture(true)` để lặp lại hình ảnh dưới dạng texture.  
- **Java 8 có đủ không?** Thư viện hỗ trợ JDK 8 và các phiên bản mới hơn.

## “save PowerPoint chart” là gì?
Lưu biểu đồ PowerPoint đề cập đến việc nhúng một biểu đồ vào trong slide và lưu lại mọi thay đổi về hình ảnh—như hình nền tùy chỉnh—vào tệp `.pptx` cuối cùng. Điều này cho phép bạn phân phối các bản trình bày đã có sẵn giao diện và cảm giác mong muốn.

## Tại sao đặt nền cho biểu đồ bằng GroupDocs.Watermark?
- **Độ nhất quán thương hiệu:** Áp dụng logo công ty hoặc texture chủ đề trực tiếp phía sau dữ liệu biểu đồ.  
- **Cải thiện khả năng đọc:** Điều chỉnh độ trong suốt để các điểm dữ liệu vẫn rõ ràng trong khi nền cung cấp ngữ cảnh hình ảnh.  
- **Tự động hoá:** Tích hợp quy trình vào các dịch vụ back‑end, pipeline xử lý hàng loạt, hoặc quy trình CI/CD.  
- **Hiệu suất:** GroupDocs.Watermark xử lý các bản trình bày lớn một cách hiệu quả, đặc biệt khi bạn tuân theo các mẹo tối ưu hoá được đề cập sau trong hướng dẫn này.

## Prerequisites

### Thư viện yêu cầu
- **GroupDocs.Watermark for Java** (latest release)  
- Java Development Kit (JDK) đã được cài đặt trên máy của bạn

### Cài đặt môi trường
- Một IDE như IntelliJ IDEA hoặc Eclipse được cấu hình với JDK.  
- Maven để quản lý phụ thuộc.

### Kiến thức tiên quyết
- Lập trình Java cơ bản và thao tác I/O với tệp.  
- Quen thuộc với cấu trúc slide và biểu đồ của PowerPoint.

## Setting Up GroupDocs.Watermark for Java

### Cài đặt qua Maven
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

### Tải trực tiếp
Hoặc tải phiên bản mới nhất trực tiếp từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Đăng ký giấy phép
- **Dùng thử miễn phí:** Khám phá tất cả tính năng mà không tốn phí.  
- **Giấy phép tạm thời:** Sử dụng cho các giai đoạn đánh giá kéo dài.  
- **Mua:** Nhận giấy phép đầy đủ để sử dụng không giới hạn trong môi trường sản xuất.

## Implementation Guide

### Tải tệp trình chiếu
First, load the PowerPoint file that contains the chart you want to modify:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\presentation.pptx", loadOptions);
```
- **Tại sao:** Điều này tạo một thể hiện `Watermarker` cho phép bạn truy cập chương trình vào nội dung của bản trình bày.

### Lấy và chỉnh sửa thuộc tính biểu đồ
Next, locate the chart and load the image you want to use as its background:

```java
PresentationContent content = watermarker.getContent(PresentationContent.class);

// Load image to be set as background for chart.
File imageFile = new File("YOUR_DOCUMENT_DIRECTORY\\test_image.png");
byte[] imageBytes = new byte[(int) imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
```
- **Tại sao:** Chuyển đổi hình ảnh thành mảng byte cho phép GroupDocs.Watermark nhúng trực tiếp vào định dạng tô màu của biểu đồ.

### Đặt hình nền cho biểu đồ
Now bind the image to the first chart on the first slide:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setBackgroundImage(new PresentationWatermarkableImage(imageBytes));
```
- **Tại sao:** Lệnh này thay thế nền mặc định của biểu đồ bằng hình ảnh tùy chỉnh của bạn, đạt được hiệu ứng **set chart background**.

### Cấu hình độ trong suốt và lặp lại
Fine‑tune the appearance with transparency and texture tiling:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTransparency(0.5);
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTileAsTexture(true);
```
- **Tại sao:** Độ trong suốt (`0.5`) giữ cho dữ liệu vẫn hiển thị, trong khi `setTileAsTexture(true)` **tile chart background** để tạo mẫu liền mạch.

### Lưu và đóng tài nguyên
Finally, write the modified presentation to disk and release resources:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY\\updated_presentation.pptx");
watermarker.close();
```
- **Tại sao:** Lưu các thay đổi tạo ra một tệp mới mà bạn có thể phân phối, và việc đóng `Watermarker` giải phóng tài nguyên hệ thống.

## Practical Applications

1. **Báo cáo doanh nghiệp:** Chèn logo thương hiệu hoặc màu sắc công ty làm nền cho biểu đồ.  
2. **Slide giáo dục:** Sử dụng hình ảnh chủ đề (ví dụ: bản đồ, phân tử) để làm dữ liệu hấp dẫn hơn.  
3. **Bộ trình marketing:** Thêm texture hoặc đồ họa kiểu watermark để làm nổi bật slide của bạn so với đối thủ.

## Performance Considerations

- Thay đổi kích thước hình ảnh trước khi nhúng để giữ kích thước tệp ở mức hợp lý.  
- Sử dụng try‑with‑resources cho các stream để đảm bảo dọn dẹp tự động.  
- Tránh tải toàn bộ bản trình bày lớn vào bộ nhớ một lúc; xử lý các slide một cách tuần tự khi có thể.

## Common Pitfalls & Troubleshooting

| Vấn đề | Giải pháp |
|-------|----------|
| `OutOfMemoryError` khi xử lý hình ảnh lớn | Thay đổi kích thước hình ảnh hoặc sử dụng tải dựa trên `InputStream` thay vì đọc toàn bộ tệp vào mảng byte. |
| Hình nền không hiển thị | Kiểm tra xem `ImageFillFormat` của biểu đồ có bị ghi đè sau này trong mã không. |
| Độ trong suốt quá tối | Điều chỉnh giá trị truyền vào `setTransparency()` (phạm vi 0.0–1.0). |

## Frequently Asked Questions

**Hỏi: Sự khác biệt giữa `setBackgroundImage` và `add watermark chart` là gì?**  
**Đáp:** `setBackgroundImage` thay thế phần tô màu của biểu đồ bằng một hình ảnh, trong khi việc thêm watermark chart sẽ phủ lên văn bản hoặc đồ họa bán trong suốt trên dữ liệu biểu đồ.

**Hỏi: Tôi có thể áp dụng cùng một nền cho nhiều biểu đồ cùng lúc không?**  
**Đáp:** Có — lặp qua `content.getSlides().get_Item(i).getCharts()` và áp dụng cùng một `PresentationWatermarkableImage` cho `ImageFillFormat` của mỗi biểu đồ.

**Hỏi: GroupDocs.Watermark có hỗ trợ GIF động làm nền cho biểu đồ không?**  
**Đáp:** Thư viện xử lý GIF như hình ảnh tĩnh; chỉ khung đầu tiên được sử dụng.

**Hỏi: Làm sao để đảm bảo nền được thu phóng đúng trên các kích thước slide khác nhau?**  
**Đáp:** Sử dụng `setTileAsTexture(true)` để lặp lại hình ảnh hoặc tính toán kích thước phù hợp dựa trên chiều rộng và chiều cao của slide trước khi đặt nền.

**Hỏi: Có cách nào để kiểm tra chương trình nếu một biểu đồ đã có hình nền chưa?**  
**Đáp:** Bạn có thể kiểm tra `getImageFillFormat().getBackgroundImage()`; nếu trả về `null`, thì chưa có hình ảnh được đặt.

## Resources
- **Tài liệu:** [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)
- **Tham chiếu API:** [GroupDocs.Watermark API Reference](https://reference.groupdocs.com/watermark/java)
- **Tải xuống:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)
- **Kho GitHub:** [GroupDocs.Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- **Diễn đàn hỗ trợ miễn phí:** [GroupDocs Watermark Forum](https://forum.groupdocs.com/c/watermark/10)
- **Đăng ký giấy phép tạm thời:** [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Cập nhật lần cuối:** 2026-03-17  
**Kiểm thử với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs