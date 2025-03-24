---
title: 在 Word 文件中刪除具有特定文字格式的形狀
linktitle: 在 Word 文件中刪除具有特定文字格式的形狀
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 刪除 Word 文件中具有特定文字格式的形狀。請遵循我們的指南來有效地處理浮水印。
weight: 31
url: /zh-hant/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
---

# 在 Word 文件中刪除具有特定文字格式的形狀

## 介紹
GroupDocs.Watermark for .NET 是一個功能強大的 API，可讓開發人員以程式設計方式操作各種文件格式的浮水印。在本教學中，我們將重點放在使用 GroupDocs.Watermark for .NET 刪除 Word 文件中具有特定文字格式的形狀。無論您是經驗豐富的開發人員還是剛起步，本逐步指南都將幫助您了解高效且有效地刪除形狀的過程。
## 先決條件
在我們深入學習本教程之前，請確保您具備以下先決條件：
1.  GroupDocs.Watermark for .NET：確保您的開發環境中安裝了 GroupDocs.Watermark for .NET 程式庫。您可以從[網站](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：安裝 Visual Studio 或任何其他 .NET IDE，設定適當的開發環境。
3. Word 文件：準備一個 Word 文檔，其中包含具有要刪除的特定文字格式的形狀。

## 導入命名空間
在開始實作之前，讓我們先導入必要的名稱空間：
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文檔
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //實施在這裡
}
```
## 第 2 步：取得內容並迭代各個部分
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    //實施在這裡
}
```
## 第 3 步：迭代形狀並根據文字格式刪除
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## 步驟 4：儲存文檔
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Watermark for .NET 刪除 Word 文件中具有特定文字格式的形狀。透過遵循逐步指南並利用提供的程式碼範例，開發人員可以根據自己的要求輕鬆操作浮水印。
## 常見問題解答
### GroupDocs.Watermark for .NET 是否與 Word 以外的其他文件格式相容？
是的，GroupDocs.Watermark for .NET 支援各種文件格式，包括 Excel、PowerPoint、PDF 等。
### 我可以根據文字格式自訂刪除形狀的標準嗎？
絕對地！您可以修改程式碼以針對特定的文字屬性，例如字體大小、樣式、顏色等。
### GroupDocs.Watermark for .NET 是否也提供新增浮水印的支援？
是的，除了刪除之外，您還可以使用 GroupDocs.Watermark for .NET 將文字或影像浮水印新增至文件。
### 購買前是否有試用版可供測試？
是的，您可以從 GroupDocs 下載免費試用版[網站](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Watermark for .NET 的技術支援或協助？
如需技術協助，您可以造訪支援論壇：[GroupDocs.浮水印論壇](https://forum.groupdocs.com/c/watermark/19).