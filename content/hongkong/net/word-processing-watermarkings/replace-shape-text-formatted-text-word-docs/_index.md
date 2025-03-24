---
title: 在 Word 文件中將形狀文字替換為格式化文本
linktitle: 在 Word 文件中將形狀文字替換為格式化文本
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 將 Word 文件中的形狀文字替換為格式化文字。您的文件編輯功能毫不費力。
weight: 34
url: /zh-hant/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## 介紹
在本教學中，我們將引導您完成使用 GroupDocs.Watermark for .NET 將 Word 文件中的形狀文字替換為格式化文字的過程。該庫提供了處理浮水印的強大功能，包括替換形狀中的文字。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1.  GroupDocs.Watermark for .NET：確保您已安裝並設定 GroupDocs.Watermark for .NET。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/Watermark/net/).
2. 文件路徑：您應該擁有要替換文字的 Word 文件的路徑。

## 導入命名空間
在編寫程式碼之前，導入必要的命名空間：
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文檔
使用以下命令載入 Word 文檔`Watermarker`班級：
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //您的程式碼在這裡繼續...
}
```
## 第 2 步：獲取內容並替換文本
載入文件後，取得內容並替換形狀中的文字：
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## 第 3 步：儲存文檔
替換文字後，儲存修改後的文件：
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 結論
使用 GroupDocs for .NET，可以輕鬆地用 Word 文件中的格式化文字取代形狀文字。透過遵循本教學中概述的步驟，您可以有效地管理和操作文件中的文字。

## 常見問題解答
### 我可以使用 GroupDocs.Watermark for .NET 來取代其他類型文件中的文字嗎？
是的，GroupDocs 支援多種文件格式，例如 PDF、Excel、PowerPoint 等。
### GroupDocs.Watermark 與 .NET Core 相容嗎？
是的，GroupDocs.Watermark 同時支援 .NET Framework 和 .NET Core。
### GroupDocs.Watermark 是否支援添加影像作為浮水印？
當然，GroupDocs.Watermark 允許您在文件中添加文字和圖像浮水印。
### 我可以自訂使用 GroupDocs.Watermark 添加的水印的外觀嗎？
是的，您可以完全控制浮水印的外觀、位置和其他屬性。
### GroupDocs.Watermark for .NET 有沒有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).