---
title: Thêm hình mờ bị khóa vào các trang cụ thể trong tài liệu Word
linktitle: Thêm hình mờ bị khóa vào các trang cụ thể trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ bị khóa vào các trang cụ thể trong tài liệu Word bằng GroupDocs.Watermark dành cho .NET với hướng dẫn từng bước dễ dàng của chúng tôi.
weight: 12
url: /vi/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## Giới thiệu
Bạn đang muốn thêm hình mờ vào các trang cụ thể trong tài liệu Word của mình nhưng muốn nó bị khóa để không thể dễ dàng xóa hoặc chỉnh sửa? Bạn đang ở đúng nơi! Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm hình mờ bị khóa vào các trang cụ thể trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Thư viện mạnh mẽ này giúp bạn dễ dàng áp dụng, quản lý và tùy chỉnh hình mờ trên nhiều loại tài liệu khác nhau. Cho dù bạn là nhà phát triển hay chỉ là người cần bảo mật tài liệu của mình, hướng dẫn này sẽ hướng dẫn bạn từng bước một cách đơn giản.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có mọi thứ mình cần:
1.  GroupDocs.Watermark dành cho .NET: Bạn có thể[Tải xuống](https://releases.groupdocs.com/Watermark/net/) phiên bản mới nhất.
2. Môi trường phát triển: Một IDE như Visual Studio.
3. Kiến thức cơ bản về C#: Làm quen với lập trình C# sẽ rất hữu ích.
4. Tài liệu thành hình mờ: Một tài liệu Word (.docx hoặc .doc) mà bạn muốn thêm hình mờ vào.
## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết trong dự án C# của mình. Các không gian tên này cung cấp quyền truy cập vào các lớp và phương thức cần thiết để hoạt động với GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Bây giờ chúng ta đã có các điều kiện tiên quyết và đã nhập các không gian tên cần thiết, hãy chia nhỏ quy trình từng bước.
## Bước 1: Tải tài liệu Word
 Để bắt đầu, bạn cần tải tài liệu Word mà bạn muốn thêm hình mờ vào. Điều này có thể được thực hiện bằng cách sử dụng`Watermarker` lớp cùng với`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tiếp tục các bước tiếp theo
}
```
## Bước 2: Tạo hình mờ văn bản
Tiếp theo, tạo hình mờ văn bản. Bạn có thể tùy chỉnh văn bản, phông chữ, màu sắc và các thuộc tính khác theo yêu cầu của bạn.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Bước 3: Định cấu hình tùy chọn hình mờ
 Để áp dụng hình mờ cho các trang cụ thể và khóa nó, hãy định cấu hình`WordProcessingWatermarkPagesOptions`Tại đây, bạn chỉ định số trang nơi hình mờ sẽ xuất hiện và đặt các tùy chọn khóa.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Chỉ định các trang
options.IsLocked = true; // Khóa hình mờ
options.LockType = WordProcessingLockType.AllowOnlyComments; // Đặt loại khóa
// Để bảo vệ bằng mật khẩu
// tùy chọn.Password = "7654321";
```
## Bước 4: Thêm hình mờ vào tài liệu
Với hình mờ và các tùy chọn được định cấu hình, giờ đây bạn có thể thêm hình mờ vào tài liệu.
```csharp
watermarker.Add(watermark, options);
```
## Bước 5: Lưu tài liệu
Cuối cùng, lưu tài liệu có áp dụng hình mờ. Chọn đường dẫn đầu ra thích hợp và lưu tệp.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Phần kết luận
Chúc mừng! Bạn đã thêm thành công hình mờ bị khóa vào các trang cụ thể trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Hướng dẫn này bao gồm tất cả các bước cần thiết từ tải tài liệu đến lưu tệp có hình chìm mờ. Bằng cách làm theo các bước này, bạn có thể đảm bảo rằng tài liệu của mình được gắn hình mờ một cách an toàn, bảo vệ nội dung của bạn khỏi bị chỉnh sửa và sử dụng trái phép.
 Để biết thêm thông tin, bạn có thể tham khảo[Tài liệu GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . Nếu bạn có thắc mắc hoặc cần hỗ trợ thêm, vui lòng truy cập[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19).
## Câu hỏi thường gặp
### GroupDocs.Watermark cho .NET là gì?
GroupDocs.Watermark cho .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm hình mờ vào nhiều loại tài liệu khác nhau, bao gồm Word, PDF, Excel, v.v.
### Tôi có thể áp dụng hình mờ cho nhiều trang trong tài liệu không?
 Có, bạn có thể chỉ định nhiều số trang trong`PageNumbers` array để áp dụng hình mờ cho nhiều trang.
### Làm cách nào để bảo vệ hình mờ bằng mật khẩu?
 Bạn có thể bảo vệ hình mờ bằng mật khẩu bằng cách đặt`Password` tài sản ở`WordProcessingWatermarkPagesOptions`.
### Có thể tùy chỉnh sự xuất hiện của hình mờ?
Tuyệt đối! Bạn có thể tùy chỉnh văn bản, phông chữ, màu sắc, kích thước và các thuộc tính khác của hình mờ để phù hợp với nhu cầu của bạn.
### Tôi có thể lấy giấy phép tạm thời cho GroupDocs.Watermark ở đâu?
 Bạn có thể xin giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/).