---
title: 取得支援的文件格式
linktitle: 取得支援的文件格式
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs.Watermark for .NET 輕鬆地在文件中新增浮水印。請遵循我們全面的逐步指南來保護您的數位資產。
weight: 13
url: /zh-hant/net/document-manipulation/get-supported-file-formats/
type: docs
---
# 取得支援的文件格式

## 介紹
對文件加浮水印是保護數位資產的關鍵一步。無論是為了保護智慧財產權、確保機密性還是僅僅為了品牌宣傳，水印都扮演著至關重要的角色。如果您是 .NET 開發人員，希望將浮水印功能整合到您的應用程式中，那麼 GroupDocs.Watermark for .NET 是您應該考慮的強大且多功能的工具。本教學將引導您了解使用 GroupDocs.Watermark 的基本知識，從安裝到應用第一個浮水印，分解每個步驟以確保您可以輕鬆遵循。
## 先決條件
在我們深入了解具體細節之前，讓我們確保您已具備開始使用所需的一切：
1.  Visual Studio：確保您的電腦上安裝了 Visual Studio。您可以從[視覺工作室網站](https://visualstudio.microsoft.com/).
2. .NET Framework：GroupDocs.Watermark 支援各種版本的 .NET Framework。確保您的專案面向相容版本。
3. GroupDocs.Watermark for .NET：您可以從以下位置下載最新版本：[發布頁面](https://releases.groupdocs.com/Watermark/net/).
4. C# 基礎：本教學假設您對 C# 和 .NET 開發有基本的了解。
## 導入命名空間
首先，讓我們在專案中導入必要的命名空間。開啟 C# 檔案並在頂部新增以下 using 指令：
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
匯入這些命名空間後，您就可以開始在文件中新增浮水印了。

## 第 1 步：初始化浮水印引擎
第一步是初始化水印引擎。這涉及到創建一個實例`Watermarker`類別與您想要加浮水印的文件。
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
此程式碼片段設定`Watermarker`對象，您將使用該對象將浮水印套用到文件。
## 步驟2：新增文字浮水印
現在，讓我們為您的文件添加一個簡單的文字浮水印。文字浮水印非常適合添加“機密”或“草稿”等標籤。
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
在這裡，我們創建了一個`TextWatermark`文字為「機密」的對象，設定其字體和顏色，並將其與文件的中心對齊。
## 步驟 3：新增影像浮水印
如果您喜歡使用影像作為浮水印，GroupDocs.Watermark 可以輕鬆實現這一點。
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
在這個例子中，我們創建一個`ImageWatermark`對象，設定其尺寸，並將其與文件的右上角對齊。
## 步驟 4：儲存文檔
新增所需的浮水印後，最後一步是儲存修改後的文件。
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
這會將帶有浮水印的文件儲存到指定路徑並釋放其使用的所有資源`Watermarker`實例。
## 第 5 步：取得支援的文件格式
若要查看 GroupDocs.Watermark 支援哪些檔案格式，您可以使用以下程式碼片段：
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
這將列印出 GroupDocs.Watermark 可以處理的所有檔案類型，讓您全面了解其功能。
## 結論
使用 GroupDocs for .NET 對文件添加浮水印既簡單又有效率。透過學習本教程，您已了解如何初始化浮水印引擎、添加文字和圖像浮水印、保存帶有浮水印的文檔以及列出支援的文件格式。借助這些工具，您可以放心地保護您的文件。
如果您有任何疑問或需要進一步協助，請隨時訪問[GroupDocs.Watermark 支援論壇](https://forum.groupdocs.com/c/watermark/19).
## 常見問題解答
### 如何安裝 GroupDocs.Watermark for .NET？
您可以從[發布頁面](https://releases.groupdocs.com/Watermark/net/)並將 DLL 新增至您的專案中。
### 我可以免費試用 GroupDocs.Watermark 嗎？
是的，您可以請求[免費試用](https://releases.groupdocs.com/)在購買前評估軟體。
### GroupDocs.Watermark 支援哪些檔案格式？
您可以使用提供的程式碼片段列出所有支援的文件格式。
### 如何購買 GroupDocs.Watermark 的授權？
許可證可以直接從[購買頁面](https://purchase.groupdocs.com/buy).
### 有適用於 GroupDocs.Watermark 的任何文件嗎？
是的，提供全面的文檔[這裡](https://tutorials.groupdocs.com/Watermark/net/).