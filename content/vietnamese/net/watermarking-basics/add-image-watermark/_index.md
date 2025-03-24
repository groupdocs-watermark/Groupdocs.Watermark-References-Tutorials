---
title: Thêm hình mờ hình ảnh
linktitle: Thêm hình mờ hình ảnh
second_title: API GroupDocs.Watermark .NET
description: Dễ dàng thêm hình mờ hình ảnh vào tài liệu của bạn bằng GroupDocs.Watermark cho .NET. Bảo vệ tài sản trí tuệ của bạn một cách dễ dàng.
weight: 10
url: /vi/net/watermarking-basics/add-image-watermark/
---

# Thêm hình mờ hình ảnh

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ đi sâu vào quy trình thêm hình mờ vào tài liệu của bạn bằng GroupDocs.Watermark cho .NET. Tài liệu có hình mờ là điều cần thiết để bảo vệ sở hữu trí tuệ và thương hiệu. Với GroupDocs.Watermark cho .NET, bạn có thể tích hợp liền mạch hình mờ vào các định dạng tài liệu khác nhau như Word, Excel, PowerPoint, PDF, v.v.
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1.  GroupDocs.Watermark cho Thư viện .NET: Tải xuống và cài đặt thư viện GroupDocs.Watermark cho .NET từ[trang mạng](https://releases.groupdocs.com/Watermark/net/).
2. Tài liệu: Chuẩn bị sẵn tài liệu mà bạn muốn thêm hình mờ.
3. Hình ảnh cho Hình mờ: Chuẩn bị tệp hình ảnh mà bạn muốn sử dụng làm hình mờ.

## Nhập không gian tên
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Bước 1: Khởi tạo đường dẫn tài liệu và thư mục đầu ra
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"`với đường dẫn tuyệt đối hoặc tương đối đến tài liệu của bạn và`"Your Document Directory"` với thư mục mà bạn muốn lưu tài liệu có hình mờ.
## Bước 2: Mở luồng tài liệu và khởi tạo Watermarker
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Quá trình đóng dấu chìm sẽ diễn ra ở đây
    }
}
```
 Mở luồng tài liệu bằng cách sử dụng`FileStream` và khởi tạo`Watermarker` sự vật.
## Bước 3: Thêm hình mờ hình ảnh
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Tạo ra một`ImageWatermark` đối tượng có đường dẫn đến tệp hình ảnh bạn muốn sử dụng làm hình mờ. Đặt căn chỉnh ngang và dọc của hình mờ.
## Bước 4: Lưu tài liệu có hình chìm mờ
```csharp
watermarker.Save(outputFileName);
```
Lưu tài liệu có hình mờ vào thư mục đầu ra được chỉ định với tên tệp mong muốn.

## Phần kết luận
Tóm lại, GroupDocs.Watermark cho .NET cung cấp giải pháp toàn diện để thêm hình mờ vào các định dạng tài liệu khác nhau một cách dễ dàng. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể thêm hình mờ vào tài liệu của mình một cách hiệu quả và bảo vệ tài sản trí tuệ của mình.
## Câu hỏi thường gặp
### Tôi có thể thêm hình mờ văn bản bằng GroupDocs.Watermark cho .NET không?
Có, GroupDocs.Watermark for .NET hỗ trợ thêm cả hình mờ hình ảnh và văn bản vào tài liệu.
### GroupDocs.Watermark cho .NET có tương thích với các định dạng tài liệu khác nhau không?
Hoàn toàn có thể, GroupDocs.Watermark for .NET hỗ trợ nhiều định dạng tài liệu bao gồm Word, Excel, PowerPoint, PDF, v.v.
### GroupDocs.Watermark cho .NET có cung cấp các tùy chọn tùy chỉnh cho hình mờ không?
Có, bạn có thể tùy chỉnh các khía cạnh khác nhau của hình mờ như vị trí, kích thước, độ mờ và xoay.
### Tôi có thể xóa hình mờ khỏi tài liệu bằng GroupDocs.Watermark cho .NET không?
Có, GroupDocs.Watermark for .NET cung cấp chức năng phát hiện và xóa hình mờ khỏi tài liệu.
### Có phiên bản dùng thử cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể sử dụng phiên bản dùng thử miễn phí từ trang web để khám phá các tính năng trước khi mua[đây](https://releases.groupdocs.com/).