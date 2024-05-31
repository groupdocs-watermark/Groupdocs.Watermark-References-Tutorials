---
title: 為 PDF 新增註釋浮水印
linktitle: 為 PDF 新增註釋浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 輕鬆地在 PDF 文件中新增註解浮水印。輕鬆增強文件品牌和安全性。
type: docs
weight: 10
url: /zh-hant/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---
## 介紹
在文件管理領域，為 PDF 文件添加浮水印是一個至關重要的方面，特別是對於品牌、安全性和文件識別目的。 GroupDocs.Watermark for .NET 是一個功能強大的程式庫，有助於將浮水印無縫整合到各種文件格式（包括 PDF）中。在本教學中，我們將利用 GroupDocs.Watermark for .NET 提供的功能，逐步深入研究在 PDF 文件中新增註解浮水印的過程。
## 先決條件
在繼續學習本教程之前，請確保您符合以下先決條件：
1.  GroupDocs.Watermark for .NET 函式庫：從下列位置下載並安裝 GroupDocs.Watermark for .NET 函式庫[網站](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：設定適當的開發環境，例如 Visual Studio 或任何其他 .NET IDE。
3. 對 C# 的基本了解：建議熟悉 C# 程式語言基礎。

## 導入必要的命名空間
首先，將所需的命名空間匯入到您的 C# 專案中：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入 PDF 文檔
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 第 2 步：定義浮水印選項
```csharp
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## 第三步：新增文字浮水印
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## 第四步：新增圖片浮水印
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## 步驟5：儲存有浮水印的文檔
```csharp
	watermarker.Save(outputFileName);
}
```

## 結論
總而言之，GroupDocs.Watermark for .NET 提供了一個以程式設計方式為 PDF 文件添加註解浮水印的全面解決方案。透過遵循概述的步驟，使用者可以將文字和圖像浮水印無縫整合到 PDF 文件中，從而增強文件品牌和安全性。
## 常見問題解答
### GroupDocs.Watermark 是否與 PDF 以外的其他文件格式相容？
是的，GroupDocs.Watermark 支援多種文件格式，包括 Word、Excel、PowerPoint 等。
### 我可以自訂浮水印的外觀嗎？
絕對地！ GroupDocs.Watermark 為文字和影像浮水印提供了廣泛的自訂選項，讓使用者可以調整大小、位置、不透明度和其他參數。
### GroupDocs.Watermark適合大量處理文件嗎？
當然！ GroupDocs.Watermark 提供高效率的批次功能，使用戶能夠同時將浮水印套用到多個文件。
### GroupDocs.Watermark 支援 .NET Core 開發嗎？
是的，GroupDocs.Watermark 支援 .NET Core，允許開發人員將浮水印功能整合到跨平台應用程式中。
### GroupDocs.Watermark 用戶可以獲得技術支援嗎？
是的，GroupDocs 透過其專門的論壇和客戶服務管道提供全面的技術支援。