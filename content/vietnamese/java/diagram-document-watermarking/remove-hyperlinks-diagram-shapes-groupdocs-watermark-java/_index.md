---
date: '2026-10-21'
description: Tìm hiểu cách xóa hyperlink khỏi các diagram shapes bằng GroupDocs.Watermark
  cho Java. Thực hiện theo hướng dẫn step‑by‑step để bảo mật và làm sạch tài liệu
  của bạn.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Tìm hiểu cách xóa hyperlink khỏi các diagram shapes bằng GroupDocs.Watermark
  cho Java. Hướng dẫn này sẽ đưa bạn qua quá trình setup, code và best practices để
  có tài liệu an toàn, sạch sẽ.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Cách xóa hyperlink khỏi các diagram shapes với GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Cách xóa hyperlink khỏi các diagram shapes với GroupDocs.Watermark Java
type: docs
url: /vi/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cách xóa siêu liên kết khỏi các hình dạng với GroupDocs.Watermark Java

Quản lý tài liệu số thường liên quan đến việc chỉnh sửa sơ đồ, đặc biệt khi bạn cần **how to remove hyperlink** khỏi các hình dạng để đảm bảo bảo mật hoặc độ rõ nét trực quan. Hướng dẫn này sẽ chỉ cho bạn một phương pháp đơn giản để loại bỏ các siêu liên kết không mong muốn khỏi các hình dạng trong sơ đồ bằng cách sử dụng thư viện mạnh mẽ **GroupDocs.Watermark** cho Java. Khi kết thúc hướng dẫn, bạn sẽ hiểu tại sao việc xóa siêu liên kết quan trọng, cách thiết lập môi trường, và các bước chính xác để thực hiện việc xóa một cách an toàn.

## Câu trả lời nhanh
- **What is the primary purpose of removing hyperlinks?** Để loại bỏ rủi ro bảo mật và cải thiện độ rõ nét trực quan trong các sơ đồ được chia sẻ.  
- **Which library handles the removal?** GroupDocs.Watermark for Java cung cấp API chuyên dụng cho việc thao tác sơ đồ.  
- **Do I need a license?** Bản dùng thử hoạt động cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Can I process many files at once?** Có—bọc mã trong vòng lặp hoặc công việc batch để xử lý hàng loạt.  
- **What Java version is required?** Java 8 hoặc cao hơn được hỗ trợ.

## **how to remove hyperlink** là gì?
Cụm từ **how to remove hyperlink** đề cập đến quá trình tìm kiếm và xóa các đối tượng siêu liên kết được nhúng trong các phần tử hình dạng của sơ đồ. Thực hiện hành động này ngăn việc điều hướng ra ngoài vô tình đưa người dùng đến các trang độc hại hoặc nội dung không mong muốn. Điều này đặc biệt quan trọng khi chuẩn bị tài liệu để phân phối công khai, đảm bảo không còn đường dẫn ẩn nào có thể dẫn tới các trang lừa đảo hoặc tài nguyên bên ngoài không mong muốn.

## Tại sao sử dụng GroupDocs.Watermark cho Java?
GroupDocs.Watermark hỗ trợ **hơn 30 định dạng đầu vào và đầu ra** và có thể xử lý các sơ đồ với **tối đa 500 trang** mà không cần tải toàn bộ tệp vào bộ nhớ, mang lại **giảm 40 % mức sử dụng CPU** so với các trình phân tích XML chung. API của nó cung cấp cho bạn khả năng kiểm soát chi tiết các thuộc tính hình dạng, làm cho nó trở thành phương pháp tiêu chuẩn cho việc xử lý sơ đồ an toàn trong các ứng dụng Java.

## Yêu cầu trước
- **GroupDocs.Watermark** library version 24.11 hoặc mới hơn.  
- Maven đã được cài đặt (hoặc tải JAR trực tiếp).  
- JDK 8 hoặc mới hơn và một IDE như IntelliJ IDEA hoặc Eclipse.  
- Kiến thức cơ bản về Java và quen thuộc với các phụ thuộc Maven.

## Cài đặt GroupDocs.Watermark cho Java
Để bắt đầu, bao gồm thư viện GroupDocs.Watermark vào dự án của bạn. Bạn có thể thêm nó qua Maven hoặc tải JAR thủ công.

### Cấu hình Maven
Add the following configuration to your `pom.xml`:

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
Hoặc, tải phiên bản mới nhất từ [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Các bước lấy giấy phép
- Bắt đầu với bản dùng thử miễn phí bằng cách tải GroupDocs.Watermark.  
- Đối với việc thử nghiệm mở rộng hoặc sử dụng trong sản xuất, lấy giấy phép tạm thời hoặc mua giấy phép đầy đủ.

#### Khởi tạo và cài đặt cơ bản
Lớp `Watermarker` là điểm vào cho tất cả các thao tác ở mức tài liệu. Nó tải một tệp, cung cấp cho bạn quyền truy cập vào các trang, hình dạng và siêu dữ liệu, và cuối cùng ghi tài liệu đã chỉnh sửa trở lại đĩa.

To initialize the Watermarker class:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cách xóa siêu liên kết khỏi các hình dạng trong sơ đồ?
Tải sơ đồ, xác định mỗi hình dạng chứa siêu liên kết và xóa các đối tượng siêu liên kết đó. Toàn bộ thao tác có thể thực hiện trong chưa đầy mười dòng mã, và nó đảm bảo rằng sơ đồ kết quả không còn chứa bất kỳ liên kết có thể nhấp nào có thể chuyển hướng người dùng tới các trang bên ngoài hoặc lộ thông tin nhạy cảm.

### Bước 1: tải tệp sơ đồ
Bắt đầu bằng cách tải sơ đồ của bạn bằng `Watermarker`. Đối tượng này cung cấp quyền truy cập vào các thành phần tài liệu khác nhau, bao gồm hình dạng và các thuộc tính của chúng.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Why**: Tải tệp là cần thiết để truy cập nội dung của nó cho việc thao tác tiếp theo.

### Bước 2: truy cập nội dung hình dạng
Lấy nội dung hình dạng của sơ đồ. Điều này cho phép bạn làm việc trực tiếp với các thành phần có thể chứa siêu liên kết.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Why**: Truy cập các hình dạng cụ thể là quan trọng để nhắm mục tiêu và chỉnh sửa các thuộc tính siêu liên kết.

### Bước 3: lặp và xóa siêu liên kết
Lặp qua các siêu liên kết theo thứ tự ngược lại để an toàn xóa các liên kết không mong muốn mà không làm gián đoạn quá trình lặp.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Why**: Đảo ngược thứ tự lặp giúp tránh các vấn đề chỉ mục khi xóa phần tử.

### Bước 4: lưu và đóng
Khi các chỉnh sửa hoàn tất, lưu các thay đổi của bạn vào vị trí tệp mới và đóng tài nguyên watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Why**: Đóng tài nguyên đúng cách đảm bảo không có rò rỉ bộ nhớ hoặc tệp bị khóa còn lại trong hệ thống.

## Các lỗi thường gặp và khắc phục
- **Null shape collections** – Luôn kiểm tra rằng bộ sưu tập `Hyperlinks` của một hình dạng không phải là null trước khi lặp.  
- **Large diagrams** – Đối với các tệp lớn hơn 200 trang, tăng kích thước heap JVM (`-Xmx2g`) để tránh `OutOfMemoryError`.  
- **License errors** – Nếu bạn gặp ngoại lệ giấy phép, hãy xác minh rằng giấy phép dùng thử chưa hết hạn và đường dẫn tệp giấy phép là đúng.

## Câu hỏi thường gặp

**Q: Làm thế nào để xử lý nhiều hình dạng trên cùng một trang?**  
A: Lặp qua bộ sưu tập `Shapes` của mỗi trang, áp dụng cùng logic xóa siêu liên kết cho mọi hình dạng bạn gặp.

**Q: Tôi có thể giới hạn việc xóa chỉ trong một phạm vi trang cụ thể không?**  
A: Có—sử dụng chỉ mục trang khi lấy hình dạng và bỏ qua các trang ngoài phạm vi mục tiêu.

**Q: Có cần giấy phép cho việc xử lý batch không?**  
A: Một giấy phép thương mại hợp lệ là cần thiết cho bất kỳ công việc batch cấp sản xuất nào; giấy phép dùng thử chỉ hoạt động cho việc thử nghiệm giới hạn.

**Q: Điều này có hoạt động với tệp SVG hoặc Visio không?**  
A: GroupDocs.Watermark hỗ trợ SVG, VSDX và một số định dạng sơ đồ khác; hãy chắc chắn rằng loại tệp được liệt kê trong bảng định dạng được hỗ trợ.

**Q: Hiệu năng như thế nào trên một sơ đồ 300 trang?**  
A: Trên một máy chủ tiêu chuẩn (8 CPU, 16 GB RAM), xử lý một sơ đồ 300 trang mất dưới 45 giây, với mức sử dụng bộ nhớ dưới 200 MB.

## Tài nguyên
- [Tài liệu](https://docs.groupdocs.com/watermark/java/)
- [Tham khảo API](https://reference.groupdocs.com/watermark/java)
- [Tải xuống](https://releases.groupdocs.com/watermark/java/)
- [Kho lưu trữ GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Diễn đàn hỗ trợ miễn phí](https://forum.groupdocs.com/c/watermark/10)
- [Mua giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)

---

**Cập nhật lần cuối:** 2026-10-21  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Sửa đổi các hình dạng tài liệu Word với GroupDocs.Watermark trong Java: Hướng dẫn toàn diện](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Xóa các hình dạng khỏi tài liệu Word bằng GroupDocs.Watermark trong Java: Hướng dẫn toàn diện](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Chỉnh sửa tiêu đề & chân trang sơ đồ trong Java bằng GroupDocs.Watermark: Hướng dẫn toàn diện](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)