---
date: '2025-12-19'
description: 學習如何使用 GroupDocs Watermark Maven 於 Java 中管理 .vsdx 等圖表檔案的浮水印，以提升文件完整性並保護智慧財產權。
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark Maven – 使用 Java 管理圖表水印
type: docs
url: /zh-hant/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – 使用 Java 管理圖表浮水印

在文件中管理浮水印對於保護智慧財產權與維持文件完整性至關重要。**在本教學中，我們將示範如何使用 groupdocs watermark maven 高效載入、搜尋及移除 `.vsdx` 等圖表檔案中的浮水印**。無論您是開發企業軟體或自動化文件工作流程，精通這些技巧都能讓您全面掌控圖表浮水印的管理。

## 快速解答
- **需要的函式庫是什麼？** GroupDocs.Watermark for Java（可透過 Maven 取得）。  
- **支援哪些圖表格式？** `.vsdx`、`.vdx` 以及其他 Visio 格式。  
- **可以同時搜尋文字與圖片浮水印嗎？** 可以 – 使用 `or()` 結合搜尋條件。  
- **正式環境需要授權嗎？** 需要有效的 GroupDocs.Watermark 授權。  
- **如何將其整合至 Maven？** 在下方加入儲存庫與相依性設定。

## 什麼是 groupdocs watermark maven？
`groupdocs watermark maven` 指的是基於 Maven 的 GroupDocs.Watermark Java 函式庫整合。只要在 `pom.xml` 中聲明此函式庫，Maven 會自動解析所有必要的二進位檔，讓您專注於載入圖表、搜尋浮水印以及以程式方式移除它們的程式碼。

## 為何使用 GroupDocs.Watermark 來管理圖表浮水印？
- **功能完整的 API** – 支援多種圖表類型的文字、圖片與形狀浮水印。  
- **精準移除** – 在不破壞原始圖表版面配置的情況下消除浮水印。  
- **具擴充性** – 適用於批次處理大量圖表。  
- **Maven 友好** – 簡易的相依性管理，保持專案整潔。

## 前置條件
1. **Java Development Kit (JDK) 8+** – 確保與函式庫相容。  
2. **IDE** – 如 IntelliJ IDEA、Eclipse 或任何支援 Java 的編輯器。  
3. **GroupDocs.Watermark for Java** – 透過 Maven（建議）或直接下載 JAR 加入。  

### 必要的函式庫與相依性
#### Maven 設定
將以下設定加入您的 `pom.xml` 檔案：

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

#### 直接下載
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權
- **免費試用：** 使用試用授權測試函式庫。  
- **臨時授權：** 申請短期金鑰以進行評估。  
- **購買：** 取得正式授權以無限制使用。  

## 使用 groupdocs watermark maven 載入圖表文件
載入圖表文件是執行任何浮水印操作的第一步。以下是一個最小範例，示範如何使用 `DiagramLoadOptions` 建立 `Watermarker` 實例。

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

- **參數：**  
  - `inputFilePath` – 您的 `.vsdx` 檔案路徑。  
  - `loadOptions` – 讓您控制圖表的解析方式（例如密碼保護）。  

## 使用 groupdocs watermark maven 搜尋浮水印
### 文字浮水印
要定位文字型浮水印，請定義 `TextSearchCriteria` 並對圖表的第一頁進行查詢。

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

- **關鍵方法：**  
  - `TextSearchCriteria` – 指定要搜尋的精確文字。  
  - `PossibleWatermarkCollection` – 儲存找到的所有匹配項目。  

### 圖片浮水印
如果圖表中包含標誌或圖片浮水印，請使用 `ImageDctHashSearchCriteria` 與參考圖像進行比對。

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

- **關鍵方法：**  
  - `ImageDctHashSearchCriteria` – 為參考圖像產生感知雜湊，以實現穩健的匹配。  

## 移除浮水印
當您識別出不需要的浮水印後，即可將其清除並儲存圖表的乾淨副本。

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

- **關鍵方法：** `clear()` 會移除所有符合組合條件的浮水印，保持圖表完整不變。

## 實務應用
1. **企業軟體整合** – 將浮水印管理嵌入商業應用，以保護專有圖表。  
2. **內容管理系統 (CMS)** – 在發佈前自動偵測並移除未授權的標誌。  
3. **法律文件工作流程** – 在合約處理的不同階段加入或移除浮水印。  

## 常見問題與故障排除
- **授權錯誤：** 在建立 `Watermarker` 前，確保正確引用授權檔案。  
- **大型檔案：** 使用串流 API 或將 JVM 堆積大小提升（如 `-Xmx2g`）以處理超過 100 MB 的圖表。  
- **找不到浮水印：** 確認搜尋條件（文字大小寫、圖片相似度閾值）與實際浮水印內容相符。  

## 常見問答

**Q: 可以同時搜尋文字與圖片嗎？**  
A: 可以。如移除範例所示，使用 `or()` 結合條件。

**Q: 移除浮水印會不會影響圖表版面配置？**  
A: 絕對不會。API 精準定位浮水印物件，保留其他所有圖表元素。

**Q: GroupDocs.Watermark 支援哪些圖表格式？**  
A: 支援 Visio 格式如 `.vsdx`、`.vdx`，以及其他向量圖表類型。

**Q: 如何有效處理數百個圖表？**  
A: 實作批次迴圈，盡可能重複使用單一 `Watermarker` 實例，並考慮使用 Java 的 `ExecutorService` 進行平行處理。

**Q: 能否將浮水印偵測整合至 CI/CD 流程？**  
A: 可以。將 Java 程式碼片段加入建置腳本（例如 Maven 插件或 Gradle 任務），於部署前驗證圖表。

## 結論
透過 **groupdocs watermark maven**，您即可使用 Java 以強大且受 Maven 管理的方式載入、搜尋與移除圖表檔案中的浮水印。此功能提升文件安全性、簡化內容工作流程，且能輕鬆擴展至大型文件集合。

---

**最後更新：** 2025-12-19  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs