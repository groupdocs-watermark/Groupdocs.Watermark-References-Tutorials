---
title: 將鎖定浮水印新增至 Word 文件中的特定頁面
linktitle: 將鎖定浮水印新增至 Word 文件中的特定頁面
second_title: GroupDocs.Watermark .NET API
description: 透過我們簡單的逐步指南，了解如何使用 GroupDocs.Watermark for .NET 將鎖定浮水印新增至 Word 文件中的特定頁面。
type: docs
weight: 12
url: /zh-hant/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## 介紹
您是否希望在 Word 文件中的特定頁面上新增浮水印，但希望將其鎖定以使其無法輕鬆刪除或編輯？您來對地方了！在本教學中，我們將引導您完成使用 GroupDocs.Watermark for .NET 將鎖定浮水印新增至 Word 文件中的特定頁面的流程。這個功能強大的庫可以輕鬆地在各種文件類型上套用、管理和自訂浮水印。無論您是開發人員還是只是需要保護文件的人員，本指南都將以簡單的方式引導您完成每個步驟。
## 先決條件
在我們深入學習本教程之前，讓我們確保您擁有所需的一切：
1.  GroupDocs.Watermark for .NET：您可以[下載](https://releases.groupdocs.com/Watermark/net/)最新版本。
2. 開發環境：像Visual Studio這樣的IDE。
3. C# 基礎知識：熟悉 C# 程式設計將會有所幫助。
4. 文件至浮水印：要新增浮水印的 Word 文件（.docx 或 .doc）。
## 導入命名空間
首先，您需要在 C# 專案中匯入必要的命名空間。這些命名空間提供對使用 GroupDocs.Watermark 所需的類別和方法的存取。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
現在我們已經涵蓋了先決條件並導入了必要的命名空間，讓我們逐步分解這個過程。
## 第 1 步：載入 Word 文檔
首先，您需要載入要新增浮水印的Word文件。這可以使用以下方法完成`Watermarker`類與`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //繼續執行後續步驟
}
```
## 步驟2：建立文字浮水印
接下來，建立文字浮水印。您可以根據您的要求自訂文字、字體、顏色和其他屬性。
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 步驟 3：配置浮水印選項
若要將浮水印套用到特定頁面並鎖定它，請配置`WordProcessingWatermarkPagesOptions`。在這裡，您可以指定浮水印應出現的頁碼並設定鎖定選項。
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; //指定頁面
options.IsLocked = true; //鎖定浮水印
options.LockType = WordProcessingLockType.AllowOnlyComments; //設定鎖類型
//使用密碼保護
//選項.密碼 = "7654321";
```
## 步驟 4：將浮水印加入文件中
配置浮水印和選項後，您現在可以將浮水印新增至文件。
```csharp
watermarker.Add(watermark, options);
```
## 第 5 步：儲存文檔
最後，保存應用了水印的文檔。選擇合適的輸出路徑並儲存檔案。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## 結論
恭喜！您已使用 GroupDocs.Watermark for .NET 成功將鎖定浮水印新增至 Word 文件中的特定頁面。本教學涵蓋了從載入文件到保存浮水印文件的所有基本步驟。透過執行這些步驟，您可以確保您的文件帶有安全的浮水印，從而保護您的內容免遭未經授權的編輯和使用。
欲了解更多信息，您可以參考[GroupDocs.Watermark 文檔](https://reference.groupdocs.com/Watermark/net/)。如果您有任何疑問或需要進一步協助，請隨時訪問[支援論壇](https://forum.groupdocs.com/c/watermark/19).
## 常見問題解答
### 什麼是 .NET 的 GroupDocs.Watermark？
GroupDocs.Watermark for .NET 是一個功能強大的程式庫，可讓開發人員在各種類型的文件中添加浮水印，包括 Word、PDF、Excel 等。
### 我可以將浮水印套用到文件的多個頁面嗎？
是的，您可以在中指定多個頁碼`PageNumbers`陣列將浮水印套用到多個頁面。
### 如何使用密碼保護浮水印？
您可以透過設定密碼來保護浮水印`Password`財產在`WordProcessingWatermarkPagesOptions`.
### 是否可以自訂浮水印的外觀？
絕對地！您可以自訂浮水印的文字、字體、顏色、大小和其他屬性以滿足您的需求。
### 在哪裡可以獲得 GroupDocs.Watermark 的臨時許可證？
您可以從以下地址取得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).