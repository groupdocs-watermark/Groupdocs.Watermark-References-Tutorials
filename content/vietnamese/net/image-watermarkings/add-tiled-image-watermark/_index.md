---
title: Thêm hình mờ hình ảnh lát gạch
linktitle: Thêm hình mờ hình ảnh lát gạch
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ hình ảnh xếp kề vào tài liệu của bạn bằng GroupDocs.Watermark cho .NET. Dễ dàng, hiệu quả và có thể tùy chỉnh.
weight: 10
url: /vi/net/image-watermarkings/add-tiled-image-watermark/
type: docs
---
# Thêm hình mờ hình ảnh lát gạch

## Giới thiệu
GroupDocs.Watermark cho .NET là một API mạnh mẽ cho phép các nhà phát triển thêm, xóa và tìm kiếm hình mờ ở các định dạng tài liệu khác nhau theo chương trình. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm hình mờ hình ảnh xếp kề vào tài liệu của bạn bằng GroupDocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Kiến thức cơ bản về ngôn ngữ lập trình C#.
- Visual Studio được cài đặt trên hệ thống của bạn.
- Thư viện GroupDocs.Watermark cho .NET đã được thêm vào dự án của bạn. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/Watermark/net/).

## Nhập không gian tên
Đảm bảo nhập các không gian tên cần thiết ở đầu tệp C# của bạn:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Bước 1: Đặt đường dẫn tài liệu và thư mục đầu ra
Xác định đường dẫn của tài liệu đầu vào và thư mục bạn muốn lưu tài liệu đầu ra:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"` với đường dẫn tuyệt đối hoặc tương đối đến tài liệu đầu vào của bạn.
## Bước 2: Khởi tạo đối tượng Watermarker
Tạo đối tượng Watermarker bằng đường dẫn tài liệu đầu vào:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Thêm hình mờ ở đây
}
```
## Bước 3: Thêm hình mờ hình ảnh xếp cạnh
Khởi tạo một đối tượng ImageWatermark bằng đường dẫn đến tệp hình ảnh bạn muốn sử dụng làm hình mờ:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Định cấu hình tùy chọn ô
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Thêm hình mờ vào tài liệu
    watermarker.Add(watermark);
    // Lưu tài liệu đã sửa đổi
    watermarker.Save(outputFileName);
}
```
 Thay thế`"Path to Your Image"` với đường dẫn thực tế đến tệp hình ảnh mờ của bạn.

## Phần kết luận
Bằng cách làm theo các bước này, bạn có thể dễ dàng thêm hình mờ theo ô xếp kề vào tài liệu của mình bằng GroupDocs.Watermark cho .NET. Thử nghiệm với các tùy chọn và cấu hình khác nhau để đạt được kết quả mong muốn.
## Câu hỏi thường gặp
### Tôi có thể thêm nhiều hình mờ vào một tài liệu không?
Có, bạn có thể thêm nhiều hình mờ thuộc các loại khác nhau vào tài liệu bằng GroupDocs.Watermark cho .NET.
### GroupDocs.Watermark có hỗ trợ tất cả các định dạng tài liệu không?
GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, Word, Excel, PowerPoint, v.v.
### Có phiên bản dùng thử cho GroupDocs.Watermark không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Tôi có thể tùy chỉnh hình thức của hình mờ không?
Có, bạn có thể tùy chỉnh các khía cạnh khác nhau của hình mờ, chẳng hạn như vị trí, kích thước, góc xoay, độ trong suốt, v.v.
### GroupDocs.Watermark có cung cấp hỗ trợ kỹ thuật không?
 Có, bạn có thể nhận hỗ trợ kỹ thuật từ diễn đàn GroupDocs.Watermark[đây](https://forum.groupdocs.com/c/watermark/19).