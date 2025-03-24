---
title: 在 Word 文件中新增具有形狀設定的浮水印
linktitle: 在 Word 文件中新增具有形狀設定的浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs for .NET 將具有形狀設定的浮水印新增至 Word 文件。有效保護您的文件。
weight: 20
url: /zh-hant/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---

# 在 Word 文件中新增具有形狀設定的浮水印

## 介紹
在本教學中，我們將逐步介紹使用 GroupDocs.Watermark for .NET 將具有形狀設定的浮水印新增至 Word 文件的過程。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1. 安裝了 .NET 的 GroupDocs.Watermark。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/Watermark/net/).
2. C# 程式設計基礎知識。
3. 了解Word文檔處理。

## 導入命名空間
首先，您需要匯入必要的命名空間來存取所需的類別和方法。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：載入文檔
載入Word文檔要新增浮水印的位置。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //添加水印代碼在這裡
}
```
## 第2步：新增浮水印
實例化一個`TextWatermark`物件並指定要用作浮水印的文字。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## 步驟 3：自訂浮水印設置
設定浮水印的各種設置，例如對齊方式、旋轉角度、顏色和不透明度。
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## 步驟 4：定義浮水印部分選項
定義浮水印部分的選項，例如形狀名稱和替代文字。
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## 步驟5：為文件添加浮水印
使用指定選項將浮水印新增至文件。
```csharp
watermarker.Add(watermark, options);
```
## 第 6 步：儲存文檔
儲存附有新增浮水印的文件。
```csharp
watermarker.Save(outputFileName);
```

## 結論
使用 GroupDocs for .NET 將具有形狀設定的浮水印新增至 Word 文件是一個簡單的過程。透過遵循本教學中概述的步驟，您可以使用自訂浮水印有效保護您的文件。
## 常見問題解答
### 我可以在同一個文件中添加多個浮水印嗎？
是的，您可以將具有不同設定的多個浮水印新增至同一文件。
### GroupDocs.Watermark 是否支援 Word 以外的其他文件格式？
是的，GroupDocs.Watermark 支援各種文件格式，包括 Excel、PowerPoint、PDF 等。
### 我可以進一步自訂浮水印的外觀嗎？
當然，您可以調整各種參數，例如字體大小、樣式、顏色和位置來滿足您的需求。
### GroupDocs.Watermark for .NET 有沒有試用版？
是的，您可以從以下位置獲得免費試用[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到對 GroupDocs.Watermark 的支援？
您可以在 GroupDocs 論壇上尋求支援並提出問題[這裡](https://forum.groupdocs.com/c/watermark/19).