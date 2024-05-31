---
title: 將鎖定浮水印新增至 Word 文件中的部分
linktitle: 將鎖定浮水印新增至 Word 文件中的部分
second_title: GroupDocs.Watermark .NET API
description: 透過這份全面的逐步指南，了解如何使用 Groupdocs for .NET 將鎖定浮水印新增至 Word 文件中的特定部分。
type: docs
weight: 13
url: /zh-hant/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---
## 介紹
您是否正在尋找一種向 Word 文件中的某個部分添加鎖定浮水印的有效方法？別再猶豫了！使用 Groupdocs.Watermark for .NET，您可以將浮水印無縫插入 Word 文檔，同時確保它們保持鎖定和防篡改。這個強大的工具提供了多種功能來滿足您的浮水印需求，無論是出於品牌、保密還是安全目的。在本逐步教學中，我們將引導您了解如何使用 Groupdocs.Watermark for .NET 將鎖定浮水印新增至 Word 文件的特定部分。讓我們深入了解吧！
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1.  Groupdocs.Watermark for .NET：確保您已安裝 Groupdocs.Watermark 庫。你可以下載它[這裡](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework：確保您的開發環境中設定了 .NET Framework。
3. IDE：使用整合開發環境 (IDE)，例如 Visual Studio。
4. 文件：用於套用浮水印的 Word 文件 (.docx)。
## 導入命名空間
首先，您需要在專案中匯入必要的命名空間。操作方法如下：
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入您的文檔
首先，您需要載入要新增浮水印的文件。此步驟涉及指定文件的路徑並使用`Watermarker`班級。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //您的浮水印代碼將位於此處。
}
```
## 第 2 步：建立浮水印
接下來，建立要新增到文件中的浮水印。在此範例中，我們將建立具有特定字體設定和顏色的文字浮水印。
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 步驟 3：配置浮水印選項
現在，配置浮水印選項以指定部分索引和鎖定設定。這可確保水印添加到正確的部分並被鎖定。
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; //添加到第一部分
options.IsLocked = true; //鎖定浮水印
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; //鎖型
```
## 步驟 4：將浮水印加入文件中
配置好浮水印和選項後，就可以使用以下命令將浮水印新增至文件中`Add`的方法`Watermarker`班級。
```csharp
watermarker.Add(watermark, options);
```
## 第五步：儲存修改後的文檔
最後，將新增浮水印的文檔儲存到所需的輸出位置。
```csharp
watermarker.Save(outputFileName);
```
## 結論
使用 Groupdocs for .NET 將鎖定浮水印新增至 Word 文件中的特定部分是一個簡單的過程。透過執行這些步驟，您可以增強文件的安全性和完整性，確保重要資訊受到保護。無論您是保護敏感資料還是為文件添加專業風格，Groupdocs.Watermark for .NET 都能提供您有效實現目標所需的工具。
## 常見問題解答
### 什麼是 .NET 的 Groupdocs.Watermark？
Groupdocs.Watermark for .NET 是一個功能強大的程式庫，可讓開發人員在各種文件類型（包括 Word、PDF 和圖像）中添加浮水印，並具有高級自訂和安全功能。
### 可以用密碼鎖定浮水印嗎？
是的，您可以透過設定密碼來保護浮水印`options.Password`財產在`WordProcessingWatermarkSectionOptions`班級。
### 是否可以將不同的浮水印應用到文件的不同部分？
絕對地！透過設定不同`SectionIndex`中的值`WordProcessingWatermarkSectionOptions`，您可以將獨特的浮水印套用到文件的不同部分。
### 我可以使用 Groupdocs.Watermark 添加哪些類型的水印？
Groupdocs.Watermark 支援各種類型的浮水印，包括文字、圖像和形狀浮水印，為每種類型提供廣泛的自訂選項。
### 在哪裡可以找到有關 Groupdocs.Watermark for .NET 的更多資訊？
欲了解更多信息，您可以訪問[文件](https://reference.groupdocs.com/Watermark/net/)和[支援論壇](https://forum.groupdocs.com/c/watermark/19).