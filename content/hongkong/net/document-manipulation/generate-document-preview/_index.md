---
title: 生成文件預覽
linktitle: 生成文件預覽
second_title: GroupDocs.Watermark .NET API
description: 透過本指南了解如何使用 GroupDocs.Watermark for .NET 產生文件預覽。輕鬆增強您的文件安全性和管理。
weight: 10
url: /zh-hant/net/document-manipulation/generate-document-preview/
type: docs
---
# 生成文件預覽

## 介紹
在數位文件管理領域，水印在確保文件的安全性和真實性方面發揮著至關重要的作用。 GroupDocs.Watermark for .NET 是一個功能強大的工具，可讓開發人員輕鬆地在文件中新增浮水印。在本教學中，我們將引導您完成使用 GroupDocs.Watermark for .NET 產生文件預覽的流程。無論您是經驗豐富的開發人員還是剛入門，本指南都將為您提供全面的逐步流程來實現您的目標。
## 先決條件
在深入實施之前，讓我們確保您擁有開始所需的一切：
- 對 C# 和 .NET 架構有基本了解。
- Visual Studio 安裝在您的電腦上。
- .NET 函式庫的 GroupDocs.Watermark。你可以[在這裡下載](https://releases.groupdocs.com/Watermark/net/).
- GroupDocs.Watermark 的有效許可證。您可以購買[這裡](https://purchase.groupdocs.com/buy)或獲得[臨時執照](https://purchase.groupdocs.com/temporary-license/)出於評估目的。
## 導入命名空間
要開始在專案中使用 GroupDocs.Watermark，您需要匯入必要的命名空間。這可以透過在程式碼中加入以下 using 指令來完成：
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
這些命名空間將提供對加浮水印和產生文件預覽所需的類別和方法的存取。

讓我們將產生文件預覽的過程分解為簡單、易於遵循的步驟。
## 第 1 步：設定您的項目
首先，在 Visual Studio 中設定 .NET 專案。如果您還沒有項目，請按照以下步驟建立新項目：
1. 打開視覺工作室。
2. 按一下“建立新專案”。
3. 選擇“控制台應用程式（.NET Core）”，然後按一下“下一步”。
4. 為您的專案命名並選擇儲存位置，然後按一下「建立」。
## 步驟 2：安裝適用於 .NET 的 GroupDocs.Watermark
要在專案中使用 GroupDocs.Watermark，您需要安裝該程式庫。這可以使用 NuGet 套件管理器來完成：
1. 在解決方案資源管理器中以滑鼠右鍵按一下您的專案。
2. 選擇“管理 NuGet 套件”。
3. 在「瀏覽」標籤中搜尋「GroupDocs.Watermark」。
4. 點擊“安裝”將庫新增到您的專案中。
或者，您可以透過套件管理器控制台安裝它：
```powershell
Install-Package GroupDocs.Watermark
```
## 步驟 3：定義文件路徑和輸出目錄
在產生預覽之前，您需要指定要預覽的文件的路徑以及預覽影像的儲存目錄：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
將「您的文件路徑」替換為文件的路徑，將「您的文件目錄」替換為要儲存預覽影像的目錄。
## 第四步：初始化水印對象
建立一個實例`Watermarker`類別透過將文檔路徑傳遞給其建構函數來實現。該物件將用於執行所有水印操作：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //你的程式碼在這裡
}
```
## 第 5 步：建立流處理的委託方法
要產生預覽，您需要定義用於建立和釋放流的委託方法。這些方法將處理文件每個頁面的流的建立和釋放：
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
這`createPageStreamDelegate`方法為文件的每個頁面建立一個流，而`releasePageStreamDelegate`方法在預覽生成後關閉串流。
## 第 6 步：配置預覽選項
接下來，透過建立一個實例來配置預覽選項`PreviewOptions`班級。指定委託方法並將預覽格式設定為 PNG。您也可以指定預覽中包含哪些頁面：
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
在此範例中，我們正在產生文件前兩頁的預覽。
## 第 7 步：產生文件預覽
最後，致電`GeneratePreview`方法上的`Watermarker`對象，傳入配置的`PreviewOptions`。這將生成預覽圖像並將其保存到指定目錄：
```csharp
watermarker.GeneratePreview(previewOptions);
```
## 結論
使用 GroupDocs.Watermark for .NET 產生文件預覽是一個簡單的過程，只需幾行程式碼即可完成。透過遵循本指南中概述的步驟，您可以輕鬆設定專案、配置必要的選項並產生文件預覽。這個強大的庫不僅簡化了水印過程，而且還提供了管理和操作水印的強大功能。
如果您有任何疑問或需要進一步協助，請隨時訪問[GroupDocs.Watermark 支援論壇](https://forum.groupdocs.com/c/watermark/19)或參考[文件](https://tutorials.groupdocs.com/Watermark/net/).
## 常見問題解答
### GroupDocs.Watermark for .NET 支援哪些檔案格式？
 GroupDocs.Watermark for .NET 支援多種檔案格式，包括 PDF、DOCX、PPTX、XLSX 等。有關支援格式的完整列表，請參閱[文件](https://tutorials.groupdocs.com/Watermark/net/).
### 我可以自訂浮水印的外觀嗎？
是的，GroupDocs.Watermark 可讓您完全自訂浮水印的外觀，包括文字、圖像和形狀浮水印。您可以調整字體、顏色、大小和透明度等屬性。
### 有試用版嗎？
是的，您可以獲得[免費試用](https://releases.groupdocs.com/)GroupDocs.Watermark for .NET 在購買前評估其功能。
### 如何購買 GroupDocs.Watermark 的授權？
您可以購買 GroupDocs.Watermark 的許可證[這裡](https://purchase.groupdocs.com/buy)。有多種授權選項可滿足不同的需求。
### 我可以在商業專案中使用 GroupDocs.Watermark 嗎？
是的，只要您擁有有效的許可證，您就可以在商業專案中使用 GroupDocs.Watermark。請務必查看許可條款和條件[購買頁面](https://purchase.groupdocs.com/buy).