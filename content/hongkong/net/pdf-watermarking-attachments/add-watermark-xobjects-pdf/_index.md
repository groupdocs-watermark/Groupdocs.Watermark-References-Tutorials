---
title: 在 PDF 中的 XObject 新增浮水印
linktitle: 在 PDF 中的 XObject 新增浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 將浮水印新增至 PDF 中的 XObject。請遵循我們的逐步指南以輕鬆實施。
type: docs
weight: 20
url: /zh-hant/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## 介紹
為 PDF 新增浮水印是確保您的文件免遭未經授權使用的關鍵步驟。借助 Groupdocs.Watermark for .NET，在 PDF 中的 XObject 新增浮水印從未如此簡單。在本教程中，我們將逐步引導您完成流程，確保您可以自信地將浮水印套用到 PDF 文件。讓我們開始吧！
## 先決條件
在深入學習本教程之前，讓我們確保您擁有無縫學習所需的一切：
-  Groupdocs.Watermark for .NET：從以下位置下載並安裝最新版本[這裡](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework：確保您的開發電腦上安裝了 .NET Framework。
- 開發環境：使用Visual Studio或任何其他支援.NET開發的IDE。
- 臨時許可證：取得[臨時執照](https://purchase.groupdocs.com/temporary-license/)如果您正在評估產品。
滿足這些先決條件後，您就可以開始為 PDF 添加浮水印了。
## 導入命名空間
首先，您需要在專案中匯入必要的命名空間。開啟您的 C# 專案並新增以下 using 指令：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：設定文檔路徑
第一步涉及設定文檔的路徑。定義 PDF 所在的路徑以及要儲存帶有浮水印的 PDF 的位置。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`與您機器上的實際路徑。
## 步驟 2：初始化 PDF 載入選項
接下來，您需要初始化 PDF 載入選項。這對於正確載入 PDF 內容至關重要。
```csharp
var loadOptions = new PdfLoadOptions();
```
## 第 3 步：載入 PDF 文檔
使用載入選項，載入 PDF 文檔`Watermarker`班級。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 第四步：建立浮水印
現在，您需要建立將新增至 PDF 的浮水印。在本教程中，我們將建立文字浮水印。
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## 第 5 步：向 XObject 新增浮水印
迭代 PDF 中的每個頁面和每個 XObject 以套用浮水印。
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            //為影像添加浮水印
            xObject.Image.Add(watermark);
        }
    }
}
```
## 步驟 6：儲存有浮水印的 PDF
最後，將帶有浮水印的PDF儲存到指定的輸出檔案中。
```csharp
    watermarker.Save(outputFileName);
}
```
現在你就得到它了！現在，您的 PDF 的所有 XObject 上都包含浮水印。
## 結論
使用 Groupdocs for .NET 在 PDF 文件中新增浮水印是一個簡單的過程，可提供額外的安全層。透過遵循本教學中概述的步驟，您可以確保您的文件免受未經授權的使用。請記住，您可以隨時參考[文件](https://reference.groupdocs.com/Watermark/net/)了解更多詳細資訊和進階功能。
## 常見問題解答
### 我可以使用圖像而不是文字作為浮水印嗎？
是的，Groupdocs.Watermark for .NET 支援文字和影像浮水印。
### 如何在不購買 Groupdocs.Watermark 的情況下測試它？
您可以使用[臨時執照](https://purchase.groupdocs.com/temporary-license/)來評估產品。
### 是否可以自訂浮水印的外觀？
絕對地！您可以自訂字體、大小、旋轉角度等。
### Groupdocs.Watermark 支援其他文件格式嗎？
是的，它支援多種格式，包括 Word、Excel 和 PowerPoint。
### 如果遇到問題，我可以在哪裡獲得支援？
您可以從以下方面獲得支持[群組文檔論壇](https://forum.groupdocs.com/c/watermark/19).