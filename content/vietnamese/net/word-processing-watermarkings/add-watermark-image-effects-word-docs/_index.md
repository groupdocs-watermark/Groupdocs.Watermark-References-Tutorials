---
title: Thêm Watermark kèm hiệu ứng hình ảnh trong Word Docs
linktitle: Thêm Watermark kèm hiệu ứng hình ảnh trong Word Docs
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ kèm hiệu ứng hình ảnh vào tài liệu Word của bạn bằng GroupDocs.Watermark cho .NET. Hãy làm theo hướng dẫn từng bước của chúng tôi để có kết quả tuyệt vời.
weight: 19
url: /vi/net/word-processing-watermarkings/add-watermark-image-effects-word-docs/
type: docs
---
# Thêm Watermark kèm hiệu ứng hình ảnh trong Word Docs

## Giới thiệu
Bạn đang muốn thêm một số điểm thú vị vào tài liệu Word của mình bằng các hình mờ bắt mắt? GroupDocs.Watermark dành cho .NET sẽ giúp bạn! Hướng dẫn toàn diện này sẽ hướng dẫn bạn quy trình thêm hình mờ với các hiệu ứng hình ảnh tuyệt đẹp vào tài liệu Word bằng GroupDocs cho .NET. Cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay người mới bắt đầu, hướng dẫn từng bước này sẽ giúp quá trình này trở nên dễ dàng.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
- Kiến thức cơ bản về lập trình C#: Làm quen với C# là điều cần thiết vì chúng ta sẽ làm việc với .NET.
- Visual Studio: Đã cài đặt và thiết lập để phát triển .NET.
-  GroupDocs.Watermark cho .NET: Tải xuống và cài đặt từ[đây](https://releases.groupdocs.com/Watermark/net/).
- Tài liệu có hình mờ: Tài liệu Word mà bạn sẽ áp dụng hình mờ vào.
- Hình ảnh cho hình mờ: Tệp hình ảnh được sử dụng làm hình mờ.
Bây giờ chúng ta đã sắp xếp được các điều kiện tiên quyết, hãy đi sâu vào phần hướng dẫn.
## Nhập không gian tên
Trước tiên, hãy nhập các không gian tên cần thiết để bắt đầu với GroupDocs.Watermark cho .NET.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Các không gian tên này sẽ cung cấp cho chúng ta các lớp và phương thức cần thiết để thêm hình mờ và áp dụng hiệu ứng hình ảnh.
## Bước 1: Thiết lập dự án của bạn
Để bắt đầu, hãy tạo một dự án mới trong Visual Studio. Bạn có thể thực hiện việc này bằng cách mở Visual Studio, chọn "Tạo dự án mới" rồi chọn Ứng dụng bảng điều khiển C# (.NET Core hoặc .NET Framework). Đặt tên cho dự án của bạn và nhấp vào "Tạo."
## Bước 2: Cài đặt GroupDocs.Watermark cho .NET
Để cài đặt GroupDocs.Watermark, bạn có thể sử dụng Trình quản lý gói NuGet. Nhấp chuột phải vào dự án của bạn trong Solution Explorer, chọn "Quản lý gói NuGet", tìm kiếm "GroupDocs.Watermark" và cài đặt nó.
Ngoài ra, bạn có thể cài đặt nó thông qua Bảng điều khiển quản lý gói bằng lệnh sau:
```powershell
Install-Package GroupDocs.Watermark
```
## Bước 3: Tải tài liệu Word của bạn
 Bây giờ, hãy tải tài liệu Word mà bạn muốn đóng dấu mờ. Chúng tôi sẽ sử dụng`WordProcessingLoadOptions` để xác định rằng chúng ta đang làm việc với một tài liệu Word.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Các bước tiếp theo sẽ diễn ra ở đây
}
```
## Bước 4: Tạo và định cấu hình hình mờ cho hình ảnh
 Tiếp theo, chúng ta tạo một`ImageWatermark`sự vật. Đối tượng này sẽ giữ hình ảnh mà chúng ta muốn sử dụng làm hình mờ.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Cấu hình hiệu ứng hình ảnh sẽ ở đây
}
```
## Bước 5: Áp dụng hiệu ứng hình ảnh
Để làm nổi bật hình mờ của bạn, bạn có thể áp dụng nhiều hiệu ứng hình ảnh khác nhau. Ở đây, chúng tôi sẽ điều chỉnh độ sáng và độ tương phản, đặt phím sắc độ và thêm đường viền.
```csharp
WordProcessingImageEffects effects = new WordProcessingImageEffects
{
    Brightness = 0.7,
    Contrast = 0.6,
    ChromaKey = Color.Red,
    BorderLineFormat = new BorderLineFormat
    {
        Enabled = true,
        Weight = 1
    }
};
```
## Bước 6: Đặt tùy chọn hình mờ
Bây giờ, chúng ta cần đặt các tùy chọn hình mờ và áp dụng các hiệu ứng mà chúng ta vừa cấu hình.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    Effects = effects
};
```
## Bước 7: Thêm hình mờ vào tài liệu
Với hình mờ và các hiệu ứng được định cấu hình, giờ đây chúng ta có thể thêm hình mờ vào tài liệu.
```csharp
watermarker.Add(watermark, options);
```
## Bước 8: Lưu tài liệu có hình mờ
Cuối cùng, lưu tài liệu có hình mờ được áp dụng. 
```csharp
watermarker.Save(outputFileName);
```
## Phần kết luận
Thêm hình mờ vào tài liệu Word của bạn có thể nâng cao tính chuyên nghiệp của chúng và bảo vệ nội dung của bạn. Với GroupDocs.Watermark dành cho .NET, quá trình này rất đơn giản và có thể tùy chỉnh. Bằng cách làm theo hướng dẫn từng bước này, bạn có thể dễ dàng thêm hình mờ bằng nhiều hiệu ứng hình ảnh khác nhau để làm nổi bật tài liệu của mình. 
Hãy nhớ rằng, cho dù bạn đang bảo mật tài liệu của mình hay chỉ muốn thêm một chút tinh tế, GroupDocs.Watermark for .NET đều cung cấp một giải pháp mạnh mẽ cho tất cả các nhu cầu về hình mờ của bạn. 
## Câu hỏi thường gặp
### Tôi có thể sử dụng các định dạng hình ảnh khác cho hình mờ không?
Có, GroupDocs hỗ trợ nhiều định dạng hình ảnh khác nhau bao gồm JPEG, PNG, BMP và GIF.
### Có thể điều chỉnh độ trong suốt của hình mờ không?
 Tuyệt đối! Bạn có thể điều chỉnh độ trong suốt bằng cách đặt`Opacity` tài sản của`ImageWatermark` sự vật.
### Tôi có thể thêm nhiều hình mờ vào một tài liệu không?
 Có, bạn có thể thêm nhiều hình mờ bằng cách gọi`Add` phương pháp nhiều lần với các đối tượng hình mờ khác nhau.
### Làm cách nào để xóa hình mờ khỏi tài liệu?
 Để xóa hình mờ, bạn có thể sử dụng`Remove` phương pháp được cung cấp bởi`Watermarker` lớp học.
### Có cách nào để xem trước hình mờ trước khi lưu tài liệu không?
Hiện tại, không có chức năng xem trước trực tiếp trong GroupDocs.Watermark. Tuy nhiên, bạn có thể lưu tài liệu dưới dạng tệp tạm thời để xem lại hình mờ.