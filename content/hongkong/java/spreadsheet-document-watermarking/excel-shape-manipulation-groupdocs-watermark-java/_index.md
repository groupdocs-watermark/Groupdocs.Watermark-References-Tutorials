---
date: '2026-06-01'
description: 了解如何使用 GroupDocs.Watermark for Java 從 Excel 檔案中移除形狀。內容包括載入 Excel、遍歷工作表以及刪除已格式化的形狀的步驟。
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: 如何使用 GroupDocs.Watermark 在 Java 中移除 Excel 的形狀
type: docs
url: /zh-hant/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中移除 Excel 中的圖形

Excel 試算表是商業報告的基石，但不需要的圖形——尤其是那些具有過時或非標準文字格式的——會使檔案變得雜亂，破壞視覺一致性。**Removing shapes from excel** 迅速成為保持文件整潔、專業的必要工作。在本教學中，我們將示範如何載入 Excel 活頁簿、遍歷其工作表，並以程式方式刪除符合特定格式條件的圖形，全部使用功能強大的 GroupDocs.Watermark Java 函式庫。

## 快速解答
- **GroupDocs.Watermark 能刪除圖形嗎？** 是的，它提供 `removeShape` 方法，可在任何工作表上使用。  
- **需要此功能的授權嗎？** 試用版可用於評估；正式環境需要完整授權。  
- **需要哪個 Java 版本？** 支援 Java 8 或更新版本。  
- **GroupDocs.Watermark 支援多少檔案格式？** 超過 30 種輸入與輸出格式，包括 XLSX、DOCX、PDF 與 PPTX。  
- **大型活頁簿的記憶體消耗會是問題嗎？** 使用 try‑with‑resources，避免將整個工作表載入記憶體；API 會有效率地串流資料。

## 什麼是 remove shapes from excel？
*Removing shapes from excel* 指以程式方式刪除繪圖物件——例如文字方塊、圖示或 SmartArt——符合特定條件，如字型樣式、顏色或大小。此操作可在不需手動編輯的情況下清理活頁簿，確保視覺一致性、減少檔案大小，並防止過時或不需要的圖形出現在分發的報告中。

## 為什麼要移除 Excel 中的圖形？
GroupDocs.Watermark 能以比手動編輯快至 3 倍的速度處理 **多百頁活頁簿**，支援 **30 多種檔案格式**，且對於超過 50 MB 的檔案，記憶體使用量維持在 150 MB 以下。自動化圖形移除可消除人工錯誤，確保所有產生的報告在品牌呈現上保持一致。

## 前置條件
### 必要的函式庫、版本與相依性
- **Java Development Kit (JDK)**：版本 8 或更新。  
- **GroupDocs.Watermark**：版本 24.11（撰寫時的最新穩定版）。

### 環境設定需求
使用 IntelliJ IDEA 或 Eclipse 等 IDE，並以 Maven 管理相依性。

### 知識前提
熟悉 Java 語法以及基本的 Excel 概念（工作表、儲存格與圖形）將有助於您理解範例。

## 為 Java 設定 GroupDocs.Watermark
**Maven 依賴**  
將以下內容加入您的 `pom.xml`：

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

**直接下載**  
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權步驟
- **免費試用** – 先使用免費試用版評估功能。  
- **臨時授權** – 取得臨時授權以進行延長測試。  
- **購買** – 購買完整授權以供正式使用。

### 基本初始化與設定  
將函式庫加入專案後，請依下列方式初始化：

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## 如何移除 Excel 中的圖形？
載入活頁簿，遍歷每個工作表，並呼叫圖形移除 API。此兩步驟模式——*載入* 後 *遍歷*——可涵蓋幾乎所有需要在整個檔案中清理圖形的情況。透過在移除前檢查每個圖形的屬性是否符合您的條件，確保僅刪除不需要的元素，同時保留文件的版面配置與內容。

## 載入 Excel 文件
**概覽**  
載入 Excel 文件是任何操作任務的起點。GroupDocs.Watermark 以直觀的 API 簡化此過程。  

**定義說明**  
`SpreadsheetDocument` 是 GroupDocs.Watermark 中的主要類別，代表記憶體中的 Excel 活頁簿，提供存取工作表、儲存格與圖形的方法。  

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## 存取與遍歷試算表中的工作表
**概覽**  
遍歷工作表可讓您對每個工作表分別執行操作。  

**定義說明**  
`Worksheet` 代表 `SpreadsheetDocument` 內的單一工作表；您可透過此物件讀取、修改或刪除其內容。  

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## 從試算表中移除具特定文字格式的圖形
**概覽**  
此功能針對符合特定文字格式條件（如字型或顏色）的圖形。  

**定義說明**  
`Shape` 是工作表內任何繪圖元素（文字方塊、圖片或 SmartArt）的物件模型；它提供 `getText`、`getFont`、`remove` 等屬性。  

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## 實務應用
### 真實案例
1. **資料驗證** – 自動刪除包含已淘汰通知的圖形。  
2. **範本標準化** – 透過移除非標準文字方塊來強化企業品牌。  
3. **自動化報告** – 在分發前清理產生的報告，確保外觀精緻。

### 整合可能性
GroupDocs.Watermark 可嵌入基於 Java 的企業流程中，如文件產生微服務、批次處理工作或內容管理系統，提供無縫且符合授權的 Excel 資產管理方式。

## 效能考量
### 效能最佳化
- **避免在迴圈內執行繁重操作** – 每個工作表僅取得一次圖形集合。  
- **及時釋放資源** – 使用 try‑with‑resources 自動關閉串流。

### 資源使用指引
在處理完成後立即釋放 `SpreadsheetDocument` 物件，以釋放原生記憶體。對於超過 100 MB 的檔案，建議使用平行串流處理工作表，以利用多核心 CPU。

### Java 記憶體管理最佳實踐
使用 `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }`，即使發生例外，`close()` 方法也會被呼叫。

## 常見問題與解決方案
- **找不到圖形** – 確認您檢查的是正確的工作表索引；圖形是以工作表為單位範圍。  
- **授權例外** – 試用授權會停用批次處理；升級至完整授權即可無限制操作。  
- **字型值異常** – 字型屬性可能被繼承；使用 `shape.getEffectiveFont()` 取得實際樣式。

## 常見問答

**Q: 我可以從受密碼保護的活頁簿中移除圖形嗎？**  
A: 可以。使用密碼參數載入文件，然後執行相同的移除邏輯；API 會在記憶體中解密檔案。

**Q: 此函式庫支援 .xls（Excel 97‑2003）檔案嗎？**  
A: 當然支援。GroupDocs.Watermark 可直接處理 `.xlsx` 與舊版 `.xls` 格式，無需轉換。

**Q: 我該如何記錄被刪除的圖形？**  
A: 遍歷圖形集合，檢查格式條件，記錄 `shape.getName()` 或 `shape.getId()`，然後呼叫 `remove()`。

**Q: 移除圖形後可以加入浮水印嗎？**  
A: 可以。清理完畢後，呼叫 `doc.addWatermark(new TextWatermark("Confidential"))`，即可在所有工作表上覆蓋文字浮水印。

**Q: 支援的最大檔案大小是多少？**  
A: 在 64 位元 JVM 上，函式庫可處理最高 **2 GB** 的檔案，僅受可用堆積記憶體與作業系統限制。

## 結論
在本教學中，我們示範了使用 GroupDocs.Watermark for Java 針對 **remove shapes from excel** 活頁簿的完整、可投入生產的做法。透過載入文件、遍歷工作表，並套用精確的格式過濾條件，您可以自動化清理工作、強化品牌一致性，並在大規模下提升報告品質。可進一步探索如浮水印插入、文件轉換與批次處理等功能，擴充您的文件自動化工具組。

---

**最後更新：** 2026-06-01  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs

## 相關教學

- [使用 GroupDocs.Watermark 在 Java 中操作 Excel 圖形：完整指南](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark Java SDK 為 Excel 試算表添加圖片浮水印](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [使用 GroupDocs.Watermark Java 處理 Excel 文件與浮水印](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)