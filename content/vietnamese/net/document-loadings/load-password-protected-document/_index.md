---
title: Tải tài liệu được bảo vệ bằng mật khẩu
linktitle: Tải tài liệu được bảo vệ bằng mật khẩu
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào tài liệu được bảo vệ bằng mật khẩu bằng Groupdocs cho .NET với hướng dẫn từng bước của chúng tôi. Bảo mật và gắn nhãn hiệu cho các tập tin của bạn một cách dễ dàng.
type: docs
weight: 13
url: /vi/net/document-loadings/load-password-protected-document/
---
## Giới thiệu
Bạn đang tìm cách bảo vệ tài liệu của mình bằng cách thêm hình mờ, ngay cả khi chúng được bảo vệ bằng mật khẩu? Groupdocs.Watermark cho .NET là một công cụ mạnh mẽ cho phép bạn làm việc đó. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình tải tài liệu được bảo vệ bằng mật khẩu và thêm hình mờ vào tài liệu đó bằng Groupdocs.Watermark cho .NET. Hãy đi sâu vào!
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
1. Visual Studio: Bất kỳ phiên bản Visual Studio nào được cài đặt trên máy của bạn.
2. .NET Framework: Đảm bảo rằng bạn có .NET Framework 4.6.1 trở lên.
3. Groupdocs.Watermark cho .NET: Tải xuống và cài đặt thư viện Groupdocs.Watermark cho .NET từ[Liên kết tải xuống](https://releases.groupdocs.com/Watermark/net/).
## Nhập không gian tên
Đầu tiên, chúng ta cần nhập các không gian tên cần thiết vào dự án của mình. Điều này đảm bảo rằng chúng tôi có thể truy cập tất cả các phương thức và thuộc tính do Groupdocs.Watermark cung cấp cho .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Bây giờ, hãy chia quy trình thành các bước đơn giản, dễ thực hiện.
## Bước 1: Thiết lập dự án của bạn
Để bắt đầu, hãy tạo Ứng dụng bảng điều khiển C# mới trong Visual Studio. Sau khi dự án của bạn được thiết lập, hãy cài đặt thư viện Groupdocs.Watermark cho .NET thông qua Trình quản lý gói NuGet.
1. Mở Visual Studio và tạo Ứng dụng Console mới (.NET Framework).
2.  Đi đến`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Tìm kiếm`GroupDocs.Watermark` và cài đặt gói.
## Bước 2: Xác định đường dẫn tài liệu
Tiếp theo, bạn sẽ cần xác định đường dẫn đến tài liệu được bảo vệ bằng mật khẩu và đường dẫn tệp đầu ra nơi tài liệu có hình mờ sẽ được lưu.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"` Và`"Your Document Directory"` với các đường dẫn thực tế trên máy của bạn.
## Bước 3: Đặt tùy chọn tải bằng mật khẩu
Để mở tài liệu được bảo vệ bằng mật khẩu, bạn phải cung cấp mật khẩu trong tùy chọn tải.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Thay thế`"P@$w0rd"` bằng mật khẩu thực tế của tài liệu của bạn.
## Bước 4: Tải tài liệu
 Bây giờ, hãy tải tài liệu bằng cách sử dụng`Watermarker` lớp học.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã để thêm hình mờ của bạn sẽ xuất hiện ở đây
}
```
## Bước 5: Tạo hình mờ
Chúng tôi sẽ tạo hình mờ văn bản mà chúng tôi có thể thêm vào tài liệu. Bạn có thể tùy chỉnh văn bản, phông chữ, kích thước và các thuộc tính khác nếu cần.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Hãy thoải mái thay đổi`"Test watermark"`, `"Arial"` , Và`12` theo văn bản, phông chữ và kích thước ưa thích của bạn.
## Bước 6: Thêm hình mờ
 Thêm hình mờ vào tài liệu bằng cách sử dụng`Add` phương pháp của`Watermarker` lớp học.
```csharp
watermarker.Add(watermark);
```
## Bước 7: Lưu tài liệu có hình chìm mờ
Cuối cùng, lưu tài liệu có hình mờ vào đường dẫn tệp đầu ra đã chỉ định.
```csharp
watermarker.Save(outputFileName);
```
## Phần kết luận
Thêm hình mờ vào tài liệu được bảo vệ bằng mật khẩu của bạn là một quá trình đơn giản với Hình mờ cho .NET. Bằng cách làm theo các bước đơn giản này, bạn có thể đảm bảo rằng tài liệu của mình được bảo vệ và gắn nhãn hiệu theo yêu cầu của bạn. Cho dù đó là vì mục đích bảo mật, xây dựng thương hiệu hay tuân thủ, việc tạo hình mờ cho tài liệu của bạn chưa bao giờ dễ dàng hơn thế.
## Câu hỏi thường gặp
### Tôi có thể thêm hình mờ hình ảnh bằng Groupdocs.Watermark cho .NET không?
 Có, bạn có thể thêm cả hình mờ văn bản và hình ảnh. Đơn giản chỉ cần sử dụng`ImageWatermark` lớp học thay vì`TextWatermark`.
### Có thể xóa hình mờ khỏi tài liệu không?
Có, Groupdocs.Watermark for .NET cung cấp các phương pháp tìm kiếm và xóa hình mờ.
### Groupdocs.Watermark cho .NET có hỗ trợ các định dạng tài liệu khác ngoài PDF không?
Có, nó hỗ trợ nhiều định dạng bao gồm Word, Excel, PowerPoint, v.v.
### Tôi có thể tùy chỉnh hình thức của hình mờ không?
Tuyệt đối! Bạn có thể tùy chỉnh phông chữ, kích thước, màu sắc, độ mờ, v.v.
### Tôi có thể nhận hỗ trợ ở đâu nếu gặp vấn đề?
 Bạn có thể ghé thăm[Diễn đàn hỗ trợ Groupdocs](https://forum.groupdocs.com/c/watermark/19) để được giúp đỡ và hướng dẫn.