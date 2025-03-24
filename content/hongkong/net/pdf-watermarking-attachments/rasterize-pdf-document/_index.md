---
title: 光柵化 PDF 文件
linktitle: 光柵化 PDF 文件
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 光柵化 PDF 文件。輕鬆增強文件安全性和視覺吸引力。
weight: 27
url: /zh-hant/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## 介紹
在文件管理和操作領域，GroupDocs.Watermark for .NET 是一款強大的工具，提供強大的功能來新增、刪除和搜尋各種文件格式的浮水印。無論是使用版權聲明保護您的文件、添加企業徽標以進行品牌推廣，還是只是使用圖章對文件進行註釋，GroupDocs.Watermark 都可以透過其直觀的 API 和廣泛的功能集簡化流程。
## 先決條件
在使用 GroupDocs.Watermark for .NET 深入研究水印世界之前，請確保滿足以下先決條件：
### 1.安裝.NET框架
確保您的開發電腦上安裝了 .NET Framework。您可以從 Microsoft 網站下載它或使用您喜歡的套件管理器。
#### 第 1 步：下載 .NET Framework
造訪 Microsoft .NET Framework 下載頁面。
#### 第 2 步：安裝 .NET Framework
請依照下載頁面上提供的安裝說明在您的系統上安裝 .NET Framework。
### 2. 取得GroupDocs.Watermark許可證
要利用 GroupDocs.Watermark 的全部功能，您需要有效的許可證。您可以購買許可證或取得臨時許可證以進行評估。
#### 第 1 步：取得許可證
造訪 GroupDocs.Watermark 購買頁面。
#### 第 2 步：購買或取得臨時許可證
根據您的需求選擇適當的許可選項 - 購買許可證以繼續使用或取得臨時許可證以進行評估。

## 導入命名空間
在開始為文件添加浮水印之前，請確保匯入必要的命名空間以無縫存取 GroupDocs 的功能。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

現在您已完成所有設置，讓我們深入研究使用 GroupDocs.Watermark for .NET 對 PDF 文件進行光柵化。光柵化將 PDF 文件的每一頁轉換為光柵影像格式，例如 PNG。
## 第 1 步：初始化變數
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
確保將「您的文件路徑」和「您的文件目錄」分別替換為 PDF 文件的實際路徑和所需的輸出目錄。
## 步驟2：載入文件並新增浮水印
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //初始化圖像或文字浮水印
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    //先添加任意類型的浮水印
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    //光柵化所有頁面
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    //所有頁面的內容均替換為光柵圖像
    watermarker.Save(outputFileName);
}
```
在此步驟中，我們載入 PDF 文件並使用指定屬性（例如文字、字體、對齊方式、旋轉角度、尺寸類型、比例因子和不透明度）初始化文字浮水印。然後，我們將浮水印新增到文件中。接下來，我們檢索 PDF 文件的內容並將所有頁面光柵化為 100 DPI 解析度的 PNG 格式。最後，我們用柵格化內容保存修改後的文件。

## 結論
GroupDocs.Watermark for .NET 提供了一個全面的解決方案，可以輕鬆地將浮水印新增至各種文件格式。透過遵循本教學中概述的步驟，您可以有效地光柵化 PDF 文件並增強其安全性和視覺吸引力。
## 常見問題解答
### GroupDocs.Watermark 是否與 PDF 以外的其他文件格式相容？
是的，GroupDocs.Watermark 支援多種文件格式，包括 Microsoft Word、Excel、PowerPoint、Visio、Outlook 等。
### 我可以自訂使用 GroupDocs.Watermark 添加的水印的外觀嗎？
絕對地！ GroupDocs.Watermark 提供了自訂浮水印屬性的廣泛選項，例如文字、字體、顏色、大小、不透明度、旋轉和位置。
### GroupDocs.Watermark 是否提供批次支援？
是的，您可以使用 Watermark 以批次模式輕鬆處理多個文檔，從而節省為大量文件添加浮水印的時間和精力。
### GroupDocs.Watermark 是否有試用版？
是的，您可以從網站下載 GroupDocs.Watermark 的免費試用版，以便在購買前評估其功能。
### 如果我遇到任何問題或對 GroupDocs.Watermark 有疑問，如何獲得協助？
您可以造訪 GroupDocs.Watermark 論壇尋求社群支援或聯絡 GroupDocs 支援團隊尋求協助。