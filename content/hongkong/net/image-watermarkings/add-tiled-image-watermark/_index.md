---
title: 新增平鋪影像浮水印
linktitle: 新增平鋪影像浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 將平鋪影像浮水印新增至文件。簡單、高效且可自訂。
type: docs
weight: 10
url: /zh-hant/net/image-watermarkings/add-tiled-image-watermark/
---
## 介紹
GroupDocs.Watermark for .NET 是一個功能強大的 API，可讓開發人員以程式設計方式新增、刪除和搜尋各種文件格式的浮水印。在本教學中，我們將指導您完成使用 GroupDocs.Watermark for .NET 將平鋪影像浮水印新增至文件的流程。
## 先決條件
在開始之前，請確保您具備以下條件：
- C# 程式語言的基礎知識。
- Visual Studio 安裝在您的系統上。
- GroupDocs.Watermark for .NET 程式庫已新增至您的專案中。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/Watermark/net/).

## 導入命名空間
確保在 C# 檔案的開頭導入必要的命名空間：
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 步驟1：設定文檔路徑和輸出目錄
定義輸入文檔的路徑和要儲存輸出文檔的目錄：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`輸入文檔的絕對或相對路徑。
## 第2步：初始化水印對象
使用輸入文檔路徑建立 Watermarker 物件：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //在此添加浮水印
}
```
## 步驟3：新增平鋪影像浮水印
使用要用作浮水印的影像檔案的路徑實例化 ImageWatermark 物件：
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    //配置圖塊選項
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    //為文件添加浮水印
    watermarker.Add(watermark);
    //儲存修改後的文檔
    watermarker.Save(outputFileName);
}
```
代替`"Path to Your Image"`與水印影像檔案的實際路徑。

## 結論
透過執行以下步驟，您可以使用 GroupDocs.Watermark for .NET 輕鬆地將平鋪影像浮水印新增至文件。嘗試不同的選項和配置以獲得所需的結果。
## 常見問題解答
### 我可以在單一文件中添加多個浮水印嗎？
是的，您可以使用 GroupDocs.Watermark for .NET 將多個不同類型的浮水印新增至文件中。
### GroupDocs.Watermark 支援所有文件格式嗎？
GroupDocs.Watermark 支援多種文件格式，包括 PDF、Word、Excel、PowerPoint 等。
### GroupDocs.Watermark 是否有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 我可以自訂浮水印的外觀嗎？
是的，您可以自訂浮水印的各個方面，例如位置、大小、旋轉、透明度等。
### GroupDocs.Watermark 提供技術支援嗎？
是的，您可以從 GroupDocs.Watermark 論壇獲得技術支持[這裡](https://forum.groupdocs.com/c/watermark/19).