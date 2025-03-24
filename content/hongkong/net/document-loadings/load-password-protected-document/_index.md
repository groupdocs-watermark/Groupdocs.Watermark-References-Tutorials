---
title: 載入受密碼保護的文檔
linktitle: 載入受密碼保護的文檔
second_title: GroupDocs.Watermark .NET API
description: 透過我們的逐步指南，了解如何使用 Groupdocs for .NET 將浮水印新增至受密碼保護的文件。輕鬆保護您的文件並為其建立品牌。
weight: 13
url: /zh-hant/net/document-loadings/load-password-protected-document/
---

# 載入受密碼保護的文檔

## 介紹
您是否希望透過添加浮水印來保護您的文檔，即使它們受密碼保護？ Groupdocs.Watermark for .NET 是一個功能強大的工具，可以讓您做到這一點。在本教學中，我們將指導您完成載入受密碼保護的文件並使用 Groupdocs.Watermark for .NET 新增浮水印的過程。讓我們深入了解吧！
## 先決條件
在我們開始之前，請確保您具備以下條件：
1. Visual Studio：電腦上安裝的任何版本的 Visual Studio。
2. .NET Framework：確保您擁有 .NET Framework 4.6.1 或更高版本。
3. Groupdocs.Watermark for .NET：從以下位置下載並安裝 Groupdocs.Watermark for .NET 函式庫：[下載連結](https://releases.groupdocs.com/Watermark/net/).
## 導入命名空間
首先，我們需要將必要的命名空間匯入到我們的專案中。這確保了我們可以存取 Groupdocs.Watermark for .NET 提供的所有方法和屬性。
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
現在，讓我們將該過程分解為簡單、易於遵循的步驟。
## 第 1 步：設定您的項目
首先，在 Visual Studio 中建立一個新的 C# 控制台應用程式。設定專案後，透過 NuGet 套件管理器安裝 Groupdocs.Watermark for .NET 函式庫。
1. 開啟 Visual Studio 並建立一個新的控制台應用程式 (.NET Framework)。
2. 去`Tools`>`NuGet Package Manager`>`Manage NuGet Packages for Solution`.
3. 搜尋`GroupDocs.Watermark`並安裝該軟體包。
## 第 2 步：定義文檔路徑
接下來，您需要定義受密碼保護的文件的路徑以及保存帶有浮水印的文件的輸出文件路徑。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`與您機器上的實際路徑。
## 第 3 步：使用密碼設定載入選項
若要開啟受密碼保護的文檔，您必須在載入選項中提供密碼。
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
代替`"P@$w0rd"`使用您文件的實際密碼。
## 第 4 步：載入文檔
現在，讓我們使用以下命令來載入文檔`Watermarker`班級。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //添加浮水印的程式碼將位於此處
}
```
## 第 5 步：建立浮水印
我們將建立一個可以新增到文件中的文字浮水印。您可以根據需要自訂文字、字體、大小和其他屬性。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
隨意改變`"Test watermark"`, `"Arial"`， 和`12`您喜歡的文字、字體和大小。
## 第6步：新增浮水印
使用以下命令將浮水印新增至文件中`Add`的方法`Watermarker`班級。
```csharp
watermarker.Add(watermark);
```
## 步驟7：保存有浮水印的文檔
最後將加浮水印的文檔儲存到指定的輸出檔案路徑。
```csharp
watermarker.Save(outputFileName);
```
## 結論
使用 Groupdocs for .NET，在受密碼保護的文件中添加浮水印的過程非常簡單。透過執行這些簡單的步驟，您可以確保您的文件根據您的要求受到保護和標記。無論是出於安全、品牌還是合規性的考慮，為文件添加浮水印從未如此簡單。
## 常見問題解答
### 我可以使用 Groupdocs.Watermark for .NET 新增影像浮水印嗎？
是的，您可以添加文字和圖像浮水印。只需使用`ImageWatermark`類別而不是`TextWatermark`.
### 是否可以從文件中刪除浮水印？
是的，Groupdocs.Watermark for .NET 提供了搜尋和刪除浮水印的方法。
### Groupdocs.Watermark for .NET 是否支援 PDF 以外的其他文件格式？
是的，它支援多種格式，包括 Word、Excel、PowerPoint 等。
### 我可以自訂浮水印的外觀嗎？
絕對地！您可以自訂字體、大小、顏色、不透明度等。
### 如果遇到問題，我可以在哪裡獲得支援？
您可以訪問[Groupdocs 支援論壇](https://forum.groupdocs.com/c/watermark/19)尋求幫助和指導。