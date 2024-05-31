---
title: Rasterize tài liệu PDF
linktitle: Rasterize tài liệu PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách phân loại tài liệu PDF bằng GroupDocs.Watermark cho .NET. Tăng cường bảo mật tài liệu và thu hút trực quan một cách dễ dàng.
type: docs
weight: 27
url: /vi/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## Giới thiệu
Trong lĩnh vực quản lý và thao tác tài liệu, GroupDocs.Watermark dành cho .NET được coi là một công cụ mạnh mẽ, cung cấp các khả năng mạnh mẽ để thêm, xóa và tìm kiếm hình mờ ở nhiều định dạng tài liệu khác nhau. Cho dù đó là bảo vệ tài liệu của bạn bằng thông báo bản quyền, thêm logo công ty để xây dựng thương hiệu hay chỉ đơn giản là chú thích tài liệu bằng tem, GroupDocs.Watermark sẽ đơn giản hóa quy trình bằng API trực quan và bộ tính năng mở rộng.
## Điều kiện tiên quyết
Trước khi đi sâu vào thế giới hình mờ với GroupDocs.Watermark cho .NET, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
### 1. Cài đặt .NET Framework
Đảm bảo rằng bạn đã cài đặt .NET Framework trên máy phát triển của mình. Bạn có thể tải xuống từ trang web của Microsoft hoặc sử dụng trình quản lý gói ưa thích của bạn.
#### Bước 1: Tải xuống .NET Framework
Truy cập trang tải xuống Microsoft .NET Framework.
#### Bước 2: Cài đặt .NET Framework
Làm theo hướng dẫn cài đặt được cung cấp trên trang tải xuống để cài đặt .NET Framework trên hệ thống của bạn.
### 2. Nhận giấy phép GroupDocs.Watermark
Để sử dụng toàn bộ khả năng của GroupDocs.Watermark, bạn cần có giấy phép hợp lệ. Bạn có thể mua giấy phép hoặc lấy giấy phép tạm thời cho mục đích đánh giá.
#### Bước 1: Nhận giấy phép
Truy cập trang mua GroupDocs.Watermark.
#### Bước 2: Mua hoặc lấy giấy phép tạm thời
Chọn tùy chọn cấp phép phù hợp dựa trên nhu cầu của bạn—mua giấy phép để tiếp tục sử dụng hoặc mua giấy phép tạm thời cho mục đích đánh giá.

## Nhập không gian tên
Trước khi bạn bắt đầu tạo hình mờ cho tài liệu của mình, hãy đảm bảo nhập các không gian tên cần thiết để truy cập liền mạch chức năng của Hình mờ.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Bây giờ bạn đã thiết lập xong mọi thứ, hãy đi sâu vào việc tạo điểm ảnh cho tài liệu PDF bằng GroupDocs.Watermark cho .NET. Rasterization chuyển đổi từng trang của tài liệu PDF thành định dạng hình ảnh raster, chẳng hạn như PNG.
## Bước 1: Khởi tạo biến
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Đảm bảo bạn thay thế "Đường dẫn tài liệu của bạn" và "Thư mục tài liệu của bạn" bằng đường dẫn thực tế tương ứng đến tài liệu PDF và thư mục đầu ra mong muốn.
## Bước 2: Tải tài liệu và thêm hình mờ
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Khởi tạo hình mờ hình ảnh hoặc văn bản
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Thêm hình mờ thuộc bất kỳ loại nào trước
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasterize tất cả các trang
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Nội dung của tất cả các trang được thay thế bằng hình ảnh raster
    watermarker.Save(outputFileName);
}
```
Trong bước này, chúng tôi tải tài liệu PDF và khởi tạo hình mờ văn bản với các thuộc tính được chỉ định như văn bản, phông chữ, căn chỉnh, góc xoay, loại kích thước, hệ số tỷ lệ và độ mờ. Sau đó, chúng tôi thêm hình mờ vào tài liệu. Tiếp theo, chúng tôi truy xuất nội dung của tài liệu PDF và rasterize tất cả các trang sang định dạng PNG với độ phân giải 100 dpi. Cuối cùng, chúng tôi lưu tài liệu đã sửa đổi với nội dung được rasterized.

## Phần kết luận
GroupDocs.Watermark cho .NET cung cấp giải pháp toàn diện để thêm hình mờ vào các định dạng tài liệu khác nhau một cách dễ dàng. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể phân loại các tài liệu PDF một cách hiệu quả và nâng cao tính bảo mật cũng như sự hấp dẫn trực quan của chúng.
## Câu hỏi thường gặp
### GroupDocs.Watermark có tương thích với các định dạng tài liệu khác ngoài PDF không?
Có, GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu, bao gồm Microsoft Word, Excel, PowerPoint, Visio, Outlook, v.v.
### Tôi có thể tùy chỉnh hình thức của hình mờ được thêm bằng GroupDocs.Watermark không?
Tuyệt đối! GroupDocs.Watermark cung cấp các tùy chọn mở rộng để tùy chỉnh các thuộc tính hình mờ như văn bản, phông chữ, màu sắc, kích thước, độ mờ, xoay và vị trí.
### GroupDocs.Watermark có hỗ trợ xử lý hàng loạt không?
Có, bạn có thể dễ dàng xử lý nhiều tài liệu ở chế độ hàng loạt bằng GroupDocs, tiết kiệm thời gian và công sức trong việc tạo hình mờ cho các tập hợp tệp lớn.
### Có phiên bản dùng thử cho GroupDocs.Watermark không?
Có, bạn có thể tải xuống phiên bản dùng thử miễn phí của GroupDocs.Watermark từ trang web để đánh giá các tính năng của nó trước khi mua hàng.
### Làm cách nào tôi có thể nhận được hỗ trợ nếu tôi gặp bất kỳ vấn đề nào hoặc có thắc mắc về GroupDocs.Watermark?
Bạn có thể truy cập diễn đàn GroupDocs.Watermark để tìm kiếm sự hỗ trợ từ cộng đồng hoặc liên hệ với nhóm hỗ trợ GroupDocs để được hỗ trợ.