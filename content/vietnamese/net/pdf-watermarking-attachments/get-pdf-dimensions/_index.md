---
title: Nhận kích thước PDF
linktitle: Nhận kích thước PDF
second_title: API GroupDocs.Watermark .NET
description: Bảo vệ tài liệu của bạn một cách dễ dàng bằng Groupdocs.Watermark cho .NET. Thêm hình mờ, tem và chú thích một cách dễ dàng.
weight: 26
url: /vi/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# Nhận kích thước PDF

## Giới thiệu
Trong thời đại kỹ thuật số ngày nay, việc bảo vệ tài liệu của bạn là điều tối quan trọng. Cho dù bạn là chuyên gia kinh doanh, chuyên gia pháp lý hay nghệ sĩ sáng tạo thì việc bảo vệ tài sản trí tuệ của mình là điều cần thiết. Groupdocs.Watermark cho .NET cung cấp một giải pháp mạnh mẽ để thêm hình mờ, tem và chú thích vào tài liệu của bạn, đảm bảo tính bảo mật và tính xác thực của chúng.
## Điều kiện tiên quyết
Trước khi đi sâu vào thế giới Groupdocs.Watermark dành cho .NET, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1.  Cài đặt Groupdocs.Watermark cho .NET: Tải xuống và cài đặt Groupdocs.Watermark cho .NET từ[Liên kết tải xuống](https://releases.groupdocs.com/Watermark/net/).
2.  Khóa cấp phép (Tùy chọn): Mặc dù Groupdocs.Watermark cho .NET cung cấp bản dùng thử miễn phí nhưng bạn có thể chọn giấy phép tạm thời hoặc mua giấy phép đầy đủ từ[đây](https://purchase.groupdocs.com/buy) cho chức năng mở rộng.
3. Làm quen với C#: Nên có kiến thức cơ bản về ngôn ngữ lập trình C# để hiểu và triển khai các ví dụ được cung cấp.
4. Tài liệu cần bảo vệ: Chuẩn bị sẵn một tài liệu mẫu (ví dụ: PDF, Word, Excel) trên máy cục bộ của bạn để thử nghiệm.

## Nhập không gian tên
Để bắt đầu làm việc với Groupdocs.Watermark cho .NET, bạn cần nhập các vùng tên cần thiết vào dự án C# của mình.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Bước 1: Khai báo biến
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Bước 2: Tải tài liệu
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Bước 3: Nhận nội dung PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Bước 4: Truy xuất kích thước
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Phần kết luận
Tóm lại, Groupdocs.Watermark cho .NET cung cấp một giải pháp toàn diện để bảo vệ tài liệu của bạn khỏi việc sử dụng và phân phối trái phép. Bằng cách làm theo các bước được nêu ở trên và tận dụng sức mạnh của Groupdocs.Watermark cho .NET, bạn có thể đảm bảo tính bảo mật và tính toàn vẹn của tài sản kỹ thuật số có giá trị của mình.
## Câu hỏi thường gặp
### Tôi có thể sử dụng Groupdocs.Watermark cho .NET miễn phí không?
Có, Groupdocs.Watermark cho .NET cung cấp phiên bản dùng thử miễn phí cho mục đích đánh giá. Tuy nhiên, để có chức năng mở rộng, bạn có thể cân nhắc mua giấy phép đầy đủ.
### Groupdocs.Watermark có hỗ trợ nhiều định dạng tài liệu không?
Có, Groupdocs hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Word, Excel, PowerPoint, v.v.
### Tôi có thể tùy chỉnh hình mờ và tem bằng Groupdocs.Watermark không?
Tuyệt đối! Groupdocs.Watermark cung cấp các tùy chọn tùy chỉnh mở rộng cho hình mờ, tem và chú thích để phù hợp với yêu cầu cụ thể của bạn.
### Có hỗ trợ kỹ thuật cho người dùng Groupdocs.Watermark không?
 Có, bạn có thể nhận hỗ trợ kỹ thuật và tương tác với cộng đồng Groupdocs thông qua[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19).
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho Groupdocs.Watermark?
 Bạn có thể nhận giấy phép tạm thời cho Groupdocs.Watermark từ[đây](https://purchase.groupdocs.com/temporary-license/).