---
title: Nhận các định dạng tệp được hỗ trợ
linktitle: Nhận các định dạng tệp được hỗ trợ
second_title: API GroupDocs.Watermark .NET
description: Dễ dàng thêm hình mờ vào tài liệu của bạn bằng GroupDocs.Watermark cho .NET. Hãy làm theo hướng dẫn từng bước toàn diện của chúng tôi để bảo vệ tài sản kỹ thuật số của bạn.
type: docs
weight: 13
url: /vi/net/document-manipulation/get-supported-file-formats/
---
## Giới thiệu
Hình mờ tài liệu của bạn là một bước quan trọng trong việc bảo vệ tài sản kỹ thuật số của bạn. Cho dù đó là để bảo vệ tài sản trí tuệ, đảm bảo bí mật hay đơn giản là xây dựng thương hiệu, hình mờ đều đóng một vai trò quan trọng. Nếu bạn là nhà phát triển .NET đang tìm cách tích hợp khả năng tạo hình mờ vào ứng dụng của mình thì GroupDocs.Watermark dành cho .NET là một công cụ mạnh mẽ và linh hoạt mà bạn nên xem xét. Hướng dẫn này sẽ hướng dẫn bạn những điều cơ bản khi sử dụng GroupDocs.Watermark, từ cài đặt đến áp dụng hình mờ đầu tiên, chia nhỏ từng bước để đảm bảo bạn có thể dễ dàng làm theo.
## Điều kiện tiên quyết
Trước khi đi sâu vào chi tiết cụ thể, hãy đảm bảo bạn có mọi thứ bạn cần để bắt đầu:
1.  Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên máy của mình. Bạn có thể tải nó xuống từ[Trang web Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark hỗ trợ nhiều phiên bản khác nhau của .NET Framework. Đảm bảo rằng dự án của bạn hướng tới một phiên bản tương thích.
3. GroupDocs.Watermark dành cho .NET: Bạn có thể tải xuống phiên bản mới nhất từ[trang phát hành](https://releases.groupdocs.com/Watermark/net/).
4. Kiến thức cơ bản về C#: Hướng dẫn này giả định rằng bạn có hiểu biết cơ bản về phát triển C# và .NET.
## Nhập không gian tên
Trước tiên, hãy nhập các không gian tên cần thiết trong dự án của bạn. Mở tệp C# của bạn và thêm các lệnh sử dụng sau ở trên cùng:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Với những không gian tên này được nhập, bạn đã sẵn sàng bắt đầu thêm hình mờ vào tài liệu của mình.

## Bước 1: Khởi tạo công cụ tạo hình chìm mờ
 Bước đầu tiên là khởi tạo công cụ tạo hình mờ. Điều này liên quan đến việc tạo một thể hiện của`Watermarker` class với tài liệu bạn muốn đóng dấu mờ.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Đoạn mã này thiết lập`Watermarker` đối tượng mà bạn sẽ sử dụng để áp dụng hình mờ cho tài liệu của mình.
## Bước 2: Thêm hình mờ văn bản
Bây giờ, hãy thêm hình mờ văn bản đơn giản vào tài liệu của bạn. Hình mờ văn bản rất phù hợp để thêm các nhãn như "Bí mật" hoặc "Bản nháp".
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Ở đây, chúng tôi đã tạo một`TextWatermark`đối tượng có văn bản "Bí mật", hãy đặt phông chữ và màu sắc, đồng thời căn chỉnh nó vào giữa tài liệu.
## Bước 3: Thêm hình mờ hình ảnh
Nếu bạn muốn sử dụng hình ảnh làm hình mờ, GroupDocs.Watermark sẽ giúp bạn thực hiện điều đó một cách dễ dàng.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 Trong ví dụ này, chúng tôi tạo một`ImageWatermark` đối tượng, đặt kích thước và căn chỉnh nó ở góc trên bên phải của tài liệu.
## Bước 4: Lưu tài liệu
Sau khi thêm hình mờ mong muốn, bước cuối cùng là lưu tài liệu đã sửa đổi.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Điều này sẽ lưu tài liệu có hình mờ vào đường dẫn đã chỉ định và giải phóng mọi tài nguyên được nó sử dụng`Watermarker` ví dụ.
## Bước 5: Nhận các định dạng tệp được hỗ trợ
Để xem định dạng tệp nào được GroupDocs.Watermark hỗ trợ, bạn có thể sử dụng đoạn mã sau:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Thao tác này sẽ in ra tất cả các loại tệp mà GroupDocs.Watermark có thể xử lý, cung cấp cho bạn cái nhìn toàn diện về khả năng của nó.
## Phần kết luận
Tạo hình mờ cho tài liệu của bạn bằng GroupDocs cho .NET rất đơn giản và hiệu quả. Bằng cách làm theo hướng dẫn này, bạn đã học cách khởi tạo công cụ tạo hình mờ, thêm hình mờ văn bản và hình ảnh, lưu tài liệu có hình mờ và liệt kê các định dạng tệp được hỗ trợ. Với những công cụ này, bạn có thể tự tin bảo vệ tài liệu của mình.
 Nếu bạn có thắc mắc hoặc cần hỗ trợ thêm, đừng ngần ngại truy cập[Diễn đàn hỗ trợ GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## Câu hỏi thường gặp
### Làm cách nào để cài đặt GroupDocs.Watermark cho .NET?
 Bạn có thể tải nó xuống từ[trang phát hành](https://releases.groupdocs.com/Watermark/net/) và thêm DLL vào dự án của bạn.
### Tôi có thể dùng thử GroupDocs.Watermark miễn phí không?
 Có, bạn có thể yêu cầu một[dùng thử miễn phí](https://releases.groupdocs.com/) để đánh giá phần mềm trước khi mua.
### Những định dạng tệp nào được GroupDocs.Watermark hỗ trợ?
Bạn có thể sử dụng đoạn mã được cung cấp để liệt kê tất cả các định dạng tệp được hỗ trợ.
### Làm cách nào tôi có thể mua giấy phép cho GroupDocs.Watermark?
 Giấy phép có thể được mua trực tiếp từ[trang mua hàng](https://purchase.groupdocs.com/buy).
### Có tài liệu nào có sẵn cho GroupDocs.Watermark không?
 Có, tài liệu đầy đủ có sẵn[đây](https://reference.groupdocs.com/Watermark/net/).