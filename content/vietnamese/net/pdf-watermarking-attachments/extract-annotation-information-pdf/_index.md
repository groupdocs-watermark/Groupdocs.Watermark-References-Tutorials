---
title: Trích xuất thông tin chú thích từ PDF
linktitle: Trích xuất thông tin chú thích từ PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách trích xuất thông tin chú thích từ tài liệu PDF bằng GroupDocs.Watermark cho .NET trong hướng dẫn chi tiết từng bước này.
weight: 23
url: /vi/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# Trích xuất thông tin chú thích từ PDF

## Giới thiệu
Bạn có thường thấy mình cần trích xuất thông tin chú thích chi tiết từ tài liệu PDF của mình không? Cho dù bạn là nhà phát triển làm việc trên hệ thống quản lý tài liệu hay chuyên gia kinh doanh xử lý nhiều tệp PDF, việc trích xuất và xử lý chú thích một cách hiệu quả có thể rất quan trọng. Với GroupDocs.Watermark dành cho .NET, bạn có sẵn một bộ công cụ mạnh mẽ để thực hiện nhiệm vụ này một cách đơn giản và hiệu quả.
## Điều kiện tiên quyết
Trước khi đi sâu vào mã, hãy đảm bảo bạn có mọi thứ cần thiết để bắt đầu:
1. Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio. Đây sẽ là IDE của chúng tôi để viết và chạy mã.
2.  GroupDocs.Watermark cho .NET: Bạn cần có thư viện GroupDocs.Watermark cho .NET. Bạn có thể[tải về tại đây](https://releases.groupdocs.com/Watermark/net/).
3. Kiến thức cơ bản về C#: Cần phải làm quen với lập trình C# để làm theo các ví dụ.
## Nhập không gian tên
Để bắt đầu, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Các không gian tên này chứa các lớp và phương thức cần thiết để làm việc với tệp PDF và trích xuất các chú thích.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Bước 1: Thiết lập dự án của bạn
Đầu tiên, hãy thiết lập dự án của chúng ta trong Visual Studio. Tạo dự án Ứng dụng Console (.NET Core) mới. Sau khi dự án của bạn được tạo, bạn cần thêm tham chiếu đến thư viện GroupDocs.Watermark cho .NET.
1. Mở Trình quản lý gói NuGet.
2.  Tìm kiếm`GroupDocs.Watermark`.
3.  Cài đặt`GroupDocs.Watermark` bưu kiện.
## Bước 2: Xác định đường dẫn tài liệu
Tiếp theo, bạn sẽ cần chỉ định đường dẫn cho tài liệu PDF đầu vào và thư mục đầu ra nơi lưu thông tin trích xuất. Điều này đảm bảo rằng ứng dụng của bạn biết nơi tìm tệp PDF và nơi lưu trữ kết quả.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Bước 3: Tải tài liệu PDF
 Để làm việc với tài liệu PDF, chúng ta cần tải nó bằng cách sử dụng`PdfLoadOptions`. Lớp này cung cấp các tùy chọn để cấu hình quá trình tải.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã để trích xuất chú thích sẽ ở đây
}
```
## Bước 4: Truy cập nội dung PDF
Sau khi tài liệu được tải, chúng ta có thể truy cập nội dung của nó. Cụ thể, chúng tôi muốn lấy nội dung PDF để có thể duyệt qua các trang và chú thích.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Bước 5: Lặp lại các trang và chú thích
Với nội dung PDF trong tay, chúng ta có thể lặp qua từng trang rồi qua từng chú thích trên các trang đó. Điều này cho phép chúng tôi trích xuất thông tin chúng tôi cần.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Trích xuất chi tiết chú thích tại đây
    }
}
```
## Bước 6: Trích xuất chi tiết chú thích
Trong các vòng lặp lồng nhau, chúng tôi trích xuất nhiều chi tiết khác nhau về từng chú thích. Điều này bao gồm loại chú thích, mọi hình ảnh, văn bản và dữ liệu vị trí liên quan.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Bước 7: Lưu hoặc xử lý dữ liệu được trích xuất
Cuối cùng, hãy quyết định xem bạn muốn làm gì với thông tin chú thích được trích xuất. Bạn có thể in nó ra bảng điều khiển, lưu nó vào một tệp hoặc thậm chí lưu trữ nó trong cơ sở dữ liệu, tùy theo nhu cầu của bạn.
```csharp
// Ví dụ về lưu dữ liệu được trích xuất vào một tệp
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Phần kết luận
Trích xuất thông tin chú thích từ tài liệu PDF bằng GroupDocs.Watermark cho .NET là một quá trình đơn giản có thể giúp bạn tiết kiệm rất nhiều thời gian và công sức. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể dễ dàng tích hợp chức năng này vào dự án của mình và tự động trích xuất dữ liệu chú thích có giá trị.
 Cho dù bạn đang quản lý khối lượng lớn tệp PDF hay chỉ cần trích xuất thông tin cụ thể, GroupDocs.Watermark dành cho .NET đều cung cấp giải pháp đáng tin cậy và hiệu quả. Đừng quên kiểm tra[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) để biết thêm các tính năng nâng cao và tùy chọn tùy chỉnh.
## Câu hỏi thường gặp
### GroupDocs.Watermark cho .NET là gì?
GroupDocs.Watermark cho .NET là một thư viện toàn diện cho phép các nhà phát triển thêm, tìm kiếm và xóa hình mờ khỏi các định dạng tài liệu khác nhau, bao gồm PDF, tài liệu Word và hình ảnh.
### Tôi có thể dùng thử GroupDocs.Watermark miễn phí không?
 Vâng, bạn có thể nhận được một[dùng thử miễn phí](https://releases.groupdocs.com/) để kiểm tra các tính năng của thư viện trước khi mua hàng.
### Làm cách nào để nhận được hỗ trợ nếu tôi gặp sự cố?
 Bạn có thể nhận hỗ trợ từ nhóm GroupDocs bằng cách truy cập họ[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19).
### Có thể xin giấy phép tạm thời để thử nghiệm không?
 Có, bạn có thể yêu cầu một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)cho mục đích thử nghiệm.
### Tôi có thể mua phiên bản đầy đủ của GroupDocs.Watermark cho .NET ở đâu?
 Bạn có thể mua phiên bản đầy đủ từ[Trang web GroupDocs](https://purchase.groupdocs.com/buy).