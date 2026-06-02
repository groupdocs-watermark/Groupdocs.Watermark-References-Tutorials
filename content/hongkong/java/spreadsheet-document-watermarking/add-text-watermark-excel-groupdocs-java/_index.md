---
date: '2026-03-20'
description: 學習如何使用 GroupDocs.Watermark for Java 為 Excel 工作表添加浮水印，涵蓋 Excel 文字浮水印的添加以及
  Java 為 Excel 添加浮水印的技巧。
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: 如何使用 GroupDocs.Watermark Java 為 Excel 添加水印
type: docs
url: /zh-hant/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark for Java 為 Excel 試算表添加浮水印

在 Excel 檔案中加入 **how to add watermark** 功能是一種實用的方式，可保護敏感資料並主張所有權。在本步驟指南中，您將學習如何為 Excel 試算表添加浮水印、自訂其外觀，並將其放置於頁首或頁尾——全部使用 GroupDocs.Watermark for Java。

## 快速回答
- **需要的函式庫是什麼？** GroupDocs.Watermark for Java (24.11 或更新版本)。  
- **我可以自訂字型和顏色嗎？** 可以，使用 `Font` 和 `Color` 類別。  
- **浮水印會出現在何處？** 於所選工作表的頁首或頁尾。  
- **正式環境需要授權嗎？** 非試用使用時需擁有有效的 GroupDocs 授權。  
- **大型活頁簿能使用嗎？** 可以，但請關閉 `Watermarker` 物件以釋放資源。

## 介紹

您是否想透過添加文字浮水印來提升 Excel 試算表的安全性？無論是保護機密資料或主張所有權，將浮水印嵌入試算表的頁首或頁尾都相當有價值。在本教學中，我們將指導您如何使用 GroupDocs.Watermark for Java 實作此功能。

**您將學會**
- 為 Excel 試算表添加文字浮水印  
- 使用自訂字型與顏色設定浮水印  
- 在文件中設定頁首/頁尾對齊方式

掌握這些技能後，您將能有效保護試算表。現在，讓我們深入了解開始所需的前置條件。

## 在 Excel 中什麼是 “how to add watermark”

浮水印是一種淡淡的、半透明的文字或圖像，顯示在主要內容的背後（或前面）。在 Excel 中，浮水印通常放置於頁首或頁尾區域，讓其在每一列印頁面上顯示，同時不干擾儲存格資料。

## 為什麼使用 GroupDocs.Watermark for Java？

- **跨平台**：可在任何支援 Java 的作業系統上執行。  
- **完整控制**：自訂字型、大小、顏色與對齊方式。  
- **效能導向**：有效處理大型活頁簿。

## 前置條件

- **GroupDocs.Watermark for Java**（24.11 或更新版本）  
- **Java Development Kit (JDK)** 已安裝並設定  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE  
- Maven（若您偏好相依性管理）  

### 必要的函式庫

- **GroupDocs.Watermark for Java** – 提供浮水印 API。

### 知識前置條件

- 基本的 Java 程式設計  
- 熟悉 Maven 或手動 JAR 處理  

## 設定 GroupDocs.Watermark for Java

您可以透過 Maven 安裝此函式庫，或直接下載 JAR 檔案。

**Maven 安裝**

Add the following configuration to your `pom.xml`:

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
另請從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權
- **免費試用** – 無償探索 API。  
- **臨時授權** – 延長評估期間。  
- **購買** – 完整功能、無限制使用。

To initialize GroupDocs.Watermark, include the import statement:

```java
import com.groupdocs.watermark.Watermarker;
```

## 如何為 Excel 試算表添加浮水印

以下提供完整可執行的程式碼，分為清晰的步驟。每個步驟在程式碼區塊前都有簡短說明，讓您不會看到沒有上下文的片段。

### 步驟 1：載入試算表

首先，使用適當的載入選項載入活頁簿。

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**說明**：此程式碼會建立與您的 Excel 檔案相關聯的 `Watermarker` 實例，準備進行浮水印操作。

### 步驟 2：建立文字浮水印

設定浮水印的視覺外觀。

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**說明**：我們設定浮水印文字，選擇粗體 **Segoe UI** 字型，並套用對比的前景與背景顏色。

### 步驟 3：設定浮水印位置

決定要將浮水印放置於哪個工作表以及頁面的哪個部分（頁首/頁尾）。

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**說明**：`SpreadsheetWatermarkHeaderFooterOptions` 物件告訴 API 將浮水印套用於第一張工作表的頁首/頁尾。

### 步驟 4：添加浮水印並儲存

套用浮水印並將結果寫入新檔案。

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**說明**：`add` 方法插入浮水印，`save` 寫入已修改的活頁簿，`close` 釋放資源。

## 為 Excel 添加文字浮水印 – 進階技巧

- **多工作表**：迴圈遍歷工作表索引，對每個工作表呼叫 `options.setWorksheetIndex(i)`。  
- **動態文字**：從資料庫或設定檔取得浮水印文字，以客製化每份文件。  
- **不透明度控制**：使用 `watermark.setOpacity(0.5)` 使浮水印更為淡化。  

## 常見問題與解決方案

| 問題 | 解決方案 |
|-------|----------|
| **找不到檔案** | 驗證路徑字串 (`YOUR_DOCUMENT_DIRECTORY/...`) 是否正確，測試時使用絕對路徑。 |
| **找不到授權** | 將 `GroupDocs.Watermark.lic` 檔案放在專案根目錄，或以程式方式設定授權：`License license = new License(); license.setLicense("path/to/license.lic");`。 |
| **不支援的格式** | 確保活頁簿已儲存為 `.xlsx` 或 `.xls`。較舊格式可能需要先轉換。 |
| **大型檔案效能延遲** | 一次處理一個工作表，完成每個檔案後立即呼叫 `watermarker.close()`。 |

## 實務應用

1. **機密資料保護** – 透過在每頁列印上顯示標記，阻止未授權的複製。  
2. **所有權主張** – 嵌入公司名稱或標誌作為浮水印，以證明文件來源。  
3. **文件追蹤** – 在浮水印中加入唯一識別碼，以追蹤分發路徑。  

## 效能考量

- 最小化每次執行的浮水印數量。  
- 及時關閉 `Watermarker` 物件以釋放檔案句柄。  
- 對於非常大的活頁簿，建議增加 JVM 堆積大小（`-Xmx2g`）。  

## 常見問答

**Q: 我可以更改浮水印的字型樣式嗎？**  
A: 可以，使用 `Font` 物件自訂任何已安裝的字型系列、大小，以及 `FontStyle`（粗體、斜體等）。

**Q: 能否為多個工作表添加浮水印？**  
A: 當然可以。迴圈遍歷工作表索引，對每個工作表套用相同的 `SpreadsheetWatermarkHeaderFooterOptions`。

**Q: GroupDocs.Watermark 支援哪些 Excel 檔案格式？**  
A: 完全支援 XLS、XLSX 以及其他 Office Open XML 試算表格式。

**Q: 如何有效處理非常大的文件？**  
A: 一次處理一個活頁簿，儲存後關閉 `Watermarker`，並監控 JVM 記憶體使用情況。

**Q: 需要時能移除浮水印嗎？**  
A: 雖未提供直接移除功能，但您可重新產生未套用浮水印的原始檔案，或保留未加浮水印的副本以備未來使用。

## 資源

- [GroupDocs.Watermark 文件說明](https://docs.groupdocs.com/watermark/java/)
- [API 參考文件](https://reference.groupdocs.com/watermark/java)
- [下載 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GitHub 程式庫](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/watermark/10)
- [臨時授權資訊](https://purchase.groupdocs.com/temporary-license/)

---

**最後更新：** 2026-03-20  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs