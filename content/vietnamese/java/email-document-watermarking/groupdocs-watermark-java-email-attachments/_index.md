---
date: '2026-04-07'
description: Tìm hiểu cách tạo dấu watermark văn bản cho tệp đính kèm email bằng GroupDocs.Watermark
  cho Java, bảo mật các tệp đính kèm email và bảo vệ dữ liệu bí mật.
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: Tạo Đánh Dấu Văn Bản cho Tệp Đính Kèm Email bằng GroupDocs Java
type: docs
url: /vi/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# Cách Thêm Đánh Dấu Nước vào Tệp Đính Kèm Email Sử Dụng GroupDocs.Watermark cho Java

Trong hướng dẫn này, bạn sẽ **tạo đối tượng watermark văn bản** và áp dụng chúng cho mọi tệp đính kèm được hỗ trợ trong một tin nhắn email. Thêm watermark là một cách hiệu quả để **bảo mật tệp đính kèm email**, biểu thị tính bảo mật, và củng cố nhận diện thương hiệu — chỉ với vài dòng mã Java.

## Giới thiệu

Bảo vệ thông tin nhạy cảm khi truyền qua email quan trọng hơn bao giờ hết. Dù bạn cần gắn nhãn báo cáo nội bộ, đánh dấu hợp đồng pháp lý, hay chỉ đơn giản là thương hiệu cho tài sản marketing, một watermark văn bản cung cấp lớp bảo vệ nhẹ, khó bị giả mạo. Hướng dẫn này sẽ đưa bạn qua toàn bộ quy trình sử dụng **GroupDocs.Watermark cho Java** để thêm watermark tùy chỉnh vào mỗi tệp đính kèm trong tệp Outlook `.msg`.

### Những Điều Bạn Sẽ Học
- Cách **tạo đối tượng watermark văn bản** với phông chữ và màu sắc tùy chỉnh.  
- Tích hợp watermark từng bước vào quy trình xử lý email bằng Java.  
- Mẹo tối ưu hiệu suất khi xử lý các tệp đính kèm lớn.  
- Các kịch bản thực tế mà việc watermark tệp đính kèm email mang lại giá trị.

Hãy kiểm tra rằng bạn có mọi thứ cần thiết trước khi chúng ta bắt đầu.

## Câu trả lời nhanh
- **What does “create text watermark” mean?** It means instantiating a `TextWatermark` object that defines the visible text, font, size, and style to overlay on a document.  
- **Can I watermark encrypted attachments?** No – GroupDocs.Watermark does not support encrypted files for security reasons.  
- **Which file types are supported?** PDFs, Word, Excel, PowerPoint, images, and many more – see the official docs for the full list.  
- **Do I need a license?** A trial license works for development; a commercial license is required for production use.  
- **How fast is the process?** Watermarking a typical 2 MB attachment takes less than a second on modern hardware.

## Yêu cầu trước

- **Java Development Kit (JDK)** – version 8 or newer.  
- Một IDE như IntelliJ IDEA hoặc Eclipse.  
- **GroupDocs.Watermark cho Java** added to your project (see the setup steps below).  
- Truy cập vào tệp email (`.msg`, `.eml`, v.v.) chứa các tệp đính kèm bạn muốn bảo vệ.

## Cài đặt GroupDocs.Watermark cho Java

### Cài đặt Maven

If you manage dependencies with Maven, add the repository and dependency to your `pom.xml`:

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

### Tải xuống trực tiếp

Alternatively, download the latest JAR from the official site:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### Nhận giấy phép
- **Dùng thử:** Register on the GroupDocs website and request a temporary license.  
- **Thương mại:** Purchase a full license here: [purchase page](https://purchase.groupdocs.com/temporary-license/).

### Khởi tạo cơ bản

Import the core classes you’ll need in your Java source file:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Watermark Văn Bản là gì?

A **text watermark** is a semi‑transparent piece of text that is rendered on top of each page of a document. With GroupDocs.Watermark you can control the font, size, color, rotation, and opacity, giving you full flexibility to create a branding or confidentiality notice that blends naturally with the original content.

## Tại sao sử dụng GroupDocs.Watermark cho các tệp đính kèm email?

- **Bảo mật tệp đính kèm email** bằng cách đánh dấu chúng là bí mật.  
- **Duy trì tính nhất quán thương hiệu** trên mọi tài liệu gửi đi.  
- **Xử lý hàng loạt** nhiều email bằng một vòng lặp, tiết kiệm thời gian và giảm lỗi thủ công.  
- **Hỗ trợ đa định dạng** – cùng một đoạn mã hoạt động cho PDF, tệp Word, hình ảnh và hơn nữa.

## Hướng dẫn triển khai

We'll walk through each step, explaining the *why* behind the code so you can adapt it to your own projects.

### Bước 1: Tạo Watermark Văn Bản

First, instantiate a `TextWatermark` with the text you want to display and the desired font settings.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **Pro tip:** Adjust the font size or color to match your corporate style guide. You can also set the opacity via `watermark.setOpacity(0.5)` if you need a subtler effect.

### Bước 2: Thiết lập Email Load Options

`EmailLoadOptions` tells the library how to interpret the incoming email file.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Bước 3: Khởi tạo Watermarker cho Tệp Email của Bạn

Point the `Watermarker` constructor at the `.msg` (or `.eml`) file you wish to process.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Bước 4: Lấy Nội Dung Email

Extract the email’s internal structure so you can loop through its attachments.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Bước 5: Duyệt qua các Tệp Đính Kèm

For each attachment, we verify that the file type is supported and that it isn’t encrypted.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Bước 6‑9: Thêm Watermark vào Các Tệp Được Hỗ Trợ

Inside the conditional block, we create a dedicated `Watermarker` for the attachment, apply the watermark, and then push the modified content back into the email.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Bước 10: Lưu Email Đã Đánh Dấu Nước

Write the updated email to a new file so the original remains untouched.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Bước 11: Dọn Dẹp

Always release resources to avoid memory leaks.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Lý do | Giải pháp |
|-------|--------|-----|
| **Watermark không hiển thị** | Độ trong suốt được đặt quá thấp hoặc màu phông chữ trùng nền. | Tăng độ trong suốt (`watermark.setOpacity(0.7)`) hoặc chọn màu tương phản. |
| **Loại tệp đính kèm không được hỗ trợ** | Định dạng tệp không có trong danh sách được GroupDocs hỗ trợ. | Chuyển đổi tệp sang định dạng được hỗ trợ trước (ví dụ, PDF) hoặc bỏ qua nó với một thông báo log. |
| **OutOfMemoryError trên PDF lớn** | Tải các tệp đính kèm rất lớn tiêu tốn quá nhiều bộ nhớ heap. | Tăng heap JVM (`-Xmx2g`) hoặc xử lý các tệp đính kèm theo lô nhỏ hơn. |

## Câu hỏi thường gặp

**Q: Can I add watermarks to encrypted files?**  
A: No, GroupDocs.Watermark does not support adding watermarks to encrypted files due to security restrictions.

**Q: What file types are supported for watermarking?**  
A: Supported types include PDFs, Word documents, Excel spreadsheets, PowerPoint presentations, and common image formats. See the official documentation for a full list.

**Q: How do I customize the appearance of my watermark?**  
A: Use the `Font` class to set size, style, and color, and call methods like `setOpacity` and `setRotationAngle` on the `TextWatermark` instance.

**Q: Is batch processing multiple emails possible?**  
A: Yes. Wrap the entire workflow in a loop that iterates over files in a directory, reusing the same `TextWatermark` instance for efficiency.

**Q: My watermark appears clipped on the last page—what’s wrong?**  
A: Ensure the watermark fits within the page margins. You can adjust its position with `watermark.setHorizontalAlignment` and `watermark.setVerticalAlignment`.

## Ứng dụng thực tiễn

1. **Chia sẻ tài liệu nội bộ:** Nhúng thương hiệu công ty hoặc thông báo bảo mật trước khi phân phối báo cáo trong toàn tổ chức.  
2. **Giao tiếp với khách hàng:** Gắn nhãn hợp đồng và đề xuất với “Confidential” để nhắc nhở người nhận về chính sách xử lý dữ liệu.  
3. **Tiếp thị qua email:** Thêm watermark thương hiệu nhẹ nhàng vào các PDF quảng cáo đính kèm bản tin, tăng nhận diện thương hiệu mà không làm gián đoạn thiết kế.

## Các cân nhắc về hiệu suất

- **Quản lý bộ nhớ:** Đóng mỗi `attachedWatermarker` ngay lập tức (như trong Bước 9) để giải phóng tài nguyên gốc.  
- **Giới hạn kích thước tệp:** Đối với tệp đính kèm lớn hơn 10 MB, cân nhắc stream tệp hoặc tăng kích thước heap JVM.  
- **Xử lý song song:** Sử dụng `ExecutorService` của Java để watermark nhiều email đồng thời, nhưng giám sát việc sử dụng CPU để tránh tranh chấp.

## Kết luận

You now have a complete, production‑ready recipe for how to **create text watermark** objects and apply them to every supported attachment within an email file using GroupDocs.Watermark for Java. By integrating this workflow into your existing email‑handling pipeline, you’ll boost document security, enforce branding, and maintain compliance with minimal overhead.

Ready to take the next step? Try extending the code to process an entire folder of `.msg` files, or explore additional watermark types such as images and QR codes.

---

**Cập nhật lần cuối:** 2026-04-07  
**Kiểm tra với:** GroupDocs.Watermark 24.11 for Java  
**Tác giả:** GroupDocs  

**Tài nguyên**  
- [Tài liệu](https://docs.groupdocs.com/watermark/java/)  
- [Tham chiếu API](https://reference.groupdocs.com/watermark/java)  
- [Tải xuống GroupDocs.Watermark cho Java](https://releases.groupdocs.com/watermark/java/)