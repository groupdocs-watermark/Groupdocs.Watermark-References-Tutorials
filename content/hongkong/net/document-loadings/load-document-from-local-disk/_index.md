---
title: 從本機磁碟載入文檔
linktitle: 從本機磁碟載入文檔
second_title: GroupDocs.Watermark .NET API
description: 使用 Groupdocs for .NET 保護和管理您的文件。按照我們的詳細指南無縫添加浮水印。
weight: 10
url: /zh-hant/net/document-loadings/load-document-from-local-disk/
---

# 從本機磁碟載入文檔

## 介紹
在當今的數位時代，為文件添加浮水印對於確保內容保護、所有權聲明和機密性至關重要。 Groupdocs.Watermark for .NET 是一個功能強大的程式庫，可讓開發人員新增、搜尋和管理各種文件格式的浮水印。在本教學中，我們將透過詳細的逐步說明逐步介紹使用 Groupdocs.Watermark for .NET 為文件添加浮水印的過程。
## 先決條件
在深入實施之前，請確保您具備以下條件：
1. 已安裝 Visual Studio：您需要 Visual Studio 或其他相容的 .NET IDE。
2.  Groupdocs.Watermark for .NET：從以下位置下載該程式庫[下載連結](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework：確保已安裝了 .NET Framework 4.6.1 或更高版本。
4. 範例文件：準備範例文件來測試浮水印過程。
## 導入命名空間
首先，您需要在專案中匯入必要的命名空間。這些對於存取浮水印所需的類別和方法至關重要。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 步驟一：從本機磁碟載入文檔
首先，您需要從本機磁碟載入文件。您將在該文件中新增浮水印。
定義要加浮水印的文件的路徑。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 第 2 步：初始化載入選項
接下來，初始化載入選項。例如，如果您正在處理 Word 文檔，您將使用`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 第 3 步：建立並配置浮水印
現在，您將建立一個實例`Watermarker`班級。該實例將用於管理浮水印並將其套用到您的文件。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //該區塊將包含添加和保存浮水印的進一步步驟
}
```
## 第 4 步：建立浮水印
建立文字浮水印。該浮水印可以包含您選擇的任何文字。在這裡，我們將使用“測試浮水印”。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## 步驟5：為文件添加浮水印
使用以下命令將建立的浮水印新增至文件中`Add`的方法`Watermarker`班級。
```csharp
watermarker.Add(watermark);
```
## 步驟 6：儲存有浮水印的文檔
最後將帶有浮水印的文檔儲存到指定路徑。
```csharp
watermarker.Save(outputFileName);
```

## 結論
使用 Watermark for .NET 為文件添加浮水印既簡單又有效率。本指南引導您完成從設定環境到儲存帶有浮水印的文件的整個過程。借助這個強大的工具，您可以確保您的文件受到保護並確保您的智慧財產權安全。 
欲了解更多詳情，請查看[文件](https://tutorials.groupdocs.com/Watermark/net/)，如果您遇到任何問題，[支援論壇](https://forum.groupdocs.com/c/watermark/19)是尋求幫助的絕佳場所。 
## 常見問題解答
### 我可以使用自訂字體作為浮水印嗎？
是的，Groupdocs 支援自訂字體。您可以指定係統上安裝的任何字型。
### 支援哪些類型的文件？
Groupdocs.Watermark 支援多種文件格式，包括 Word、Excel、PDF、PowerPoint 等。
### 如何從文件中刪除浮水印？
您可以使用`Remove`提供的方法`Watermarker`類別來刪除浮水印。
### 可以添加圖片浮水印嗎？
是的，您可以使用以下命令新增圖像浮水印`ImageWatermark`班級。
### 我可以免費試用 Groupdocs.Watermark 嗎？
絕對可以，你可以下載一個[免費試用](https://releases.groupdocs.com/)在購買之前評估圖書館。