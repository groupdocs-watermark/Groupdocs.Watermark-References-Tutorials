---
title: 刪除 PDF 中具有特定文字格式的註釋
linktitle: 刪除 PDF 中具有特定文字格式的註釋
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs for .NET 刪除 PDF 文件中具有特定文字格式的註解。
type: docs
weight: 30
url: /zh-hant/net/pdf-watermarking-attachments/remove-annotations-text-formatting-pdf/
---
## 介紹
在本教學中，我們將引導您完成使用 Groupdocs.Watermark for .NET 刪除 PDF 文件中具有特定文字格式的註解的過程。該庫提供了強大的功能來處理各種格式的浮水印、註釋和其他文件元素。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1.  Groupdocs.Watermark for .NET 函式庫：從以下位置下載並安裝此函式庫[這裡](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：在您的電腦上設定的.NET 開發環境。
3. PDF 文件：擁有一個帶有您要修改的註釋的 PDF 文件。

## 導入命名空間
首先，導入必要的命名空間來存取所需的類別和方法：
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using System.IO;
using System;
```
## 第 1 步：載入 PDF 文檔
```csharp
string documentPath = "YourDocumentPath";
string outputDirectory = "YourDocumentDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 步驟 2： 取得 PDF 內容並迭代頁面
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfPage page in pdfContent.Pages)
    {
```
## 第 3 步：迭代註釋並檢查文字格式
```csharp
        for (int i = page.Annotations.Count - 1; i >= 0; i--)
        {
            foreach (FormattedTextFragment fragment in page.Annotations[i].FormattedTextFragments)
            {
```
## 步驟 4：刪除具有特定文字格式的註釋
```csharp
                if (fragment.Font.FamilyName == "Verdana")
                {
                    page.Annotations.RemoveAt(i);
                    break;
                }
            }
        }
    }
```
## 步驟5：儲存修改後的PDF文檔
```csharp
    watermarker.Save(outputFileName);
}
```
現在，您已使用 Groupdocs.Watermark for .NET 成功從 PDF 文件中刪除了具有特定文字格式的註解。

## 結論
Groupdocs.Watermark for .NET 為處理 PDF 文件中的註解和其他元素提供了便捷的解決方案。透過遵循本教程，您可以輕鬆地基於特定文字格式操作註釋，從而增強 PDF 文件的可讀性和外觀。
## 常見問題解答
### 我可以將 Groupdocs.Watermark for .NET 與其他文件格式一起使用嗎？
是的，Groupdocs.Watermark 支援各種文件格式，包括 DOCX、PPTX、XLSX、PDF 等。
### Groupdocs.Watermark for .NET 是否有免費試用版？
是的，您可以存取 Groupdocs.Watermark for .NET 的免費試用版：[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到 Groupdocs.Watermark for .NET 的文件？
您可以找到詳細的文件和 API 參考[這裡](https://reference.groupdocs.com/Watermark/net/).
### 對於與 Groupdocs.Watermark 相關的任何問題或查詢，如何獲得支援？
您可以在 Groupdocs.Watermark 論壇上發布您的疑問或問題[這裡](https://forum.groupdocs.com/c/watermark/19).
### 我可以購買 Groupdocs.Watermark for .NET 的臨時授權嗎？
是的，您可以從以下位置購買臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).