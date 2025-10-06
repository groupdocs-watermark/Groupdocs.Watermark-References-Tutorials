---
title: 添加文字浮水印
linktitle: 添加文字浮水印
second_title: GroupDocs.Watermark .NET API
description: 透過此逐步指南，了解如何使用 Groupdocs for .NET 將文字浮水印新增至文件。
weight: 11
url: /zh-hant/net/watermarking-basics/add-text-watermark/
type: docs
---
# 添加文字浮水印

## 介紹
GroupDocs.Watermark for .NET 是一個功能強大的程式庫，可讓開發人員在 .NET 應用程式中的各種文件格式中新增、搜尋和刪除浮水印。在本教程中，我們將重點介紹如何使用 GroupDocs.Watermark 將文字浮水印新增至文件。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1. C# 程式語言的基礎知識。
2. Visual Studio 安裝在您的系統上。
3. 安裝了 .NET 函式庫的 GroupDocs.Watermark。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/Watermark/net/).

## 導入命名空間
首先，您需要將必要的命名空間匯入到您的 C# 專案中。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 步驟1：定義文檔路徑和輸出目錄
定義輸入文件的路徑和儲存帶有浮水印文件的輸出目錄。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`輸入文件的絕對或相對路徑，例如：`@"C:\Docs\document.pdf"`。另外，指定要儲存有浮水印的文件的目錄。
## 第2步：新增文字浮水印
實例化`Watermarker`帶有輸入文檔路徑的類別。然後，創建一個`TextWatermark`具有所需文字和字體設定的物件。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Watermark for .NET 將文字浮水印加入文件中。憑藉其直覺的 API，開發人員可以輕鬆操作各種文件格式的浮水印。
## 常見問題解答
### GroupDocs.Watermark for .NET 是否與所有文件格式相容？
GroupDocs.Watermark 支援多種文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以自訂文字浮水印的外觀嗎？
是的，您可以自訂文字浮水印的各種屬性，例如字體、顏色、對齊方式和不透明度。
### GroupDocs.Watermark 是否支援從文件中刪除浮水印？
是的，GroupDocs.Watermark 提供了搜尋和刪除文件浮水印的功能。
### 我可以在購買前試用 GroupDocs.Watermark for .NET 嗎？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Watermark 的技術支援？
您可以透過訪問獲得技術支持[GroupDocs.Watermark 論壇](https://forum.groupdocs.com/c/watermark/19).