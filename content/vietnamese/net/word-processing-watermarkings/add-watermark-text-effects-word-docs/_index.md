---
title: Thêm Watermark với hiệu ứng văn bản trong Word Docs
linktitle: Thêm Watermark với hiệu ứng văn bản trong Word Docs
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ tùy chỉnh cùng với hiệu ứng văn bản vào tài liệu Word bằng GroupDocs.Watermark cho .NET. Bảo mật tài liệu và thu hút trực quan một cách dễ dàng.
weight: 21
url: /vi/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---

# Thêm Watermark với hiệu ứng văn bản trong Word Docs

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm hình mờ có hiệu ứng văn bản vào tài liệu Word bằng GroupDocs.Watermark cho .NET. Bằng cách làm theo các hướng dẫn từng bước này, bạn sẽ có thể cải thiện tài liệu của mình bằng các hình mờ tùy chỉnh bao gồm nhiều hiệu ứng văn bản khác nhau.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
1.  GroupDocs.Watermark cho .NET: Tải xuống và cài đặt thư viện từ[trang mạng](https://releases.groupdocs.com/Watermark/net/).
2. Đường dẫn tài liệu: Biết đường dẫn của tài liệu Word mà bạn muốn thêm hình mờ.
3. Thư mục đầu ra: Có một thư mục mà bạn muốn lưu tài liệu đã sửa đổi.

## Nhập không gian tên
Đảm bảo nhập các không gian tên cần thiết để truy cập các lớp và phương thức được yêu cầu:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
Tải tài liệu Word mà bạn muốn thêm hình mờ vào.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã để thêm hình mờ ở đây
}
```
## Bước 2: Thêm hình mờ với hiệu ứng văn bản
Tạo hình mờ văn bản với văn bản và phông chữ mong muốn, sau đó xác định các hiệu ứng văn bản như định dạng dòng.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## Bước 3: Tùy chỉnh tùy chọn hình mờ
Xác định các tùy chọn phần hình mờ, chẳng hạn như hiệu ứng văn bản và gán chúng cho hình mờ.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Bước 4: Lưu tài liệu
Lưu tài liệu đã sửa đổi với hình mờ được thêm vào.
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Việc thêm hình mờ kèm hiệu ứng văn bản vào tài liệu Word có thể nâng cao đáng kể sự hấp dẫn và khả năng bảo vệ trực quan của chúng. Với GroupDocs.Watermark dành cho .NET, quy trình này trở nên hợp lý và có thể tùy chỉnh, cho phép bạn tạo tài liệu trông chuyên nghiệp một cách hiệu quả.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh phông chữ và kích thước của văn bản hình mờ không?
Có, bạn có thể chỉ định phông chữ và kích thước trong khi tạo đối tượng TextWatermark.
### Có thể thêm nhiều hình mờ vào một tài liệu không?
Hoàn toàn có thể, GroupDocs.Watermark for .NET hỗ trợ thêm nhiều hình mờ với các cài đặt khác nhau vào một tài liệu.
### GroupDocs.Watermark có hỗ trợ các định dạng tài liệu khác ngoài Word không?
Có, nó hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Excel, PowerPoint, v.v.
### Tôi có thể xóa hình mờ sau khi nó được thêm vào tài liệu không?
Có, thư viện cung cấp các phương pháp để dễ dàng xóa hình mờ khỏi tài liệu.
### Có phiên bản dùng thử nào dành cho mục đích thử nghiệm không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).