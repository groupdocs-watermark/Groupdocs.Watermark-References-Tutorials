---
date: '2026-06-01'
description: 了解如何使用 GroupDocs.Watermark Java 在 Java 中搜尋圖片並載入 Excel 檔案，以高效自動化試算表中的圖片搜尋。
keywords:
- how to search images
- load excel file java
- GroupDocs.Watermark image search
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to search images and load Excel file java using GroupDocs.Watermark
    Java to automate image searches in spreadsheets efficiently.
  headline: How to Search Images in Excel with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to search images and load Excel file java using GroupDocs.Watermark
    Java to automate image searches in spreadsheets efficiently.
  name: How to Search Images in Excel with GroupDocs.Watermark Java
  steps:
  - name: '**Document Management Systems:** Automatically index and tag spreadsheets
      based on embedded logos or product photos.'
    text: '**Document Management Systems:** Automatically index and tag spreadsheets
      based on embedded logos or product photos.'
  - name: '**Data Auditing:** Verify that visual data (charts, screenshots) has not
      been altered by comparing DCT hashes across versions.'
    text: '**Data Auditing:** Verify that visual data (charts, screenshots) has not
      been altered by comparing DCT hashes across versions.'
  - name: '**Content Verification:** Ensure only authorized brand assets appear in
      financial reports or marketing decks.'
    text: '**Content Verification:** Ensure only authorized brand assets appear in
      financial reports or marketing decks.'
  type: HowTo
- questions:
  - answer: It supports XLSX, XLS, CSV, and ODS, handling both legacy and modern workbook
      structures.
    question: What file formats can GroupDocs.Watermark read for Excel?
  - answer: Yes, by setting `SpreadsheetSearchableObjects.All` you can include floating
      pictures, charts, and other drawing objects.
    question: Can I search for images that are not attached (e.g., floating shapes)?
  - answer: The algorithm achieves > 95 % similarity detection for resized or slightly
      recolored images, making it ideal for branding checks.
    question: How accurate is DCT hash matching?
  - answer: Absolutely. After locating a `Watermark`, call `watermarker.replace(watermark,
      newImagePath)` to swap the graphic.
    question: Is it possible to replace found images automatically?
  - answer: Yes, GroupDocs.Watermark is pure Java and runs on any platform with a
      compatible JRE, including Docker‑based Linux containers.
    question: Does the library work on Linux containers?
  type: FAQPage
title: 如何在 Excel 中使用 GroupDocs.Watermark Java 搜尋圖片
type: docs
url: /zh-hant/java/spreadsheet-document-watermarking/excel-image-search-groupdocs-watermark-java/
weight: 1
---

# 如何在 Excel 中使用 GroupDocs.Watermark Java 搜尋圖像

在 Excel 活頁簿中搜尋特定圖像可能相當繁瑣，尤其是面對大型檔案或大量嵌入式圖形時。**How to search images** 迅速成為自動化文件工作流程者的關鍵問題。本指南將向您展示如何使用 GroupDocs.Watermark Java 在 Excel 試算表中搜尋圖像，同時說明如何有效地 **load Excel file java** 專案的必要步驟。

## 快速解答
- **最快的方式是什麼來定位嵌入的圖像？** Use `ImageDctHashSearchCriteria` with `SpreadsheetSearchableObjects.AttachedImages`.  
- **我需要特別的授權嗎？** A temporary or trial license unlocks full search capabilities.  
- **需要哪個 Maven 相依性？** Add `com.groupdocs:groupdocs-watermark` to your `pom.xml`.  
- **我可以將搜尋限制在單一工作表嗎？** Yes, configure `SpreadsheetLoadOptions` with the sheet name.  
- **API 是執行緒安全的嗎？** All public methods are safe for concurrent use after proper initialization.  

`ImageDctHashSearchCriteria` 定義用於圖像比較的 DCT 雜湊。`SpreadsheetSearchableObjects.AttachedImages` 將搜尋限制於嵌入的圖片。

## 在 GroupDocs.Watermark 中「how to search images」是什麼？
**「How to search images」** 指的是使用 Watermarker API 以程式方式定位文件內嵌的圖片物件。此函式庫會掃描每個工作表，提取圖片物件，計算其離散餘弦轉換 (DCT) 雜湊，並與目標圖像的雜湊進行比較，將任何匹配項作為水印物件返回，以便進一步處理。

## 為何在 Excel 圖像搜尋中使用 GroupDocs.Watermark？
GroupDocs.Watermark 支援 **超過 50 種輸入與輸出格式**——包括 XLSX、XLS、CSV 與 ODS——同時在不將整個檔案載入記憶體的情況下處理多百頁的活頁簿。其 DCT‑hash 演算法能以 > 95 % 的準確度辨識視覺上相似的圖像，顯著降低誤報。此外，函式庫提供串流存取，讓您能處理大於可用記憶體的檔案，並內建支援受密碼保護的活頁簿，適合企業級自動化流程。

## 前置條件

在開始之前，請確保您已具備：

- **Java Development Kit (JDK) 8+** 已安裝並在 `PATH` 中設定。  
- **Maven** 用於相依性管理（或您也可以手動下載 JAR）。  
- 一份 **GroupDocs.Watermark 授權**（試用、臨時或永久）以解鎖搜尋 API。  
- 具備 Java 集合與例外處理的基本知識。  

### 必要的函式庫與相依性
- **Maven 設定：** 將 GroupDocs 儲存庫與相依性加入 `pom.xml`。  
- **Java Development Kit (JDK)：** 需要 8 版或更高。  

### 環境設定需求
確保您的系統已正確安裝 Java，並在選擇此安裝方式時同時安裝 Maven 以管理相依性。

### 知識前提
具備 Java 程式設計的基本概念以及以程式方式處理 Excel 檔案的經驗將會有幫助。若您對此尚未熟悉，建議先參考入門資源。

## 如何為 Java 設定 GroupDocs.Watermark？
載入您的 Maven 專案，加入相依性，並以適當的設定初始化 Watermarker。此兩步驟流程可讓您準備好開始搜尋。首先，將 Maven 儲存庫與相依性加入 `pom.xml`，接著建立 Watermarker 實例，傳入 Excel 檔案路徑與 `WatermarkLoadOptions` 物件，以指定欲搜尋的工作表與設定。`SpreadsheetLoadOptions` 允許您指定要載入的工作表並設定搜尋選項，例如大小寫敏感度。`Watermarker` 是載入文件及執行搜尋或水印操作的主要入口。

``` 
```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```
```

## 如何以特定搜尋設定載入 Excel 檔案 java？
載入活頁簿，同時指示函式庫僅檢視附加的圖像。此聚焦方式可將一般試算表的處理時間縮短最多 **30 %**。

``` 
```java
import com.groupdocs.watermark.Watermarker;
// Basic initialization code here...
```
```

## 如何設定搜尋僅針對附加圖像？
`SpreadsheetSearchableObjects` 列舉允許您精確指定要掃描的項目。將其設定為 `AttachedImages` 可將引擎限制於圖片物件，忽略文字、公式或圖表。

``` 
```java
import com.groupdocs.watermark.WatermarkerSettings;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

WatermarkerSettings settings = new WatermarkerSettings();
settings.getSearchableObjects().setSpreadsheetSearchableObjects(SpreadsheetSearchableObjects.AttachedImages);
```
```

## 如何使用 DCT 雜湊條件執行圖像搜尋？
DCT‑hash 方法會為參考圖像產生緊湊的指紋，並與每個嵌入的圖片進行比較，返回具有高度視覺相似度的匹配項。

``` 
```java
import com.groupdocs.watermark.Watermarker;

String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker(filePath, loadOptions, settings);
```
```

## 如何定義 DCT 雜湊搜尋條件？
`ImageDctHashSearchCriteria` 包含參考圖像與可選的相似度閾值。您可以調整閾值（0‑100）以收緊或放寬匹配。

``` 
```java
// Reuse the previous configuration from the 'Load Spreadsheet' section.
```
```

## 如何執行搜尋並處理結果？
呼叫 `watermarker.search(criteria)` 會返回 `Watermark` 物件的集合。遍歷此集合即可取得頁碼、儲存格位址，或替換圖像。

``` 
```java
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;

String imagePath = "YOUR_DOCUMENT_DIRECTORY/sample_image.png";
ImageDctHashSearchCriteria criteria = new ImageDctHashSearchCriteria(imagePath);
```
```

## 實務應用
以下是這些功能在實務中發揮效益的情境：

1. **文件管理系統：** 自動根據嵌入的商標或產品照片為試算表建立索引與標籤。  
2. **資料稽核：** 透過比較不同版本的 DCT 雜湊，驗證視覺資料（圖表、螢幕截圖）未被更改。  
3. **內容驗證：** 確保財務報告或行銷簡報中僅出現授權的品牌資產。  

## 效能考量
為了讓您的應用程式保持快速：

- **將搜尋範圍** 限定於 `AttachedImages`；平均可降低約 30 % 的 CPU 使用率。  
- **分段處理大型檔案**，透過載入單一工作表而非整個活頁簿。  
- **在多次搜尋間重複使用 `WatermarkerSettings`**，以避免重複建立物件。  
- **使用 Java 效能分析工具監控記憶體**；函式庫會串流資料，但極大圖像仍可能影響堆積使用量。  

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方案 |
|---|---|---|
| 未返回結果 | 搜尋物件設定為 `None` | 設定為 `SpreadsheetSearchableObjects.AttachedImages`。 |
| `OutOfMemoryError` 發生於 500 頁檔案 | 整個活頁簿載入記憶體 | 使用 `SpreadsheetLoadOptions` 並呼叫 `setLoadAllSheets(false)`，逐一載入工作表。 |
| 雜湊比較產生誤報 | 閾值過低（例如 30） | 將相似度閾值提升至 80‑90，以加強匹配嚴格度。 |

## 常見問答

**Q: GroupDocs.Watermark 能讀取哪些 Excel 檔案格式？**  
A: 它支援 XLSX、XLS、CSV 與 ODS，能處理舊版與新版的活頁簿結構。

**Q: 我可以搜尋未附加的圖像（例如浮動形狀）嗎？**  
A: 可以，將 `SpreadsheetSearchableObjects.All` 設定為搜尋範圍，即可包含浮動圖片、圖表及其他繪圖物件。

**Q: DCT 雜湊匹配的準確度如何？**  
A: 此演算法在重新調整大小或稍微變色的圖像上可達 > 95 % 的相似度偵測，適合品牌檢查。

**Q: 能自動替換找到的圖像嗎？**  
A: 完全可以。定位到 `Watermark` 後，呼叫 `watermarker.replace(watermark, newImagePath)` 以交換圖形。

**Q: 此函式庫能在 Linux 容器上運行嗎？**  
A: 能，GroupDocs.Watermark 完全基於 Java，可在任何具相容 JRE 的平台上執行，包括基於 Docker 的 Linux 容器。

## 結論
在本教學中，我們從環境設定到執行 DCT‑hash 基礎的搜尋，完整說明了如何使用 GroupDocs.Watermark Java 在 Excel 活頁簿中 **how to search images**。透過將掃描限制於附加圖像並利用強大的雜湊比較，您可大幅加速圖像驗證工作流程，同時保持高準確度。接下來，您可以探索函式庫的水印添加功能，或將搜尋邏輯整合至更大的文件處理管線中。

---

**最後更新：** 2026-06-01  
**測試版本：** GroupDocs.Watermark 23.12 for Java  
**作者：** GroupDocs  

**資源**  
- **文件說明：** [GroupDocs.Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API 參考：** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **下載：** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)

```java
import com.groupdocs.watermark.PossibleWatermarkCollection;

PossibleWatermarkCollection possibleWatermarks = watermarker.search(criteria);
```

## 資源
- [GroupDocs.Watermark for Java 版本發佈](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark Java 文件說明](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs API 參考](https://reference.groupdocs.com/watermark/java)
- [GroupDocs 下載](https://releases.groupdocs.com/watermark/java/)

## 相關教學

- [使用 GroupDocs.Watermark Java SDK 為 Excel 試算表添加圖像水印](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [使用 GroupDocs.Watermark for Java 替換 Excel 形狀中的圖像：完整指南](/watermark/java/spreadsheet-document-watermarking/replace-images-excel-shapes-groupdocs-watermark-java/)
- [在 Java 中使用 GroupDocs.Watermark 保護您的 Excel 試算表](/watermark/java/spreadsheet-document-watermarking/protect-excel-spreadsheets-groupdocs-watermark-java/)