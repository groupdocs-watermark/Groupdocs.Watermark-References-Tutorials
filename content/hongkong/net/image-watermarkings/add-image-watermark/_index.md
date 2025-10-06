---
title: 新增影像浮水印
linktitle: 新增影像浮水印
second_title: GroupDocs.Watermark .NET API
description: 透過我們詳細的逐步教學，了解如何使用 GroupDocs.Watermark for .NET 將影像浮水印新增至文件。
weight: 11
url: /zh-hant/net/image-watermarkings/add-image-watermark/
type: docs
---
# 新增影像浮水印

## 介紹
歡迎閱讀這份使用 GroupDocs.Watermark for .NET 新增影像浮水印的綜合指南！浮水印是保護您的文件和影像免遭未經授權使用的強大方法，可確保您的智慧財產權的安全。在本教程中，我們將引導您完成從設定環境到將浮水印應用到文件的整個過程。無論您是經驗豐富的開發人員還是剛入門，您都會發現本指南很有幫助且易於遵循。
## 先決條件
在我們深入學習本教程之前，讓我們確保您擁有所需的一切：
- 開發環境：Visual Studio 或任何與 .NET 相容的 IDE
- .NET Framework：.NET Framework 4.0 或更高版本
- GroupDocs.Watermark for .NET：您可以從[集團文件網站](https://releases.groupdocs.com/Watermark/net/)
- 影像檔案：用作浮水印的影像檔案（例如，`watermark.jpg`）
- 文件檔案：要新增浮水印的文件（例如，`presentation.pptx`）
## 導入命名空間
首先，您需要將必要的命名空間匯入到您的專案中。這對於存取 GroupDocs 功能至關重要。
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
在本節中，我們將把添加影像浮水印的過程分解為清晰、可管理的步驟。仔細遵循每個步驟，成功為您的文件添加浮水印。
## 第 1 步：設定您的環境
首先，確保您的開發環境已正確設定。從以下位置下載安裝 GroupDocs.Watermark 庫[集團文件網站](https://releases.groupdocs.com/Watermark/net/).
1. 在 Visual Studio 中開啟您的專案。
2. 在解決方案資源管理器中以滑鼠右鍵按一下您的專案。
3. 選擇“管理 NuGet 套件...”
4. 搜尋`GroupDocs.Watermark`並安裝它。
## 第 2 步：定義檔路徑
接下來，您需要定義輸入文件和輸出目錄的路徑。這有助於程式找到它需要使用的檔案。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`包含文件的實際路徑和所需的輸出目錄。
## 第三步：初始化浮水印
現在，初始化`Watermarker`類與您的文件的路徑。該類負責管理水印過程。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //繼續此 using 區塊中的後續步驟
}
```
## 第四步：建立影像浮水印
內`Watermarker`區塊，建立一個實例`ImageWatermark`使用水印影像路徑的類別。此類代表要用作浮水印的圖像。
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    //繼續此 using 區塊中的下一步
}
```
## 步驟5：為文件添加浮水印
隨著`ImageWatermark`實例準備就緒，使用以下命令將其新增至您的文件中`Add`的方法`Watermarker`班級。
```csharp
watermarker.Add(watermark);
```
## 第 6 步：儲存文檔
最後，將帶有浮水印的文檔儲存到指定的輸出目錄。此步驟可確保您的變更寫入新檔案。
```csharp
watermarker.Save(outputFileName);
```
## 結論
恭喜！您已使用 GroupDocs.Watermark for .NET 成功將影像浮水印新增至文件。透過遵循此逐步指南，您可以輕鬆使用自訂浮水印保護您的文件。請記住，浮水印是保護您的數位資產免於未經授權使用的關鍵步驟。

## 常見問題解答
### GroupDocs.Watermark 支援哪些檔案格式？
GroupDocs.Watermark 支援多種檔案格式，包括 PDF、DOCX、PPTX、XLSX 以及 JPEG 和 PNG 等圖片檔案。
### 我可以將 GroupDocs.Watermark 與 .NET Core 一起使用嗎？
是的，GroupDocs.Watermark 與 .NET Framework 和 .NET Core 也相容。
### 如何取得 GroupDocs.Watermark 的臨時授權？
您可以從以下機構獲得臨時許可證[集團文件網站](https://purchase.groupdocs.com/temporary-license/).
### 是否可以為單一文件添加多個浮水印？
絕對地！您可以透過呼叫添加多個浮水印`Add`使用不同的水印實例多次方法。
### 在哪裡可以找到更多範例和文件？
有關更多範例和詳細文檔，請訪問[GroupDocs.Watermark 文檔](https://tutorials.groupdocs.com/Watermark/net/).