---
title: Thêm hình mờ bị khóa vào tất cả các trang trong tài liệu Word
linktitle: Thêm hình mờ bị khóa vào tất cả các trang trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Bảo mật tài liệu của bạn bằng cách thêm hình mờ bị khóa bằng Groupdocs.Watermark cho .NET. Hãy làm theo hướng dẫn từng bước của chúng tôi để dễ dàng thực hiện.
weight: 11
url: /vi/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Thêm hình mờ bị khóa vào tất cả các trang trong tài liệu Word

## Giới thiệu
Thêm hình mờ vào tài liệu của bạn là một bước quan trọng trong việc bảo mật và xây dựng thương hiệu cho nội dung của bạn. Cho dù bạn đang ngăn chặn việc sử dụng trái phép hay chỉ đơn giản là thêm một nét chuyên nghiệp, hình mờ có thể phục vụ nhiều mục đích. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm hình mờ bị khóa vào tất cả các trang của tài liệu Word bằng Groupdocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn từng bước, hãy đảm bảo bạn có mọi thứ mình cần:
1. Groupdocs.Watermark cho .NET: Tải xuống phiên bản mới nhất từ[đây](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy của mình.
3. Môi trường phát triển: Một môi trường phát triển như Visual Studio.
4.  Giấy phép: Bạn có thể chọn một[dùng thử miễn phí](https://releases.groupdocs.com/) hoặc mua một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/).
## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Đây là những điều cần thiết để truy cập các lớp và phương thức do Groupdocs.Watermark cung cấp.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Thiết lập dự án của bạn

Mở môi trường phát triển của bạn và tạo một dự án .NET mới. Đây có thể là ứng dụng bảng điều khiển hoặc bất kỳ loại nào khác phù hợp với nhu cầu của bạn.

Bạn cần thêm gói Groupdocs.Watermark vào dự án của mình. Điều này có thể được thực hiện thông qua Trình quản lý gói NuGet. Chạy lệnh sau trong Bảng điều khiển quản lý gói NuGet:
```sh
Install-Package GroupDocs.Watermark
```
## Bước 2: Tải tài liệu Word
### Xác định đường dẫn tài liệu
Chỉ định đường dẫn đến tài liệu Word của bạn. Đây sẽ là tài liệu mà bạn muốn thêm hình mờ.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Đặt tùy chọn tải
 Tạo một thể hiện của`WordProcessingLoadOptions` để tải tài liệu Word của bạn với các tùy chọn cụ thể.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Bước 3: Tạo hình mờ
### Khởi tạo Watermarker
 Sử dụng`Watermarker`class, tải tài liệu với các tùy chọn tải được chỉ định.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Các bước tiếp theo sẽ ở bên trong khối sử dụng này
}
```
### Xác định thuộc tính hình mờ
 Tạo một`TextWatermark` Ví dụ với văn bản, phông chữ và màu sắc mà bạn mong muốn.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Bước 4: Áp dụng hình mờ cho tất cả các trang
### Đặt tùy chọn hình mờ
 Định nghĩa`WordProcessingWatermarkPagesOptions` và thiết lập`IsLocked` thuộc tính thành true để khóa hình mờ. Điều này đảm bảo rằng hình mờ không thể bị xóa dễ dàng.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Tùy chọn: Thêm bảo vệ bằng mật khẩu
Nếu muốn thêm một lớp bảo mật bổ sung, bạn có thể đặt mật khẩu cho hình mờ.
```csharp
// Để bảo vệ bằng mật khẩu
// tùy chọn.Password = "7654321";
```
### Thêm hình mờ
 Sử dụng`Add` phương pháp của`Watermarker` class để thêm hình mờ vào tài liệu với các tùy chọn đã chỉ định.
```csharp
watermarker.Add(watermark, options);
```
## Bước 5: Lưu tài liệu
Cuối cùng, lưu tài liệu đã sửa đổi vào tệp đầu ra được chỉ định.
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Bằng cách làm theo các bước này, bạn có thể dễ dàng thêm hình mờ bị khóa vào tất cả các trang trong tài liệu Word của mình bằng Groupdocs.Watermark cho .NET. Điều này không chỉ giúp bảo vệ tài liệu của bạn khỏi việc sử dụng trái phép mà còn tạo thêm nét chuyên nghiệp cho nội dung của bạn. Groupdocs.Watermark cung cấp giải pháp toàn diện cho nhu cầu tạo hình mờ, đảm bảo tài liệu của bạn vẫn được bảo mật và có thương hiệu.
## Câu hỏi thường gặp
### Tôi có thể sử dụng hình ảnh làm hình mờ thay vì văn bản không?
 Có, Groupdocs hỗ trợ cả hình mờ văn bản và hình ảnh. Bạn có thể thay thế`TextWatermark` với`ImageWatermark` và chỉ định hình ảnh của bạn.
### Có thể tùy chỉnh vị trí của hình mờ không?
 Tuyệt đối! Bạn có thể đặt vị trí của hình mờ bằng các thuộc tính như`HorizontalAlignment` Và`VerticalAlignment`.
### Tôi có thể áp dụng các hình mờ khác nhau cho các trang khác nhau của tài liệu không?
 Có, bạn có thể tùy chỉnh hình mờ cho các trang cụ thể bằng cách sử dụng`PageIndex` tài sản ở`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark có hỗ trợ các định dạng tài liệu khác ngoài Word không?
Có, Groupdocs hỗ trợ nhiều định dạng khác nhau bao gồm PDF, Excel, PowerPoint, v.v.
### Yêu cầu hệ thống để sử dụng Groupdocs.Watermark là gì?
Bạn cần một hệ thống được cài đặt .NET Framework và môi trường phát triển như Visual Studio.