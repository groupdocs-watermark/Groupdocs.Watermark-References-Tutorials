---
title: Thêm hình mờ vào XObjects trong PDF
linktitle: Thêm hình mờ vào XObjects trong PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào XObjects trong PDF bằng Groupdocs.Watermark cho .NET. Hãy làm theo hướng dẫn từng bước của chúng tôi để dễ dàng thực hiện.
weight: 20
url: /vi/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---

# Thêm hình mờ vào XObjects trong PDF

## Giới thiệu
Hình chìm mờ các tệp PDF là một bước quan trọng để đảm bảo tài liệu của bạn được bảo vệ khỏi việc sử dụng trái phép. Với Groupdocs.Watermark cho .NET, việc thêm hình mờ vào XObject trong tệp PDF của bạn chưa bao giờ dễ dàng hơn thế. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước quy trình, đảm bảo bạn có thể tự tin áp dụng hình mờ cho tài liệu PDF của mình. Bắt đầu nào!
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có mọi thứ bạn cần để làm theo một cách liền mạch:
-  Groupdocs.Watermark cho .NET: Tải xuống và cài đặt phiên bản mới nhất từ[đây](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy phát triển của mình.
- Môi trường phát triển: Sử dụng Visual Studio hoặc bất kỳ IDE nào khác hỗ trợ phát triển .NET.
-  Giấy phép tạm thời: Lấy một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) nếu bạn đang đánh giá sản phẩm.
Khi bạn đã có những điều kiện tiên quyết này, bạn đã sẵn sàng bắt đầu tạo hình mờ cho các tệp PDF của mình.
## Nhập không gian tên
Trước tiên, bạn sẽ cần nhập các không gian tên cần thiết trong dự án của mình. Mở dự án C# của bạn và thêm các lệnh sử dụng sau:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Thiết lập đường dẫn tài liệu của bạn
Bước đầu tiên liên quan đến việc thiết lập đường dẫn cho tài liệu của bạn. Xác định đường dẫn nơi đặt tệp PDF của bạn và nơi bạn muốn lưu tệp PDF có hình mờ.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"` Và`"Your Document Directory"` với các đường dẫn thực tế trên máy của bạn.
## Bước 2: Khởi tạo tùy chọn tải PDF
Tiếp theo, bạn sẽ cần khởi tạo các tùy chọn tải PDF. Điều này rất quan trọng để tải nội dung PDF một cách chính xác.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Bước 3: Tải tài liệu PDF
Sử dụng các tùy chọn tải, tải tài liệu PDF bằng`Watermarker` lớp học.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Bước 4: Tạo hình mờ
Bây giờ, bạn cần tạo hình mờ sẽ được thêm vào tệp PDF. Đối với hướng dẫn này, chúng ta sẽ tạo hình mờ văn bản.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Bước 5: Thêm hình mờ vào XObjects
Lặp lại qua từng trang và từng XObject trong tệp PDF để áp dụng hình mờ.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Thêm hình mờ vào hình ảnh
            xObject.Image.Add(watermark);
        }
    }
}
```
## Bước 6: Lưu tệp PDF có hình mờ
Cuối cùng, lưu tệp PDF có hình mờ vào tệp đầu ra được chỉ định.
```csharp
    watermarker.Save(outputFileName);
}
```
Và bạn có nó rồi đấy! Tệp PDF của bạn hiện chứa hình mờ trên tất cả các XObject của nó.
## Phần kết luận
 Thêm hình mờ vào tài liệu PDF của bạn bằng Groupdocs cho .NET là một quy trình đơn giản cung cấp lớp bảo mật bổ sung. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể đảm bảo rằng tài liệu của mình được bảo vệ khỏi việc sử dụng trái phép. Hãy nhớ rằng, bạn luôn có thể tham khảo[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) để biết thêm thông tin chi tiết và các tính năng nâng cao.
## Câu hỏi thường gặp
### Tôi có thể sử dụng hình ảnh làm hình mờ thay vì văn bản không?
Có, Groupdocs.Watermark for .NET hỗ trợ cả hình mờ văn bản và hình ảnh.
### Làm cách nào tôi có thể kiểm tra Groupdocs.Watermark mà không cần mua nó?
 Bạn có thể sử dụng một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) để đánh giá sản phẩm.
### Có thể tùy chỉnh hình thức của hình mờ không?
Tuyệt đối! Bạn có thể tùy chỉnh phông chữ, kích thước, góc xoay, v.v.
### Groupdocs.Watermark có hỗ trợ các định dạng tài liệu khác không?
Có, nó hỗ trợ nhiều định dạng khác nhau, bao gồm Word, Excel và PowerPoint.
### Tôi có thể nhận hỗ trợ ở đâu nếu gặp vấn đề?
 Bạn có thể nhận được sự hỗ trợ từ[diễn đàn Groupdocs](https://forum.groupdocs.com/c/watermark/19).