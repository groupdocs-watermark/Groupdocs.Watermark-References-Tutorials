---
title: Nhận thông tin tài liệu từ đĩa cục bộ
linktitle: Nhận thông tin tài liệu từ đĩa cục bộ
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm, xóa và trích xuất hình mờ trong tài liệu bằng GroupDocs cho .NET với hướng dẫn từng bước toàn diện này.
weight: 11
url: /vi/net/document-manipulation/get-document-info-local-disk/
type: docs
---
# Nhận thông tin tài liệu từ đĩa cục bộ

## Giới thiệu
Chào mừng bạn đến với hướng dẫn cơ bản về cách sử dụng GroupDocs.Watermark cho .NET! Cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay chỉ mới bắt đầu, bài viết này sẽ hướng dẫn bạn những điều cơ bản về cách tạo hình mờ cho tài liệu của bạn bằng công cụ mạnh mẽ này. Cuối cùng, bạn sẽ trở thành chuyên gia trong việc nhúng hình mờ vào tài liệu của mình, đảm bảo chúng được bảo vệ và gắn nhãn hiệu theo thông số kỹ thuật của bạn.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn từng bước, bạn cần phải đáp ứng một số điều kiện tiên quyết:
1.  .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên hệ thống của mình. GroupDocs.Watermark cho .NET tương thích với nhiều phiên bản khác nhau của .NET Framework, vì vậy hãy kiểm tra[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) để biết chi tiết về khả năng tương thích.
2.  GroupDocs.Watermark for .NET Library: Tải xuống và cài đặt phiên bản mới nhất từ[trang tải xuống](https://releases.groupdocs.com/Watermark/net/).
3. Môi trường phát triển: Bạn nên thiết lập môi trường phát triển. Visual Studio là một lựa chọn phổ biến để phát triển .NET.
4. Kiến thức cơ bản về C#: Hiểu những điều cơ bản về lập trình C# sẽ giúp bạn theo dõi các ví dụ.
## Nhập không gian tên
Trước khi có thể sử dụng GroupDocs.Watermark cho .NET, bạn cần nhập các vùng tên cần thiết vào dự án của mình. Đây là một quá trình đơn giản và cần thiết để truy cập các tính năng của thư viện.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Hãy chia nhỏ quy trình tạo hình mờ cho tài liệu thành các bước rõ ràng và dễ quản lý. Mỗi bước được thiết kế để giúp bạn hiểu và triển khai chức năng một cách dễ dàng.
## Bước 1: Tải tài liệu của bạn
 Bước đầu tiên là tải tài liệu bạn muốn đóng dấu mờ. Việc này được thực hiện bằng cách sử dụng`Watermarker` lớp, cho phép bạn truy cập và thao tác với tài liệu của mình.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Tài liệu hiện đã được tải và sẵn sàng để đóng dấu mờ
}
```
 Ở bước này, thay thế`"Your Document Path"` với đường dẫn thực tế đến tài liệu của bạn. Điều này khởi tạo`Watermarker`đối tượng, cho phép bạn truy cập vào các chức năng tạo hình chìm mờ khác nhau.
## Bước 2: Lấy thông tin tài liệu
Trước khi thêm hình mờ, bạn có thể muốn thu thập một số thông tin về tài liệu. Điều này có thể hữu ích cho việc tùy chỉnh hình mờ của bạn dựa trên thuộc tính tài liệu.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Ở bước này,`GetDocumentInfo` phương thức lấy các chi tiết như loại tệp, số trang và kích thước tài liệu. Thông tin này được in ra bảng điều khiển nhưng bạn có thể sử dụng nó trong ứng dụng của mình nếu cần.
## Bước 3: Thêm hình mờ văn bản
Bây giờ bạn đã tải tài liệu của mình và thông tin trong đó, đã đến lúc thêm hình mờ. Chúng ta sẽ bắt đầu với một hình mờ văn bản đơn giản.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Tại đây, bạn tạo một`TextWatermark` đối tượng với văn bản, phông chữ và kiểu dáng mà bạn mong muốn. Điều chỉnh các thuộc tính như màu sắc, độ mờ và góc xoay để phù hợp với nhu cầu của bạn. Cuối cùng, hình mờ được thêm vào tài liệu và được lưu vào một đường dẫn cụ thể.
## Bước 4: Thêm hình mờ hình ảnh
Hình mờ văn bản rất tuyệt, nhưng nếu bạn muốn thêm logo hoặc hình ảnh khác thì sao? Bước này bao gồm cách thêm hình mờ vào hình ảnh.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Thay thế`"Path to Your Image"` với đường dẫn đến hình ảnh mờ của bạn. Đặt các thuộc tính như độ mờ và góc xoay để tùy chỉnh hình thức hình mờ của hình ảnh của bạn. Quá trình thêm và lưu hình mờ tương tự như hình mờ văn bản.
## Bước 5: Xóa hình mờ hiện có
 Đôi khi, bạn có thể cần xóa hình mờ hiện có khỏi tài liệu. Điều này có thể được thực hiện bằng cách sử dụng`Remove` phương pháp được cung cấp bởi`Watermarker` lớp học.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Ở đây,`Remove` phương pháp được sử dụng để xóa hình mờ văn bản khỏi tài liệu. Bạn có thể chỉ định các loại hình mờ khác nhau cần xóa, chẳng hạn như hình ảnh hoặc văn bản, tùy theo nhu cầu của bạn. Lưu tài liệu vào một đường dẫn mới để xem những thay đổi.
## Bước 6: Trích xuất hình mờ
Nếu bạn cần trích xuất và kiểm tra hình mờ từ một tài liệu, GroupDocs.Watermark dành cho .NET sẽ thực hiện việc này một cách dễ dàng.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Các thuộc tính và logic bổ sung cho mỗi hình mờ
    }
}
```
 Bước này liên quan đến việc sử dụng`GetWatermarks`phương pháp truy xuất tất cả hình mờ trong tài liệu. Sau đó, bạn có thể duyệt qua danh sách hình mờ và kiểm tra thuộc tính của chúng hoặc thực hiện các hành động bổ sung nếu cần.
## Phần kết luận
 Chúc mừng! Bây giờ bạn đã học cách sử dụng GroupDocs.Watermark cho .NET để thêm, xóa và trích xuất hình mờ khỏi tài liệu của mình. Với những kỹ năng này, bạn có thể bảo vệ và gắn nhãn hiệu cho tài liệu của mình một cách hiệu quả. Nhớ cái gì đó[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) luôn ở đó nếu bạn cần thông tin chi tiết hơn hoặc chức năng nâng cao.
## Câu hỏi thường gặp
### Tôi có thể sử dụng GroupDocs.Watermark cho .NET với bất kỳ phiên bản .NET nào không?
 Có, GroupDocs.Watermark cho .NET tương thích với nhiều phiên bản .NET Framework khác nhau. Kiểm tra[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) để biết chi tiết cụ thể.
### Tôi có thể tải xuống GroupDocs.Watermark cho .NET ở đâu?
 Bạn có thể tải phiên bản mới nhất từ[trang tải xuống](https://releases.groupdocs.com/Watermark/net/).
### Làm thế nào để tôi có được giấy phép tạm thời?
 Bạn có thể xin giấy phép tạm thời từ[trang giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/).
### Có bản dùng thử miễn phí không?
 Có, bạn có thể bắt đầu dùng thử miễn phí bằng cách truy cập[trang dùng thử miễn phí](https://releases.groupdocs.com/).
### Tôi có thể nhận hỗ trợ ở đâu nếu gặp vấn đề?
 Hỗ trợ có sẵn trên[Diễn đàn Hình mờ GroupDocs](https://forum.groupdocs.com/c/watermark/19).