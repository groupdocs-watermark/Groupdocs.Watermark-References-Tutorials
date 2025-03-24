---
title: Tải tài liệu từ luồng
linktitle: Tải tài liệu từ luồng
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào tài liệu bằng GroupDocs.Watermark cho .NET với hướng dẫn này. Hoàn hảo cho các nhà phát triển muốn tăng cường bảo mật tài liệu.
weight: 11
url: /vi/net/document-loadings/load-document-from-stream/
---

# Tải tài liệu từ luồng

## Giới thiệu
Bạn đang muốn thêm hình mờ vào tài liệu của mình một cách liền mạch bằng .NET? Đừng tìm đâu xa! GroupDocs.Watermark cho .NET là một thư viện mạnh mẽ và dễ sử dụng, cho phép bạn quản lý hình mờ ở nhiều định dạng tài liệu khác nhau. Cho dù bạn đang làm việc với tệp PDF, tài liệu Word hay hình ảnh, công cụ này đều có thể giúp bạn. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình tải tài liệu từ luồng và thêm hình mờ theo từng bước. Vì vậy, hãy đi sâu vào ngay!
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập sau:
1. Visual Studio: Mọi phiên bản Visual Studio gần đây đều hoạt động tốt.
2. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework 4.0 trở lên.
3.  GroupDocs.Watermark cho .NET: Bạn có thể tải xuống từ[đây](https://releases.groupdocs.com/Watermark/net/).
4. Kiến thức cơ bản về C#: Làm quen với C# và các khái niệm lập trình hướng đối tượng sẽ hữu ích.

## Nhập không gian tên
Để sử dụng GroupDocs.Watermark trong dự án của bạn, bạn sẽ cần nhập các vùng tên cần thiết. Điều này sẽ cho phép bạn truy cập các tính năng của thư viện mà không gặp bất kỳ sự cố nào.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Bước 1: Thiết lập dự án của bạn
Trước tiên, bạn cần thiết lập dự án của mình trong Visual Studio. Đây là cách bạn làm điều đó:
1. Tạo một dự án mới: Mở Visual Studio và tạo dự án Ứng dụng bảng điều khiển C# mới.
2.  Cài đặt GroupDocs.Watermark: Cài đặt thư viện GroupDocs.Watermark thông qua Trình quản lý gói NuGet. Đơn giản chỉ cần tìm kiếm`GroupDocs.Watermark` và cài đặt nó.
## Bước 2: Xác định đường dẫn tài liệu
Tiếp theo, bạn cần xác định đường dẫn cho tài liệu của mình và tệp đầu ra nơi tài liệu có hình mờ sẽ được lưu.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"` với đường dẫn thực tế của tài liệu bạn muốn tạo hình mờ và`"Your Document Directory"` với thư mục mà bạn muốn lưu tài liệu có hình mờ.
## Bước 3: Tải tài liệu từ luồng
Bây giờ, hãy tải tài liệu từ một luồng. Điều này liên quan đến việc mở tài liệu dưới dạng luồng và sau đó sử dụng`Watermarker` lớp từ thư viện GroupDocs.Watermark để quản lý nó.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Mã quản lý hình mờ của bạn sẽ có ở đây
}
```
 Đoạn mã này đảm bảo rằng tài liệu được mở dưới dạng luồng và`Watermarker` lớp được khởi tạo với luồng này. Các`using` Tuyên bố đảm bảo rằng tài nguyên được xử lý đúng cách sau khi sử dụng.
## Bước 4: Tạo và thêm hình mờ
Tạo hình mờ thật đơn giản với GroupDocs.Watermark. Trong ví dụ này, chúng ta sẽ tạo một hình mờ văn bản đơn giản.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Ở đây, chúng tôi tạo ra một`TextWatermark` đối tượng có nội dung "Kiểm tra hình mờ" và chỉ định chi tiết phông chữ. Sau đó, chúng tôi thêm hình mờ này vào tài liệu bằng cách sử dụng`Add` phương pháp của`Watermarker` lớp học.
## Bước 5: Lưu tài liệu có hình chìm mờ
Cuối cùng, lưu tài liệu có hình mờ vào đường dẫn đầu ra đã chỉ định.
```csharp
watermarker.Save(outputFileName);
```
 Mã này lưu tài liệu với hình mờ mới được thêm vào`outputFileName` đường dẫn bạn đã xác định trước đó.

## Phần kết luận
Chúc mừng! Bạn đã thêm thành công hình mờ vào tài liệu của mình bằng GroupDocs.Watermark cho .NET. Thư viện này giúp việc quản lý hình mờ trên nhiều định dạng tài liệu trở nên vô cùng dễ dàng. Cho dù bạn cần thêm văn bản, hình ảnh hay các loại hình mờ khác, GroupDocs.Watermark đều có những công cụ bạn cần. Đừng quên kiểm tra[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) để biết thêm các tính năng nâng cao và tùy chọn tùy chỉnh.
## Câu hỏi thường gặp
### Tôi có thể thêm những loại hình mờ nào bằng GroupDocs.Watermark cho .NET?
Bạn có thể thêm hình mờ văn bản, hình mờ hình ảnh và thậm chí cả các hình dạng và biểu tượng phức tạp. Thư viện hỗ trợ nhiều tùy chọn tùy chỉnh.
### Tôi có thể xóa hình mờ khỏi tài liệu bằng GroupDocs.Watermark không?
Có, GroupDocs.Watermark cũng cho phép bạn xóa hình mờ hiện có khỏi tài liệu.
### Có bản dùng thử miễn phí cho GroupDocs.Watermark không?
 Có, bạn có thể tải xuống bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào để mua giấy phép cho GroupDocs.Watermark?
Bạn có thể mua giấy phép trực tiếp từ[Trang web GroupDocs](https://purchase.groupdocs.com/buy).
### Tôi có thể nhận hỗ trợ ở đâu nếu gặp vấn đề?
 Để được hỗ trợ, bạn có thể truy cập[Diễn đàn hỗ trợ GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).