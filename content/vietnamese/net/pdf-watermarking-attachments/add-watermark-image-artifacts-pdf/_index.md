---
title: Thêm hình mờ vào các tạo phẩm hình ảnh trong PDF
linktitle: Thêm hình mờ vào các tạo phẩm hình ảnh trong PDF
second_title: API GroupDocs.Watermark .NET
description: Bảo vệ tệp PDF của bạn bằng hình mờ được cá nhân hóa bằng GroupDocs.Watermark cho .NET. Dễ dàng thêm hình mờ văn bản hoặc hình ảnh vào các tạo phẩm hình ảnh trong tài liệu PDF.
weight: 18
url: /vi/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---

# Thêm hình mờ vào các tạo phẩm hình ảnh trong PDF

## Giới thiệu
Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm hình mờ vào các tạo phẩm hình ảnh trong tài liệu PDF bằng GroupDocs.Watermark cho .NET. Bằng cách làm theo các bước này, bạn có thể bảo vệ các tệp PDF của mình một cách hiệu quả bằng các hình mờ được cá nhân hóa.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1.  GroupDocs.Watermark cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Watermark cho .NET từ[đây](https://releases.groupdocs.com/Watermark/net/).
2. Đường dẫn tài liệu: Có đường dẫn đến tài liệu PDF nơi bạn muốn thêm hình mờ.
3. Thư mục đầu ra: Tạo một thư mục nơi tài liệu có hình mờ sẽ được lưu.

## Nhập không gian tên
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Bước 1: Tải tài liệu và khởi tạo Watermarker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Bước 2: Nhận nội dung PDF và thêm hình mờ
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Khởi tạo hình mờ hình ảnh hoặc văn bản
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Thêm hình mờ vào hình ảnh
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Bước 3: Lưu tài liệu có hình mờ
```csharp
	watermarker.Save(outputFileName);
}
```

## Phần kết luận
Với GroupDocs.Watermark dành cho .NET, việc thêm hình mờ vào các tạo phẩm hình ảnh trong tài liệu PDF trở thành một quá trình liền mạch. Bằng cách làm theo hướng dẫn này, bạn có thể bảo vệ các tệp PDF của mình một cách hiệu quả bằng các hình mờ tùy chỉnh, đảm bảo tính bảo mật và tính xác thực của chúng.
## Câu hỏi thường gặp
### Tôi có thể thêm hình mờ cả hình ảnh và văn bản vào tài liệu PDF của mình không?
Có, GroupDocs.Watermark cho .NET hỗ trợ thêm đồng thời cả hình mờ hình ảnh và văn bản.
### Có giới hạn nào về số lượng hình mờ mà tôi có thể thêm vào tài liệu không?
Không, bạn có thể thêm nhiều hình mờ vào tài liệu mà không có bất kỳ hạn chế nào.
### Tôi có thể tùy chỉnh hình thức và vị trí của hình mờ không?
Tuyệt đối, bạn có toàn quyền kiểm soát hình thức, vị trí và thuộc tính của hình mờ.
### GroupDocs.Watermark cho .NET có hỗ trợ các định dạng tài liệu khác ngoài PDF không?
Có, nó hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm Word, Excel, PowerPoint, v.v.
### Có cách nào để xóa hình mờ khỏi tài liệu không?
Có, GroupDocs.Watermark for .NET cung cấp các phương pháp xóa hình mờ khỏi tài liệu nếu cần.