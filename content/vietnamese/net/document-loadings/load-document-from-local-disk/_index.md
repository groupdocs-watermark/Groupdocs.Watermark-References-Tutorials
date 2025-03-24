---
title: Tải tài liệu từ đĩa cục bộ
linktitle: Tải tài liệu từ đĩa cục bộ
second_title: API GroupDocs.Watermark .NET
description: Bảo vệ và quản lý tài liệu của bạn bằng Groupdocs cho .NET. Hãy làm theo hướng dẫn chi tiết của chúng tôi để thêm hình mờ một cách liền mạch.
weight: 10
url: /vi/net/document-loadings/load-document-from-local-disk/
---

# Tải tài liệu từ đĩa cục bộ

## Giới thiệu
Hình mờ tài liệu là điều cần thiết trong thời đại kỹ thuật số ngày nay để đảm bảo bảo vệ nội dung, khẳng định quyền sở hữu và bảo mật. Groupdocs.Watermark cho .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm, tìm kiếm và quản lý hình mờ ở nhiều định dạng tài liệu khác nhau. Trong hướng dẫn này, chúng ta sẽ tìm hiểu quy trình sử dụng Groupdocs.Watermark cho .NET để thêm hình mờ vào tài liệu của bạn với hướng dẫn chi tiết từng bước.
## Điều kiện tiên quyết
Trước khi đi sâu vào triển khai, hãy đảm bảo bạn có những điều sau:
1. Đã cài đặt Visual Studio: Bạn sẽ cần Visual Studio hoặc .NET IDE tương thích khác.
2.  Groupdocs.Watermark cho .NET: Tải xuống thư viện từ[Liên kết tải xuống](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework 4.6.1 trở lên.
4. Tài liệu mẫu: Chuẩn bị một tài liệu mẫu để kiểm tra quá trình đóng dấu chìm.
## Nhập không gian tên
Để bắt đầu, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Đây là những điều cần thiết để truy cập các lớp và phương pháp cần thiết cho hình mờ.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu từ đĩa cục bộ
Trước tiên, bạn cần tải tài liệu từ đĩa cục bộ của mình. Tài liệu này sẽ là tài liệu mà bạn sẽ thêm hình mờ.
Xác định đường dẫn của tài liệu bạn muốn tạo hình mờ.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Bước 2: Khởi tạo tùy chọn tải
 Tiếp theo, khởi tạo các tùy chọn tải. Ví dụ: nếu bạn đang làm việc với tài liệu Word, bạn sẽ sử dụng`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Bước 3: Tạo và định cấu hình Watermarker
 Bây giờ, bạn sẽ tạo một phiên bản của`Watermarker` lớp học. Phiên bản này sẽ được sử dụng để quản lý và áp dụng hình mờ cho tài liệu của bạn.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Khối này sẽ chứa các bước tiếp theo để thêm và lưu hình mờ
}
```
## Bước 4: Tạo hình mờ
Tạo hình mờ văn bản. Hình mờ này có thể chứa bất kỳ văn bản nào bạn chọn. Ở đây, chúng tôi sẽ sử dụng "Kiểm tra hình mờ".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Bước 5: Thêm hình mờ vào tài liệu
Thêm hình mờ đã tạo vào tài liệu bằng cách sử dụng`Add` phương pháp của`Watermarker` lớp học.
```csharp
watermarker.Add(watermark);
```
## Bước 6: Lưu tài liệu có hình mờ
Cuối cùng, lưu tài liệu có hình mờ vào đường dẫn đã chỉ định.
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Thêm hình mờ vào tài liệu của bạn bằng Groupdocs cho .NET rất đơn giản và hiệu quả. Hướng dẫn này đã hướng dẫn bạn toàn bộ quá trình từ thiết lập môi trường cho đến lưu tài liệu có hình mờ. Với công cụ mạnh mẽ này, bạn có thể đảm bảo tài liệu của mình được bảo vệ và tài sản trí tuệ của bạn được bảo mật. 
 Để biết thêm chi tiết, hãy kiểm tra[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) và nếu bạn gặp phải bất kỳ vấn đề nào,[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19) là một nơi tuyệt vời để được hỗ trợ. 
## Câu hỏi thường gặp
### Tôi có thể sử dụng phông chữ tùy chỉnh cho hình mờ không?
Có, Groupdocs hỗ trợ phông chữ tùy chỉnh. Bạn có thể chỉ định bất kỳ phông chữ nào được cài đặt trên hệ thống của bạn.
### Những loại tài liệu nào được hỗ trợ?
Groupdocs.Watermark hỗ trợ nhiều định dạng tài liệu bao gồm Word, Excel, PDF, PowerPoint, v.v.
### Làm cách nào để xóa hình mờ khỏi tài liệu?
 Bạn có thể dùng`Remove` phương pháp được cung cấp bởi`Watermarker` lớp để loại bỏ hình mờ.
### Có thể thêm hình mờ hình ảnh?
 Có, bạn có thể thêm hình mờ vào hình ảnh bằng cách sử dụng`ImageWatermark` lớp học.
### Tôi có thể dùng thử Groupdocs.Watermark miễn phí không?
 Hoàn toàn có thể, bạn có thể tải xuống một[dùng thử miễn phí](https://releases.groupdocs.com/) để đánh giá thư viện trước khi mua.