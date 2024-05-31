---
title: Lưu tài liệu vào cùng một tệp hoặc luồng
linktitle: Lưu tài liệu vào cùng một tệp hoặc luồng
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào tài liệu bằng Groupdocs.Watermark cho .NET. Hướng dẫn này cung cấp hướng dẫn để đảm bảo tính toàn vẹn và bảo vệ tài liệu.
type: docs
weight: 10
url: /vi/net/document-savings/save-document-same-file-stream/
---
## Giới thiệu
Trong thời đại kỹ thuật số ngày nay, việc thêm hình mờ vào tài liệu đã trở nên cần thiết để bảo vệ tài sản trí tuệ và đảm bảo tính toàn vẹn của thương hiệu. Groupdocs.Watermark cho .NET cung cấp một giải pháp mạnh mẽ cho các nhà phát triển muốn nhúng hình mờ vào tài liệu một cách liền mạch. Hướng dẫn toàn diện này sẽ hướng dẫn bạn các bước lưu tài liệu có hình mờ vào cùng một tệp hoặc luồng bằng Groupdocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có những điều sau:
1. Môi trường phát triển: Visual Studio được cài đặt trên máy của bạn.
2. .NET Framework: Đảm bảo bạn có .NET Framework 4.0 trở lên.
3.  Groupdocs.Watermark cho .NET: Tải xuống và cài đặt phiên bản mới nhất từ[địa điểm](https://releases.groupdocs.com/Watermark/net/).
4.  Giấy phép: Xin giấy phép tạm thời hoặc vĩnh viễn từ[đây](https://purchase.groupdocs.com/temporary-license/).
## Nhập không gian tên
Để bắt đầu sử dụng Groupdocs.Watermark trong dự án .NET của bạn, bạn cần nhập các vùng tên cần thiết:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Bước 1: Thiết lập dự án của bạn
Trước khi thêm hình mờ vào tài liệu của mình, chúng ta cần thiết lập dự án .NET của mình. Đây là cách thực hiện:
1. Tạo một dự án mới: Mở Visual Studio và tạo Ứng dụng Console mới.
2. Thêm tài liệu tham khảo Groupdocs.Watermark: Nhấp chuột phải vào dự án trong Solution Explorer, chọn "Quản lý gói NuGet" và cài đặt gói Groupdocs.Watermark.
## Bước 2: Sao chép tài liệu sang vị trí mới
Để tránh thay đổi trực tiếp tài liệu gốc, trước tiên bạn nên sao chép tài liệu đó sang vị trí mới. Đây là cách bạn làm điều đó:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Bước 3: Khởi tạo Watermarker
Bây giờ chúng ta đã sao chép tài liệu của mình, chúng ta có thể khởi tạo lớp Watermarker để thêm hình mờ của mình:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Hình mờ ở đây
}
```
## Bước 4: Tạo và thêm hình mờ văn bản
Tiếp theo, chúng tôi tạo hình mờ văn bản và thêm nó vào tài liệu của mình:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Bước 5: Lưu tài liệu
Cuối cùng, lưu tài liệu có áp dụng hình mờ:
```csharp
watermarker.Save();
```
## Phần kết luận
Thêm hình mờ vào tài liệu của bạn bằng Groupdocs cho .NET rất đơn giản và hiệu quả. Bằng cách làm theo các bước được nêu ở trên, bạn có thể bảo vệ tài liệu của mình và duy trì tính toàn vẹn của chúng một cách dễ dàng. Để biết thêm chi tiết, bạn có thể tham khảo[tài liệu](https://reference.groupdocs.com/Watermark/net/).
## Câu hỏi thường gặp
### Tôi có thể sử dụng hình ảnh làm hình mờ thay vì văn bản không?
Có, Groupdocs.Watermark cho phép bạn sử dụng hình ảnh, hình dạng và văn bản làm hình mờ.
### Làm cách nào để xóa hình mờ khỏi tài liệu?
 Bạn có thể xóa hình mờ bằng cách truy cập bộ sưu tập hình mờ trong tài liệu và sử dụng`Remove` phương pháp.
### Có thể tùy chỉnh hình thức của hình mờ không?
Tuyệt đối. Bạn có thể tùy chỉnh phông chữ, kích thước, màu sắc và vị trí của hình mờ.
### Tôi có thể áp dụng nhiều hình mờ cho một tài liệu không?
 Có, bạn có thể thêm nhiều hình mờ bằng cách gọi`Add` phương pháp nhiều lần với các đối tượng hình mờ khác nhau.
### Groupdocs.Watermark có tương thích với tất cả các định dạng tài liệu không?
Groupdocs.Watermark hỗ trợ nhiều định dạng tài liệu bao gồm PDF, DOCX, PPTX và nhiều định dạng khác.