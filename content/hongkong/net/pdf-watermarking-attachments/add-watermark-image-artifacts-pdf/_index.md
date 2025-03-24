---
title: 在 PDF 中的圖像工件添加浮水印
linktitle: 在 PDF 中的圖像工件添加浮水印
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs.Watermark for .NET 使用個人化浮水印保護您的 PDF 檔案。輕鬆將文字或影像浮水印新增至 PDF 文件中的影像工件。
weight: 18
url: /zh-hant/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## 介紹
在本教學中，我們將引導您完成使用 GroupDocs.Watermark for .NET 為 PDF 文件中的影像工件新增浮水印的流程。透過執行以下步驟，您可以使用個人化浮水印有效保護您的 PDF 檔案。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1.  GroupDocs.Watermark for .NET：下載並安裝 GroupDocs.Watermark for .NET 函式庫[這裡](https://releases.groupdocs.com/Watermark/net/).
2. 文件路徑：包含要新增浮水印的 PDF 文件的路徑。
3. 輸出目錄：建立保存帶有浮水印文件的目錄。

## 導入命名空間
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文件並初始化 Watermarker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 步驟2：取得PDF內容並新增浮水印
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	//初始化圖像或文字浮水印
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
				//為影像添加浮水印
				artifact.Image.Add(watermark);
			}
		}
	}
```
## 步驟 3：儲存有浮水印的文檔
```csharp
	watermarker.Save(outputFileName);
}
```

## 結論
透過 GroupDocs.Watermark for .NET，在 PDF 文件中的影像工件中添加浮水印成為無縫流程。透過遵循本教學課程，您可以使用自訂浮水印有效保護您的PDF文件，確保其安全性和真實性。
## 常見問題解答
### 我可以在 PDF 文件中添加圖像和文字浮水印嗎？
是的，GroupDocs.Watermark for .NET 支援同時新增影像和文字浮水印。
### 我可以添加到文件中的水印數量有限制嗎？
不，您可以在文件中添加多個浮水印，沒有任何限制。
### 我可以自訂浮水印的外觀和位置嗎？
當然，您可以完全控制浮水印的外觀、位置和屬性。
### GroupDocs.Watermark for .NET 是否支援 PDF 以外的其他文件格式？
是的，它支援多種文件格式，包括 Word、Excel、PowerPoint 等。
### 有沒有辦法從文件中刪除浮水印？
是的，GroupDocs.Watermark for .NET 提供了根據需要從文件中刪除浮水印的方法。