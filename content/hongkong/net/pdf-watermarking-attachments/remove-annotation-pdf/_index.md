---
title: 從 PDF 刪除註釋
linktitle: 從 PDF 刪除註釋
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 從 PDF 中刪除註解。輕鬆增強文件的可讀性。
weight: 29
url: /zh-hant/net/pdf-watermarking-attachments/remove-annotation-pdf/
---

# 從 PDF 刪除註釋

## 介紹
PDF 文件中的註釋有時會使內容混亂或影響文件的可讀性。使用 GroupDocs.Watermark for .NET，您可以輕鬆地從 PDF 檔案中刪除註解。在本教程中，我們將逐步指導您完成流程。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1.  GroupDocs.Watermark for .NET：確保您已安裝 GroupDocs.Watermark for .NET。您可以從[網站](https://releases.groupdocs.com/Watermark/net/).
2. 文件路徑：包含要從中刪除註解的 PDF 文件的路徑。
3. 輸出目錄：準備一個儲存修改後的文件的目錄。
4. .NET 環境：確保您已設定 .NET 環境來執行提供的程式碼。

## 導入命名空間
首先，匯入必要的命名空間以存取 GroupDocs for .NET 功能。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System.IO;
using System;
```
## 第 1 步：載入文檔
首先使用提供的文檔路徑載入 PDF 文件。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 第 2 步：刪除註釋
現在，讓我們繼續從 PDF 文件中刪除註釋。您有兩種刪除註釋的選項：透過索引或透過引用。
### 按索引刪除註釋
若要按索引刪除註解：
```csharp
//按索引刪除註釋
pdfContent.Pages[0].Annotations.RemoveAt(0);
```
### 透過引用刪除註釋
若要透過引用刪除註釋：
```csharp
//透過引用刪除註釋
pdfContent.Pages[0].Annotations.Remove(pdfContent.Pages[0].Annotations[0]);
```
## 第 3 步：儲存文檔
去掉註解後，將修改後的文件儲存到指定的輸出目錄中。
```csharp
    watermarker.Save(outputFileName);
}
```

## 結論
使用 GroupDocs.Watermark for .NET 從 PDF 文件中刪除註解是一個簡單的過程。透過遵循本教程中概述的步驟，您可以有效地管理註釋並增強 PDF 文件的可讀性。
## 常見問題解答
### 我可以同時刪除多個註解嗎？
是的，您可以使用 GroupDocs.Watermark for .NET 迭代註解並根據需要刪除它們。
### GroupDocs.Watermark 是否支援 PDF 以外的其他文件格式？
是的，GroupDocs 支援多種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Watermark for .NET 有沒有試用版？
是的，您可以從以下位置存取免費試用版：[這裡](https://releases.groupdocs.com/).
### 可以修改註解而不是完全刪除註解嗎？
是的，GroupDocs.Watermark 也提供了修改現有註解的方法。
### 我可以在哪裡找到額外的支援或協助？
您可以造訪 GroupDocs.Watermark 論壇[這裡](https://forum.groupdocs.com/c/watermark/19)如有任何疑問或幫助。