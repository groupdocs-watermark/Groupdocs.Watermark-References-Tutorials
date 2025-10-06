---
title: 為 PDF 中的註釋圖像添加浮水印
linktitle: 為 PDF 中的註釋圖像添加浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 為註釋影像添加浮水印來保護您的 PDF 文件。
weight: 17
url: /zh-hant/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
type: docs
---
# 為 PDF 中的註釋圖像添加浮水印

## 介紹
在本教學中，我們將探討如何使用 Groupdocs.Watermark for .NET 在 PDF 文件中的註解影像中新增浮水印。浮水印對於保護您的文件免遭未經授權的使用或散佈至關重要。透過遵循本逐步指南，您將了解如何有效地將文字浮水印應用到 PDF 中的註釋圖像。
## 先決條件
在繼續之前，請確保您具備以下條件：
1. 對 C# 程式語言有基本了解。
2. 已安裝 Groupdocs.Watermark for .NET 函式庫。
3. 造訪 Visual Studio 等開發環境。
4. 帶有註釋圖像和浮水印的 PDF 文件。

## 導入命名空間
首先，您需要將必要的命名空間匯入到 C# 程式碼中：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入 PDF 文檔
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 步驟2：取得PDF內容並初始化浮水印
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    //初始化圖像或文字浮水印
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## 第 3 步：迭代 PDF 頁面和註釋圖像
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                //為影像添加浮水印
                annotation.Image.Add(watermark);
            }
        }
    }
```
## 第四步：保存有浮水印的文檔
```csharp
    watermarker.Save(outputFileName);
}
```
執行這些步驟後，您的 PDF 文件將在註釋影像中新增指定的浮水印。

## 結論
在 PDF 中的註釋影像中添加浮水印對於保護文件的完整性並確保它們不會被濫用至關重要。透過 Groupdocs.Watermark for .NET，此流程變得簡單且高效，使您能夠有效地保護 PDF 檔案。
## 常見問題解答
### 我可以在同一個 PDF 文件中新增多個浮水印嗎？
是的，您可以使用 Groupdocs.Watermark for .NET 將多個浮水印新增至相同 PDF 文件。
### Groupdocs.Watermark 是否支援 PDF 以外的其他文件格式？
是的，Groupdocs 支援各種文件格式，包括 Word、Excel、PowerPoint 等。
### 是否可以自訂浮水印的外觀？
當然，您可以根據自己的喜好自訂浮水印的文字、字體、顏色、大小和位置。
### 我可以使用 Groupdocs.Watermark 從 PDF 文件中刪除浮水印嗎？
是的，Groupdocs.Watermark 提供了輕鬆從 PDF 文件中移除浮水印的功能。
### Groupdocs.Watermark for .NET 是否有免費試用版？
是的，您可以免費從網站試用 Groupdocs.Watermark for .NET。