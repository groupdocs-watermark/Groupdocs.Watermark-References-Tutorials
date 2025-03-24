---
title: 添加浮水印以在 Word 文件中塑造圖像
linktitle: 添加浮水印以在 Word 文件中塑造圖像
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 新增浮水印以在 Word 文件中塑造圖像。透過本教學增強文件安全性。
weight: 17
url: /zh-hant/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---

# 添加浮水印以在 Word 文件中塑造圖像

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Watermark for .NET 在 Word 文件中加入浮水印以塑造圖像。水印是文件保護的重要方面，尤其是在處理敏感或機密資訊時。透過在形狀影像中新增浮水印，您可以確保文件的完整性和安全性。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1.  GroupDocs.Watermark for .NET：從以下位置下載並安裝 GroupDocs.Watermark 函式庫：[下載頁面](https://releases.groupdocs.com/Watermark/net/).
2. 文件：準備好要新增浮水印的Word文件。
3. 開發環境：設定您首選的 .NET 開發環境。
## 導入命名空間
在編寫程式碼之前，請確保導入必要的命名空間：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文檔
首先，定義文檔的路徑並指定輸出檔案名稱：
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 步驟2：初始化浮水印
實例化一個`Watermarker`透過提供文檔路徑和可選載入選項來物件：
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //在這裡添加浮水印邏輯
}
```
## 步驟3：建立文字浮水印
使用所需屬性定義文字浮水印，例如文字、字體、對齊方式、旋轉、大小調整等：
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 步驟 4：將浮水印套用到影像形狀
迭代文件部分和形狀以識別形狀圖像並添加浮水印：
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## 第 5 步：儲存文檔
將新增浮水印的文件儲存到指定的輸出檔案：
```csharp
watermarker.Save(outputFileName);
```

## 結論
在本教程中，我們學習如何使用 GroupDocs.Watermark for .NET 在 Word 文件中添加浮水印來塑造圖像。透過遵循逐步指南並利用 GroupDocs.Watermark 的強大功能，您可以有效地增強文件的安全性和保護。
## 常見問題解答
### 我可以自訂浮水印文字的外觀嗎？
是的，您可以根據您的喜好調整字體、大小、顏色、旋轉角度和對齊方式等各種屬性來自訂浮水印。
### GroupDocs.Watermark 是否支援 Word 以外的其他文件格式？
是的，GroupDocs.Watermark 提供對多種文件格式的支持，包括 PDF、Excel、PowerPoint 等。
### 是否可以為單一文件添加多個浮水印？
當然，您可以在同一文件中添加具有不同內容、樣式和位置的多個浮水印。
### 我可以使用 GroupDocs.Watermark 從文件中刪除浮水印嗎？
是的，GroupDocs.Watermark 提供了有效檢測和刪除文件中的水印的功能。
### GroupDocs.Watermark 是否提供跨平台相容性？
是的，GroupDocs.Watermark 與 .NET Framework、.NET Core 和 .NET Standard 相容，確保跨不同平台的無縫整合。