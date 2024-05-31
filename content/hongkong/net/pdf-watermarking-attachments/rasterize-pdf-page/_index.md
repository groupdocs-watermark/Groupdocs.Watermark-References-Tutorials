---
title: 光柵化 PDF 頁面
linktitle: 光柵化 PDF 頁面
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs for .NET 增強文件安全性。無縫地向 PDF 和其他格式添加浮水印。
type: docs
weight: 28
url: /zh-hant/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## 介紹
GroupDocs.Watermark for .NET 是一個功能強大的 API，可讓開發人員將浮水印無縫地新增至各種文件格式，包括 PDF、Word、Excel、PowerPoint 等。憑藉其直覺的介面和廣泛的功能，GroupDocs.Watermark 簡化了在文件中添加文字或圖像浮水印的過程，使用戶能夠輕鬆保護其智慧財產權並增強文件安全性。
## 先決條件
在深入使用 GroupDocs.Watermark for .NET 之前，請確保滿足以下先決條件：
1. 安裝：從以下位置下載並安裝 GroupDocs.Watermark for .NET[下載頁面](https://releases.groupdocs.com/Watermark/net/).
2. 許可證：取得 GroupDocs.Watermark for .NET 的許可證。您可以從以下位置取得用於評估目的的臨時許可證：[這裡](https://purchase.groupdocs.com/temporary-license/) ，或從[購買頁面](https://purchase.groupdocs.com/buy).
3. .NET Framework：確保您的開發電腦上安裝了 .NET Framework。
4. 文件：準備要新增浮水印的文件。

## 導入命名空間
要開始使用 GroupDocs.Watermark for .NET，請將必要的命名空間匯入到您的專案中：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文檔
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //你的程式碼放在這裡
}
```
## 步驟2：初始化浮水印
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## 第三步：新增浮水印
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## 第 4 步：光柵化頁面
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## 第 5 步：儲存文檔
```csharp
watermarker.Save(outputFileName);
```

## 結論
總而言之，GroupDocs.Watermark for .NET 提供了一個向 PDF 和其他文件格式添加浮水印的無縫解決方案。透過遵循上述逐步指南，開發人員可以輕鬆有效地光柵化 PDF 頁面並增強文件安全性。
## 常見問題解答
### GroupDocs.Watermark 是否與 PDF 以外的其他文件格式相容？
是的，GroupDocs.Watermark 支援多種文件格式，包括 Word、Excel、PowerPoint、Visio 等。
### 我可以自訂添加到文件中的浮水印的外觀嗎？
絕對地！ GroupDocs.Watermark 為文字和圖像浮水印提供了廣泛的自訂選項，讓使用者可以根據自己的喜好調整字體、大小、顏色、不透明度和位置。
### GroupDocs.Watermark 適合個人和商業用途嗎？
是的，GroupDocs.Watermark 提供靈活的授權選項來滿足個人和企業的需求，使其適合個人專案以及大型商業應用程式。
### GroupDocs.Watermark 是否為開發人員提供技術支援？
是的，開發人員可以透過 GroupDocs.Watermark 論壇獲得全面的技術支持，在那裡他們可以尋求協助、分享經驗並與其他開發人員互動。
### 我可以在購買前試用 GroupDocs.Watermark 嗎？
當然！您可以從 GroupDocs.Watermark 取得免費試用版[發布頁面](https://releases.groupdocs.com/)，讓您在決定購買之前探索其特性和功能。