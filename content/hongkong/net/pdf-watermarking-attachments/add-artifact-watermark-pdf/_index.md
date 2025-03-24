---
title: 為 PDF 新增工件浮水印
linktitle: 為 PDF 新增工件浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 輕鬆地將工件浮水印新增至 PDF 檔案。輕鬆保護您的文件。
weight: 11
url: /zh-hant/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## 介紹
在 PDF 文件中添加浮水印是文件管理的重要方面，尤其是在保護智慧財產權或品牌文件時。 Groupdocs.Watermark for .NET 提供了一個強大的解決方案，可以輕鬆地在 PDF 檔案中新增浮水印。在本教學中，我們將逐步介紹在 PDF 檔案中新增人工浮水印的過程。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1.  Groupdocs.Watermark for .NET：從以下位置下載並安裝 Groupdocs.Watermark for .NET[這裡](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：建置.NET開發環境。
3. PDF文件：準備要新增浮水印的PDF文件。
4. 輸出目錄：建立一個目錄來保存帶有浮水印的 PDF 檔案。

## 導入命名空間
首先，在 C# 專案中導入必要的命名空間：
```csharp
using GroupDocs.Watermark.Common;
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
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## 第三步：新增文字浮水印
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## 第四步：新增圖片浮水印
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## 步驟5：儲存有浮水印的PDF
```csharp
watermarker.Save(outputFileName);
```

## 結論
在本教學中，我們學習如何使用 Groupdocs.Watermark for .NET 將工件浮水印新增至 PDF 檔案。透過執行這些步驟，您可以將浮水印功能無縫整合到 .NET 應用程式中，從而確保文件的安全性和完整性。
## 常見問題解答
### 我可以自訂文字浮水印的外觀嗎？
是的，您可以根據自己的喜好自訂文字浮水印的字體、大小、顏色和對齊方式等各個方面。
### Groupdocs.Watermark 是否支援向其他文件格式新增浮水印？
是的，Groupdocs.Watermark 支援將浮水印，包括 Word、Excel、PowerPoint 等。
### Groupdocs.Watermark for .NET 有沒有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 對於與 Groupdocs.Watermark 相關的任何問題或查詢，如何獲得支援？
您可以從 Groupdocs 社群論壇獲得支持[這裡](https://forum.groupdocs.com/c/watermark/19).
### 我可以將 Groupdocs.Watermark 用於商業目的嗎？
是的，您可以從以下位置購買商業用途的許可證[這裡](https://purchase.groupdocs.com/buy).