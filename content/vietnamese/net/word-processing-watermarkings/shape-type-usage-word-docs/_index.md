---
title: Cách sử dụng kiểu hình dạng trong tài liệu Word
linktitle: Cách sử dụng kiểu hình dạng trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thao tác các hình dạng trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Hướng dẫn này cung cấp hướng dẫn để xử lý tài liệu hiệu quả.
weight: 37
url: /vi/net/word-processing-watermarkings/shape-type-usage-word-docs/
type: docs
---
# Cách sử dụng kiểu hình dạng trong tài liệu Word

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng các loại hình dạng trong tài liệu Word bằng GroupDocs.Watermark cho .NET. Hình dạng trong tài liệu Word có thể khác nhau và việc hiểu cách thao tác với chúng có thể rất quan trọng đối với các tác vụ xử lý tài liệu khác nhau.
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1.  GroupDocs.Watermark cho Thư viện .NET: Tải xuống và cài đặt thư viện GroupDocs.Watermark cho .NET từ[Liên kết tải xuống](https://releases.groupdocs.com/Watermark/net/).
2. Đường dẫn tài liệu: Chuẩn bị sẵn tài liệu Word để xử lý.
3. Môi trường phát triển: Thiết lập môi trường phát triển phù hợp với sự hỗ trợ .NET framework.

## Nhập không gian tên
Để bắt đầu, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Các không gian tên này sẽ cung cấp quyền truy cập vào các lớp và phương thức cần thiết để làm việc với tài liệu Word.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Bước 1: Tải tài liệu
Bắt đầu bằng cách tải tài liệu Word vào đối tượng Watermarker. Đảm bảo chỉ định đường dẫn tài liệu và mọi tùy chọn bổ sung cần thiết trong quá trình tải.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã xử lý tài liệu ở đây
}
```
## Bước 2: Truy cập nội dung tài liệu
 Truy cập nội dung của tài liệu Word đã tải bằng cách sử dụng`GetContent<WordProcessingContent>()` phương pháp. Điều này sẽ cung cấp quyền truy cập vào các phần, đoạn văn và hình dạng có trong tài liệu.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Bước 3: Lặp lại các phần và hình dạng
Lặp lại qua từng phần và hình dạng trong tài liệu để kiểm tra và thao tác chúng theo yêu cầu.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Mã thao tác hình dạng ở đây
    }
}
```
## Bước 4: Kiểm tra các loại hình dạng
Trong vòng lặp, hãy kiểm tra các loại hình dạng cụ thể bằng cách sử dụng`ShapeType` tài sản. Ví dụ này thể hiện việc xác định và xử lý các góc chéo Hình tròn.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Mã thao tác dành riêng cho hình dạng ở đây
}
```
## Bước 5: Thao tác với hình dạng
Thực hiện các hành động như thêm văn bản, sửa đổi định dạng hoặc áp dụng các thay đổi trực quan cho các hình dạng đã xác định.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Bước 6: Lưu tài liệu
Sau khi thực hiện tất cả các sửa đổi cần thiết, hãy lưu tài liệu với các thay đổi được áp dụng vào tệp đầu ra đã chỉ định.
```csharp
watermarker.Save(outputFileName);
```

## Phần kết luận
Thao tác với các hình dạng trong tài liệu Word có thể cần thiết cho các tác vụ xử lý tài liệu khác nhau. Với GroupDocs.Watermark dành cho .NET, bạn có thể dễ dàng xác định, sửa đổi và thao tác các hình dạng để đáp ứng yêu cầu của mình một cách hiệu quả.
## Câu hỏi thường gặp
### GroupDocs.Watermark cho .NET có thể xử lý các định dạng tài liệu khác ngoài Word không?
Có, GroupDocs.Watermark cho .NET hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, Excel, PowerPoint, v.v.
### Có bản dùng thử miễn phí cho GroupDocs.Watermark cho .NET không?
 Có, bạn có thể truy cập phiên bản dùng thử miễn phí từ[trang phát hành](https://releases.groupdocs.com/).
### GroupDocs.Watermark cho .NET có cung cấp hỗ trợ kỹ thuật không?
 Có, bạn có thể tìm kiếm sự trợ giúp và tương tác với cộng đồng thông qua[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19).
### Tôi có thể tùy chỉnh quy trình tạo hình mờ cho các yêu cầu tài liệu cụ thể không?
Hoàn toàn có thể, GroupDocs.Watermark for .NET cung cấp các tùy chọn tùy chỉnh mở rộng để điều chỉnh quy trình tạo hình mờ theo nhu cầu của bạn.
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Watermark cho .NET?
 Bạn có thể có được giấy phép tạm thời từ[Trang mua giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) nhằm mục đích kiểm tra và đánh giá.