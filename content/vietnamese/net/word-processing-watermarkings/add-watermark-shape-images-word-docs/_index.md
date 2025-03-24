---
title: Thêm hình mờ để định hình hình ảnh trong tài liệu Word
linktitle: Thêm hình mờ để định hình hình ảnh trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ để định hình hình ảnh trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Tăng cường bảo mật tài liệu với hướng dẫn này.
weight: 17
url: /vi/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm hình mờ để định hình hình ảnh trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Hình mờ là một khía cạnh quan trọng của việc bảo vệ tài liệu, đặc biệt khi xử lý thông tin nhạy cảm hoặc bí mật. Bằng cách thêm hình mờ để định hình hình ảnh, bạn có thể đảm bảo tính toàn vẹn và bảo mật cho tài liệu của mình.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
1.  GroupDocs.Watermark cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Watermark từ[trang tải xuống](https://releases.groupdocs.com/Watermark/net/).
2. Tài liệu: Chuẩn bị tài liệu Word nơi bạn muốn thêm hình mờ.
3. Môi trường phát triển: Thiết lập môi trường phát triển .NET ưa thích của bạn.
## Nhập không gian tên
Trước khi viết mã, hãy đảm bảo nhập các không gian tên cần thiết:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
Đầu tiên, xác định đường dẫn đến tài liệu của bạn và chỉ định tên tệp đầu ra:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Bước 2: Khởi tạo Watermarker
 Khởi tạo một`Watermarker` đối tượng bằng cách cung cấp đường dẫn tài liệu và các tùy chọn tải tùy chọn:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Thêm logic hình mờ vào đây
}
```
## Bước 3: Tạo hình mờ văn bản
Xác định hình mờ văn bản với các thuộc tính mong muốn như văn bản, phông chữ, căn chỉnh, xoay, định cỡ, v.v.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Bước 4: Áp dụng Watermark để định hình hình ảnh
Lặp lại qua các phần và hình dạng tài liệu để xác định hình ảnh hình dạng và thêm hình mờ:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Bước 5: Lưu tài liệu
Lưu tài liệu có hình mờ được thêm vào tệp đầu ra được chỉ định:
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách thêm hình mờ để định hình hình ảnh trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Bằng cách làm theo hướng dẫn từng bước và tận dụng các tính năng mạnh mẽ của GroupDocs.Watermark, bạn có thể nâng cao tính bảo mật và bảo vệ tài liệu của mình một cách hiệu quả.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh hình thức của văn bản hình mờ không?
Có, bạn có thể điều chỉnh các thuộc tính khác nhau như phông chữ, kích thước, màu sắc, góc xoay và căn chỉnh để tùy chỉnh hình mờ theo sở thích của bạn.
### GroupDocs.Watermark có hỗ trợ các định dạng tài liệu khác ngoài Word không?
Có, GroupDocs.Watermark cung cấp hỗ trợ cho nhiều định dạng tài liệu bao gồm PDF, Excel, PowerPoint, v.v.
### Có thể thêm nhiều hình mờ vào một tài liệu không?
Hoàn toàn có thể, bạn có thể thêm nhiều hình mờ với nội dung, kiểu dáng và vị trí khác nhau trong cùng một tài liệu.
### Tôi có thể xóa hình mờ khỏi tài liệu bằng GroupDocs.Watermark không?
Có, GroupDocs.Watermark cung cấp các tính năng để phát hiện và xóa hình mờ khỏi tài liệu một cách hiệu quả.
### GroupDocs.Watermark có cung cấp khả năng tương thích đa nền tảng không?
Có, GroupDocs.Watermark tương thích với .NET Framework, .NET Core và .NET Standard, đảm bảo tích hợp liền mạch trên các nền tảng khác nhau.