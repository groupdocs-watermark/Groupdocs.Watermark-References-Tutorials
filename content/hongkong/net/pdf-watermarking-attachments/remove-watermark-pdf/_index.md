---
title: 從 PDF 移除浮水印
linktitle: 從 PDF 移除浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 從 PDF 檔案中移除浮水印。專業文檔編輯的簡單步驟。
weight: 34
url: /zh-hant/net/pdf-watermarking-attachments/remove-watermark-pdf/
type: docs
---
# 從 PDF 移除浮水印

## 介紹
在當今的數位時代，使用水印保護敏感文件是一種常見的做法。但是，在某些情況下，您可能會因各種原因需要從 PDF 檔案中刪除浮水印。無論您是在編輯文件還是只是需要一個乾淨的版本進行演示，GroupDocs.Watermark for .NET 都提供了從 PDF 文件中刪除水印的無縫解決方案。
## 先決條件
在我們深入研究使用 GroupDocs.Watermark for .NET 從 PDF 檔案中刪除浮水印之前，請確保您符合以下先決條件：
1.  GroupDocs.Watermark for .NET 函式庫：從以下位置下載並安裝此函式庫[這裡](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：系統上安裝了 Visual Studio 或任何相容的 IDE。
3. 帶有浮水印的文件：準備包含要刪除的浮水印的 PDF 文件。

## 導入命名空間
在您的 C# 專案中，首先匯入必要的命名空間：
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## 第 1 步：載入 PDF 文檔
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
在此步驟中，指定 PDF 文件的路徑以及要儲存輸出檔案的目錄。
## 第 2 步：初始化浮水印和搜尋條件
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
使用 PDF 文件路徑和載入選項初始化 Watermarker 物件。然後，定義要刪除的浮水印的搜尋條件。您可以根據圖像或文字搜尋浮水印。
## 第三步：搜尋並刪除浮水印
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    //刪除所有找到的浮水印
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
根據定義的搜尋條件在 PDF 文件的第一頁上搜尋可能的浮水印。然後，迭代可能的水印集合並將其一一刪除。最後，儲存修改後的無浮水印PDF文件。

## 結論
從文件編輯到簡報準備，從 PDF 文件中刪除浮水印是各種場景中的關鍵任務。透過 GroupDocs.Watermark for .NET，您可以使用簡單的 C# 程式碼輕鬆地從 PDF 文件中刪除浮水印，確保您的文件乾淨且專業。
## 常見問題解答
### GroupDocs.Watermark for .NET 是否與所有版本的 Visual Studio 相容？
是的，GroupDocs.Watermark for .NET 與所有版本的 Visual Studio 相容，包括 Visual Studio 2019 和 Visual Studio 2022。
### 我可以使用 GroupDocs.Watermark for .NET 從單一 PDF 文件中刪除多個浮水印嗎？
是的，您可以透過指定適當的搜尋條件來搜尋並刪除單一 PDF 文件中的多個浮水印。
### GroupDocs.Watermark for .NET 是否支援 PDF 以外的其他文件格式？
是的，GroupDocs.Watermark for .NET 支援多種文件格式，包括 Word 文件、Excel 電子表格、PowerPoint 簡報等。
### GroupDocs.Watermark for .NET 有沒有試用版？
是的，您可以從以下位置下載 GroupDocs.Watermark for .NET 的免費試用版：[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到 GroupDocs.Watermark for .NET 的其他支援和協助？
如需更多支持，您可以造訪 GroupDocs.Watermark 論壇[這裡](https://forum.groupdocs.com/c/watermark/19).