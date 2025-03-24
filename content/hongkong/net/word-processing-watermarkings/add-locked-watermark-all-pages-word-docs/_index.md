---
title: 在 Word 文件中的所有頁面中新增鎖定浮水印
linktitle: 在 Word 文件中的所有頁面中新增鎖定浮水印
second_title: GroupDocs.Watermark .NET API
description: 使用 Groupdocs.Watermark for .NET 新增鎖定浮水印來保護您的文件。請遵循我們的逐步指南以輕鬆實施。
weight: 11
url: /zh-hant/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---
## 介紹
在文件中添加浮水印是保護內容並打造品牌的重要一步。無論您是要防止未經授權的使用還是只是添加專業風格，水印都可以發揮多種作用。在本教學中，我們將引導您完成使用 Groupdocs.Watermark for .NET 將鎖定浮水印新增至 Word 文件的所有頁面的過程。
## 先決條件
在我們深入了解逐步指南之前，讓我們確保您擁有所需的一切：
1. Groupdocs.Watermark for .NET：從以下位置下載最新版本[這裡](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
3. 開發環境：Visual Studio等開發環境。
4. 許可證：您可以選擇[免費試用](https://releases.groupdocs.com/)或購買一個[臨時執照](https://purchase.groupdocs.com/temporary-license/).
## 導入命名空間
首先，您需要在專案中匯入必要的命名空間。這些對於存取 Groupdocs.Watermark 提供的類別和方法至關重要。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：設定您的項目

開啟您的開發環境並建立一個新的.NET 專案。這可以是控制台應用程式或適合您需求的任何其他類型。

您需要將 Groupdocs.Watermark 套件新增至您的專案。這可以透過 NuGet 套件管理器來完成。在 NuGet 套件管理器控制台中執行以下命令：
```sh
Install-Package GroupDocs.Watermark
```
## 步驟2：載入Word文檔
### 定義文檔路徑
指定 Word 文件的路徑。這將是您要新增浮水印的文件。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### 設定載入選項
建立一個實例`WordProcessingLoadOptions`使用特定選項載入 Word 文件。
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 第 3 步：建立浮水印
### 初始化浮水印
使用`Watermarker`類，使用指定的載入選項載入文件。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //進一步的步驟將在此 using 區塊內
}
```
### 定義浮水印屬性
創建一個`TextWatermark`包含您想要的文字、字體和顏色的實例。
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 步驟 4：將浮水印套用到所有頁面
### 設定浮水印選項
定義`WordProcessingWatermarkPagesOptions`並設定`IsLocked`屬性設定為 true 以鎖定浮水印。這確保了水印不能輕易被刪除。
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### 可選：新增密碼保護
如果您想新增額外的安全層，可以為浮水印設定密碼。
```csharp
//用密碼保護
//選項.密碼 = "7654321";
```
### 添加浮水印
使用`Add`的方法`Watermarker`類，使用指定的選項將浮水印添加到文件中。
```csharp
watermarker.Add(watermark, options);
```
## 第 5 步：儲存文檔
最後將修改後的文檔儲存到指定的輸出檔案。
```csharp
watermarker.Save(outputFileName);
```

## 結論
透過執行以下步驟，您可以使用 Groupdocs.Watermark for .NET 輕鬆地將鎖定浮水印新增至 Word 文件的所有頁面。這不僅有助於保護您的文件免於未經授權的使用，還可以為您的內容增添專業氣息。 Groupdocs.Watermark 提供了滿足水印需求的全面解決方案，確保您的文件保持安全和品牌化。
## 常見問題解答
### 我可以使用圖像而不是文字作為浮水印嗎？
是的，Groupdocs 支援文字和圖像浮水印。您可以更換`TextWatermark`和`ImageWatermark`並指定您的圖像。
### 可以自訂浮水印的位置嗎？
絕對地！您可以使用下列屬性設定浮水印的位置`HorizontalAlignment`和`VerticalAlignment`.
### 我可以在文件的不同頁面套用不同的浮水印嗎？
是的，您可以使用以下命令為特定頁面自訂浮水印`PageIndex`財產在`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark 是否支援 Word 以外的其他文件格式？
是的，Groupdocs 支援多種格式，包括 PDF、Excel、PowerPoint 等。
### 使用 Groupdocs.Watermark 有哪些系統需求？
您需要一個安裝了.NET Framework的系統和一個像Visual Studio這樣的開發環境。