---
date: '2026-08-19'
description: 了解如何在 Java 中使用 GroupDocs.Watermark 替換圖表圖片，並有效地為圖表添加水印。提供逐步程式碼與最佳實踐。
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: 了解如何在 Java 中使用 GroupDocs.Watermark 替換圖表圖片，並有效地為圖表添加水印。提供逐步程式碼與最佳實踐。
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: 使用 GroupDocs.Watermark 在 Java 中替換圖表圖片
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: 使用 GroupDocs.Watermark 在 Java 中替換圖表圖片
type: docs
url: /zh-hant/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在 Java 中取代圖表圖像

手動在圖表檔案中更新圖像既耗時又容易出錯。在本教學中，您將學會如何僅用幾行程式碼 **在 Java 中取代圖表圖像**，同時也會看到在需要時 **為圖表加入浮水印** 的方法。完成後，您將擁有一段可直接放入任何使用 Visio、Draw.io 或其他支援圖表格式的 Java 專案的可重用程式碼片段。

## 快速解答
- **什麼程式庫負責圖表圖像取代？** GroupDocs.Watermark for Java.
- **基本取代需要多少行程式碼？** 只需在建立 Watermarker 後的三行程式碼。
- **我可以同時加入浮水印嗎？** 可以 – 使用相同的 Watermarker 實例搭配浮水印物件。
- **需要哪個 Java 版本？** JDK 8 或更高。
- **生產環境需要授權嗎？** 需要有效的 GroupDocs.Watermark 授權；可使用免費試用版。

## 什麼是 Java 圖表圖像取代？
在 Java 中取代圖表圖像指的是以程式方式在圖表檔案（如 .vsdx、.drawio 或 .svg）中尋找包含位圖圖形的形狀，並使用 GroupDocs.Watermark API 將這些內嵌圖像換成新圖像。此方式可自動化原本需要在圖表編輯器中手動編輯的更新工作。

## 為什麼使用 GroupDocs.Watermark 進行圖表圖像取代？
GroupDocs.Watermark 支援 **超過 50 種輸入與輸出格式**，包括 Visio、Draw.io 與 SVG，且可在不將整個文件載入記憶體的情況下處理 **最高 500 MB 的檔案**，相較於傳統檔案串流方式可減少 **30 % 的 CPU 使用率**。

## 前置條件
- 已安裝 JDK 8 或更新版本。
- Java 開發的 IDE（IntelliJ IDEA、Eclipse 或 VS Code）。
- Maven（或手動加入 JAR 的能力）。
- 有效的 GroupDocs.Watermark 授權（試用或永久）。可從 [GroupDocs](https://purchase.groupdocs.com/temporary-license/) 取得授權。

### 必要的函式庫、版本與相依性
將 GroupDocs.Watermark 的儲存庫與相依性加入您的 `pom.xml`：

```xml
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

如果您偏好手動管理 JAR，請從官方網站下載最新發行版： [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)。

## 如何在 Java 中逐步取代圖表圖像

### 如何為圖表檔案初始化 Watermarker？
Watermarker 是代表文件並提供內容操作方法的主要類別。首先，建立一個 `Watermarker` 物件將圖表檔案載入記憶體。`Watermarker` 類別是 GroupDocs.Watermark 的核心入口，允許您讀取、修改與儲存文件。使用 `DiagramLoadOptions` 可指定格式特定的設定，例如 DPI 或頁面範圍。`DiagramLoadOptions` 會設定圖表的載入方式，例如 DPI 或載入模式。

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### 如何存取圖表內容以定位圖形？
載入檔案後，從 `Watermarker` 取得 `DiagramContent` 物件。`DiagramContent` 代表圖表內部的頁面與圖形層級結構。此模型會公開頁面與圖形的集合，讓您可以遍歷，輕鬆定位圖像或文字等特定元素。

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### 如何在圖表中取代圖形圖像？
遍歷目標頁面的每個 `DiagramShape`，檢查該圖形是否包含圖像，若有則以新檔案的位元組取代圖像。`DiagramShape` 是圖表中單一圖形的模型，而 `DiagramWatermarkableImage` 則儲存可套用於圖形的圖像資料。

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### 如何儲存變更並關閉 Watermarker？
完成所有修改後，呼叫 `Watermarker` 的 `save` 方法將更新後的圖表寫入檔案，然後呼叫 `close` 釋放原生資源。這可確保檔案句柄被釋放，避免在批次處理大量圖表時產生記憶體洩漏。

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## 為相同圖表加入浮水印（可選）

如果您也需要為圖表加上品牌標記，可在圖像取代前或之後加入浮水印：

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## 常見陷阱與疑難排解

| 症狀 | 可能原因 | 解決方法 |
|---------|--------------|-----|
| 執行程式碼後圖像未變更 | `DiagramShape.hasImage()` 回傳 false | 確認圖形類型；某些向量圖形以不同方式儲存圖像。 |
| 大型檔案發生 OutOfMemoryError | 一次載入整個圖表 | 使用 `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` 以逐頁串流方式處理。 |
| 浮水印未顯示 | 浮水印被放在現有內容之後 | 在儲存前呼叫 `watermarker.setWatermarkPosition(Position.Foreground)`。 |

## 常見問答

**問：我可以取代受密碼保護的圖表圖像嗎？**  
答：可以。建立 `Watermarker` 時，將密碼傳入 `DiagramLoadOptions`。

**問：此程式庫支援 .drawio（XML）檔案嗎？**  
答：當然支援 – GroupDocs.Watermark 支援 Draw.io XML 格式，並將每個節點視為圖形。

**問：我可以平行處理多少個圖表？**  
答：程式庫對唯讀操作是執行緒安全的；寫入操作時，請將併發數限制在 CPU 核心數，以避免檔案句柄衝突。

**問：圖像大小有上限嗎？**  
答：支援最高 100 MB 的圖像；較大的檔案請事先調整大小，以降低記憶體使用。

**問：有哪些授權方案可供選擇？**  
答：可先使用 30 天免費試用；正式使用需購買授權，可從 GroupDocs 商店取得。

---

**最後更新：** 2026-08-19  
**測試於：** GroupDocs.Watermark 23.9 for Java  
**作者：** GroupDocs

## 相關教學

- [GroupDocs.Watermark Java 圖表浮水印教學](/watermark/java/diagram-document-watermarking/)
- [使用 GroupDocs.Watermark Java 從圖表圖形移除超連結以提升文件安全性](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [如何在 Java 中使用 GroupDocs.Watermark 加入圖像浮水印：逐步指南](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)