---
title: 從流中添加圖像浮水印
linktitle: 從流中添加圖像浮水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 將影像浮水印新增至文件。請遵循我們的無縫水印集成分步指南。
weight: 12
url: /zh-hant/net/image-watermarkings/add-image-watermark-from-stream/
type: docs
---
# 從流中添加圖像浮水印

## 介紹
在文件管理和安全領域，將浮水印合併到文件中至關重要。無論是品牌推廣、版權保護或維護文件完整性，水印都扮演著至關重要的角色。幸運的是，GroupDocs.Watermark for .NET 提供了一個強大的解決方案，用於新增、刪除和搜尋各種文件格式的浮水印。
## 先決條件
在深入使用 GroupDocs.Watermark for .NET 實作浮水印之前，請確保滿足以下先決條件：
1. 安裝 GroupDocs.Watermark for .NET：從下列位置下載並安裝 GroupDocs.Watermark for .NET 程式庫[下載連結](https://releases.groupdocs.com/Watermark/net/).
2. 存取文件：有權存取要新增或刪除浮水印的文件。
3. C# 基礎知識：為了理解和實作所提供的程式碼片段，需要熟悉 C# 程式語言。

## 導入命名空間
在繼續從流程中新增影像浮水印之前，請匯入必要的命名空間：
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## 步驟1：定義文檔路徑和輸出目錄
首先，定義要新增浮水印的文件的路徑，並指定處理後的文件的輸出目錄。
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 第2步：打開水印流
使用以下命令以流形式開啟浮水印圖像文件`File.OpenRead`方法。
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    //水印處理邏輯將會放在這裡
}
```
## 步驟 3：向文件添加浮水印
初始化一個`Watermarker`物件與文件路徑，然後建立一個`ImageWatermark`物件與步驟2中所獲得的浮水印流。`Add`的方法`Watermarker`目的。
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        //為文件添加浮水印
        watermarker.Add(watermark);
        //儲存帶有浮水印的文檔
        watermarker.Save(outputFileName);
    }
}
```

## 結論
GroupDocs.Watermark for .NET 提供了一個無縫解決方案，用於在文件中添加浮水印，確保品牌識別、版權保護和文件完整性。透過遵循概述的步驟並利用提供的程式碼片段，使用者可以輕鬆地將浮水印合併到他們的文件中。
## 常見問題解答
### GroupDocs.Watermark 是否相容於各種文件格式？
是的，GroupDocs.Watermark 支援多種文件格式，包括 Word 文件、Excel 試算表、PowerPoint 簡報、PDF 等。
### 我可以自訂浮水印的外觀和位置嗎？
當然，GroupDocs.Watermark 提供了廣泛的選項來自訂浮水印外觀、位置、透明度、旋轉等，以滿足特定要求。
### GroupDocs.Watermark 是否提供刪除現有浮水印的 API？
是的，GroupDocs.Watermark 不僅允許使用者添加浮水印，還可以輕鬆地從文件中刪除現有浮水印。
### GroupDocs.Watermark 用戶可以獲得技術支援嗎？
是的，用戶可以透過專門的技術支援和幫助[GroupDocs.Watermark 論壇](https://forum.groupdocs.com/c/watermark/19).
### 我可以在購買前評估 GroupDocs.Watermark 嗎？
當然，用戶可以在做出購買決定之前選擇免費試用 GroupDocs.Watermark 以探索其功能和功能。