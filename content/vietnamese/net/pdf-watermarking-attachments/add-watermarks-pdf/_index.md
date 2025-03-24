---
title: Thêm hình mờ vào PDF
linktitle: Thêm hình mờ vào PDF
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ văn bản và hình ảnh vào tệp PDF của bạn bằng GroupDocs.Watermark cho .NET với hướng dẫn từng bước toàn diện của chúng tôi.
weight: 14
url: /vi/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## Giới thiệu
Bạn đang muốn thêm hình mờ vào tệp PDF để bảo vệ tài liệu hoặc gắn nhãn hiệu cho chúng bằng logo của mình? Đừng tìm đâu xa! Trong hướng dẫn này, chúng ta sẽ đi sâu vào quy trình sử dụng GroupDocs.Watermark cho .NET để thêm cả hình mờ văn bản và hình ảnh vào tệp PDF của bạn. Cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay mới bắt đầu, hướng dẫn này sẽ hướng dẫn bạn từng bước, đảm bảo bạn có thể áp dụng hình mờ một cách dễ dàng và chính xác.
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có mọi thứ bạn cần để làm theo hướng dẫn này:
-  GroupDocs.Watermark dành cho .NET: Đảm bảo bạn đã cài đặt phiên bản mới nhất. Bạn có thể[tải về tại đây](https://releases.groupdocs.com/Watermark/net/).
- Môi trường phát triển .NET: Visual Studio hoặc bất kỳ IDE nào khác hỗ trợ .NET.
- Kiến thức cơ bản về C#: Hiểu những điều cơ bản về lập trình C# sẽ giúp bạn thực hiện các bước một cách dễ dàng.
- Tài liệu PDF: Chuẩn bị sẵn một tài liệu PDF mẫu để đóng dấu mờ.
- Hình ảnh cho Hình mờ: Nếu bạn đang thêm hình mờ hình ảnh, hãy chuẩn bị sẵn tệp hình ảnh của bạn.
## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết trong dự án C# của mình. Điều này sẽ cho phép bạn truy cập chức năng GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Bây giờ, hãy chia quy trình thành các bước có thể quản lý được.
## Bước 1: Tải tài liệu PDF của bạn
Bước đầu tiên là tải tài liệu PDF của bạn vào hình mờ. Đây là cách bạn có thể làm điều đó:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Các bước tiếp theo sẽ được thêm vào đây
}
```
## Bước 2: Thêm hình mờ văn bản vào trang đầu tiên
Tiếp theo, chúng tôi sẽ thêm hình mờ văn bản vào trang đầu tiên trong tệp PDF của bạn. Làm theo các hướng dẫn này:
```csharp
// Thêm hình mờ văn bản vào trang đầu tiên
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Việc thêm hình mờ văn bản có thể giúp bảo vệ tài liệu của bạn khỏi việc sử dụng trái phép hoặc đơn giản là gắn nhãn hiệu cho tài liệu đó. Hãy tưởng tượng việc đóng dấu tài liệu của bạn bằng một con dấu xác thực vô hình.
## Bước 3: Thêm hình mờ hình ảnh vào trang thứ hai
Bây giờ, hãy thêm hình mờ vào trang thứ hai. Điều này đặc biệt hữu ích cho các logo hoặc bất kỳ hình mờ đồ họa nào.
```csharp
// Thêm hình mờ vào trang thứ hai
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Hình mờ có thể làm cho tài liệu của bạn trông chuyên nghiệp và đảm bảo rằng thương hiệu của bạn luôn hiển thị. Nó giống như thêm chữ ký của bạn vào mỗi trang.
## Bước 4: Lưu tệp PDF có hình mờ
Sau khi thêm hình mờ, bước cuối cùng là lưu tệp PDF có hình mờ vào vị trí bạn muốn.
```csharp
watermarker.Save(outputFileName);
```
Việc lưu tài liệu sẽ hoàn tất tất cả những thay đổi bạn đã thực hiện. Đây là thời điểm những nỗ lực của bạn được củng cố thành kết quả hữu hình, sẵn sàng để sử dụng hoặc phân phối.
## Phần kết luận
Chúc mừng! Bạn đã thêm thành công cả hình mờ văn bản và hình ảnh vào tệp PDF của mình bằng GroupDocs.Watermark cho .NET. Quá trình này không chỉ đơn giản mà còn có khả năng tùy chỉnh cao để phù hợp với nhu cầu cụ thể của bạn. Cho dù bạn đang bảo vệ tài liệu của mình hay xây dựng thương hiệu cho chúng, hình mờ vẫn là một công cụ mạnh mẽ theo ý bạn.
## Câu hỏi thường gặp
### Tôi có thể thêm nhiều hình mờ vào cùng một trang không?
 Có, bạn có thể thêm nhiều hình mờ vào cùng một trang bằng cách gọi`Add` phương pháp nhiều lần với các đối tượng hình mờ khác nhau.
### Làm cách nào để tùy chỉnh hình thức của hình mờ văn bản?
 Bạn có thể tùy chỉnh hình mờ văn bản bằng cách điều chỉnh các thuộc tính như phông chữ, kích thước, màu sắc và độ mờ bằng cách sử dụng`TextWatermark` sự vật.
### Có thể chỉ tạo hình mờ cho các trang cụ thể của tệp PDF không?
 Có, bạn có thể chỉ định những trang nào cần đóng dấu mờ bằng cách đặt`PageIndex` tài sản ở`PdfArtifactWatermarkOptions`.
### Tôi có thể xóa hình mờ khỏi tệp PDF không?
Có, GroupDocs.Watermark cung cấp chức năng tìm kiếm và xóa hình mờ khỏi tài liệu PDF.
### Làm cách nào để nhận được giấy phép tạm thời cho GroupDocs.Watermark?
Bạn có thể nhận được giấy phép tạm thời bằng cách truy cập[trang giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/).