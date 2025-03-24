---
title: Thêm hình mờ hình ảnh
linktitle: Thêm hình mờ hình ảnh
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ hình ảnh vào tài liệu của bạn bằng GroupDocs.Watermark cho .NET với hướng dẫn chi tiết từng bước của chúng tôi.
weight: 11
url: /vi/net/image-watermarkings/add-image-watermark/
---

# Thêm hình mờ hình ảnh

## Giới thiệu
Chào mừng bạn đến với hướng dẫn toàn diện này về cách thêm hình mờ bằng GroupDocs.Watermark cho .NET! Hình mờ là một cách mạnh mẽ để bảo vệ tài liệu và hình ảnh của bạn khỏi việc sử dụng trái phép, đảm bảo rằng tài sản trí tuệ của bạn vẫn được an toàn. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn toàn bộ quá trình, từ thiết lập môi trường đến áp dụng hình mờ cho tài liệu của bạn. Cho dù bạn là nhà phát triển dày dạn hay chỉ mới bắt đầu, bạn sẽ thấy hướng dẫn này hữu ích và dễ làm theo.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có mọi thứ mình cần:
- Môi trường phát triển: Visual Studio hoặc bất kỳ IDE tương thích .NET nào
- .NET Framework: .NET Framework 4.0 trở lên
-  GroupDocs.Watermark dành cho .NET: Bạn có thể tải xuống từ[Trang web GroupDocs](https://releases.groupdocs.com/Watermark/net/)
-  Tệp hình ảnh: Tệp hình ảnh được sử dụng làm hình mờ (ví dụ:`watermark.jpg`)
- Tệp Tài liệu: Một tài liệu mà bạn muốn thêm hình mờ (ví dụ:`presentation.pptx`)
## Nhập không gian tên
Để bắt đầu, bạn cần nhập các vùng tên cần thiết vào dự án của mình. Điều này rất cần thiết để truy cập các chức năng của GroupDocs.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Trong phần này, chúng tôi sẽ chia nhỏ quy trình thêm hình mờ vào hình ảnh thành các bước rõ ràng và dễ quản lý. Hãy thực hiện cẩn thận từng bước để tạo hình mờ thành công cho tài liệu của bạn.
## Bước 1: Thiết lập môi trường của bạn
 Đầu tiên, hãy đảm bảo rằng môi trường phát triển của bạn được thiết lập đúng cách. Cài đặt thư viện GroupDocs.Watermark bằng cách tải xuống từ[Trang web GroupDocs](https://releases.groupdocs.com/Watermark/net/).
1. Mở dự án của bạn trong Visual Studio.
2. Nhấp chuột phải vào dự án của bạn trong Solution Explorer.
3. Chọn "Quản lý gói NuGet ..."
4.  Tìm kiếm`GroupDocs.Watermark` và cài đặt nó.
## Bước 2: Xác định đường dẫn tệp
Tiếp theo, bạn sẽ cần xác định đường dẫn cho tài liệu đầu vào và thư mục đầu ra. Điều này giúp chương trình xác định vị trí các tập tin cần làm việc.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Thay thế`"Your Document Path"` Và`"Your Document Directory"` với các đường dẫn thực tế tới tài liệu của bạn và thư mục đầu ra mong muốn.
## Bước 3: Khởi tạo Watermarker
Bây giờ, khởi tạo`Watermarker` class bằng đường dẫn đến tài liệu của bạn. Lớp này chịu trách nhiệm quản lý quá trình đóng dấu thủy ấn.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Tiến hành các bước tiếp theo trong khối sử dụng này
}
```
## Bước 4: Tạo hình mờ cho hình ảnh
 Trong`Watermarker` khối, tạo một phiên bản của`ImageWatermark` class bằng cách sử dụng đường dẫn đến hình ảnh mờ của bạn. Lớp này đại diện cho hình ảnh bạn muốn sử dụng làm hình mờ.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Tiếp tục đến bước tiếp theo trong khối sử dụng này
}
```
## Bước 5: Thêm hình mờ vào tài liệu
 Với`ImageWatermark` phiên bản đã sẵn sàng, hãy thêm nó vào tài liệu của bạn bằng cách sử dụng`Add` phương pháp của`Watermarker` lớp học.
```csharp
watermarker.Add(watermark);
```
## Bước 6: Lưu tài liệu
Cuối cùng, lưu tài liệu có hình mờ vào thư mục đầu ra được chỉ định. Bước này đảm bảo rằng những thay đổi của bạn được ghi vào một tệp mới.
```csharp
watermarker.Save(outputFileName);
```
## Phần kết luận
Chúc mừng! Bạn đã thêm thành công hình mờ vào tài liệu của mình bằng GroupDocs.Watermark cho .NET. Bằng cách làm theo hướng dẫn từng bước này, bạn có thể dễ dàng bảo vệ tài liệu của mình bằng hình mờ tùy chỉnh. Hãy nhớ rằng, hình mờ là một bước quan trọng trong việc bảo vệ tài sản kỹ thuật số của bạn khỏi việc sử dụng trái phép.

## Câu hỏi thường gặp
### Những định dạng tệp nào được GroupDocs.Watermark hỗ trợ?
GroupDocs.Watermark hỗ trợ nhiều định dạng tệp, bao gồm PDF, DOCX, PPTX, XLSX và các tệp hình ảnh như JPEG và PNG.
### Tôi có thể sử dụng GroupDocs.Watermark với .NET Core không?
Có, GroupDocs.Watermark tương thích với cả .NET Framework và .NET Core.
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Watermark?
 Bạn có thể xin giấy phép tạm thời từ[Trang web GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Có thể thêm nhiều hình mờ vào một tài liệu không?
 Tuyệt đối! Bạn có thể thêm nhiều hình mờ bằng cách gọi`Add` phương pháp nhiều lần với các trường hợp hình mờ khác nhau.
### Tôi có thể tìm thêm ví dụ và tài liệu ở đâu?
 Để biết thêm ví dụ và tài liệu chi tiết, hãy truy cập[Tài liệu GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).