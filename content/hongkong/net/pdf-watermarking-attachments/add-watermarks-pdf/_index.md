---
title: 為 PDF 新增浮水印
linktitle: 為 PDF 新增浮水印
second_title: GroupDocs.Watermark .NET API
description: 透過我們全面的逐步指南，了解如何使用 GroupDocs.Watermark for .NET 將文字和影像浮水印新增至 PDF。
weight: 14
url: /zh-hant/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## 介紹
您是否希望在 PDF 中添加浮水印以保護您的文件或在其上添加您的徽標？別再猶豫了！在本教學中，我們將深入探討使用 GroupDocs.Watermark for .NET 將文字和影像浮水印新增至 PDF 檔案的過程。無論您是經驗豐富的開發人員還是新手，本指南都將引導您完成每個步驟，確保您可以輕鬆且精確地套用浮水印。
## 先決條件
在開始之前，讓我們確保您已掌握本教學所需的一切：
-  GroupDocs.Watermark for .NET：確保您安裝了最新版本。你可以[在這裡下載](https://releases.groupdocs.com/Watermark/net/).
- .NET 開發環境：Visual Studio 或任何其他支援 .NET 的 IDE。
- C# 基礎知識：了解 C# 程式設計基礎將幫助您輕鬆執行以下步驟。
- PDF 文件：準備好用於新增浮水印的範例 PDF 文件。
- 浮水印影像：如果您要新增影像浮水印，請準備好影像檔案。
## 導入命名空間
首先，您需要在 C# 專案中匯入必要的命名空間。這將允許您存取 GroupDocs.Watermark 功能。
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
現在，讓我們將該流程分解為可管理的步驟。
## 第 1 步：載入您的 PDF 文檔
第一步是將 PDF 文件載入到浮水印中。您可以這樣做：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //進一步的步驟將在此處添加
}
```
## 步驟 2：在首頁新增文字浮水印
接下來，我們將在 PDF 的第一頁添加文字浮水印。請遵循以下說明：
```csharp
//在首頁加入文字浮水印
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

新增文字浮水印可以幫助保護您的文件免遭未經授權的使用或簡單地對其進行品牌化。想像一下，在您的文件上蓋上隱形的真實性印章。
## 步驟 3：將影像浮水印新增至第二頁
現在，讓我們為第二頁添加圖像浮水印。這對於徽標或任何圖形浮水印特別有用。
```csharp
//第二頁新增圖片浮水印
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

影像浮水印可以使您的文件看起來很專業，並確保您的品牌始終可見。這就像在每一頁上添加您的簽名一樣。
## 步驟 4：儲存有浮水印的 PDF
新增浮水印後，最後一步是將帶有浮水印的 PDF 儲存到您想要的位置。
```csharp
watermarker.Save(outputFileName);
```
儲存文件將完成您所做的所有變更。這是您的努力被固化為有形結果、可供使用或分發的時刻。
## 結論
恭喜！您已使用 GroupDocs.Watermark for .NET 成功將文字和影像浮水印新增至 PDF 。這個過程不僅簡單，而且可以高度客製化以滿足您的特定需求。無論您是要保護文件還是對其進行品牌化，水印都是您可以使用的強大工具。
## 常見問題解答
### 我可以在同一頁面上新增多個浮水印嗎？
是的，您可以透過呼叫下列方法來為同一頁面新增多個浮水印`Add`使用不同的水印物件多次方法。
### 如何自訂文字浮水印的外觀？
您可以使用以下命令調整字體、大小、顏色和不透明度等屬性來自訂文字浮水印`TextWatermark`目的。
### 是否可以僅在 PDF 的特定頁面上新增浮水印？
是的，您可以透過設定來指定要新增浮水印的頁面`PageIndex`財產在`PdfArtifactWatermarkOptions`.
### 我可以從 PDF 中移除浮水印嗎？
是的，GroupDocs.Watermark 提供了在 PDF 文件中搜尋和刪除浮水印的功能。
### 如何取得 GroupDocs.Watermark 的臨時授權？
您可以透過訪問獲得臨時許可證[臨時許可證頁面](https://purchase.groupdocs.com/temporary-license/).