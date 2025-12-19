---
date: '2025-12-19'
description: Học cách thêm dấu nước văn bản vào sơ đồ với GroupDocs.Watermark cho
  Java. Hướng dẫn từng bước này bao gồm cài đặt, thiết lập phông chữ dấu nước và các
  trường hợp sử dụng thực tế.
keywords:
- text watermarks in Java
- add text watermark to diagram
- GroupDocs Watermark for Java setup
title: Cách thêm watermark văn bản vào sơ đồ bằng GroupDocs.Watermark cho Java
type: docs
url: /vi/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Cách thêm watermark văn bản vào sơ đồ bằng GroupDocs.Watermark cho Java

Bảo vệ các sơ đồ của bạn khỏi việc sử dụng trái phép là ưu tiên hàng đầu của nhiều nhà phát triển và nhà thiết kế. Trong hướng dẫn này, bạn sẽ học **cách thêm watermark văn bản** vào các tệp sơ đồ bằng thư viện mạnh mẽ **GroupDocs.Watermark cho Java**. Chúng tôi sẽ hướng dẫn từng bước—từ cài đặt Maven đến việc áp dụng các cài đặt font watermark tùy chỉnh—để bạn có thể bảo vệ tài sản hình ảnh của mình một cách nhanh chóng và đáng tin cậy.

## Câu trả lời nhanh
- **Thư viện làm gì?** Nó nhúng watermark văn bản (hoặc hình ảnh) vào hơn 100 định dạng tài liệu và sơ đồ.  
- **Từ khóa chính tôi nên nhắm tới là gì?** *add text watermark* – được sử dụng xuyên suốt trong hướng dẫn này.  
- **Tôi có cần giấy phép không?** Giấy phép dùng thử tạm thời hoạt động cho việc phát triển; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Tôi có thể tùy chỉnh phông chữ không?** Có, bạn có thể điều khiển họ phông, kích thước, màu sắc và góc quay qua cài đặt font watermark.  
- **Có tương thích với Java‑8 không?** Chắc chắn – thư viện hỗ trợ JDK 8 và các phiên bản mới hơn.

## “add text watermark” là gì?
Thêm watermark văn bản có nghĩa là chồng lên văn bản bán trong suốt trên mỗi trang hoặc hình dạng của tài liệu để nội dung vẫn có thể nhận dạng được. Kỹ thuật này thường được sử dụng cho việc xây dựng thương hiệu, bảo vệ bản quyền và chỉnh sửa hợp tác.

## Tại sao nên sử dụng GroupDocs.Watermark cho Java?
- **Hỗ trợ định dạng rộng** – hoạt động với Visio, SVG, PDF, Word và nhiều hơn nữa.  
- **Kiểm soát chi tiết** – bạn có thể đặt phông chữ, màu sắc, góc quay, độ mờ và vị trí.  
- **API đơn giản** – chỉ vài dòng mã đã hoàn thành công việc, tiết kiệm thời gian phát triển.  
- **Tối ưu hiệu năng** – xử lý các tệp lớn hiệu quả khi bạn đóng tài nguyên kịp thời.

## Yêu cầu trước
- JDK 8 hoặc cao hơn đã được cài đặt trên máy của bạn.  
- Một IDE như IntelliJ IDEA hoặc Eclipse.  
- Kiến thức Java cơ bản (lớp, đối tượng và Maven).

### Thư viện và phụ thuộc cần thiết
Chúng tôi sẽ sử dụng Maven để kéo thư viện GroupDocs.Watermark. Thêm kho và phụ thuộc vào `pom.xml` của bạn chính xác như sau:

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

Nếu bạn muốn tải xuống thủ công, hãy truy cập trang chính thức: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) và làm theo hướng dẫn.

### Cách lấy giấy phép
Bắt đầu với bản dùng thử miễn phí bằng cách lấy giấy phép tạm thời từ cổng thử nghiệm: [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Tải file giấy phép trước khi thực hiện bất kỳ thao tác watermark nào:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Hướng dẫn triển khai

### Bước 1: Tải sơ đồ của bạn
Đầu tiên, chỉ định `Watermarker` tới tệp sơ đồ nguồn của bạn. Đối tượng `DiagramLoadOptions` cho thư viện biết rằng tệp này là định dạng sơ đồ.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Bước 2: Khởi tạo Text Watermark (với **cài đặt font watermark** tùy chỉnh)
Tạo một thể hiện `TextWatermark`, chỉ định văn bản, họ phông, kích thước và bất kỳ kiểu dáng bổ sung nào bạn cần.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

> **Mẹo chuyên nghiệp:** Điều chỉnh `setColor` và `setRotationAngle` để phù hợp với hướng dẫn thương hiệu của bạn. Lệnh `setBackground(false)` đảm bảo watermark nằm trên các hình dạng của sơ đồ thay vì phía sau chúng.

### Bước 3: Chọn vị trí – Nền hay phía trước
GroupDocs cho phép bạn quyết định watermark xuất hiện phía sau các hình dạng của sơ đồ (nền) hay ở trên (phía trước). Trong hầu hết các trường hợp thương hiệu, vị trí nền là lựa chọn tốt nhất.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Bước 4: Lưu sơ đồ đã được watermark
Cuối cùng, ghi tệp đã chỉnh sửa ra đĩa và giải phóng tài nguyên.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Các vấn đề thường gặp và giải pháp

| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|------------|-------------------|----------------|
| **Lỗi File không tìm thấy** | Sai `inputFilePath` hoặc thiếu quyền đọc | Kiểm tra lại đường dẫn và đảm bảo quá trình Java có thể đọc tệp. |
| **Watermark không hiển thị** | Vị trí được đặt là `Foreground` với màu trong suốt | Sử dụng vị trí `Background` hoặc chọn màu tương phản. |
| **Ngoại lệ Out‑of‑memory** trên các sơ đồ lớn | Không đóng `Watermarker` hoặc xử lý nhiều tệp trong vòng lặp | Gọi `watermarker.close()` sau mỗi tệp và cân nhắc xử lý theo lô. |
| **Giấy phép không được nhận dạng** | Đường dẫn file giấy phép sai hoặc bản dùng thử đã hết hạn | Kiểm tra lại đường dẫn và sử dụng file giấy phép hiện tại. |

## Ứng dụng thực tiễn
1. **Bảo mật tài liệu** – Ngăn đối thủ sao chép các sơ đồ luồng độc quyền.  
2. **Xây dựng thương hiệu** – Nhúng tên công ty hoặc logo trên mọi trang sơ đồ.  
3. **Theo dõi hợp tác** – Thêm chữ ký người dùng dưới dạng watermark để chỉ ra ai đã chỉnh sửa sơ đồ.  

## Các cân nhắc về hiệu năng
- Đóng `Watermarker` ngay sau khi lưu để giải phóng tài nguyên gốc.  
- Giữ văn bản watermark ngắn gọn; phông chữ quá lớn làm tăng thời gian xử lý.  
- Kiểm tra trên mẫu đại diện trước khi xử lý hàng nghìn tệp theo lô.  

## Kết luận
Bạn giờ đã có một phương pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **thêm watermark văn bản** vào các tệp sơ đồ bằng **GroupDocs.Watermark cho Java**. Cách tiếp cận này bảo vệ tài sản trí tuệ của bạn đồng thời cho phép bạn kiểm soát toàn bộ cài đặt font watermark và vị trí.

### Các bước tiếp theo
- Khám phá watermark hình ảnh để tạo điểm nhấn thương hiệu trực quan.  
- Kết hợp nhiều watermark (văn bản + hình ảnh) để bảo vệ lớp.  
- Tự động hoá xử lý hàng loạt bằng vòng lặp `for` đơn giản và các cuộc gọi API tương tự.  

## Phần Câu hỏi thường gặp
1. **Tôi có thể sử dụng GroupDocs.Watermark cho các định dạng tệp khác không?**  
   Có, nó hỗ trợ một loạt các loại tài liệu ngoài sơ đồ, bao gồm PDF, DOCX, PPTX và nhiều hơn nữa.  
2. **Có giới hạn số lượng watermark tôi có thể thêm không?**  
   Không có giới hạn cứng, nhưng việc thêm quá nhiều watermark phức tạp có thể ảnh hưởng đến hiệu năng.  
3. **Làm sao để loại bỏ watermark khỏi một sơ đồ?**  
   Thư viện cung cấp API phát hiện và loại bỏ; xem tài liệu chính thức để biết chi tiết.  
4. **Có thể thêm watermark văn bản chỉ vào một số trang hoặc các hình dạng được chọn không?**  
   Bạn có thể cấu hình `DiagramShapeWatermarkOptions` để nhắm mục tiêu các trang hoặc hình dạng cụ thể.  
5. **Nếu watermark không xuất hiện như mong đợi, tôi nên làm gì?**  
   Kiểm tra lại cài đặt vị trí, độ tương phản màu phông và đảm bảo bạn đã lưu tệp sau khi thêm watermark.  

## Câu hỏi thường gặp

**Q: GroupDocs.Watermark có hoạt động với các phiên bản Java mới nhất không?**  
A: Có, nó hoàn toàn tương thích với Java 8 đến Java 21.  

**Q: Tôi có thể tùy chỉnh độ mờ của watermark văn bản không?**  
A: Chắc chắn. Sử dụng `textWatermark.setOpacity(0.5)` để đặt độ mờ 50 %.  

**Q: Có cách nào để chỉ thêm watermark vào các hình dạng sơ đồ được chọn không?**  
A: Bạn có thể lọc các hình dạng qua `DiagramShapeWatermarkOptions` bằng cách cung cấp ID hoặc tên hình dạng.  

**Q: Làm sao để xử lý các tệp sơ đồ được bảo vệ bằng mật khẩu?**  
A: Tải tệp bằng `DiagramLoadOptions` bao gồm mật khẩu, sau đó áp dụng watermark như bình thường.  

**Q: Có bất kỳ hạn chế nào về giấy phép cho việc sử dụng thương mại không?**  
A: Giấy phép thương mại là bắt buộc cho các triển khai sản xuất; giấy phép dùng thử chỉ dành cho đánh giá.  

## Tài nguyên
- [Tài liệu](https://docs.groupdocs.com/watermark/java/)
- [Tham chiếu API](https://reference.groupdocs.com/watermark/java)
- [Tải phiên bản mới nhất](https://releases.groupdocs.com/watermark/java/)
- [Kho GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Diễn đàn hỗ trợ miễn phí](https://forum.groupdocs.com/c/watermark/10)

---

**Cập nhật lần cuối:** 2025-12-19  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs