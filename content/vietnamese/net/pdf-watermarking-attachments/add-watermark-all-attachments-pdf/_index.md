---
title: Thêm hình mờ vào tất cả tệp đính kèm trong PDF
linktitle: Thêm hình mờ vào tất cả tệp đính kèm trong PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào tệp đính kèm PDF bằng GroupDocs.Watermark cho .NET. Bảo vệ tài liệu của bạn bằng hình mờ tùy chỉnh một cách dễ dàng.
type: docs
weight: 16
url: /vi/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Giới thiệu
Thêm hình mờ vào tệp đính kèm PDF có thể là một bước quan trọng trong việc quản lý tài liệu, đặc biệt là khi đảm bảo tính bảo mật hoặc thương hiệu. GroupDocs.Watermark dành cho .NET cung cấp giải pháp toàn diện để nhúng hình mờ vào tệp PDF một cách liền mạch. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm hình mờ vào tất cả các tệp đính kèm trong tài liệu PDF bằng GroupDocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
1.  GroupDocs.Watermark cho .NET: Nếu bạn chưa có, hãy tải xuống và cài đặt GroupDocs.Watermark cho .NET từ[trang mạng](https://releases.groupdocs.com/Watermark/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển phù hợp với Visual Studio hoặc bất kỳ IDE tương thích .NET nào khác.
3. Tài liệu PDF: Chuẩn bị tài liệu PDF mà bạn muốn thêm hình mờ, cùng với các tệp đính kèm mà bạn muốn tạo hình mờ.

## Nhập không gian tên
Trước khi đi sâu vào mã, hãy đảm bảo nhập các vùng tên cần thiết để truy cập GroupDocs.Watermark cho các chức năng .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Xác định đường dẫn tài liệu và thư mục đầu ra
Trước tiên, hãy xác định đường dẫn đến tài liệu PDF đầu vào của bạn và thư mục nơi tài liệu có hình mờ sẽ được lưu:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Bước 2: Khởi tạo tùy chọn tải và hình mờ
Tiếp theo, khởi tạo các tùy chọn tải cho tài liệu PDF và tạo hình mờ văn bản:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Bước 3: Tải tài liệu và tệp đính kèm
Tải tài liệu PDF và duyệt qua các tệp đính kèm của nó:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Bước 4: Kiểm tra hỗ trợ tệp đính kèm
Kiểm tra xem tệp đính kèm có được GroupDocs.Watermark hỗ trợ hay không:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Bước 5: Thêm hình mờ vào tệp đính kèm
Tải tài liệu đính kèm và thêm hình mờ:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Bước 6: Lưu thay đổi
Cuối cùng, lưu các thay đổi vào tài liệu PDF có hình mờ:
```csharp
    watermarker.Save(outputFileName);
}
```

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã khám phá cách thêm hình mờ vào tất cả các tệp đính kèm trong tài liệu PDF bằng GroupDocs.Watermark cho .NET. Bằng cách làm theo hướng dẫn từng bước, bạn có thể tích hợp hình mờ vào tệp PDF của mình một cách liền mạch, đảm bảo tính bảo mật và thương hiệu của tài liệu.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh hình thức của hình mờ không?
Có, bạn có thể tùy chỉnh các khía cạnh khác nhau như văn bản, phông chữ, kích thước, màu sắc và vị trí của hình mờ theo yêu cầu của bạn.
### GroupDocs.Watermark có hỗ trợ các định dạng tài liệu khác ngoài PDF không?
Có, GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu bao gồm Microsoft Word, Excel, PowerPoint, Visio, Outlook và Hình ảnh.
### Có phiên bản dùng thử cho GroupDocs.Watermark không?
Có, bạn có thể khám phá các tính năng của GroupDocs.Watermark bằng cách tải xuống phiên bản dùng thử miễn phí từ trang web.
### Tôi có thể thêm nhiều hình mờ vào một tài liệu không?
Hoàn toàn có thể, GroupDocs.Watermark cho phép bạn thêm đồng thời nhiều hình mờ bao gồm văn bản, hình ảnh và chú thích để tăng cường bảo mật tài liệu và xây dựng thương hiệu.
### Có hỗ trợ kỹ thuật cho người dùng GroupDocs.Watermark không?
Có, GroupDocs cung cấp hỗ trợ kỹ thuật toàn diện thông qua các diễn đàn và các kênh hỗ trợ chuyên dụng để hỗ trợ người dùng với bất kỳ thắc mắc hoặc vấn đề nào họ có thể gặp phải.