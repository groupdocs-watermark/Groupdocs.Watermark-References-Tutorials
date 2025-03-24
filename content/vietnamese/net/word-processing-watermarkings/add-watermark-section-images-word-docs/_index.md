---
title: Thêm hình mờ vào hình ảnh phần trong tài liệu Word
linktitle: Thêm hình mờ vào hình ảnh phần trong tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào hình ảnh trong tài liệu Word bằng Groupdocs cho .NET. Hãy làm theo hướng dẫn của chúng tôi để bảo vệ tài liệu an toàn và chuyên nghiệp.
weight: 16
url: /vi/net/word-processing-watermarkings/add-watermark-section-images-word-docs/
---
## Giới thiệu
Trong thế giới kỹ thuật số ngày nay, việc bảo vệ tài liệu của bạn là điều cần thiết. Thêm hình mờ vào tài liệu Word là cách đơn giản nhưng hiệu quả để bảo mật nội dung của bạn. Hướng dẫn này sẽ hướng dẫn bạn quy trình thêm hình mờ vào hình ảnh phần trong tài liệu Word bằng Groupdocs.Watermark cho .NET. Cho dù bạn là nhà phát triển đang tìm cách tích hợp tính năng này vào ứng dụng của mình hay chỉ muốn bảo vệ tài liệu của mình thì hướng dẫn này là dành cho bạn.
## Điều kiện tiên quyết
Trước khi chúng ta đi sâu vào chi tiết, hãy đảm bảo bạn có những điều sau:
1.  Groupdocs.Watermark cho .NET: Tải xuống[đây](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy của mình.
3. Tài liệu Word: Chuẩn bị sẵn tài liệu Word mà bạn muốn thêm hình mờ vào.
4. Môi trường phát triển: Visual Studio hoặc bất kỳ IDE tương thích .NET nào khác.
5.  Giấy phép tạm thời: Lấy một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) cho Groupdocs.Watermark.
## Nhập không gian tên
Để bắt đầu, hãy nhập các không gian tên cần thiết vào dự án của bạn. Đây là một bước quan trọng để đảm bảo rằng tất cả các chức năng của Groupdocs.Watermark đều khả dụng.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Bây giờ, hãy chia quy trình thành các bước có thể quản lý được.
## Bước 1: Thiết lập dự án của bạn
Đầu tiên, hãy thiết lập dự án của bạn trong IDE ưa thích của bạn. Tạo một dự án .NET mới và cài đặt thư viện Groupdocs.Watermark.
```bash
dotnet add package GroupDocs.Watermark
```
## Bước 2: Tải tài liệu Word
Tải tài liệu Word mà bạn muốn tạo hình mờ. Đảm bảo đường dẫn đến tài liệu của bạn là chính xác.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã của bạn sẽ ở đây
}
```
## Bước 3: Tạo hình mờ
Tạo hình mờ văn bản mà bạn sẽ áp dụng cho hình ảnh trong tài liệu Word. Tùy chỉnh văn bản, phông chữ, kích thước và căn chỉnh cho phù hợp với nhu cầu của bạn.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Bước 4: Truy xuất hình ảnh từ phần đầu tiên
Truy cập vào nội dung văn bản Word và tìm toàn bộ hình ảnh ở phần đầu tiên. Bước này rất quan trọng vì nó xác định những hình ảnh sẽ được áp dụng hình mờ.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WatermarkableImageCollection images = content.Sections[0].FindImages();
```
## Bước 5: Áp dụng hình mờ cho hình ảnh
Lặp lại từng hình ảnh trong phần đầu tiên và áp dụng hình mờ đã tạo. Điều này đảm bảo rằng tất cả hình ảnh trong phần này đều được bảo vệ.
```csharp
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Bước 6: Lưu tài liệu
Cuối cùng, lưu tài liệu có hình mờ vào đường dẫn đã chỉ định. Điều này hoàn tất quá trình thêm hình mờ vào các phần hình ảnh trong tài liệu Word.
```csharp
watermarker.Save(outputFileName);
```
## Phần kết luận
Thêm hình mờ vào hình ảnh trong tài liệu Word là một cách mạnh mẽ để bảo vệ nội dung của bạn. Với Groupdocs.Watermark dành cho .NET, quá trình này rất đơn giản và hiệu quả. Hãy làm theo các bước được nêu trong hướng dẫn này để đảm bảo tài liệu của bạn được an toàn và bảo vệ tốt.
 Để biết thêm tài liệu chi tiết, hãy truy cập[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) . Nếu bạn có bất kỳ câu hỏi nào hoặc cần hỗ trợ thêm, hãy xem[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19).
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh văn bản hình mờ không?
Có, bạn có thể tùy chỉnh văn bản hình mờ, phông chữ, kích thước, căn chỉnh và xoay để phù hợp với nhu cầu của bạn.
### Có thể thêm hình mờ vào nhiều phần không?
Có, bạn có thể lặp qua từng phần và áp dụng hình mờ cho hình ảnh trong tất cả các phần.
### Tôi có thể sử dụng phương pháp này cho các định dạng tài liệu khác không?
 Groupdocs hỗ trợ nhiều định dạng tài liệu khác nhau. Kiểm tra[tài liệu](https://tutorials.groupdocs.com/Watermark/net/) để biết thêm chi tiết.
### Làm thế nào tôi có thể có được giấy phép tạm thời?
 Bạn có thể có được giấy phép tạm thời[đây](https://purchase.groupdocs.com/temporary-license/).
### Điều gì sẽ xảy ra nếu tôi gặp sự cố khi sử dụng Groupdocs.Watermark?
 Tham quan[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19)để được hỗ trợ về mọi vấn đề bạn có thể gặp phải.