---
date: '2026-03-27'
description: 了解如何使用 GroupDocs.Watermark for Java 為 Excel 檔案添加浮水印。本指南將逐步說明設定、程式碼以及在試算表中加入浮水印的最佳實踐。
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: 使用 GroupDocs.Watermark Java 為 Excel 添加水印
type: docs
url: /zh-hant/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark Java 為 Excel 添加浮水印

為 Excel 檔案添加浮水印可以帶來顯著的效益——無論是需要保護敏感資料、為報告加上品牌標誌，或只是想增添專業感。在本教學中，您將學習 **如何為 Excel 添加浮水印** 試算表，提供清晰說明、實務案例以及避免常見問題的技巧。

## 快速解答
- **需要哪個函式庫？** GroupDocs.Watermark for Java（最新版本）。  
- **支援哪些 Excel 格式？** .xlsx 與 .xls 檔案（未加密）。  
- **可以添加圖片浮水印嗎？** 可以——SDK 同時支援文字與圖片浮水印。  
- **正式環境需要授權嗎？** 非試用部署必須購買商業授權。  
- **實作需要多久？** 基本文字浮水印大約需要 10‑15 分鐘。

## 什麼是 **在 Excel 中添加浮水印**？
在 Excel 活頁簿中添加浮水印，表示在每個工作表或嵌入的文件上蓋上一層可見（或半透明）的文字或圖片。這可協助您聲明所有權、標示機密性，或在整個檔案中加強品牌形象。

## 為何使用 GroupDocs.Watermark for Java？
GroupDocs.Watermark 提供高階 API，抽象化處理 Office Open XML 結構的複雜性。它讓您能夠：

- 一次呼叫即可對多個工作表套用浮水印。  
- 自動處理嵌入的附件（例如嵌入的 PDF）。  
- 保留原始格式與公式。  
- 同時支援文字與圖片浮水印（例如 **add image watermark java**）。

## 前置條件

- **Java 開發環境** – Java 8 或更高（JDK）。  
- **GroupDocs.Watermark for Java SDK** – 從 [here](https://releases.groupdocs.com/watermark/java/) 下載最新版本。  
- **IDE** – IntelliJ IDEA、Eclipse 或任何相容 Java 的編輯器。  
- **範例試算表** – 您想要保護的 .xlsx 檔案。

您可以透過 Maven、Gradle，或手動將 JAR 檔案放入 classpath 來將 SDK 加入專案。

## 匯入套件

以下匯入讓您取得核心浮水印類別、試算表處理與字型工具。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## 如何 **為試算表加浮水印** – 步驟說明

以下是一個實用的編號步驟說明，精確展示 **如何為試算表加浮水印** 的 Java 實作。每一步都包含簡短說明，並附上原始程式碼區塊（保持不變）。

### 步驟 1：設定浮水印物件  
**為何？** 此物件定義您將套用的印章之視覺外觀。

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### 步驟 2：載入試算表  
**為何？** 開啟活頁簿讓 SDK 取得可編輯的句柄。

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### 步驟 3：存取試算表內容與工作表  
**為何？** Excel 檔案可能包含多個工作表；您需要逐一遍歷。

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### 步驟 4：遍歷每個工作表中的附件  
**為何？** 某些工作表會嵌入其他文件（例如 PDF）。處理它們可確保整個檔案的浮水印一致。

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### 步驟 5：為每個附加文件加浮水印  
**為何？** 您希望在每個嵌入的文件上都有相同的「機密」印章。

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### 步驟 6：儲存所有變更  
**為何？** 將修改持久化至新活頁簿。

```java
watermarker.save("your-output-file.xlsx");
```

### 步驟 7：關閉資源  
**為何？** 釋放資源可防止記憶體洩漏，特別是在處理大型活頁簿時。

```java
watermarker.close();
```

## 整合示範：完整範例

以下類別將每個步驟整合為單一可執行的程式。**請勿修改程式碼區塊**——它與原始範例完全相同。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## 常見問題與解決方案

| 問題 | 為何發生 | 解決方案 |
|-------|----------------|-----|
| **加密的活頁簿被跳過** | SDK 無法在未提供密碼的情況下讀取加密檔案。 | 先解密檔案，或透過 `SpreadsheetLoadOptions.setPassword("pwd")` 提供密碼。 |
| **浮水印在某些工作表上不可見** | 該工作表可能有自訂檢視或保護，導致繪圖物件被隱藏。 | 在加入浮水印前先停用工作表保護，必要時再重新啟用。 |
| **大型檔案效能下降** | 將整個活頁簿載入記憶體可能會佔用大量資源。 | 分批處理工作表或增加 JVM 堆積大小（`-Xmx2g`）。 |
| **圖片浮水印變形** | 縮放設定不正確。 | 使用 `ImageWatermark` 並明確設定寬度/高度參數，以維持長寬比。 |

## 常見問答

**問：可以改用圖片浮水印而非文字嗎？**  
A: 可以。使用 SDK 提供的 `ImageWatermark`，並傳入 `java.awt.Image` 物件。這符合 **add image watermark java** 情境。

**問：如何控制浮水印的位置？**  
A: `TextWatermark`（或 `ImageWatermark`）類別提供 `setHorizontalAlignment`、`setVerticalAlignment`、`setOpacity` 等屬性，以微調位置與透明度。

**問：能否在一次執行中為多個 Excel 檔案加浮水印？**  
A: 完全可以。將整個工作流程包在 `for` 迴圈中，遍歷目錄內的檔案，並重複使用同一個 `TextWatermark` 物件。

**問：如果試算表包含圖表會怎樣？**  
A: 圖表被視為獨立的繪圖物件；浮水印會加在工作表畫布上，圖表本身不受影響，但仍會被半透明的印章覆蓋。

**問：能否移除先前加入的浮水印？**  
A: SDK 提供 `watermarker.remove(watermark)` 方法，但您必須保留原始浮水印物件的參考，或透過文字/內容搜尋來定位它。

---

**最後更新：** 2026-03-27  
**測試環境：** GroupDocs.Watermark 23.12 (Java)  
**作者：** GroupDocs