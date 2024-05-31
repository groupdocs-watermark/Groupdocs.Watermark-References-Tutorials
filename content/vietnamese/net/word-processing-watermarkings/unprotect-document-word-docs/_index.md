---
title: Bỏ bảo vệ tài liệu trong Word Docs
linktitle: Bỏ bảo vệ tài liệu trong Word Docs
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách dễ dàng bỏ bảo vệ tài liệu Word bằng GroupDocs.Watermark cho .NET. Thực hiện theo hướng dẫn từng bước của chúng tôi.
type: docs
weight: 38
url: /vi/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## Giới thiệu
GroupDocs.Watermark cho .NET là một API mạnh mẽ cho phép các nhà phát triển làm việc với hình mờ ở nhiều định dạng tài liệu khác nhau, bao gồm cả tài liệu Word. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình bỏ bảo vệ tài liệu Word bằng GroupDocs.Watermark cho .NET. Cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay mới bắt đầu phát triển .NET, hướng dẫn từng bước này sẽ giúp bạn hoàn thành nhiệm vụ một cách hiệu quả.
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1.  GroupDocs.Watermark cho .NET: Bạn cần cài đặt API GroupDocs.Watermark cho .NET trong môi trường phát triển của mình. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/Watermark/net/).
2. Môi trường phát triển: Đảm bảo bạn có môi trường phát triển phù hợp được thiết lập để phát triển .NET, bao gồm Visual Studio hoặc bất kỳ IDE tương thích nào khác.
3. Tài liệu Word: Có sẵn tài liệu Word mà bạn muốn bỏ bảo vệ trong hệ thống tệp của mình.

## Nhập không gian tên
Trước khi đi sâu vào mã, bạn cần nhập các vùng tên cần thiết vào dự án .NET của mình. Điều này cho phép bạn truy cập liền mạch các chức năng do GroupDocs.Watermark cung cấp cho .NET.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Bước 1: Chỉ định đường dẫn tài liệu
Xác định đường dẫn đến tài liệu Word mà bạn muốn bỏ bảo vệ.
```csharp
string documentPath = "Your Document Path";
```
 Thay thế`"Your Document Path"` với đường dẫn thực tế tới tài liệu Word của bạn.
## Bước 2: Đặt tên tệp đầu ra
Chỉ định thư mục nơi bạn muốn lưu tài liệu không được bảo vệ và cung cấp tên cho tệp đầu ra.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Directory"` với đường dẫn thư mục nơi bạn muốn lưu tệp đầu ra.
## Bước 3: Tải tài liệu với các tùy chọn
 Tạo một thể hiện của`WordProcessingLoadOptions` để tải tài liệu Word với các tùy chọn cụ thể.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Bước 4: Bỏ bảo vệ tài liệu
 Khởi tạo`Watermarker` class với đường dẫn tài liệu và các tùy chọn tải. Sau đó, lấy nội dung của tài liệu dưới dạng WordProcessingContent và bỏ bảo vệ nó.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## Phần kết luận
Bằng cách làm theo các bước này, bạn có thể dễ dàng bỏ bảo vệ tài liệu Word bằng GroupDocs.Watermark cho .NET. API này cung cấp một cách đơn giản để thao tác hình mờ và bảo vệ tài liệu của bạn một cách hiệu quả.
## Câu hỏi thường gặp
### GroupDocs.Watermark cho .NET có tương thích với tất cả các phiên bản .NET không?
Có, GroupDocs.Watermark cho .NET tương thích với .NET Framework 2.0 và các phiên bản mới hơn, bao gồm .NET Core và .NET Standard.
### Tôi có thể áp dụng hình mờ cho tài liệu ở các định dạng khác ngoài Word không?
Tuyệt đối! GroupDocs.Watermark cho .NET hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, Excel, PowerPoint, v.v.
### Có phiên bản dùng thử cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể tải phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ kỹ thuật cho GroupDocs.Watermark cho .NET?
 Bạn có thể ghé thăm[Diễn đàn GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) để được hỗ trợ kỹ thuật và hỗ trợ cộng đồng.
### Tôi có thể mua giấy phép tạm thời cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể mua giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/).