---
title: 從 PDF 中提取註釋信息
linktitle: 從 PDF 中提取註釋信息
second_title: GroupDocs.Watermark .NET API
description: 在此詳細的逐步指南中了解如何使用 GroupDocs.Watermark for .NET 從 PDF 文件中提取註釋資訊。
weight: 23
url: /zh-hant/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# 從 PDF 中提取註釋信息

## 介紹
您是否經常發現自己需要從 PDF 文件中提取詳細的註釋資訊？無論您是文件管理系統的開發人員還是處理大量 PDF 的業務專業人員，高效提取和處理註釋都至關重要。透過 GroupDocs.Watermark for .NET，您可以使用強大的工具包來讓此任務變得簡單且有效率。
## 先決條件
在我們深入研究程式碼之前，讓我們確保您擁有開始使用所需的一切：
1. Visual Studio：確保您已安裝 Visual Studio。這將是我們用於編寫和運行程式碼的 IDE。
2.  GroupDocs.Watermark for .NET：您需要擁有 GroupDocs.Watermark for .NET 函式庫。你可以[在這裡下載](https://releases.groupdocs.com/Watermark/net/).
3. C# 基礎知識：需要熟悉 C# 程式設計才能理解範例。
## 導入命名空間
首先，您需要將必要的命名空間匯入到您的專案中。這些命名空間包含處理 PDF 檔案和提取註釋所需的類別和方法。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## 第 1 步：設定您的項目
首先，讓我們在 Visual Studio 中設定我們的專案。建立一個新的控制台應用程式（.NET Core）專案。建立專案後，您需要新增對 GroupDocs.Watermark for .NET 程式庫的參考。
1. 開啟 NuGet 套件管理器。
2. 搜尋`GroupDocs.Watermark`.
3. 安裝`GroupDocs.Watermark`包裹。
## 第 2 步：定義文檔路徑
接下來，您需要指定輸入 PDF 文件的路徑以及保存提取資訊的輸出目錄。這可確保您的應用程式知道在哪裡可以找到 PDF 文件以及在哪裡儲存結果。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 第 3 步：載入 PDF 文檔
要使用 PDF 文檔，我們需要使用以下命令加載它`PdfLoadOptions`。此類提供了配置載入過程的選項。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //提取註釋的程式碼將放在此處
}
```
## 第 4 步：存取 PDF 內容
載入文件後，我們就可以存取其內容。具體來說，我們想要取得 PDF 內容，以便可以迭代頁面和註釋。
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 第 5 步：迭代頁面和註釋
有了 PDF 內容，我們就可以循環瀏覽每個頁面，然後瀏覽這些頁面上的每個註釋。這使我們能夠提取我們需要的資訊。
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        //在此提取註釋詳細信息
    }
}
```
## 第 6 步：提取註釋詳細信息
在嵌套循環中，我們提取有關每個註釋的各種詳細資訊。這包括註釋的類型、任何關聯的圖像、文字和位置資料。
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## 第 7 步：保存或處理提取的數據
最後，決定要如何處理提取的註釋資訊。您可以根據需要將其列印到控制台、將其儲存到文件，甚至儲存在資料庫中。
```csharp
//將提取的資料儲存到檔案的範例
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## 結論
使用 GroupDocs.Watermark for .NET 從 PDF 文件中提取註釋資訊是一個簡單的過程，可以為您節省大量時間和精力。透過遵循本指南中概述的步驟，您可以輕鬆地將此功能整合到您的專案中並自動提取有價值的註釋資料。
無論您是管理大量 PDF 還是僅需要提取特定信息，GroupDocs.Watermark for .NET 都能提供可靠且高效的解決方案。不要忘記查看[文件](https://tutorials.groupdocs.com/Watermark/net/)了解更多進階功能和自訂選項。
## 常見問題解答
### 什麼是 .NET 的 GroupDocs.Watermark？
GroupDocs.Watermark for .NET 是一個綜合函式庫，可讓開發人員從各種文件格式（包括 PDF、Word 文件和影像）新增、搜尋和移除浮水印。
### 我可以免費試用 GroupDocs.Watermark 嗎？
是的，您可以獲得[免費試用](https://releases.groupdocs.com/)在購買之前測試圖書館的功能。
### 如果遇到問題，我該如何獲得支援？
您可以透過造訪 GroupDocs 團隊獲得支持[支援論壇](https://forum.groupdocs.com/c/watermark/19).
### 是否可以獲得臨時測試許可證？
是的，您可以請求[臨時執照](https://purchase.groupdocs.com/temporary-license/)用於測試目的。
### 哪裡可以購買適用於 .NET 的 GroupDocs.Watermark 的完整版本？
您可以從以下網站購買完整版本[集團文件網站](https://purchase.groupdocs.com/buy).