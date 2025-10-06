---
title: 取消保護 Word 文件中的文檔
linktitle: 取消保護 Word 文件中的文檔
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 輕鬆取消 Word 文件的保護。請遵循我們的逐步指南。
weight: 38
url: /zh-hant/net/word-processing-watermarkings/unprotect-document-word-docs/
type: docs
---
# 取消保護 Word 文件中的文檔

## 介紹
GroupDocs.Watermark for .NET 是一個功能強大的 API，可讓開發人員使用各種文件格式（包括 Word 文件）的浮水印。在本教學中，我們將引導您完成使用 GroupDocs.Watermark for .NET 取消保護 Word 文件的流程。無論您是經驗豐富的開發人員還是剛開始 .NET 開發，本逐步指南都將幫助您有效率地完成任務。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1.  GroupDocs.Watermark for .NET：您需要在開發環境中安裝 GroupDocs.Watermark for .NET API。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：確保您為 .NET 開發設定了適當的開發環境，包括 Visual Studio 或任何其他相容的 IDE。
3. Word 文件：在檔案系統中準備好要取消保護的 Word 文件。

## 導入命名空間
在深入研究程式碼之前，您需要將必要的命名空間匯入到您的 .NET 專案中。這使您可以無縫存取 GroupDocs.Watermark for .NET 提供的功能。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## 第1步：指定文檔路徑
定義要取消保護的 Word 文件的路徑。
```csharp
string documentPath = "Your Document Path";
```
代替`"Your Document Path"`與 Word 文件的實際路徑。
## 第2步：設定輸出檔名
指定要儲存未受保護文件的目錄並提供輸出檔案的名稱。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
代替`"Your Document Directory"`與要儲存輸出檔案的目錄路徑。
## 第 3 步：載入帶有選項的文檔
建立一個實例`WordProcessingLoadOptions`使用特定選項載入 Word 文件。
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 步驟 4：取消文件保護
實例化`Watermarker`具有文件路徑和載入選項的類別。然後，取得文件內容作為 WordProcessingContent 並取消保護。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## 結論
透過執行以下步驟，您可以使用 GroupDocs.Watermark for .NET 輕鬆取消 Word 文件的保護。此 API 提供了一種簡單的方法來操作浮水印並有效地保護您的文件。
## 常見問題解答
### GroupDocs.Watermark for .NET 是否與所有版本的 .NET 相容？
是的，GroupDocs.Watermark for .NET 與 .NET Framework 2.0 及更高版本相容，包括 .NET Core 和 .NET Standard。
### 我可以為 Word 以外的其他格式的文件添加浮水印嗎？
絕對地！ GroupDocs.Watermark for .NET 支援多種文件格式，包括 PDF、Excel、PowerPoint 等。
### GroupDocs.Watermark for .NET 有沒有試用版？
是的，您可以從以下位置取得免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Watermark for .NET 的技術支援？
您可以訪問[GroupDocs.Watermark 論壇](https://forum.groupdocs.com/c/watermark/19)尋求技術援助和社區支持。
### 我可以購買 GroupDocs.Watermark for .NET 的臨時授權嗎？
是的，您可以從以下位置購買臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).