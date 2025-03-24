---
title: 為 PDF 影像添加浮水印
linktitle: 為 PDF 影像添加浮水印
second_title: GroupDocs.Watermark .NET API
description: 透過我們詳細的逐步教學，了解如何使用 GroupDocs.Watermark for .NET 在 PDF 文件中的影像添加浮水印。輕鬆保護您的 PDF。
weight: 19
url: /zh-hant/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## 介紹
在 PDF 文件中的圖像添加浮水印對於保護您的智慧財產權或確保文件的真實性至關重要。使用 GroupDocs.Watermark for .NET，可以有效率且輕鬆地完成此任務。本教學將引導您完成流程的每個步驟，從設定環境到新增浮水印再到保存最終文件。讓我們深入了解吧！
## 先決條件
在我們開始之前，請確保您具備以下條件：
1. Visual Studio：安裝 Visual Studio，即 .NET 應用程式的整合開發環境 (IDE)。
2.  GroupDocs.Watermark for .NET：從以下位置下載並安裝 GroupDocs.Watermark for .NET 函式庫：[發布頁面](https://releases.groupdocs.com/Watermark/net/).
3. PDF 文件：準備好包含影像的 PDF 文件以測試浮水印功能。
4. 臨時許可證：取得[臨時執照](https://purchase.groupdocs.com/temporary-license/)如果您正在評估產品。
## 導入命名空間
首先，請確保您的專案中導入了必要的命名空間。這將包括處理 PDF 文件和浮水印所需的核心命名空間。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 步驟1：設定文檔路徑和輸出目錄
首先，定義輸入文件的路徑和儲存帶有浮水印文件的輸出目錄。此步驟對於確保您的程式知道在哪裡找到來源文件以及在哪裡儲存處理後的文件至關重要。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 第 2 步：載入 PDF 文檔
接下來，您需要使用以下命令載入 PDF 文檔`PdfLoadOptions`。此類別可讓您指定載入 PDF 的選項，例如必要時的密碼保護。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //您的浮水印代碼將位於此處
}
```
## 第 3 步：建立浮水印
現在，初始化浮水印。在此範例中，我們將建立一個文字浮水印，內容為「受保護的圖像」。根據您的需求自訂字體、對齊方式、旋轉和縮放。
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 第 4 步：存取 PDF 內容
檢索 PDF 文件的內容。具體來說，我們需要存取 PDF 中的圖像。在這裡，我們將重點放在第一頁，但您可以根據需要將其擴展到其他頁面。
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
//取得第一頁的所有圖像
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## 步驟5：將浮水印應用到影像上
循環瀏覽第一頁上找到的每個圖像並套用浮水印。這可確保指定頁面上的所有影像都將套用浮水印。
```csharp
//為所有找到的圖像添加浮水印
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## 步驟 6：儲存有浮水印的文檔
最後，將帶有浮水印的PDF儲存到指定的輸出目錄。此步驟透過將變更寫入新檔案來完成此過程。
```csharp
watermarker.Save(outputFileName);
```
## 結論
現在你就得到它了！使用 GroupDocs for .NET 為 PDF 中的影像添加浮水印是一個簡單的過程，可以大大增強文件的安全性和真實性。透過執行這些步驟，您可以確保您的智慧財產權受到保護並且您的文件安全。
## 常見問題解答
### 什麼是 .NET 的 GroupDocs.Watermark？
GroupDocs.Watermark for .NET 是一個綜合資料庫，可讓開發人員新增、搜尋和刪除各種文件格式（包括 PDF）的浮水印。
### 我可以使用 GroupDocs.Watermark 添加文字和圖像浮水印嗎？
是的，GroupDocs.Watermark 支援文字和圖像浮水印，為不同類型的水印需求提供靈活性。
### 是否可以在 PDF 的多個頁面上新增浮水印？
絕對地！您可以循環瀏覽 PDF 中的每個頁面，並將浮水印套用到每個頁面上的圖像。
### 我需要許可證才能使用 GroupDocs.Watermark for .NET 嗎？
是的，需要許可證。您可以獲得[臨時執照](https://purchase.groupdocs.com/temporary-license/)出於評估目的。
### 在哪裡可以找到更多關於 GroupDocs.Watermark for .NET 的文件？
您可以在以下位置找到全面的文檔[GroupDocs.Watermark 文件頁面](https://tutorials.groupdocs.com/Watermark/net/).