---
title: Thêm hình mờ với cài đặt hình dạng trong Word Docs
linktitle: Thêm hình mờ với cài đặt hình dạng trong Word Docs
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ có cài đặt hình dạng vào tài liệu Word bằng GroupDocs cho .NET. Bảo vệ tài liệu của bạn một cách hiệu quả.
type: docs
weight: 20
url: /vi/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ tìm hiểu quy trình thêm hình mờ có cài đặt hình dạng vào tài liệu Word bằng GroupDocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
1.  Đã cài đặt GroupDocs.Watermark cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/Watermark/net/).
2. Kiến thức cơ bản về lập trình C#.
3. Hiểu biết về xử lý văn bản Word.

## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết để truy cập các lớp và phương thức được yêu cầu.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
Tải tài liệu Word vào nơi bạn muốn thêm hình mờ.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã bổ sung hình mờ ở đây
}
```
## Bước 2: Thêm hình mờ
 Khởi tạo một`TextWatermark` đối tượng và chỉ định văn bản bạn muốn sử dụng làm hình mờ.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Bước 3: Tùy chỉnh cài đặt hình mờ
Đặt các cài đặt khác nhau cho hình mờ, chẳng hạn như căn chỉnh, góc xoay, màu sắc và độ mờ.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Bước 4: Xác định tùy chọn phần hình mờ
Xác định các tùy chọn cho phần hình mờ, chẳng hạn như tên hình dạng và văn bản thay thế.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Bước 5: Thêm hình mờ vào tài liệu
Thêm hình mờ vào tài liệu với các tùy chọn được chỉ định.
```csharp
watermarker.Add(watermark, options);
```
## Bước 6: Lưu tài liệu
Lưu tài liệu với hình mờ được thêm vào.
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Thêm hình mờ có cài đặt hình dạng vào tài liệu Word bằng GroupDocs cho .NET là một quá trình đơn giản. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể bảo vệ tài liệu của mình một cách hiệu quả bằng các hình mờ tùy chỉnh.
## Câu hỏi thường gặp
### Tôi có thể thêm nhiều hình mờ vào cùng một tài liệu không?
Có, bạn có thể thêm nhiều hình mờ với các cài đặt khác nhau vào cùng một tài liệu.
### GroupDocs.Watermark có hỗ trợ các định dạng tài liệu khác ngoài Word không?
Có, GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu khác nhau, bao gồm Excel, PowerPoint, PDF, v.v.
### Tôi có thể tùy chỉnh thêm hình thức của hình mờ không?
Hoàn toàn có thể, bạn có thể điều chỉnh các thông số khác nhau như kích thước phông chữ, kiểu dáng, màu sắc và vị trí để phù hợp với nhu cầu của bạn.
### Có phiên bản dùng thử cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Tôi có thể tìm hỗ trợ cho GroupDocs.Watermark ở đâu?
 Bạn có thể tìm sự hỗ trợ và đặt câu hỏi trên diễn đàn GroupDocs[đây](https://forum.groupdocs.com/c/watermark/19).