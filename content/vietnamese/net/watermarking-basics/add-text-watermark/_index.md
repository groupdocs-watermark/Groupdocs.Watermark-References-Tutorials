---
title: Thêm hình mờ văn bản
linktitle: Thêm hình mờ văn bản
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ văn bản vào tài liệu của bạn bằng Groupdocs cho .NET với hướng dẫn từng bước này.
weight: 11
url: /vi/net/watermarking-basics/add-text-watermark/
---

# Thêm hình mờ văn bản

## Giới thiệu
GroupDocs.Watermark cho .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm, tìm kiếm và xóa hình mờ khỏi các định dạng tài liệu khác nhau trong các ứng dụng .NET. Trong hướng dẫn này, chúng tôi sẽ tập trung vào việc thêm hình mờ văn bản vào tài liệu bằng GroupDocs.Watermark.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1. Kiến thức cơ bản về ngôn ngữ lập trình C#.
2. Visual Studio được cài đặt trên hệ thống của bạn.
3.  Đã cài đặt thư viện GroupDocs.Watermark cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/Watermark/net/).

## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết vào dự án C# của mình.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Bước 1: Xác định đường dẫn tài liệu và thư mục đầu ra
Xác định đường dẫn đến tài liệu đầu vào của bạn và thư mục đầu ra nơi tài liệu có hình mờ sẽ được lưu.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"` với đường dẫn tuyệt đối hoặc tương đối đến tài liệu đầu vào của bạn, ví dụ:`@"C:\Docs\document.pdf"`. Ngoài ra, hãy chỉ định thư mục nơi bạn muốn lưu tài liệu có hình mờ.
## Bước 2: Thêm hình mờ văn bản
 Khởi tạo`Watermarker` class với đường dẫn tài liệu đầu vào. Sau đó, tạo một`TextWatermark` đối tượng có cài đặt văn bản và phông chữ mong muốn.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm hình mờ văn bản vào tài liệu bằng GroupDocs.Watermark cho .NET. Với API trực quan, các nhà phát triển có thể dễ dàng thao tác hình mờ ở nhiều định dạng tài liệu khác nhau.
## Câu hỏi thường gặp
### GroupDocs.Watermark cho .NET có tương thích với tất cả các định dạng tài liệu không?
GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Microsoft Word, Excel, PowerPoint, v.v.
### Tôi có thể tùy chỉnh hình thức của hình mờ văn bản không?
Có, bạn có thể tùy chỉnh các thuộc tính khác nhau như phông chữ, màu sắc, căn chỉnh và độ mờ của hình mờ văn bản.
### GroupDocs.Watermark có hỗ trợ xóa hình mờ khỏi tài liệu không?
Có, GroupDocs.Watermark cung cấp chức năng tìm kiếm và xóa hình mờ khỏi tài liệu.
### Tôi có thể dùng thử GroupDocs.Watermark cho .NET trước khi mua không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ kỹ thuật cho GroupDocs.Watermark?
 Bạn có thể nhận được hỗ trợ kỹ thuật bằng cách truy cập[Diễn đàn GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).