---
title: Thêm hình mờ vào trang cụ thể trong tài liệu Word
linktitle: Thêm hình mờ vào trang cụ thể trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào các trang cụ thể trong tài liệu Word bằng GroupDocs cho .NET. Bảo vệ nội dung của bạn một cách dễ dàng.
weight: 14
url: /vi/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
type: docs
---
# Thêm hình mờ vào trang cụ thể trong tài liệu Word

## Giới thiệu
Hình mờ tài liệu là một khía cạnh quan trọng của bảo mật tài liệu và xây dựng thương hiệu. Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm hình mờ vào một trang cụ thể trong tài liệu Word bằng GroupDocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
- Kiến thức cơ bản về lập trình C#.
- Đã cài đặt Visual Studio IDE.
- GroupDocs.Watermark cho .NET được cài đặt trong dự án của bạn.

## Nhập không gian tên
Trước khi đi sâu vào mã, hãy đảm bảo bạn nhập các không gian tên cần thiết:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã của bạn sẽ ở đây
}
```
## Bước 2: Thêm hình mờ
```csharp
// Xác định văn bản và kiểu hình mờ
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Thêm hình mờ vào trang cuối cùng
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Bước 3: Lưu tài liệu
```csharp
// Lưu tài liệu có hình mờ
watermarker.Save(outputFileName);
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm hình mờ vào một trang cụ thể trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Bằng cách làm theo các bước này, bạn có thể bảo vệ tài liệu của mình một cách hiệu quả và thêm các yếu tố thương hiệu nếu cần.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh văn bản và kiểu hình mờ không?
Có, bạn có thể tùy chỉnh văn bản, phông chữ, kích thước, màu sắc và vị trí của hình mờ theo yêu cầu của bạn.
### GroupDocs.Watermark cho .NET có tương thích với các định dạng tài liệu khác không?
Có, GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu khác nhau, bao gồm Word, Excel, PowerPoint, PDF, v.v.
### Tôi có thể thêm nhiều hình mờ vào một tài liệu không?
Hoàn toàn có thể, bạn có thể thêm nhiều hình mờ với nội dung và kiểu dáng khác nhau vào cùng một tài liệu.
### Có bản dùng thử miễn phí cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể khám phá các tính năng của GroupDocs.Watermark bằng bản dùng thử miễn phí. Chỉ cần truy cập liên kết được cung cấp để bắt đầu[đây](https://releases.groupdocs.com/).
### Tôi có thể nhận hỗ trợ kỹ thuật cho GroupDocs.Watermark ở đâu?
 Bạn có thể tìm thấy các tài nguyên hữu ích và nhận hỗ trợ kỹ thuật từ[đây](https://forum.groupdocs.com/c/watermark/19)diễn đàn GroupDocs.Watermark. Truy cập liên kết được cung cấp để tham gia cộng đồng.