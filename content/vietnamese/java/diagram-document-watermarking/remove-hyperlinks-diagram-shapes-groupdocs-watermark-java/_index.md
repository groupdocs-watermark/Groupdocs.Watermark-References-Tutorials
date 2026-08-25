---
date: '2026-08-25'
description: Tìm hiểu cách chỉnh sửa tệp sơ đồ và xóa siêu liên kết bằng cách sử dụng
  GroupDocs.Watermark for Java. Bảo mật sơ đồ của bạn nhanh chóng với hướng dẫn từng
  bước.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Tìm hiểu cách chỉnh sửa tệp sơ đồ và xóa siêu liên kết bằng cách sử
  dụng GroupDocs.Watermark for Java. Thực hiện các bước rõ ràng để bảo vệ tài liệu
  của bạn.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Cách chỉnh sửa sơ đồ và xóa siêu liên kết bằng Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Cách chỉnh sửa sơ đồ và xóa siêu liên kết bằng Java
type: docs
url: /vi/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cách chỉnh sửa sơ đồ và xóa siêu liên kết bằng Java  

Quản lý tài liệu số thường liên quan đến việc chỉnh sửa sơ đồ, đặc biệt khi bạn cần **edit diagram** files để loại bỏ siêu liên kết vì lý do bảo mật hoặc độ rõ hình ảnh. Hướng dẫn này cho bạn thấy cách chỉnh sửa tệp sơ đồ và xóa các siêu liên kết không mong muốn khỏi các hình dạng trong sơ đồ bằng thư viện **GroupDocs.Watermark** mạnh mẽ cho Java. Khi kết thúc hướng dẫn, bạn sẽ có một sơ đồ sạch, không có liên kết, sẵn sàng để phân phối.  

## Câu trả lời nhanh  
- **What is the main goal?** Xóa tất cả các siêu liên kết khỏi các hình dạng trong sơ đồ để cải thiện bảo mật và trình bày.  
- **Which library is required?** GroupDocs.Watermark cho Java, phiên bản 24.11 hoặc mới hơn.  
- **Do I need a license?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Can I process many files at once?** Có – cùng một đoạn mã có thể đặt trong vòng lặp để xử lý hàng loạt.  
- **What Java version is supported?** Java 8 hoặc cao hơn (Java 11 được khuyến nghị).  

## “how to edit diagram” là gì?  
**How to edit diagram** đề cập đến quá trình mở một tệp sơ đồ một cách lập trình, sửa đổi các thành phần bên trong (như hình dạng, văn bản hoặc siêu liên kết), và lưu kết quả. Sử dụng GroupDocs.Watermark, bạn có thể chỉnh sửa tệp sơ đồ mà không cần công cụ tạo gốc.  

## Tại sao sử dụng GroupDocs.Watermark cho Java?  
GroupDocs.Watermark hỗ trợ **hơn 30 định dạng sơ đồ và hình ảnh** (bao gồm VSDX, SVG và WMF) và có thể xử lý các tệp lên tới **500 MB** mà không cần tải toàn bộ tài liệu vào bộ nhớ, mang lại tốc độ xử lý ** nhanh hơn 20 %** so với nhiều đối thủ.  

## Yêu cầu trước  
- **GroupDocs.Watermark** library version 24.11 hoặc mới hơn.  
- Maven đã cài đặt (hoặc các tệp JAR nếu bạn thích cài đặt thủ công).  
- Java Development Kit 8 hoặc mới hơn và một IDE như IntelliJ IDEA hoặc Eclipse.  

### Thư viện, phiên bản và phụ thuộc cần thiết  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (nếu bạn sử dụng cách Maven)  

### Yêu cầu thiết lập môi trường  
Đảm bảo thư mục `bin` của JDK có trong `PATH` và IDE của bạn trỏ tới phiên bản JDK đúng.  

### Kiến thức yêu cầu  
Bạn nên quen thuộc với cú pháp Java cơ bản, quản lý phụ thuộc Maven và các thao tác I/O với tệp.  

## Cách thiết lập GroupDocs.Watermark cho Java?  
Lớp `Watermarker` cung cấp điểm vào API để tải và sửa đổi tài liệu.  
Để bắt đầu sử dụng GroupDocs.Watermark, thêm tọa độ Maven của nó vào `pom.xml` dự án của bạn. Điều này sẽ tải thư viện và các phụ thuộc, cho phép bạn khởi tạo lớp Watermarker và làm việc với các tệp sơ đồ trực tiếp từ mã Java. Sau đó bạn có thể cấu hình giấy phép và đặt các tùy chọn đầu ra trước khi xử lý bất kỳ tài liệu nào.  

Thêm phụ thuộc GroupDocs.Watermark vào `pom.xml` của bạn.  

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

Nếu bạn không muốn sử dụng Maven, tải JAR mới nhất từ trang phát hành chính thức.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Các bước lấy giấy phép  
- Bắt đầu với bản dùng thử miễn phí để đánh giá API.  
- Đối với môi trường sản xuất, lấy giấy phép tạm thời hoặc vĩnh viễn từ cổng nhà cung cấp.  

#### Khởi tạo và thiết lập cơ bản  
Lớp `Watermarker` là điểm vào cho tất cả các thao tác xử lý tài liệu.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Cách chỉnh sửa sơ đồ và xóa siêu liên kết với GroupDocs.Watermark?  
Lớp `Watermarker` cung cấp điểm vào API để tải và sửa đổi tài liệu.  
Đầu tiên, tải tệp sơ đồ vào một thể hiện Watermarker. Sau đó lấy bộ sưu tập các hình dạng, xác định những hình chứa đối tượng siêu liên kết, và lặp qua chúng theo thứ tự ngược lại để xóa an toàn mỗi liên kết mà không ảnh hưởng đến chỉ mục của bộ sưu tập. Điều này đảm bảo tất cả URL nhúng được loại bỏ trong khi vẫn giữ nguyên tính toàn vẹn hình ảnh của sơ đồ.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Why this step matters**: Việc tải tệp cho phép bạn truy cập lập trình vào mọi hình dạng và các thuộc tính liên quan của chúng.  

## Cách truy cập nội dung hình dạng trong sơ đồ?  
Đối tượng `DiagramShape` đại diện cho một hình dạng riêng lẻ trong sơ đồ, hiển thị các thuộc tính và siêu dữ liệu đính kèm.  
Sau khi tải sơ đồ, gọi `getShapes()` trên Watermarker để nhận danh sách các đối tượng `DiagramShape`. Mỗi hình dạng có thể được kiểm tra để tìm bộ sưu tập siêu liên kết, cho phép nhắm mục tiêu chính xác các liên kết để xóa hoặc sửa đổi. Bạn cũng có thể đọc văn bản, màu sắc và hình học của hình dạng nếu cần điều chỉnh thêm.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Why this step matters**: Nhắm mục tiêu đúng hình dạng đảm bảo bạn chỉ xóa các liên kết không mong muốn mà không ảnh hưởng đến các yếu tố hình ảnh khác.  

## Cách lặp và xóa siêu liên kết một cách an toàn?  
Phương thức `removeHyperlink(int index)` xóa một siêu liên kết tại vị trí được chỉ định trong bộ sưu tập siêu liên kết của một hình dạng.  
Lặp qua danh sách siêu liên kết từ chỉ mục cuối cùng xuống 0. Vòng lặp ngược này ngăn việc thay đổi chỉ mục khi các mục bị xóa, đảm bảo mọi siêu liên kết được xử lý mà không bị bỏ qua. Sau khi xóa, bạn có thể làm mới trạng thái của hình dạng hoặc tiếp tục tới hình dạng tiếp theo trong sơ đồ.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Why this step matters**: Vòng lặp ngược đảm bảo rằng tất cả các siêu liên kết được xóa mà không bỏ sót bất kỳ mục nào.  

## Cách lưu sơ đồ đã chỉnh sửa và giải phóng tài nguyên?  
Phương thức `save(String path)` ghi tài liệu đã sửa đổi vào vị trí tệp được chỉ định, hoàn tất mọi thay đổi.  
Khi tất cả siêu liên kết đã được xóa, gọi phương thức `save` trên thể hiện Watermarker, cung cấp tên tệp mới để tránh ghi đè lên tệp gốc. Sau đó gọi `close()` để giải phóng các tay cầm tệp và giải phóng bộ nhớ, điều này rất quan trọng cho các quy trình batch chạy lâu. Điều này đảm bảo tệp được đóng đúng cách và sẵn sàng cho việc sử dụng tiếp theo.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Why this step matters**: Đóng đúng cách các tài nguyên tránh rò rỉ bộ nhớ và vấn đề khóa tệp trên máy chủ.  

## Ứng dụng thực tiễn  
Việc xóa siêu liên kết khỏi các hình dạng trong sơ đồ có thể hữu ích trong một số tình huống thực tế:  

1. **Security** – Ngăn chặn các liên kết bên ngoài có thể dẫn đến các trang độc hại.  
2. **Compliance** – Đáp ứng các chính sách công ty cấm URL nhúng trong tài sản chia sẻ.  
3. **Clarity** – Tạo các bản trình bày sạch hơn, nơi các liên kết có thể gây xao lạc.  

Bạn có thể nhúng logic này vào các pipeline tự động lớn hơn, chẳng hạn như các công việc batch hàng đêm làm sạch tất cả các sơ đồ trước khi chúng được công bố lên intranet.  

## Các yếu tố hiệu năng  

### Tối ưu hóa hiệu năng  
- Sử dụng một thể hiện `Watermarker` duy nhất cho mỗi tệp để giảm tải.  
- Ưu tiên lặp ngược (như đã trình bày) để tránh việc tái chỉ mục danh sách tốn kém.  

### Hướng dẫn sử dụng tài nguyên  
- Đối với các sơ đồ lớn hơn 200 MB, giám sát việc sử dụng heap và cân nhắc tăng cờ JVM `-Xmx`.  
- Các công cụ profiling như VisualVM có thể giúp xác định các nút thắt trong các chạy batch quy mô lớn.  

### Thực hành tốt cho quản lý bộ nhớ Java  
- Khai báo đối tượng trong phạm vi nhỏ nhất có thể.  
- Sử dụng try‑with‑resources khi làm việc với streams để đảm bảo đóng tự động.  

## Câu hỏi thường gặp  

**Q: Làm thế nào để xử lý các sơ đồ chứa hàng nghìn hình dạng?**  
A: Xử lý sơ đồ trang‑theo‑trang và giải phóng tài nguyên của mỗi trang trước khi chuyển sang trang tiếp theo để giữ mức sử dụng bộ nhớ thấp.  

**Q: Tôi có thể giới hạn việc xóa siêu liên kết chỉ ở các trang cụ thể không?**  
A: Có – lấy chỉ mục trang mong muốn, sau đó áp dụng vòng lặp xóa chỉ cho các hình dạng trên trang đó.  

**Q: Giấy phép thương mại có bắt buộc cho xử lý batch không?**  
A: Một giấy phép hợp lệ là cần thiết cho bất kỳ triển khai ở mức sản xuất nào; bản dùng thử miễn phí giới hạn 30 ngày và 5 tài liệu.  

**Q: GroupDocs.Watermark có hỗ trợ sơ đồ SVG không?**  
A: Hoàn toàn có – SVG nằm trong hơn 30 định dạng được hỗ trợ, và các siêu liên kết có thể được loại bỏ bằng cùng các lời gọi API.  

**Q: Nếu một hình dạng có nhiều siêu liên kết thì sao?**  
A: Vòng lặp lặp ngược sẽ xóa từng mục siêu liên kết riêng lẻ, đảm bảo mọi liên kết đều được xóa.  

## Tài nguyên  

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)  

---  

**Cập nhật lần cuối:** 2026-08-25  
**Kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs  

## Hướng dẫn liên quan

- [Hướng dẫn Đánh dấu Sơ đồ cho GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Chỉnh sửa tiêu đề & chân trang Sơ đồ trong Java bằng GroupDocs.Watermark: Hướng dẫn toàn diện](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Xóa hình dạng khỏi Sơ đồ một cách hiệu quả bằng GroupDocs.Watermark cho Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)