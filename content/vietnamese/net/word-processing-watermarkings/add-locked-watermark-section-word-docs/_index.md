---
title: Thêm Hình mờ đã khóa vào Phần trong Tài liệu Word
linktitle: Thêm Hình mờ đã khóa vào Phần trong Tài liệu Word
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ bị khóa vào một phần cụ thể trong tài liệu Word bằng Groupdocs cho .NET với hướng dẫn từng bước toàn diện này.
type: docs
weight: 13
url: /vi/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---
## Giới thiệu
Bạn đang tìm kiếm một cách hiệu quả để thêm hình mờ bị khóa vào một phần trong tài liệu Word của mình? Đừng tìm đâu xa! Với Groupdocs.Watermark dành cho .NET, bạn có thể chèn hình mờ vào tài liệu Word một cách liền mạch mà vẫn đảm bảo chúng vẫn bị khóa và chống giả mạo. Công cụ mạnh mẽ này cung cấp nhiều tính năng khác nhau để đáp ứng nhu cầu tạo hình mờ của bạn, cho dù mục đích xây dựng thương hiệu, bảo mật hay bảo mật. Trong hướng dẫn từng bước này, chúng tôi sẽ hướng dẫn bạn cách thêm hình mờ bị khóa vào một phần cụ thể của tài liệu Word bằng Groupdocs.Watermark cho .NET. Hãy đi sâu vào!
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1.  Groupdocs.Watermark cho .NET: Đảm bảo bạn đã cài đặt thư viện Groupdocs.Watermark. Bạn có thể tải nó xuống[đây](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Đảm bảo bạn đã thiết lập .NET framework trong môi trường phát triển của mình.
3. IDE: Sử dụng Môi trường phát triển tích hợp (IDE) như Visual Studio.
4. Tài liệu: Một tài liệu Word (.docx) để áp dụng hình mờ.
## Nhập không gian tên
Để bắt đầu, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Đây là cách thực hiện:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu của bạn
 Trước tiên, bạn cần tải tài liệu mà bạn muốn thêm hình mờ vào. Bước này liên quan đến việc chỉ định đường dẫn tài liệu của bạn và tải nó bằng cách sử dụng`Watermarker` lớp học.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Mã hình mờ của bạn sẽ xuất hiện ở đây.
}
```
## Bước 2: Tạo hình mờ
Tiếp theo, tạo hình mờ bạn muốn thêm vào tài liệu của mình. Trong ví dụ này, chúng tôi sẽ tạo hình mờ văn bản với cài đặt phông chữ và màu sắc cụ thể.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Bước 3: Định cấu hình tùy chọn hình mờ
Bây giờ, hãy định cấu hình các tùy chọn hình mờ để chỉ định cài đặt khóa và chỉ mục phần. Điều này đảm bảo hình mờ được thêm vào đúng phần và bị khóa.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // Thêm vào phần đầu tiên
options.IsLocked = true; // Khóa hình mờ
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Loại khóa
```
## Bước 4: Thêm hình mờ vào tài liệu
 Với hình mờ và các tùy chọn đã được định cấu hình, đã đến lúc thêm hình mờ vào tài liệu bằng cách sử dụng`Add` phương pháp của`Watermarker` lớp học.
```csharp
watermarker.Add(watermark, options);
```
## Bước 5: Lưu tài liệu đã sửa đổi
Cuối cùng, lưu tài liệu có hình mờ đã thêm vào vị trí đầu ra mà bạn mong muốn.
```csharp
watermarker.Save(outputFileName);
```
## Phần kết luận
Thêm hình mờ bị khóa vào một phần cụ thể trong tài liệu Word bằng Groupdocs cho .NET là một quá trình đơn giản. Bằng cách làm theo các bước này, bạn có thể nâng cao tính bảo mật và tính toàn vẹn của tài liệu của mình, đảm bảo rằng thông tin quan trọng được bảo vệ. Cho dù bạn đang bảo vệ dữ liệu nhạy cảm hay thêm nét chuyên nghiệp vào tài liệu của mình, Groupdocs.Watermark for .NET đều cung cấp các công cụ bạn cần để đạt được mục tiêu của mình một cách hiệu quả.
## Câu hỏi thường gặp
### Groupdocs.Watermark cho .NET là gì?
Groupdocs.Watermark cho .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm hình mờ vào nhiều loại tài liệu khác nhau, bao gồm Word, PDF và hình ảnh, với các tính năng bảo mật và tùy chỉnh nâng cao.
### Tôi có thể khóa hình mờ bằng mật khẩu không?
 Có, bạn có thể bảo vệ hình mờ bằng mật khẩu bằng cách đặt`options.Password` tài sản ở`WordProcessingWatermarkSectionOptions` lớp học.
### Có thể áp dụng các hình mờ khác nhau cho các phần khác nhau của tài liệu không?
 Tuyệt đối! Bằng cách thiết lập khác nhau`SectionIndex` các giá trị trong`WordProcessingWatermarkSectionOptions`, bạn có thể áp dụng các hình mờ duy nhất cho các phần khác nhau của tài liệu.
### Tôi có thể thêm những loại hình mờ nào bằng Groupdocs.Watermark?
Groupdocs.Watermark hỗ trợ nhiều loại hình mờ khác nhau, bao gồm hình mờ văn bản, hình ảnh và hình dạng, cung cấp các tùy chọn tùy chỉnh mở rộng cho từng loại.
### Tôi có thể tìm thêm thông tin về Groupdocs.Watermark cho .NET ở đâu?
 Để biết thêm thông tin, bạn có thể truy cập[tài liệu](https://reference.groupdocs.com/Watermark/net/) Và[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/watermark/19).