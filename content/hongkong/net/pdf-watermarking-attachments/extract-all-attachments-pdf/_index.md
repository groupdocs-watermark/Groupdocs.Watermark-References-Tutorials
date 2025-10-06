---
title: 從 PDF 中提取所有附件
linktitle: 從 PDF 中提取所有附件
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 從 PDF 中提取所有附件。請按照我們的逐步指南進行無縫提取過程。
weight: 22
url: /zh-hant/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
type: docs
---
# 從 PDF 中提取所有附件

## 介紹
您是否希望輕鬆地從 PDF 文件中提取附件？嗯，您來對地方了！在這個綜合教程中，我們將指導您完成使用 Groupdocs.Watermark for .NET 從 PDF 中提取所有附件的過程。這個強大的程式庫允許開發人員管理各種文件格式的浮水印，但它還包括提取嵌入文件的強大功能。無論您是經驗豐富的開發人員還是剛起步的開發人員，本逐步指南都將使整個過程變得輕而易舉。
## 先決條件
在深入研究程式碼之前，我們先介紹一下入門所需的基礎知識。這是一個快速清單，確保您做好準備：
1. .NET 環境：確保您已設定 .NET 開發環境。您可以使用 Visual Studio 或您選擇的任何其他 .NET IDE。
2.  Groupdocs.Watermark for .NET：從以下位置下載並安裝最新版本的 Groupdocs.Watermark for .NET[這裡](https://releases.groupdocs.com/Watermark/net/).
3. 開發技能：對 C# 程式設計有基本了解，熟悉 .NET 函式庫。
4. 範例 PDF 文件：擁有一個帶有附件的範例 PDF 文檔，可用於測試。
## 導入命名空間
在開始編碼之前，您需要匯入必要的命名空間。這有助於組織您的程式碼並允許您存取將要使用的類別和方法。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## 第 1 步：設定您的項目
首先，讓我們設定您的項目。打開您的 .NET 開發環境並建立一個新的控制台應用程式。
### 建立一個新項目
1. 打開視覺工作室。
2. 選擇“建立新項目”。
3. 根據您的喜好選擇「控制台應用程式（.NET Core）」或「.NET Framework」。
4. 為您的專案命名並點擊“建立”。
### 為 .NET 新增 Groupdocs.Watermark
1. 在解決方案資源管理器中以滑鼠右鍵按一下您的專案。
2. 選擇“管理 NuGet 套件”。
3. 搜尋“Groupdocs.Watermark”並安裝最新版本。
## 第 2 步：定義您的路徑
接下來，您需要定義文件和輸出目錄的路徑。這是您的 PDF 和提取的附件的儲存位置。

在你的`Program.cs`文件中，加入以下程式碼來定義您的路徑：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`與系統上的實際路徑。
## 步驟 3： 載入您的 PDF 文檔
現在，讓我們使用 Groupdocs.Watermark 來載入 PDF 文件。此步驟涉及建立載入選項並初始化`Watermarker`班級。
### 建立載入選項
首先，建立一個實例`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### 初始化浮水印
接下來，使用`Watermarker`類別來載入您的文件：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //您的程式碼將位於此處
}
```
## 第 4 步：提取附件
載入文檔後，就可以提取附件了。您將使用`PdfContent`類別來存取附件，然後將它們儲存到指定的輸出目錄。
### 取得PDF內容
在 - 的裡面`using`區塊，取得PDF內容：
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### 循環瀏覽附件
循環瀏覽 PDF 中的每個附件：
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    //將附件儲存到磁碟上
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
此程式碼會提取每個附件並將其儲存到您的輸出目錄。它還將有關每個附件的一些基本資訊列印到控制台。
## 結論
現在你就得到它了！您已使用 Groupdocs.Watermark for .NET 成功從 PDF 擷取附件。本教學將引導您逐步設定項目、載入文件以及提取附件。有了這些技能，您現在可以輕鬆管理和操作 .NET 應用程式中的 PDF 附件。
## 常見問題解答
### 什麼是 .NET 的 Groupdocs.Watermark？
Groupdocs.Watermark for .NET 是一個綜合庫，用於新增、刪除和管理各種文件格式（包括 PDF）的浮水印。它還提供提取嵌入文件的功能。
### 我可以提取 PDF 中嵌入的其他類型的文件嗎？
是的，Groupdocs.Watermark for .NET 允許您提取 PDF 中嵌入的任何類型的文件，而不僅僅是附件。
### 有免費試用嗎？
是的，您可以從以下位置下載 Groupdocs.Watermark for .NET 的免費試用版：[這裡](https://releases.groupdocs.com/).
### 如果遇到問題，我該如何獲得支援？
您可以透過訪問獲得支持[Groupdocs.Watermark 支援論壇](https://forum.groupdocs.com/c/watermark/19).
### 我需要許可證才能使用 Groupdocs.Watermark for .NET 嗎？
是的，您需要許可證才能在生產中使用該庫。您可以購買許可證[這裡](https://purchase.groupdocs.com/buy)或獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).