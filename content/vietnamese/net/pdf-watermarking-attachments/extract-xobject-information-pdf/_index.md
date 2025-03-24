---
title: Trích xuất thông tin XObject từ PDF
linktitle: Trích xuất thông tin XObject từ PDF
second_title: API GroupDocs.Watermark .NET
description: Khai phá sức mạnh của hình mờ tài liệu bằng GroupDocs.Watermark cho .NET. Quản lý liền mạch hình mờ trong tệp PDF, tài liệu Word và hình ảnh.
weight: 25
url: /vi/net/pdf-watermarking-attachments/extract-xobject-information-pdf/
---

# Trích xuất thông tin XObject từ PDF

## Giới thiệu
GroupDocs.Watermark cho .NET là một API tạo hình mờ tài liệu mạnh mẽ được thiết kế để xử lý hình mờ ở nhiều định dạng tài liệu khác nhau như PDF, Word, Excel, PowerPoint và hình ảnh. Nó cung cấp cho các nhà phát triển một cách tiếp cận đơn giản để thêm, xóa, tìm kiếm và thay thế hình mờ trong tài liệu theo chương trình. Cho dù bạn cần thêm logo công ty, thông báo bản quyền hay tem bí mật vào tài liệu của mình, GroupDocs.Watermark sẽ đơn giản hóa quy trình bằng API trực quan của nó.
## Điều kiện tiên quyết
Trước khi đi sâu vào GroupDocs.Watermark cho .NET, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1. Cài đặt: Tải xuống và cài đặt GroupDocs.Watermark cho .NET từ[trang tải xuống](https://releases.groupdocs.com/Watermark/net/).
2. Môi trường phát triển: Đã cài đặt Visual Studio hoặc bất kỳ .NET IDE nào khác trên hệ thống của bạn.
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework cần thiết trên máy phát triển của mình.

## Nhập không gian tên
Để bắt đầu sử dụng GroupDocs.Watermark cho .NET trong dự án của bạn, bạn cần nhập các vùng tên cần thiết.
Trong dự án .NET của bạn, hãy thêm tham chiếu đến GroupDocs.Watermark.dll.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Bước 1: Tải tài liệu
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
## Bước 2: Truy cập nội dung PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Bước 3: Lặp lại các trang
```csharp
foreach (PdfPage page in pdfContent.Pages)
```
## Bước 4: Truy cập XObjects
```csharp
foreach (PdfXObject xObject in page.XObjects)
```
## Bước 5: Trích xuất thông tin
```csharp
if (xObject.Image != null)
{
    Console.WriteLine(xObject.Image.Width);
    Console.WriteLine(xObject.Image.Height);
    Console.WriteLine(xObject.Image.GetBytes().Length);
}
Console.WriteLine(xObject.Text);
Console.WriteLine(xObject.X);
Console.WriteLine(xObject.Y);
Console.WriteLine(xObject.Width);
Console.WriteLine(xObject.Height);
Console.WriteLine(xObject.RotateAngle);
```

## Phần kết luận
GroupDocs.Watermark dành cho .NET trao quyền cho các nhà phát triển quản lý hình mờ tài liệu một cách liền mạch trong các ứng dụng .NET của họ. Với API trực quan và các tính năng mạnh mẽ, đây là giải pháp phù hợp cho mọi nhu cầu về hình mờ. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể khai thác toàn bộ tiềm năng của Hình mờ GroupDocs và nâng cao quy trình quản lý tài liệu của mình.
## Câu hỏi thường gặp
### GroupDocs.Watermark có tương thích với tất cả các khung .NET không?
Có, GroupDocs.Watermark hỗ trợ nhiều loại khung .NET, bao gồm .NET Core và .NET Framework.
### Tôi có thể áp dụng nhiều hình mờ cho một tài liệu bằng GroupDocs.Watermark không?
Tuyệt đối! GroupDocs.Watermark cho phép bạn thêm nhiều hình mờ thuộc các loại khác nhau vào một tài liệu.
### GroupDocs.Watermark có hỗ trợ mã hóa tài liệu không?
Có, GroupDocs.Watermark cung cấp khả năng mã hóa để bảo mật tài liệu của bạn khỏi bị truy cập trái phép.
### Có phiên bản dùng thử cho GroupDocs.Watermark không?
 Có, bạn có thể truy cập phiên bản dùng thử miễn phí của GroupDocs.Watermark từ[trang tải xuống](https://releases.groupdocs.com/).
### Tôi có thể tìm thêm hỗ trợ và tài nguyên cho GroupDocs.Watermark ở đâu?
Bạn có thể khám phá tài liệu GroupDocs.Watermark, tham gia diễn đàn cộng đồng hoặc liên hệ với nhóm hỗ trợ để được hỗ trợ.