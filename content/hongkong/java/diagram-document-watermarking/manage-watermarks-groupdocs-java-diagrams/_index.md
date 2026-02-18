---
date: '2026-02-18'
description: 學習如何使用 GroupDocs.Watermark for Java 為 .vsdx 等圖表檔案添加水印以及移除水印。使用 GroupDocs
  Watermark Java 保護文件完整性。
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: 如何使用 GroupDocs.Watermark for Java 為圖表添加水印
type: docs
url: /zh-hant/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# 如何使用 GroupDocs.Watermark for Java 為圖表添加水印

在圖表檔案中管理水印是保護智慧財產權及確保文件在公開發佈時保持乾淨的核心工作。本指南將教您 **如何添加水印** 到 Visio 圖表，以及在不再需要時 **如何移除水印**，全部使用 **groupdocs watermark java** 函式庫。無論您是構建企業級文件流程，或是快速工具腳本，這些步驟都能讓您完整掌控圖表水印。

## 快速解答
- **什麼函式庫在 Java 中處理圖表水印？** GroupDocs.Watermark for Java.  
- **我可以在同一次執行中同時添加與移除水印嗎？** 可以 – 只需載入圖表一次，即可同時執行添加與移除操作。  
- **支援哪些檔案格式？** Visio 格式，例如 `.vsdx`、`.vdx`，以及其他圖表類型。  
- **我需要授權嗎？** 試用授權可用於開發；正式授權則需於生產環境使用。  
- **需要哪個版本的 Java？** JDK 8 或更高版本。

## 在圖表情境中「如何添加水印」是什麼意思？

添加水印是指將可見或不可見的標記（文字、標誌或圖片）嵌入圖表檔案中。此標記會隨檔案一起傳遞，方便證明所有權或標示草稿版本。

## 為什麼使用 GroupDocs.Watermark for Java？

* **功能豐富的 API** – 只需幾行程式碼即可搜尋、添加與刪除文字與圖片水印。  
* **跨格式支援** – 可處理 Visio（`.vsdx`、`.vdx`）以及其他多種圖表類型。  
* **效能導向** – 僅載入執行水印操作所需的圖表部份，降低記憶體使用量。

## 前置條件
1. **Java Development Kit (JDK) 8+** – 確認 `java -version` 顯示 1.8 或更新版本。  
2. **IDE** – IntelliJ IDEA、Eclipse，或您偏好的任何編輯器。  
3. **GroupDocs.Watermark for Java** – 透過 Maven 或直接下載 JAR 的方式加入至您的專案。

### 必要的函式庫與相依性
將以下儲存庫與相依性加入您的 `pom.xml`：

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

*如果您不想使用 Maven，也可以從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 JAR。*

### 取得授權
- **免費試用：** 無需授權金鑰即可測試所有功能。  
- **臨時授權：** 申請限時金鑰以進行評估。  
- **正式授權：** 購買訂閱以在生產環境中無限制使用。

## 設定 GroupDocs.Watermark for Java
1. **加入函式庫** 至您的專案（Maven 或手動 JAR）。  
2. **建立 `Watermarker` 實例** – 此物件是載入圖表、搜尋、添加與移除水印的入口。

## 實作指南

### 載入圖表文件
在您能 **添加水印** 或 **移除水印** 之前，必須先載入圖表。以下程式碼示範如何使用自訂載入選項開啟 `.vsdx` 檔案。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### 搜尋文字水印
在添加新水印之前，您可能想先確認是否已存在文字水印。此程式碼片段搜尋短語「Company Name」。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### 搜尋圖片水印
若需定位作為水印的標誌或任何圖片，請使用 `ImageDctHashSearchCriteria`。當您想 **移除水印** 且符合已知標誌時，這非常方便。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### 移除水印
當您已辨識出文字、水印或兩者皆有時，即可將其從圖表中清除。以下範例示範結合式的移除操作。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## 實務應用
1. **企業軟體整合** – 將水印管理嵌入 ERP 或文件產生平台，以強化品牌一致性。  
2. **內容管理系統 (CMS)** – 自動掃描上傳的圖表，偵測未授權的標誌並將其移除。  
3. **法律文件處理** – 在草稿階段添加「機密」文字水印，最終提交前再 **移除水印**。

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方法 |
|------|----------|----------|
| 未找到任何水印 | 搜尋的文字/圖片未完全相符 | 使用 `or()` 結合條件或調整大小寫敏感設定。 |
| 大型檔案出現 `OutOfMemoryError` | 圖表被完整載入記憶體 | 使用 `DiagramLoadOptions.setLoadPages()` 僅載入所需頁面。 |
| 儲存的檔案損毀 | `watermarker.save()` 在清除所有水印之前被呼叫 | 確保 `possibleWatermarks.clear()` 完成，且在儲存後呼叫 `watermarker.close()`。 |

## 常見問答

**Q: 我可以同時搜尋文字與圖片嗎？**  
A: 可以。將 `TextSearchCriteria` 與 `ImageDctHashSearchCriteria` 使用 `or()` 方法結合，如移除範例所示。

**Q: 是否能在不損壞圖表的情況下移除水印？**  
A: 絕對可以。函式庫會將水印物件獨立，呼叫 `clear()` 只會移除水印層，保留原始圖表內容。

**Q: GroupDocs.Watermark 是否支援多種圖表格式？**  
A: 支援。`.vsdx`、`.vdx` 以及其他相容 Visio 的檔案皆完整支援。

**Q: 如何有效處理大量文件？**  
A: 實作批次處理迴圈，盡可能重複使用單一 `Watermarker` 實例，並使用 `DiagramLoadOptions` 限制頁面載入。

**Q: 有辦法在 CI/CD 流程中自動偵測水印嗎？**  
A: 您可以將提供的 Java 程式碼片段嵌入建置腳本（例如 Maven 或 Gradle），於發佈產出前驗證是否存在未授權的水印。

---

**最後更新：** 2026-02-18  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs