---
title: 新增影像浮水印
linktitle: 新增影像浮水印
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs.Watermark for .NET 輕鬆將影像浮水印新增至文件。輕鬆保護您的智慧財產權。
type: docs
weight: 10
url: /zh-hant/net/watermarking-basics/add-image-watermark/
---
## 介紹
在本教學中，我們將深入研究使用 GroupDocs.Watermark for .NET 將影像浮水印新增至文件的流程。對文件加浮水印對於保護智慧財產權和品牌至關重要。透過 GroupDocs.Watermark for .NET，您可以將浮水印無縫整合到各種文件格式中，例如 Word、Excel、PowerPoint、PDF 等。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1.  GroupDocs.Watermark for .NET 函式庫：從下列位置下載並安裝 GroupDocs.Watermark for .NET 函式庫[網站](https://releases.groupdocs.com/Watermark/net/).
2. 文件：準備好要新增浮水印的文件。
3. 水印影像：準備要用作浮水印的影像檔案。

## 導入命名空間
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## 步驟1：初始化文檔路徑和輸出目錄
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`與文檔的絕對或相對路徑以及`"Your Document Directory"`與要儲存有浮水印的文件的目錄。
## 步驟2：開啟文檔流並初始化浮水印
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        //水印過程將在此處進行
    }
}
```
使用開啟文檔流程`FileStream`並初始化`Watermarker`目的。
## 第三步：新增圖片浮水印
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
創建一個`ImageWatermark`對象，其中包含要用作浮水印的圖像檔案的路徑。設定水印的水平和垂直對齊方式。
## 步驟 4：儲存有浮水印的文檔
```csharp
watermarker.Save(outputFileName);
```
使用所需的檔案名稱將帶有浮水印的文件儲存到指定的輸出目錄。

## 結論
總而言之，GroupDocs.Watermark for .NET 提供了一個全面的解決方案，可以輕鬆地將浮水印新增至各種文件格式。透過遵循本教學中概述的步驟，您可以有效地向文件添加圖像浮水印並保護您的智慧財產權。
## 常見問題解答
### 我可以使用 GroupDocs.Watermark for .NET 新增文字浮水印嗎？
是的，GroupDocs.Watermark for .NET 支援在文件中新增影像和文字浮水印。
### GroupDocs.Watermark for .NET 是否與不同的文件格式相容？
當然，GroupDocs.Watermark for .NET 支援多種文件格式，包括 Word、Excel、PowerPoint、PDF 等。
### GroupDocs.Watermark for .NET 是否提供浮水印的自訂選項？
是的，您可以自訂浮水印的各個方面，例如位置、大小、不透明度和旋轉。
### 我可以使用 GroupDocs.Watermark for .NET 從文件中刪除浮水印嗎？
是的，GroupDocs.Watermark for .NET 提供了偵測和刪除文件中的浮水印的功能。
### GroupDocs.Watermark for .NET 有沒有試用版？
是的，您可以在購買前從網站上使用免費試用版來探索功能[這裡](https://releases.groupdocs.com/).