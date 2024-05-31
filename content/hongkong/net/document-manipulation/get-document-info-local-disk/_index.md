---
title: 從本機磁碟取得文件資訊
linktitle: 從本機磁碟取得文件資訊
second_title: GroupDocs.Watermark .NET API
description: 透過這份全面的逐步指南，了解如何使用 GroupDocs for .NET 在文件中新增、刪除和擷取浮水印。
type: docs
weight: 11
url: /zh-hant/net/document-manipulation/get-document-info-local-disk/
---
## 介紹
歡迎閱讀使用 GroupDocs.Watermark for .NET 的終極指南！無論您是經驗豐富的開發人員還是剛剛入門，本文都將引導您了解使用這個強大的工具為文件添加浮水印的基本知識。最後，您將成為在文件中嵌入浮水印的專家，確保它們受到保護並按照您的規格進行標記。
## 先決條件
在深入了解逐步指南之前，您需要滿足一些先決條件：
1.  .NET Framework：確保您的系統上安裝了 .NET Framework。 GroupDocs.Watermark for .NET 與各種版本的 .NET Framework 相容，因此請檢查[文件](https://reference.groupdocs.com/Watermark/net/)有關相容性詳細資訊。
2.  GroupDocs.Watermark for .NET Library：從以下位置下載並安裝最新版本[下載頁面](https://releases.groupdocs.com/Watermark/net/).
3. 開發環境：您應該設定一個開發環境。 Visual Studio 是 .NET 開發的熱門選擇。
4. 基本 C# 知識：了解 C# 程式設計的基礎知識將幫助您理解範例。
## 導入命名空間
在使用 GroupDocs.Watermark for .NET 之前，您需要將必要的命名空間匯入到您的專案中。這是一個簡單的過程，對於存取庫的功能至關重要。
```csharp
using System;
using GroupDocs.Watermark.Common;
```
讓我們將文件加浮水印的過程分解為清晰、可管理的步驟。每個步驟旨在幫助您輕鬆理解和實現功能。
## 第 1 步：載入您的文檔
第一步是載入要加浮水印的文件。這是使用以下方法完成的`Watermarker`類，它允許您存取和操作您的文件。
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    //文件現已載入並準備好新增浮水印
}
```
在此步驟中，替換`"Your Document Path"`與文檔的實際路徑。這會初始化`Watermarker`對象，使您可以存取各種浮水印功能。
## 步驟2：取得文件資訊
在新增浮水印之前，您可能需要收集有關文件的一些資訊。這對於根據文件屬性自訂浮水印非常有用。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
在這一步中，`GetDocumentInfo`方法檢索文件類型、頁數和文件大小等詳細資訊。此資訊將列印到控制台，但您可以根據需要在應用程式中使用它。
## 第 3 步：新增文字浮水印
現在您已加載文檔並掌握其信息，是時候添加水印了。我們將從簡單的文字浮水印開始。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
在這裡，您創建一個`TextWatermark`具有您想要的文字、字體和樣式的物件。調整顏色、不透明度和旋轉角度等屬性以滿足您的需求。最後將浮水印新增至文件並儲存到指定路徑。
## 第四步：新增影像浮水印
文字浮水印很棒，但如果您想添加徽標或其他圖像怎麼辦？此步驟介紹如何新增影像浮水印。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
代替`"Path to Your Image"`以及水印影像的路徑。設定不透明度和旋轉角度等屬性來自訂影像浮水印的外觀。新增和保存浮水印的過程與文字浮水印類似。
## 第 5 步：刪除現有浮水印
有時，您可能需要從文件中刪除現有的浮水印。這可以使用以下方法完成`Remove`提供的方法`Watermarker`班級。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
在這裡，`Remove`方法用於從文件中刪除文字浮水印。您可以根據需要指定要刪除的不同類型的浮水印，例如圖像或文字。將文件儲存到新路徑以查看變更。
## 第6步：提取浮水印
如果您需要從文件中提取和檢查水印，GroupDocs.Watermark for .NET 可以輕鬆實現這一點。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        //每個浮水印的附加屬性和邏輯
    }
}
```
此步驟涉及使用`GetWatermarks`檢索文件中所有浮水印的方法。然後，您可以遍歷水印清單並檢查其屬性或根據需要執行其他操作。
## 結論
恭喜！現在您已經了解如何使用 GroupDocs.Watermark for .NET 在文件中新增、刪除和提取浮水印。借助這些技能，您可以有效地保護您的文件並為其建立品牌。請記住，[文件](https://reference.groupdocs.com/Watermark/net/)如果您需要更詳細的資訊或高級功能，請總是在那裡。
## 常見問題解答
### 我可以將 GroupDocs.Watermark for .NET 與任何 .NET 版本一起使用嗎？
是的，GroupDocs.Watermark for .NET 與各種 .NET Framework 版本相容。檢查[文件](https://reference.groupdocs.com/Watermark/net/)了解具體情況。
### 哪裡可以下載 .NET 版 GroupDocs.Watermark？
您可以從以下位置下載最新版本[下載頁面](https://releases.groupdocs.com/Watermark/net/).
### 我如何獲得臨時許可證？
您可以從以下機構獲得臨時許可證[臨時許可證頁面](https://purchase.groupdocs.com/temporary-license/).
### 有免費試用嗎？
是的，您可以造訪以下網站開始免費試用[免費試用頁面](https://releases.groupdocs.com/).
### 如果遇到問題，我可以在哪裡獲得支援？
支援可在[GroupDocs 浮水印論壇](https://forum.groupdocs.com/c/watermark/19).