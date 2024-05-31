---
title: Tạo bản xem trước tài liệu
linktitle: Tạo bản xem trước tài liệu
second_title: API GroupDocs.Watermark .NET
description: Tìm hiểu cách tạo bản xem trước tài liệu bằng GroupDocs.Watermark cho .NET với hướng dẫn này. Tăng cường bảo mật và quản lý tài liệu của bạn một cách dễ dàng.
type: docs
weight: 10
url: /vi/net/document-manipulation/generate-document-preview/
---
## Giới thiệu
Trong thế giới quản lý tài liệu kỹ thuật số, hình mờ đóng một vai trò quan trọng trong việc đảm bảo tính bảo mật và tính xác thực của tài liệu. GroupDocs.Watermark cho .NET là một công cụ mạnh mẽ cho phép các nhà phát triển thêm hình mờ vào tài liệu một cách dễ dàng. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình tạo bản xem trước tài liệu bằng GroupDocs.Watermark cho .NET. Cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay chỉ mới bắt đầu, hướng dẫn này sẽ cung cấp cho bạn quy trình từng bước toàn diện để đạt được mục tiêu của mình.
## Điều kiện tiên quyết
Trước khi đi sâu vào triển khai, hãy đảm bảo bạn có mọi thứ cần thiết để bắt đầu:
- Hiểu biết cơ bản về C# và .NET framework.
- Visual Studio được cài đặt trên máy của bạn.
- GroupDocs.Watermark cho thư viện .NET. Bạn có thể[tải về tại đây](https://releases.groupdocs.com/Watermark/net/).
-  Giấy phép hợp lệ cho GroupDocs.Watermark. Bạn có thể mua nó[đây](https://purchase.groupdocs.com/buy) hoặc có được một[giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) cho mục đích đánh giá.
## Nhập không gian tên
Để bắt đầu sử dụng GroupDocs.Watermark trong dự án của bạn, bạn cần nhập các vùng tên cần thiết. Điều này có thể được thực hiện bằng cách thêm các lệnh sử dụng sau vào mã của bạn:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Các không gian tên này sẽ cung cấp quyền truy cập vào các lớp và phương thức cần thiết để tạo hình mờ và tạo bản xem trước tài liệu.

Hãy chia nhỏ quy trình tạo bản xem trước tài liệu thành các bước đơn giản, dễ thực hiện.
## Bước 1: Thiết lập dự án của bạn
Trước tiên, hãy thiết lập dự án .NET của bạn trong Visual Studio. Nếu bạn chưa có dự án, hãy tạo một dự án mới bằng cách làm theo các bước sau:
1. Mở Visual Studio.
2. Nhấp vào "Tạo dự án mới."
3. Chọn "Ứng dụng Console (.NET Core)" và nhấp vào "Tiếp theo".
4. Đặt tên cho dự án của bạn và chọn vị trí để lưu nó, sau đó nhấp vào "Tạo".
## Bước 2: Cài đặt GroupDocs.Watermark cho .NET
Để sử dụng GroupDocs.Watermark trong dự án của bạn, bạn cần cài đặt thư viện. Điều này có thể được thực hiện bằng Trình quản lý gói NuGet:
1. Nhấp chuột phải vào dự án của bạn trong Solution Explorer.
2. Chọn "Quản lý gói NuGet."
3. Tìm kiếm "GroupDocs.Watermark" trong tab Duyệt.
4. Nhấp vào "Cài đặt" để thêm thư viện vào dự án của bạn.
Ngoài ra, bạn có thể cài đặt nó thông qua Bảng điều khiển quản lý gói:
```powershell
Install-Package GroupDocs.Watermark
```
## Bước 3: Xác định đường dẫn tài liệu và thư mục đầu ra
Trước khi tạo bản xem trước, bạn cần chỉ định đường dẫn của tài liệu bạn muốn xem trước và thư mục lưu hình ảnh xem trước:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Thay thế "Đường dẫn tài liệu của bạn" bằng đường dẫn đến tài liệu của bạn và "Thư mục tài liệu của bạn" bằng thư mục bạn muốn lưu hình ảnh xem trước.
## Bước 4: Khởi tạo đối tượng Watermarker
Tạo một thể hiện của`Watermarker` lớp bằng cách chuyển đường dẫn tài liệu tới hàm tạo của nó. Đối tượng này sẽ được sử dụng để thực hiện tất cả các hoạt động đóng dấu chìm:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Mã của bạn ở đây
}
```
## Bước 5: Tạo phương thức đại biểu để xử lý luồng
Để tạo bản xem trước, bạn cần xác định các phương thức ủy quyền để tạo và phát hành luồng. Các phương thức này sẽ xử lý việc tạo và phát hành các luồng cho mỗi trang của tài liệu:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 Các`createPageStreamDelegate` phương thức tạo một luồng cho mỗi trang của tài liệu, trong khi`releasePageStreamDelegate` phương thức đóng luồng sau khi bản xem trước được tạo.
## Bước 6: Định cấu hình tùy chọn xem trước
 Tiếp theo, định cấu hình các tùy chọn xem trước bằng cách tạo một phiên bản của`PreviewOptions` lớp học. Chỉ định các phương thức ủy nhiệm và đặt định dạng xem trước thành PNG. Bạn cũng có thể chỉ định những trang nào sẽ được đưa vào bản xem trước:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
Trong ví dụ này, chúng tôi đang tạo bản xem trước cho hai trang đầu tiên của tài liệu.
## Bước 7: Tạo bản xem trước tài liệu
 Cuối cùng, hãy gọi`GeneratePreview` phương pháp trên`Watermarker`đối tượng, chuyển vào cấu hình`PreviewOptions`. Điều này sẽ tạo ra các hình ảnh xem trước và lưu chúng vào thư mục được chỉ định:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Phần kết luận
Tạo bản xem trước tài liệu bằng GroupDocs.Watermark cho .NET là một quá trình đơn giản có thể được thực hiện chỉ với một vài dòng mã. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể dễ dàng thiết lập dự án của mình, định cấu hình các tùy chọn cần thiết và tạo bản xem trước cho tài liệu của mình. Thư viện mạnh mẽ này không chỉ đơn giản hóa quá trình tạo hình mờ mà còn cung cấp các tính năng mạnh mẽ để quản lý và thao tác hình mờ.
 Nếu bạn có thắc mắc hoặc cần hỗ trợ thêm, đừng ngần ngại truy cập[Diễn đàn hỗ trợ GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) hoặc tham khảo[tài liệu](https://reference.groupdocs.com/Watermark/net/).
## Câu hỏi thường gặp
### Những định dạng tệp nào được GroupDocs.Watermark hỗ trợ cho .NET?
 GroupDocs.Watermark cho .NET hỗ trợ nhiều định dạng tệp, bao gồm PDF, DOCX, PPTX, XLSX, v.v. Để biết danh sách đầy đủ các định dạng được hỗ trợ, hãy tham khảo[tài liệu](https://reference.groupdocs.com/Watermark/net/).
### Tôi có thể tùy chỉnh sự xuất hiện của hình mờ không?
Có, GroupDocs.Watermark cho phép bạn tùy chỉnh hoàn toàn giao diện của hình mờ, bao gồm hình mờ văn bản, hình ảnh và hình dạng. Bạn có thể điều chỉnh các thuộc tính như phông chữ, màu sắc, kích thước và độ trong suốt.
### Có sẵn phiên bản dùng thử không?
 Có, bạn có thể nhận được một[dùng thử miễn phí](https://releases.groupdocs.com/) của GroupDocs.Watermark dành cho .NET để đánh giá các tính năng của nó trước khi mua hàng.
### Làm cách nào tôi có thể mua giấy phép cho GroupDocs.Watermark?
 Bạn có thể mua giấy phép cho GroupDocs.Watermark[đây](https://purchase.groupdocs.com/buy). Có nhiều tùy chọn cấp phép khác nhau có sẵn để phù hợp với các nhu cầu khác nhau.
### Tôi có thể sử dụng GroupDocs.Watermark trong một dự án thương mại không?
 Có, với giấy phép hợp lệ, bạn có thể sử dụng GroupDocs.Watermark trong các dự án thương mại. Hãy chắc chắn xem lại các điều khoản và điều kiện cấp phép trên[trang mua hàng](https://purchase.groupdocs.com/buy).