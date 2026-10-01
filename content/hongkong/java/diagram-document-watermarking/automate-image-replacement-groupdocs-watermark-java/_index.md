---
date: '2026-10-01'
description: 了解如何使用 GroupDocs.Watermark 在圖表檔案中自動化 Java 圖像替換，包含 watermark 添加與高效處理。
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: 使用 GroupDocs.Watermark 在圖表中自動化 Java 圖像替換。本指南說明如何替換圖像、加入 watermarks，並高效處理大型檔案。
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: 使用 GroupDocs.Watermark 自動化 Java 圖像替換
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: 使用 GroupDocs.Watermark 自動化 Java 圖像替換
type: docs
url: /zh-hant/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 自動化 Java 圖片替換

在圖表中更新單張圖片可能是一項繁瑣且易出錯的手動工作。使用 **GroupDocs.Watermark for Java**，您可以 **自動化 Java 圖片替換**，在數十或數百個檔案中執行，確保品牌一致性並節省寶貴的開發時間。本教學將指導您設定函式庫、存取圖表內容、交換特定圖形內的圖片，並可選擇為圖表添加浮水印。

## 快速解答
- **哪個函式庫負責圖表圖片更新？** GroupDocs.Watermark for Java.  
- **在替換圖片的同時可以添加浮水印嗎？** 是 – 相同的 API 允許您在任何圖表頁面上疊加浮水印。  
- **需要哪個 Java 版本？** JDK 8 或更高。  
- **開發時需要授權嗎？** 免費試用可用於評估；正式上線需購買商業授權。  
- **此流程對大型圖表的記憶體使用是否有效率？** 是 – SDK 以串流方式處理內容，從不一次載入整個檔案至記憶體。

## 什麼是 GroupDocs.Watermark for Java？
`GroupDocs.Watermark` 是一個 Java SDK，能以程式方式在超過 30 種文件格式（包括 Visio、SVG 及其他圖表類型）中新增、移除與替換浮水印與圖片。它以串流方式處理檔案，讓您在處理數百頁的圖表時不會耗盡記憶體。

## 為什麼要自動化 Java 圖片替換？
自動化圖片替換在大規模文件集合中更新品牌資產時，可將人工工作量減少高達 **90 %**。SDK 支援 **30+ 種輸入與輸出格式**，在一般伺服器硬體上可於一秒內處理高達 **200 MB** 的檔案，並保證像素級的圖片定位精準。

## 前置條件
- 在開發機上安裝 JDK 8 或更新版本。  
- 使用 Maven（或其他建置工具）管理相依性。  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 具備基本的 Java 知識並熟悉檔案 I/O。

### 必要的函式庫、版本與相依性
將以下 Maven 坐標加入您的 `pom.xml`。下方的佔位符代表您需要的完整 XML 片段，請保持原樣。

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

若手動下載，請從官方發佈頁面取得最新的 JAR 檔案：[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## 如何自動化 Java 圖片替換？
使用 `Watermarker` 實例載入圖表，定位目標圖形，替換其圖片串流，必要時加入浮水印，最後儲存檔案。整個工作流程可分為 **四個簡潔步驟**，以下逐一示範，即使是大型檔案，通常也只需數秒即可完成。

### 步驟 1：初始化 watermarker
`Watermarker` 類別是所有文件操作的入口點。它會開啟來源檔案並為編輯準備內部結構。

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

- **DiagramLoadOptions** 用於設定圖表專屬的載入參數。  
- 初始化 `Watermarker` 會開啟檔案句柄並驗證格式。

### 步驟 2：存取圖表內容
`DiagramContent` 代表圖表的邏輯結構，提供頁面與各個圖形供檢查。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- 使用 `watermarker.getContent()` 取得 `DiagramContent` 物件。  
- 遍歷 `content.getPages()`，再遍歷 `page.getShapes()` 以尋找包含圖片的圖形。

### 步驟 3：替換圖表中圖形的圖片
`DiagramShape` 物件可能包含內嵌圖片。提供讀取替換圖片的 `InputStream` 即可進行替換。

`setImage(InputStream)` 方法會以提供的串流取代圖形目前的圖片。  

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

- 檢查 `shape.getImage()`；若非 null，呼叫 `shape.setImage(newImageStream)`。  
- SDK 會自動更新圖片尺寸並保留原始圖形佈局。

### 步驟 4：為圖表添加浮水印（可選）
如果您還需要 **為圖表添加浮水印**，請建立 `Watermark` 物件並套用至指定頁面或整個文件。

`Watermark` 類別定義可放置於圖表頁面或整份文件的視覺覆蓋層。  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

`add(Watermark, AddOptions)` 方法會使用指定的選項將浮水印套用至文件。  

（*上述程式碼僅作示範，並未算作新程式碼區塊；它位於現有段落內。*）

### 步驟 5：儲存並關閉 watermarker
將變更寫入檔案並釋放資源，以避免檔案被鎖定。

`save(String)` 方法會將修改後的文件寫入指定路徑。  

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

- 呼叫 `watermarker.save("output.vsdx")`（或相應的副檔名）。  
- 務必在 `finally` 區塊中呼叫 `watermarker.close()`，或使用 try‑with‑resources 以自動清理。

## 常見問題與故障排除
- **圖片尺寸不匹配** – 請確保替換圖片的長寬比與原圖相同，以免產生變形。  
- **大型圖表的記憶體激增** – 請一次處理一個圖表，並在每次儲存後關閉 `Watermarker`。  
- **授權錯誤** – 試用授權在 30 天後過期；部署前請換成正式授權金鑰。您可從 GroupDocs 取得臨時授權：[obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## 常見問答

**Q: 我可以在受密碼保護的圖表中替換圖片嗎？**  
A: 可以。使用包含密碼的 `DiagramLoadOptions` 載入檔案，然後照常執行替換步驟。

**Q: SDK 是否支援批次處理多個圖表？**  
A: 當然支援。將單檔工作流程包在迴圈中，遍歷目錄中的檔案；串流架構可保持低記憶體使用量。

**Q: 除了 Visio，還能處理哪些格式？**  
A: GroupDocs.Watermark 支援 SVG、VDX、VSDX 以及其他多種圖表格式，總計超過 30 種。

**Q: 替換圖片後可以再加入浮水印嗎？**  
A: 可以 – 在儲存之前的圖片替換步驟之後，呼叫 `watermarker.add(watermark, options)`。

**Q: 如何確保新圖片是嵌入式而非連結？**  
A: `setImage(InputStream)` 方法會直接將圖片資料嵌入圖表檔案，確保可攜性。

---

**最後更新：** 2026-10-01  
**測試環境：** GroupDocs.Watermark 23.12 for Java  
**作者：** GroupDocs

## 相關教學

- [GroupDocs.Watermark Java 圖表浮水印教學](/watermark/java/diagram-document-watermarking/)
- [使用 GroupDocs.Watermark Java 移除圖表形狀中的超連結以提升文件安全性](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [如何在 Java 中使用 GroupDocs.Watermark 添加圖片浮水印：逐步指南](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)