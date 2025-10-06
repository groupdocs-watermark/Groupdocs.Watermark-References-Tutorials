---
title: 將僅列印註釋浮水印新增至 PDF
linktitle: 將僅列印註釋浮水印新增至 PDF
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 將僅列印註解浮水印新增至 PDF。輕鬆增強文件安全性和品牌形象。
weight: 13
url: /zh-hant/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
type: docs
---
# 將僅列印註釋浮水印新增至 PDF

## 介紹
在本教程中，我們將深入研究使用 GroupDocs.Watermark for .NET 將僅列印註解浮水印新增至 PDF 的過程。文件浮水印是文件安全和品牌塑造的一個重要方面，GroupDocs.Watermark 為 .NET 開發人員提供了實現這一目標的無縫解決方案。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
- 對 C# 程式語言有基本了解。
- Visual Studio 安裝在您的電腦上。
- GroupDocs.Watermark for .NET 程式庫安裝在您的專案中。

## 導入命名空間
首先，請確保導入必要的命名空間：
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文檔
首先，您需要載入要加浮水印的PDF文件。代替`"Your Document Path"`以及您的 PDF 文件的路徑和`"Your Document Directory"`與要保存輸出檔案的目錄。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //此處將添加浮水印代碼
}
```
## 第2步：新增浮水印
接下來，使用所需的文字和字體建立文字浮水印物件。放`isPrintOnly`到`true`確保水印僅在列印文件時可見，而不是在檢視模式下可見。
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## 步驟 3：配置浮水印選項
定義浮水印的選項，例如應新增浮水印的頁面索引並將其指定為僅列印註解。
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## 第 4 步：應用浮水印
使用指定的選項將浮水印新增至文件並儲存輸出檔案。
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Watermark for .NET 將僅列印註解浮水印新增至 PDF 文件。這使開發人員能夠輕鬆增強文件安全性和品牌化。
## 常見問題解答
### GroupDocs.Watermark 是否與 PDF 以外的其他文件格式相容？
是的，GroupDocs 支援多種文件格式，例如 Word、Excel、PowerPoint 和圖像。
### 我可以自訂浮水印的外觀嗎？
當然，GroupDocs.Watermark 提供了廣泛的選項來自訂水印文字、字體、顏色、大小和位置。
### GroupDocs.Watermark 是否提供批次功能？
當然，開發人員可以使用批次功能同時為多個文件添加浮水印。
### GroupDocs.Watermark 是否有試用版？
是的，您可以從提供的連結存取 GroupDocs.Watermark 的免費試用版。
### 如何獲得 GroupDocs.Watermark 的技術支援？
您可以透過提供的支援連結從 GroupDocs.Watermark 論壇尋求技術協助。