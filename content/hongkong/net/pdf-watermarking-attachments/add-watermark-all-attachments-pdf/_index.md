---
title: 為 PDF 中的所有配件添加浮水印
linktitle: 為 PDF 中的所有配件添加浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 為 PDF 附件新增浮水印。使用自訂浮水印輕鬆保護您的文件。
weight: 16
url: /zh-hant/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## 介紹
在 PDF 附件中新增浮水印可能是文件管理中的關鍵步驟，尤其是在確保安全或品牌時。 GroupDocs.Watermark for .NET 提供了將浮水印無縫嵌入 PDF 檔案的全面解決方案。在本教程中，我們將指導您完成使用 GroupDocs.Watermark for .NET 為 PDF 文件中的所有附件添加浮水印的過程。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1.  GroupDocs.Watermark for .NET：如果您還沒有安裝 GroupDocs.Watermark for .NET，請從[網站](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：使用 Visual Studio 或任何其他 .NET 相容 IDE 設定合適的開發環境。
3. PDF 文件：準備要新增浮水印的 PDF 文件以及要新增浮水印的附件。

## 導入命名空間
在深入研究程式碼之前，請確保匯入必要的命名空間以存取 GroupDocs.Watermark 的 .NET 功能：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 步驟1：定義文檔路徑和輸出目錄
首先，定義輸入 PDF 文件的路徑以及儲存帶有浮水印文件的目錄：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 步驟2：初始化載入選項和浮水印
接下來，初始化 PDF 文件的載入選項並建立文字浮水印：
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## 第 3 步：載入文件和附件
載入 PDF 文件並遍歷其附件：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## 第 4 步：檢查附件支持
檢查附件是否受 GroupDocs.Watermark 支援：
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## 第 5 步：為附件添加浮水印
加載附件並添加浮水印：
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## 第 6 步：儲存更改
最後，儲存對帶有浮水印的 PDF 文件的變更：
```csharp
    watermarker.Save(outputFileName);
}
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Watermark for .NET 為 PDF 文件中的所有附件新增浮水印。透過遵循逐步指南，您可以將浮水印無縫整合到 PDF 文件中，確保文件安全和品牌。
## 常見問題解答
### 我可以自訂浮水印的外觀嗎？
是的，您可以根據您的要求自訂浮水印的文字、字體、大小、顏色和位置等各個方面。
### GroupDocs.Watermark 是否支援 PDF 以外的其他文件格式？
是的，GroupDocs.Watermark 支援多種文件格式，包括 Microsoft Word、Excel、PowerPoint、Visio、Outlook 和圖片。
### GroupDocs.Watermark 是否有試用版？
是的，您可以透過從網站下載免費試用版來探索 GroupDocs.Watermark 的功能。
### 我可以在單一文件中添加多個浮水印嗎？
當然，GroupDocs.Watermark 允許您同時添加多個浮水印，包括文字、圖像和註釋，以增強文件安全性和品牌形象。
### GroupDocs.Watermark 用戶可以獲得技術支援嗎？
是的，GroupDocs 透過論壇和專門的支援管道提供全面的技術支持，以幫助用戶解決可能遇到的任何疑問或問題。