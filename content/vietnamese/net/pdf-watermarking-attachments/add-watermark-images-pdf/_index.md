---
title: Thêm hình mờ vào hình ảnh trong PDF
linktitle: Thêm hình mờ vào hình ảnh trong PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào hình ảnh trong tài liệu PDF bằng GroupDocs.Watermark cho .NET với hướng dẫn chi tiết từng bước của chúng tôi. Bảo mật các tệp PDF của bạn một cách dễ dàng.
weight: 19
url: /vi/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---

# Thêm hình mờ vào hình ảnh trong PDF

## Giới thiệu
Việc thêm hình mờ vào hình ảnh trong tài liệu PDF có thể cần thiết để bảo vệ tài sản trí tuệ của bạn hoặc đảm bảo tính xác thực của tài liệu. Sử dụng GroupDocs.Watermark cho .NET, tác vụ này có thể được thực hiện một cách hiệu quả và dễ dàng. Hướng dẫn này sẽ hướng dẫn bạn qua từng bước của quy trình, từ thiết lập môi trường cho đến thêm hình mờ cho đến lưu tài liệu cuối cùng. Hãy đi sâu vào!
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có những điều sau:
1. Visual Studio: Cài đặt Visual Studio, Môi trường phát triển tích hợp (IDE) cho các ứng dụng .NET.
2.  GroupDocs.Watermark cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Watermark cho .NET từ[trang phát hành](https://releases.groupdocs.com/Watermark/net/).
3. Tài liệu PDF: Chuẩn bị sẵn tài liệu PDF có hình ảnh để kiểm tra chức năng tạo hình chìm mờ.
4.  Giấy phép tạm thời: Lấy một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) nếu bạn đang đánh giá sản phẩm.
## Nhập không gian tên
Trước tiên, hãy đảm bảo bạn đã nhập các không gian tên cần thiết vào dự án của mình. Điều này sẽ bao gồm các không gian tên cốt lõi cần thiết để làm việc với các tài liệu PDF và hình mờ.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Thiết lập đường dẫn tài liệu và thư mục đầu ra
Để bắt đầu, hãy xác định đường dẫn cho tài liệu đầu vào và thư mục đầu ra nơi tài liệu có hình mờ sẽ được lưu. Bước này rất quan trọng để đảm bảo rằng chương trình của bạn biết nơi tìm tài liệu nguồn và nơi lưu trữ tệp đã xử lý.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Bước 2: Tải tài liệu PDF
 Tiếp theo, bạn sẽ cần tải tài liệu PDF bằng cách sử dụng`PdfLoadOptions`. Lớp này cho phép bạn chỉ định các tùy chọn để tải tệp PDF, chẳng hạn như bảo vệ bằng mật khẩu nếu cần.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã cho hình mờ của bạn sẽ ở đây
}
```
## Bước 3: Tạo hình mờ
Bây giờ, khởi tạo hình mờ. Trong ví dụ này, chúng tôi đang tạo hình mờ văn bản có nội dung "Hình ảnh được bảo vệ". Tùy chỉnh phông chữ, căn chỉnh, xoay và chia tỷ lệ theo nhu cầu của bạn.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Bước 4: Truy cập nội dung PDF
Truy xuất nội dung của tài liệu PDF. Cụ thể, chúng ta cần truy cập các hình ảnh trong PDF. Ở đây, chúng tôi đang tập trung vào trang đầu tiên nhưng bạn có thể mở rộng trang này sang các trang khác nếu cần.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Nhận tất cả hình ảnh từ trang đầu tiên
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Bước 5: Áp dụng hình mờ cho hình ảnh
Lặp lại từng hình ảnh được tìm thấy trên trang đầu tiên và áp dụng hình mờ. Điều này đảm bảo rằng tất cả hình ảnh trên trang được chỉ định sẽ được áp dụng hình mờ.
```csharp
// Thêm hình mờ vào tất cả hình ảnh tìm thấy
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Bước 6: Lưu tài liệu có hình mờ
Cuối cùng, lưu tệp PDF có hình mờ vào thư mục đầu ra được chỉ định. Bước này hoàn tất quy trình bằng cách ghi các thay đổi vào một tệp mới.
```csharp
watermarker.Save(outputFileName);
```
## Phần kết luận
Và bạn có nó rồi đấy! Thêm hình mờ vào hình ảnh trong tệp PDF bằng GroupDocs cho .NET là một quá trình đơn giản có thể nâng cao đáng kể tính bảo mật và tính xác thực cho tài liệu của bạn. Bằng cách làm theo các bước này, bạn có thể đảm bảo rằng tài sản trí tuệ của mình được bảo vệ và tài liệu của bạn được bảo mật.
## Câu hỏi thường gặp
### GroupDocs.Watermark cho .NET là gì?
GroupDocs.Watermark for .NET là một thư viện toàn diện cho phép các nhà phát triển thêm, tìm kiếm và xóa hình mờ ở nhiều định dạng tài liệu khác nhau, bao gồm cả tệp PDF.
### Tôi có thể thêm cả hình mờ văn bản và hình ảnh bằng GroupDocs.Watermark không?
Có, GroupDocs.Watermark hỗ trợ cả hình mờ văn bản và hình ảnh, mang lại sự linh hoạt cho các loại nhu cầu hình mờ khác nhau.
### Có thể tạo hình mờ nhiều trang trong PDF không?
Tuyệt đối! Bạn có thể lặp qua từng trang trong tệp PDF và áp dụng hình mờ cho hình ảnh trên mỗi trang.
### Tôi có cần giấy phép để sử dụng GroupDocs.Watermark cho .NET không?
 Có, cần phải có giấy phép. Bạn có thể có được một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) cho mục đích đánh giá.
### Tôi có thể tìm thêm tài liệu về GroupDocs.Watermark cho .NET ở đâu?
 Bạn có thể tìm thấy tài liệu đầy đủ về[Trang tài liệu GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).