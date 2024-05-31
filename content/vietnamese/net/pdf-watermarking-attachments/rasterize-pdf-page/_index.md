---
title: Rasterize trang PDF
linktitle: Rasterize trang PDF
second_title: API GroupDocs.Watermark .NET
description: Tăng cường bảo mật tài liệu với GroupDocs cho .NET. Thêm hình mờ vào PDF và các định dạng khác một cách liền mạch.
type: docs
weight: 28
url: /vi/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## Giới thiệu
GroupDocs.Watermark dành cho .NET là một API mạnh mẽ cho phép các nhà phát triển thêm hình mờ vào các định dạng tài liệu khác nhau một cách liền mạch, bao gồm PDF, Word, Excel, PowerPoint, v.v. Với giao diện trực quan và các tính năng mở rộng, GroupDocs.Watermark đơn giản hóa quá trình thêm hình mờ văn bản hoặc hình ảnh vào tài liệu, cho phép người dùng bảo vệ tài sản trí tuệ của họ và tăng cường bảo mật tài liệu một cách dễ dàng.
## Điều kiện tiên quyết
Trước khi bắt đầu sử dụng GroupDocs.Watermark cho .NET, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1. Cài đặt: Tải xuống và cài đặt GroupDocs.Watermark cho .NET từ[trang tải xuống](https://releases.groupdocs.com/Watermark/net/).
2.  Giấy phép: Nhận giấy phép GroupDocs.Watermark cho .NET. Bạn có thể xin giấy phép tạm thời cho mục đích đánh giá từ[đây](https://purchase.groupdocs.com/temporary-license/) hoặc mua giấy phép đầy đủ từ[trang mua hàng](https://purchase.groupdocs.com/buy).
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy phát triển của mình.
4. Tài liệu: Chuẩn bị tài liệu mà bạn muốn thêm hình mờ.

## Nhập không gian tên
Để bắt đầu sử dụng GroupDocs.Watermark cho .NET, hãy nhập các vùng tên cần thiết vào dự án của bạn:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã của bạn ở đây
}
```
## Bước 2: Khởi tạo Watermark
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Bước 3: Thêm hình mờ
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Bước 4: Rasterize trang
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Bước 5: Lưu tài liệu
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Tóm lại, GroupDocs.Watermark cho .NET cung cấp một giải pháp liền mạch để thêm hình mờ vào PDF và các định dạng tài liệu khác. Bằng cách làm theo hướng dẫn từng bước được nêu ở trên, các nhà phát triển có thể phân loại các trang PDF một cách hiệu quả và tăng cường bảo mật tài liệu một cách dễ dàng.
## Câu hỏi thường gặp
### GroupDocs.Watermark có tương thích với các định dạng tài liệu khác ngoài PDF không?
Có, GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu, bao gồm Word, Excel, PowerPoint, Visio, v.v.
### Tôi có thể tùy chỉnh hình thức của hình mờ được thêm vào tài liệu không?
Tuyệt đối! GroupDocs.Watermark cung cấp các tùy chọn tùy chỉnh mở rộng cho hình mờ văn bản và hình ảnh, cho phép người dùng điều chỉnh phông chữ, kích thước, màu sắc, độ mờ và vị trí theo sở thích của họ.
### GroupDocs.Watermark có phù hợp cho cả mục đích sử dụng cá nhân và thương mại không?
Có, GroupDocs.Watermark cung cấp các tùy chọn cấp phép linh hoạt để phục vụ nhu cầu của cả cá nhân và doanh nghiệp, khiến nó phù hợp với các dự án cá nhân cũng như các ứng dụng thương mại quy mô lớn.
### GroupDocs.Watermark có cung cấp hỗ trợ kỹ thuật cho nhà phát triển không?
Có, các nhà phát triển có thể truy cập hỗ trợ kỹ thuật toàn diện thông qua diễn đàn GroupDocs.Watermark, nơi họ có thể tìm kiếm sự trợ giúp, chia sẻ kinh nghiệm và tương tác với các nhà phát triển đồng nghiệp.
### Tôi có thể dùng thử GroupDocs.Watermark trước khi mua hàng không?
Chắc chắn! Bạn có thể sử dụng phiên bản dùng thử miễn phí của GroupDocs.Watermark từ[trang phát hành](https://releases.groupdocs.com/), cho phép bạn khám phá các tính năng và chức năng của nó trước khi quyết định mua hàng.