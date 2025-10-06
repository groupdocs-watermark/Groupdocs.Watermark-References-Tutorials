---
title: Thêm hình mờ hình ảnh từ luồng
linktitle: Thêm hình mờ hình ảnh từ luồng
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách thêm hình mờ vào tài liệu bằng GroupDocs.Watermark cho .NET. Hãy làm theo hướng dẫn từng bước của chúng tôi để tích hợp hình mờ liền mạch.
weight: 12
url: /vi/net/image-watermarkings/add-image-watermark-from-stream/
type: docs
---
# Thêm hình mờ hình ảnh từ luồng

## Giới thiệu
Trong lĩnh vực quản lý và bảo mật tài liệu, việc kết hợp hình mờ vào các tệp có tầm quan trọng tối cao. Cho dù đó là về xây dựng thương hiệu, bảo vệ bản quyền hay duy trì tính toàn vẹn của tài liệu, hình mờ đều đóng một vai trò quan trọng. May mắn thay, GroupDocs.Watermark cho .NET cung cấp một giải pháp mạnh mẽ để thêm, xóa và tìm kiếm hình mờ ở các định dạng tài liệu khác nhau.
## Điều kiện tiên quyết
Trước khi đi sâu vào việc triển khai hình mờ bằng GroupDocs.Watermark cho .NET, hãy đảm bảo đáp ứng các điều kiện tiên quyết sau:
1.  Cài đặt GroupDocs.Watermark cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Watermark cho .NET từ[Liên kết tải xuống](https://releases.groupdocs.com/Watermark/net/).
2. Truy cập vào Tài liệu: Có quyền truy cập vào tài liệu mà bạn muốn thêm hoặc xóa hình mờ.
3. Kiến thức cơ bản về C#: Cần phải làm quen với ngôn ngữ lập trình C# để hiểu và triển khai các đoạn mã được cung cấp.

## Nhập không gian tên
Trước khi tiếp tục thêm hình mờ hình ảnh từ một luồng, hãy nhập các không gian tên cần thiết:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Bước 1: Xác định đường dẫn tài liệu và thư mục đầu ra
Đầu tiên, xác định đường dẫn của tài liệu nơi bạn muốn thêm hình mờ và chỉ định thư mục đầu ra cho tài liệu đã xử lý.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Bước 2: Mở luồng hình mờ
 Mở tệp hình ảnh hình mờ dưới dạng luồng bằng cách sử dụng`File.OpenRead` phương pháp.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // Logic xử lý hình mờ sẽ ở đây
}
```
## Bước 3: Thêm hình mờ vào tài liệu
 Khởi tạo một`Watermarker` đối tượng bằng đường dẫn tài liệu, sau đó tạo một`ImageWatermark` đối tượng bằng luồng hình mờ thu được ở Bước 2. Thêm hình mờ vào tài liệu bằng cách sử dụng`Add` phương pháp của`Watermarker` sự vật.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Thêm hình mờ vào tài liệu
        watermarker.Add(watermark);
        // Lưu tài liệu có hình mờ
        watermarker.Save(outputFileName);
    }
}
```

## Phần kết luận
GroupDocs.Watermark dành cho .NET cung cấp giải pháp liền mạch để thêm hình mờ vào tài liệu, đảm bảo nhận dạng thương hiệu, bảo vệ bản quyền và tính toàn vẹn của tài liệu. Bằng cách làm theo các bước đã nêu và sử dụng các đoạn mã được cung cấp, người dùng có thể dễ dàng kết hợp hình mờ vào tài liệu của họ.
## Câu hỏi thường gặp
### GroupDocs.Watermark có tương thích với nhiều định dạng tài liệu khác nhau không?
Có, GroupDocs.Watermark hỗ trợ nhiều định dạng tài liệu bao gồm tài liệu Word, bảng tính Excel, bản trình bày PowerPoint, PDF, v.v.
### Tôi có thể tùy chỉnh hình thức và vị trí của hình mờ không?
Hoàn toàn có thể, GroupDocs.Watermark cung cấp các tùy chọn mở rộng để tùy chỉnh hình thức, vị trí, độ trong suốt, xoay hình mờ, v.v. để phù hợp với các yêu cầu cụ thể.
### GroupDocs.Watermark có cung cấp API để xóa hình mờ hiện có không?
Có, GroupDocs.Watermark cho phép người dùng không chỉ thêm hình mờ mà còn xóa hình mờ hiện có khỏi tài liệu một cách dễ dàng.
### Có hỗ trợ kỹ thuật cho người dùng GroupDocs.Watermark không?
 Có, người dùng có thể tận dụng hỗ trợ và trợ giúp kỹ thuật thông qua đội ngũ chuyên dụng[Diễn đàn GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### Tôi có thể đánh giá GroupDocs.Watermark trước khi mua không?
Chắc chắn, người dùng có thể chọn dùng thử miễn phí GroupDocs.Watermark để khám phá các tính năng và chức năng của nó trước khi đưa ra quyết định mua hàng.