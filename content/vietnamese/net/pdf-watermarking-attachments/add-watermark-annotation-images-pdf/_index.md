---
title: Thêm hình mờ vào hình ảnh chú thích trong PDF
linktitle: Thêm hình mờ vào hình ảnh chú thích trong PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách bảo vệ tài liệu PDF của bạn bằng cách thêm hình mờ vào hình ảnh chú thích bằng Groupdocs.Watermark cho .NET.
weight: 17
url: /vi/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---

# Thêm hình mờ vào hình ảnh chú thích trong PDF

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm hình mờ vào hình ảnh chú thích trong tài liệu PDF bằng Groupdocs.Watermark cho .NET. Hình chìm mờ rất quan trọng để bảo vệ tài liệu của bạn khỏi việc sử dụng hoặc phân phối trái phép. Bằng cách làm theo hướng dẫn từng bước này, bạn sẽ học cách áp dụng hình mờ văn bản cho hình ảnh chú thích trong tệp PDF một cách hiệu quả.
## Điều kiện tiên quyết
Trước khi tiếp tục, hãy đảm bảo bạn có những điều sau:
1. Hiểu biết cơ bản về ngôn ngữ lập trình C#.
2. Đã cài đặt Groupdocs.Watermark cho thư viện .NET.
3. Truy cập vào môi trường phát triển như Visual Studio.
4. Một tài liệu PDF có hình ảnh chú thích để tạo hình mờ.

## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết vào mã C# của mình:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Bước 2: Nhận nội dung PDF và khởi tạo hình mờ
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Khởi tạo hình mờ hình ảnh hoặc văn bản
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Bước 3: Lặp lại các trang PDF và hình ảnh chú thích
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Thêm hình mờ vào hình ảnh
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Bước 4: Lưu tài liệu có hình mờ
```csharp
    watermarker.Save(outputFileName);
}
```
Sau khi thực hiện các bước này, tài liệu PDF của bạn sẽ có hình mờ được chỉ định thêm vào hình ảnh chú thích.

## Phần kết luận
Thêm hình mờ vào hình ảnh chú thích trong tệp PDF là điều cần thiết để bảo vệ tính toàn vẹn của tài liệu của bạn và đảm bảo chúng không bị lạm dụng. Với Groupdocs.Watermark cho .NET, quá trình này trở nên đơn giản và hiệu quả, cho phép bạn bảo vệ các tệp PDF của mình một cách hiệu quả.
## Câu hỏi thường gặp
### Tôi có thể thêm nhiều hình mờ vào cùng một tài liệu PDF không?
Có, bạn có thể thêm nhiều hình mờ vào cùng một tài liệu PDF bằng Groupdocs.Watermark cho .NET.
### Groupdocs.Watermark có hỗ trợ các định dạng tài liệu khác ngoài PDF không?
Có, Groupdocs hỗ trợ nhiều định dạng tài liệu khác nhau, bao gồm Word, Excel, PowerPoint, v.v.
### Có thể tùy chỉnh sự xuất hiện của hình mờ?
Hoàn toàn có thể tùy chỉnh văn bản, phông chữ, màu sắc, kích thước và vị trí của hình mờ theo sở thích của bạn.
### Tôi có thể xóa hình mờ khỏi tài liệu PDF bằng Groupdocs.Watermark không?
Có, Groupdocs.Watermark cung cấp chức năng xóa hình mờ khỏi tài liệu PDF một cách dễ dàng.
### Có bản dùng thử miễn phí nào dành cho Groupdocs.Watermark cho .NET không?
Có, bạn có thể tận dụng bản dùng thử miễn phí Groupdocs.Watermark cho .NET từ trang web.