---
title: 從串流載入文檔
linktitle: 從串流載入文檔
second_title: GroupDocs.Watermark .NET API
description: 透過本指南了解如何使用 GroupDocs.Watermark for .NET 為文件添加浮水印。非常適合希望增強文件安全性的開發人員。
weight: 11
url: /zh-hant/net/document-loadings/load-document-from-stream/
type: docs
---
# 從串流載入文檔

## 介紹
您是否希望使用 .NET 為文件無縫添加浮水印？別再猶豫了！ GroupDocs.Watermark for .NET 是一個功能強大且易於使用的程式庫，可讓您管理各種文件格式的浮水印。無論您是處理 PDF、Word 文件還是影像，此工具都能滿足您的需求。在本教程中，我們將引導您逐步完成從流程載入文件並新增浮水印的過程。那麼，就讓我們開始吧！
## 先決條件
在我們開始之前，請確保您已進行以下設定：
1. Visual Studio：任何最新版本的 Visual Studio 都可以正常運作。
2. .NET Framework：確保您已安裝 .NET Framework 4.0 或更高版本。
3.  GroupDocs.Watermark for .NET：您可以從以下位置下載：[這裡](https://releases.groupdocs.com/Watermark/net/).
4. C# 基礎知識：熟悉 C# 和物件導向程式設計概念將會有所幫助。

## 導入命名空間
要在專案中使用 GroupDocs.Watermark，您需要匯入必要的命名空間。這將使您能夠毫無問題地存取該庫的功能。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 第 1 步：設定您的項目
首先，您需要在 Visual Studio 中設定專案。操作方法如下：
1. 建立新專案：開啟 Visual Studio 並建立一個新的 C# 控制台應用程式專案。
2. 安裝 GroupDocs.Watermark：透過 NuGet 套件管理器安裝 GroupDocs.Watermark 函式庫。只需搜尋`GroupDocs.Watermark`並安裝它。
## 第 2 步：定義文檔路徑
接下來，您需要定義文件的路徑以及將保存帶有浮水印的文檔的輸出檔案。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
代替`"Your Document Path"`與您想要加水印的文件的實際路徑和`"Your Document Directory"`與要儲存有浮水印的文件的目錄。
## 第 3 步：從流程載入文檔
現在，讓我們從流中載入文件。這涉及以流的形式打開文檔，然後使用`Watermarker`GroupDocs.Watermark 庫中的類別來管理它。
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    //您管理浮水印的程式碼將位於此處
}
```
此程式碼片段確保文件作為流打開並且`Watermarker`類別是用該流初始化的。這`using`聲明確保資源在使用後得到妥善處置。
## 第 4 步：建立並新增浮水印
使用 GroupDocs.Watermark 建立浮水印非常簡單。在此範例中，我們將建立一個簡單的文字浮水印。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
在這裡，我們創建一個`TextWatermark`物件包含文字「測試浮水印」並指定字體詳細資訊。然後，我們使用以下命令將此浮水印新增至文件中`Add`的方法`Watermarker`班級。
## 步驟5：保存有浮水印的文檔
最後將加浮水印的文檔儲存到指定的輸出路徑。
```csharp
watermarker.Save(outputFileName);
```
此程式碼保存帶有新添加的浮水印的文檔`outputFileName`您之前定義的路徑。

## 結論
恭喜！您已使用 GroupDocs.Watermark for .NET 成功地在文件中新增浮水印。該庫使管理各種文件格式的浮水印變得非常容易。無論您需要添加文字、圖像或其他類型的浮水印，GroupDocs.Watermark 都有您需要的工具。不要忘記查看[文件](https://tutorials.groupdocs.com/Watermark/net/)了解更多進階功能和自訂選項。
## 常見問題解答
### 我可以使用 GroupDocs.Watermark for .NET 新增哪些類型的浮水印？
您可以添加文字浮水印、圖像浮水印，甚至複雜的形狀和標誌。該庫支援廣泛的自訂選項。
### 我可以使用 GroupDocs.Watermark 從文件中刪除浮水印嗎？
是的，GroupDocs.Watermark 還允許您從文件中刪除現有的水印。
### GroupDocs.Watermark 是否有免費試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 如何購買 GroupDocs.Watermark 的授權？
您可以直接從[集團文件網站](https://purchase.groupdocs.com/buy).
### 如果遇到問題，我可以在哪裡獲得支援？
如需支持，您可以訪問[GroupDocs.Watermark 支援論壇](https://forum.groupdocs.com/c/watermark/19).