---
title: Thêm hình mờ với loại lề trang trong PDF
linktitle: Thêm hình mờ với loại lề trang trong PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ với loại lề trang trong PDF bằng Groupdocs cho .NET. Bảo mật tài liệu của bạn một cách dễ dàng.
weight: 21
url: /vi/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---

# Thêm hình mờ với loại lề trang trong PDF

## Giới thiệu
Trong thời đại kỹ thuật số ngày nay, việc bảo mật tài liệu trở nên quan trọng hơn bao giờ hết. Một cách để đảm bảo tính toàn vẹn và xác thực của tài liệu của bạn là thêm hình mờ. Groupdocs.Watermark cho .NET là một công cụ đặc biệt được thiết kế để giúp quá trình này trở nên dễ dàng. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn các bước để thêm hình mờ có loại lề trang trong tệp PDF bằng Groupdocs.Watermark cho .NET.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
-  Groupdocs.Watermark cho .NET: Tải xuống và cài đặt[phiên bản mới nhất](https://releases.groupdocs.com/Watermark/net/) của Groupdocs.Watermark cho .NET.
- Môi trường phát triển: Môi trường phát triển .NET như Visual Studio.
- Kiến thức cơ bản về C#: Làm quen với ngôn ngữ lập trình C#.
- Tài liệu PDF: Tài liệu PDF mà bạn muốn thêm hình mờ.
## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết trong dự án C# của mình. Các không gian tên này sẽ cung cấp quyền truy cập vào các chức năng Hình mờ của Groupdocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Bây giờ, hãy chia quy trình thành các bước có thể quản lý được. Thực hiện cẩn thận từng bước để thêm hình mờ vào tài liệu PDF của bạn.
## Bước 1: Thiết lập đường dẫn tài liệu và thư mục đầu ra của bạn
Trước tiên, bạn cần chỉ định đường dẫn đến tài liệu của mình và thư mục đầu ra nơi tệp PDF có hình mờ sẽ được lưu.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Bước 2: Tải tài liệu PDF của bạn
 Tiếp theo, bạn sẽ tải tài liệu PDF của mình bằng cách sử dụng`PdfLoadOptions` lớp học. Lớp này cho phép bạn chỉ định bất kỳ tùy chọn nào cần thiết để tải tệp PDF của bạn.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Bước 3: Tạo hình mờ văn bản
Bây giờ là lúc tạo hình mờ. Trong ví dụ này, chúng tôi sẽ tạo hình mờ văn bản với các thuộc tính cụ thể như phông chữ, kích thước và căn chỉnh.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Bước 4: Đặt kiểu lề trang
 Để định vị hình mờ phù hợp, bạn cần đặt loại lề trang. Ở đây, chúng tôi đặt loại lề trang thành`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## Bước 5: Thêm và lưu hình mờ
Cuối cùng, thêm hình mờ vào tài liệu của bạn và lưu tệp PDF đã sửa đổi vào thư mục đầu ra được chỉ định.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## Phần kết luận
Và bạn có nó rồi đấy! Bằng cách làm theo các bước này, bạn có thể dễ dàng thêm hình mờ có loại lề trang cụ thể vào tài liệu PDF của mình bằng Groupdocs.Watermark cho .NET. Điều này không chỉ giúp bảo vệ tài liệu của bạn mà còn đảm bảo tính xác thực của chúng. Cho dù bạn đang xử lý các báo cáo bí mật, tài liệu pháp lý hay tác phẩm sáng tạo, hình mờ là cách đơn giản nhưng hiệu quả để bảo vệ nội dung của bạn.
## Câu hỏi thường gặp
### Groupdocs.Watermark cho .NET là gì?
Groupdocs.Watermark cho .NET là một thư viện mạnh mẽ để thêm hình mờ vào các định dạng tài liệu khác nhau theo chương trình. Nó hỗ trợ hình ảnh, văn bản và hơn thế nữa, cho phép tùy chỉnh rộng rãi.
### Tôi có thể sử dụng phương pháp này để tạo hình mờ cho các loại tài liệu khác không?
Có, Groupdocs.Watermark for .NET hỗ trợ nhiều định dạng tài liệu, bao gồm Word, Excel, PowerPoint và hình ảnh. Quá trình này tương tự nhưng có thể bao gồm các tùy chọn và lớp khác nhau.
### Làm cách nào tôi có thể dùng thử miễn phí Groupdocs.Watermark cho .NET?
 Bạn có thể[Tải xuống bản dùng thử miễn phí](https://releases.groupdocs.com/) từ trang web Groupdocs để khám phá các tính năng và chức năng của thư viện.
### Có thể tùy chỉnh sự xuất hiện của hình mờ?
Tuyệt đối! Bạn có thể tùy chỉnh phông chữ, kích thước, màu sắc, độ mờ, căn chỉnh và các thuộc tính khác của hình mờ để phù hợp với nhu cầu của bạn.
### Tôi có thể nhận hỗ trợ cho Groupdocs.Watermark cho .NET ở đâu?
 Để được hỗ trợ, bạn có thể truy cập[Diễn đàn hỗ trợ Groupdocs Watermark](https://forum.groupdocs.com/c/watermark/19) nơi bạn có thể đặt câu hỏi và nhận hỗ trợ từ cộng đồng và nhóm Groupdocs.