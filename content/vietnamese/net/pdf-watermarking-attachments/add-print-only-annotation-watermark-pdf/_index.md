---
title: Thêm hình mờ chú thích chỉ in vào PDF
linktitle: Thêm hình mờ chú thích chỉ in vào PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ chú thích chỉ in vào tệp PDF bằng GroupDocs.Watermark cho .NET. Tăng cường bảo mật tài liệu và xây dựng thương hiệu một cách dễ dàng.
weight: 13
url: /vi/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Thêm hình mờ chú thích chỉ in vào PDF

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ đi sâu vào quy trình thêm hình mờ chú thích chỉ in vào tệp PDF bằng GroupDocs.Watermark cho .NET. Hình mờ tài liệu là một khía cạnh quan trọng của bảo mật tài liệu và xây dựng thương hiệu và GroupDocs.Watermark cung cấp giải pháp liền mạch cho các nhà phát triển .NET để đạt được điều này.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
- Hiểu biết cơ bản về ngôn ngữ lập trình C#.
- Visual Studio được cài đặt trên máy của bạn.
- Thư viện GroupDocs.Watermark cho .NET được cài đặt trong dự án của bạn.

## Nhập không gian tên
Để bắt đầu, hãy đảm bảo bạn nhập các không gian tên cần thiết:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu
 Trước tiên, bạn cần tải tài liệu PDF mà bạn muốn tạo hình mờ. Thay thế`"Your Document Path"` với đường dẫn đến tệp PDF của bạn và`"Your Document Directory"` với thư mục mà bạn muốn lưu tập tin đầu ra.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã hình mờ sẽ được thêm vào đây
}
```
## Bước 2: Thêm hình mờ
Tiếp theo, tạo đối tượng hình mờ văn bản với văn bản và phông chữ mong muốn. Bộ`isPrintOnly` ĐẾN`true` để đảm bảo rằng hình mờ chỉ hiển thị khi tài liệu được in chứ không phải ở chế độ xem.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Bước 3: Định cấu hình tùy chọn hình mờ
Xác định các tùy chọn cho hình mờ, chẳng hạn như chỉ mục trang nơi hình mờ sẽ được thêm vào và chỉ định nó làm chú thích chỉ in.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Bước 4: Áp dụng hình mờ
Thêm hình mờ vào tài liệu bằng các tùy chọn đã chỉ định và lưu tệp đầu ra.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm hình mờ chú thích chỉ in vào tài liệu PDF bằng GroupDocs.Watermark cho .NET. Điều này cho phép các nhà phát triển tăng cường bảo mật tài liệu và xây dựng thương hiệu một cách dễ dàng.
## Câu hỏi thường gặp
### GroupDocs.Watermark có tương thích với các định dạng tài liệu khác ngoài PDF không?
Có, GroupDocs hỗ trợ nhiều định dạng tài liệu khác nhau như Word, Excel, PowerPoint và hình ảnh.
### Tôi có thể tùy chỉnh hình thức của hình mờ không?
Chắc chắn, GroupDocs.Watermark cung cấp các tùy chọn mở rộng để tùy chỉnh văn bản, phông chữ, màu sắc, kích thước và vị trí hình mờ.
### GroupDocs.Watermark có cung cấp khả năng xử lý hàng loạt không?
Hoàn toàn có thể, các nhà phát triển có thể tạo hình mờ cho nhiều tài liệu cùng lúc bằng cách sử dụng các tính năng xử lý hàng loạt.
### Có phiên bản dùng thử cho GroupDocs.Watermark không?
Có, bạn có thể truy cập phiên bản dùng thử miễn phí của GroupDocs.Watermark từ liên kết được cung cấp.
### Làm cách nào tôi có thể nhận được hỗ trợ kỹ thuật cho GroupDocs.Watermark?
Bạn có thể tìm kiếm hỗ trợ kỹ thuật từ diễn đàn GroupDocs.Watermark có sẵn tại liên kết hỗ trợ được cung cấp.