---
date: '2025-12-19'
description: Tìm hiểu cách xóa siêu liên kết khỏi các hình dạng biểu đồ bằng GroupDocs.Watermark
  Java, một bước quan trọng cho bảo mật tài liệu Java và xóa hàng loạt siêu liên kết.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Cách loại bỏ siêu liên kết khỏi các hình dạng sơ đồ bằng GroupDocs.Watermark
  Java
type: docs
url: /vi/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cách Xóa Liên Kết Siêu Văn Bản khỏi Các Hình trong Sơ Đồ bằng GroupDocs.Watermark Java

Quản lý tài liệu kỹ thuật số thường liên quan đến việc chỉnh sửa sơ đồ, đặc biệt khi **xóa liên kết siêu văn bản** vì lý do bảo mật hoặc rõ ràng. Trong hướng dẫn này, bạn sẽ học **cách xóa liên kết siêu văn bản** khỏi các hình trong sơ đồ bằng GroupDocs.Watermark cho Java, giúp tệp của bạn luôn sạch sẽ, an toàn và chuyên nghiệp.

## Câu trả lời nhanh
- **Mục đích chính là gì?** Loại bỏ các liên kết siêu văn bản không mong muốn khỏi các hình trong sơ đồ để tăng cường bảo mật tài liệu.  
- **Thư viện nào được sử dụng?** GroupDocs.Watermark cho Java (phiên bản 24.11 trở lên).  
- **Có cần giấy phép không?** Bản dùng thử đủ cho việc thử nghiệm; giấy phép hợp lệ cần thiết cho môi trường sản xuất.  
- **Có thể xử lý nhiều tệp cùng lúc không?** Có – cùng một logic có thể được đặt trong vòng lặp batch.  
- **Java 8 có đủ không?** Java 8+ được hỗ trợ; khuyến nghị sử dụng các JDK mới hơn.

## “Cách xóa liên kết siêu văn bản” trong ngữ cảnh sơ đồ là gì?
Xóa liên kết siêu văn bản có nghĩa là xoá các tham chiếu URL được gắn vào các hình bên trong tệp sơ đồ (ví dụ: Visio *.vsdx). Thao tác này ngăn ngừa việc điều hướng vô tình tới các trang bên ngoài và giúp đáp ứng các quy định tuân thủ hoặc chính sách bảo mật nội bộ.

## Tại sao nên dùng GroupDocs.Watermark Java cho nhiệm vụ này?
- **Hỗ trợ định dạng mạnh mẽ** – hoạt động với nhiều loại sơ đồ khác nhau.  
- **API chi tiết** – cho phép bạn nhắm mục tiêu từng hình và bộ sưu tập liên kết của chúng.  
- **Tối ưu hiệu năng** – phù hợp cho cả tệp đơn lẻ và xử lý hàng loạt.  

## Yêu cầu trước
- Thư viện **GroupDocs.Watermark** phiên bản 24.11 trở lên.  
- Maven hoặc tải JAR trực tiếp (xem các bước thiết lập bên dưới).  
- Java Development Kit (JDK 8 hoặc mới hơn) và một IDE như IntelliJ IDEA hoặc Eclipse.  

## Thiết lập GroupDocs.Watermark cho Java
Để bắt đầu, thêm thư viện vào dự án của bạn qua Maven hoặc tải JAR.

### Cài đặt Maven
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

### Tải trực tiếp
Hoặc tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Các bước lấy giấy phép
- Bắt đầu với bản dùng thử miễn phí để đánh giá API.  
- Đối với môi trường sản xuất, lấy giấy phép tạm thời hoặc đầy đủ từ cổng thông tin GroupDocs.

#### Khởi tạo và thiết lập cơ bản
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cách Xóa Liên Kết Siêu Văn Bản khỏi Các Hình trong Sơ Đồ
Dưới đây là hướng dẫn từng bước giúp bạn tải sơ đồ, xác định các hình, và loại bỏ các liên kết siêu văn bản không mong muốn.

### Bước 1: Tải tệp sơ đồ
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Tại sao?* Tải tệp cho phép bạn truy cập chương trình vào cấu trúc nội bộ của nó.

### Bước 2: Truy cập nội dung hình
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Tại sao?* Bạn cần một tham chiếu tới hình cụ thể có thể chứa liên kết siêu văn bản.

### Bước 3: Duyệt và xóa liên kết
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Tại sao?* Duyệt ngược giúp tránh lỗi chỉ mục khi bạn xoá mục khỏi bộ sưu tập.

### Bước 4: Lưu và đóng
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Tại sao?* Ghi lại các thay đổi và giải phóng tài nguyên để tránh rò rỉ bộ nhớ và tệp bị khóa.

## Xóa Liên Kết Siêu Văn Bản Hàng Loạt (Trường Hợp Sử Dụng Nâng Cao)
Nếu bạn cần làm sạch nhiều sơ đồ cùng lúc, hãy đặt logic trên vào trong một vòng lặp duyệt danh sách các đường dẫn tệp. Các lời gọi API vẫn giống nhau; chỉ cần thay đổi thư mục đầu vào và đầu ra cho mỗi lần lặp. Cách này đáp ứng yêu cầu **xóa liên kết siêu văn bản hàng loạt** cho các kho tài liệu lớn.

## Ứng Dụng Thực Tiễn
Việc xóa liên kết siêu văn bản khỏi các hình trong sơ đồ có thể hữu ích trong một số tình huống thực tế:

1. **Mục đích bảo mật** – Ngăn chặn các liên kết bên ngoài có thể đưa mạng của bạn vào rủi ro phishing hoặc phần mềm độc hại.  
2. **Tuân thủ** – Đáp ứng các chính sách công ty cấm URL ra ngoài trong tài liệu được chia sẻ.  
3. **Rõ ràng** – Tạo ra các bản trình bày sạch sẽ hơn khi các liên kết không cần thiết hoặc gây phân tâm.  

## Các Yếu Tố Ảnh Hưởng Đến Hiệu Suất
### Tối ưu hoá hiệu suất
- Sử dụng mẫu duyệt ngược như đã trình bày ở trên để giữ vòng lặp hiệu quả.  
- Đóng đối tượng `Watermarker` ngay khi hoàn thành để giải phóng bộ nhớ.

### Hướng dẫn sử dụng tài nguyên
- Giám sát CPU và RAM khi xử lý các sơ đồ lớn.  
- Đối với công việc batch, cân nhắc streaming tệp thay vì tải toàn bộ vào bộ nhớ cùng lúc.

### Thực hành tốt cho quản lý bộ nhớ Java
- Tránh tạo đối tượng bên trong các vòng lặp chặt.  
- Sử dụng `try‑with‑resources` khi có thể để tự động dọn dẹp.

## Câu Hỏi Thường Gặp
1. **Làm sao để xử lý nhiều hình?**  
   Duyệt qua tất cả các trang và các hình của chúng, áp dụng cùng một logic xóa liên kết cho mỗi hình.  

2. **Quá trình này có thể tự động hoá cho hàng loạt sơ đồ lớn không?**  
   Có – nhúng mã vào quy trình batch‑processing hoặc tích hợp vào hệ thống quản lý tài liệu của bạn.  

3. **Nếu tôi chỉ muốn xóa liên kết trên các trang cụ thể thì sao?**  
   Truy cập trang mong muốn bằng chỉ mục (`content.getPages().get_Item(pageIndex)`) và chỉ nhắm mục tiêu các hình trên trang đó.  

4. **Có cần giấy phép nào cho việc sử dụng GroupDocs.Watermark trong môi trường sản xuất không?**  
   Cần một giấy phép thương mại hợp lệ sau thời gian dùng thử.  

5. **Phương pháp này có hoạt động với các định dạng sơ đồ khác không?**  
   GroupDocs.Watermark hỗ trợ nhiều loại sơ đồ; hãy kiểm tra tính tương thích trong tài liệu chính thức.  

**Câu hỏi bổ sung**

**Hỏi:** *Có thể ghi lại các liên kết đã bị xóa không?*  
**Đáp:** Có – trước khi gọi `removeAt(i)`, lấy địa chỉ bằng `shape.getHyperlinks().get_Item(i).getAddress()` và ghi vào file log.

**Hỏi:** *Việc xóa liên kết có ảnh hưởng đến giao diện hình không?*  
**Đáp:** Không. Hình học của hình vẫn giữ nguyên; chỉ metadata liên kết bị loại bỏ.

**Hỏi:** *Có cần áp dụng lại bất kỳ kiểu dáng nào sau khi xóa không?*  
**Đáp:** Thông thường không. Việc xóa liên kết không thay đổi màu nền, đường viền hay kiểu chữ.

## Kết Luận
Bạn đã có một phương pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **cách xóa liên kết siêu văn bản** khỏi các hình trong sơ đồ bằng GroupDocs.Watermark cho Java. Thực hiện các bước trên, bạn có thể bảo vệ sơ đồ, tuân thủ chính sách và giữ cho tài liệu của mình luôn gọn gàng, chuyên nghiệp.

**Tài nguyên**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Cập nhật lần cuối:** 2025-12-19  
**Đã kiểm tra với:** GroupDocs.Watermark 24.11 cho Java  
**Tác giả:** GroupDocs  
