---
title: 取得 PDF 尺寸
linktitle: 取得 PDF 尺寸
second_title: GroupDocs.Watermark .NET API
description: 使用 Groupdocs.Watermark for .NET 輕鬆保護您的文件。輕鬆添加浮水印、圖章和註釋。
weight: 26
url: /zh-hant/net/pdf-watermarking-attachments/get-pdf-dimensions/
---
## 介紹
在當今的數位時代，保護您的文件至關重要。無論您是商業專業人士、法律專家還是創意藝術家，保護您的智慧財產權都是至關重要的。 Groupdocs.Watermark for .NET 提供了一個強大的解決方案，可以在文件中添加浮水印、圖章和註釋，確保其安全性和真實性。
## 先決條件
在深入了解 .NET 的 Groupdocs.Watermark 世界之前，請確保滿足以下先決條件：
1. 安裝 Groupdocs.Watermark for .NET：從以下位置下載並安裝 Groupdocs.Watermark for .NET[下載連結](https://releases.groupdocs.com/Watermark/net/).
2. 許可證金鑰（可選）：雖然 Groupdocs.Watermark for .NET 提供免費試用版，但您可以選擇臨時授權或從以下位置購買完整授權：[這裡](https://purchase.groupdocs.com/buy)用於擴充功能。
3. 熟悉 C#：建議具備 C# 程式語言的基本知識，以理解和實現所提供的範例。
4. 若要保護的文件：在本機電腦上準備好範例文件（例如 PDF、Word、Excel）以進行試驗。

## 導入命名空間
要開始使用 Groupdocs.Watermark for .NET，您需要將必要的命名空間匯入到您的 C# 專案中。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### 第 1 步：宣告變數
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### 第 2 步：載入文檔
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### 第 3 步：取得 PDF 內容
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### 第 4 步：檢索尺寸
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## 結論
總而言之，Groupdocs.Watermark for .NET 提供了一個全面的解決方案來保護您的文件免於未經授權的使用和分發。透過執行上述步驟並利用 Groupdocs.Watermark for .NET 的強大功能，您可以確保寶貴數位資產的安全性和完整性。
## 常見問題解答
### 我可以免費使用 Groupdocs.Watermark for .NET 嗎？
是的，Groupdocs.Watermark for .NET 提供免費試用版用於評估目的。但是，對於擴充功能，您可以考慮購買完整許可證。
### Groupdocs.Watermark 支援多種文件格式嗎？
是的，Groupdocs 支援多種文件格式，包括 PDF、Word、Excel、PowerPoint 等。
### 我可以使用 Groupdocs.Watermark 自訂浮水印和圖章嗎？
絕對地！ Groupdocs.Watermark 提供了廣泛的浮水印、圖章和註釋自訂選項，以滿足您的特定要求。
### Groupdocs.Watermark 使用者可以獲得技術支援嗎？
是的，您可以透過以下方式獲得技術援助並與 Groupdocs 社群互動：[支援論壇](https://forum.groupdocs.com/c/watermark/19).
### 如何取得 Groupdocs.Watermark 的臨時授權？
您可以從以下位置取得 Groupdocs.Watermark 的臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).