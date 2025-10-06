---
title: Thay thế văn bản hình dạng bằng văn bản được định dạng trong tài liệu Word
linktitle: Thay thế văn bản hình dạng bằng văn bản được định dạng trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thay thế văn bản hình dạng bằng văn bản được định dạng trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Khả năng chỉnh sửa tài liệu của bạn dễ dàng.
weight: 34
url: /vi/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
type: docs
---
# Thay thế văn bản hình dạng bằng văn bản được định dạng trong tài liệu Word

## Giới thiệu
Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thay thế văn bản hình dạng bằng văn bản được định dạng trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Thư viện này cung cấp các tính năng mạnh mẽ để làm việc với hình mờ, bao gồm thay thế văn bản trong hình dạng.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1.  GroupDocs.Watermark cho .NET: Đảm bảo bạn đã cài đặt và thiết lập GroupDocs.Watermark cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/Watermark/net/).
2. Đường dẫn tài liệu: Bạn nên có đường dẫn đến tài liệu Word nơi bạn muốn thay thế văn bản.

## Nhập không gian tên
Trước khi viết mã, hãy nhập các không gian tên cần thiết:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
 Tải tài liệu Word bằng cách sử dụng`Watermarker` lớp học:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã của bạn tiếp tục ở đây...
}
```
## Bước 2: Lấy nội dung và thay thế văn bản
Sau khi tài liệu được tải, hãy lấy nội dung và thay thế văn bản trong các hình dạng:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Bước 3: Lưu tài liệu
Sau khi thay thế văn bản, lưu tài liệu đã sửa đổi:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Phần kết luận
Việc thay thế văn bản hình dạng bằng văn bản được định dạng trong tài liệu Word được thực hiện dễ dàng với GroupDocs cho .NET. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể quản lý và thao tác văn bản trong tài liệu của mình một cách hiệu quả.

## Câu hỏi thường gặp
### Tôi có thể thay thế văn bản trong các loại tài liệu khác bằng GroupDocs.Watermark cho .NET không?
Có, GroupDocs hỗ trợ nhiều định dạng tài liệu khác nhau như PDF, Excel, PowerPoint, v.v.
### GroupDocs.Watermark có tương thích với .NET Core không?
Có, GroupDocs.Watermark hỗ trợ cả .NET Framework và .NET Core.
### GroupDocs.Watermark có hỗ trợ thêm hình ảnh làm hình mờ không?
Hoàn toàn có thể, GroupDocs.Watermark cho phép bạn thêm cả hình mờ văn bản và hình ảnh vào tài liệu của mình.
### Tôi có thể tùy chỉnh giao diện của hình mờ được thêm bằng GroupDocs.Watermark không?
Có, bạn có toàn quyền kiểm soát hình thức, vị trí và các thuộc tính khác của hình mờ.
### Có phiên bản dùng thử cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể tải xuống bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).