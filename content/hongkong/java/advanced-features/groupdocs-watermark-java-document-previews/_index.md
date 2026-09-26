---
date: '2026-09-26'
description: 了解如何使用 GroupDocs.Watermark 將文件轉換為圖像並在 Java 中生成縮圖。一步一步的指南涵蓋設定、預覽串流以及效能技巧。
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: 了解如何使用 GroupDocs.Watermark 將文件轉換為圖像並在 Java 中生成縮圖。本指南將帶您完成安裝、串流處理以及針對快速預覽建立的效能優化。
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: 使用 GroupDocs.Watermark Java 將文件轉換為圖像
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: 使用 GroupDocs.Watermark Java 將文件轉換為圖像
type: docs
url: /zh-hant/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# 將文件轉換為圖像（使用 GroupDocs.Watermark Java）

為多頁文件生成輕量級圖像預覽是門戶網站、內容管理系統和雲端儲存服務的常見需求。透過 **convert document to image**，您可以在不載入完整檔案的情況下，為最終使用者提供快速的視覺提示。GroupDocs.Watermark Java 函式庫不僅能添加浮水印，還提供高效能的預覽引擎，能夠 **java generate thumbnails** 在一次處理中為每一頁產生縮圖。

在本教學中，您將學習如何設定函式庫、建立自訂頁面串流、安全釋放資源，最終為來源文件的每一頁產生圖像預覽。說明針對熟悉 Java 及物件導向概念的開發人員編寫，並包含處理大量檔案批次的最佳實踐提示。

## 快速回答
- **第一步是什麼？** 添加 GroupDocs.Watermark Maven 依賴，並使用來源檔案路徑初始化 `Watermarker`。  
- **如何建立預覽圖像？** 實作 `ICreatePageStream` 以為每一頁開啟輸出串流，然後使用適當的選項呼叫 `generatePreview()`。  
- **我需要授權嗎？** 試用版可用於基本情境，但完整授權會移除浮水印並解鎖批次處理功能。  
- **我能處理超過 200 頁的 PDF 嗎？** 可以 — 函式庫以串流方式處理頁面，即使是 500 頁的檔案也能保持低記憶體使用。  
- **支援哪些圖像格式？** PNG、JPEG、BMP 與 TIFF 均可直接使用。

## 什麼是 convert document to image？
術語 **convert document to image** 描述將來源檔案（PDF、DOCX、PPTX 等）的每一頁渲染為點陣圖（如 PNG 或 JPEG）的過程。此轉換對於縮圖畫廊、預覽窗格以及行動裝置友好的文件檢視器非常有用。

## 為何使用 GroupDocs.Watermark 產生預覽？
GroupDocs.Watermark 支援 **30+ 輸入格式**，且可為最多 **500 頁** 的文件產生預覽，而無需將整個檔案載入記憶體。內部會順序處理頁面，即使是大型 PDF，Java 堆積使用量也保持在 50 MB 以下。函式庫還提供內建的圖像優化功能，允許您指定 DPI、色彩深度與壓縮等級，產生的縮圖通常比簡單點陣化小 **70 %**。

## 先決條件
- **Java Development Kit (JDK) 11 或更新版本** – 函式庫編譯於 Java 8+，但 JDK 11 提供長期支援與更佳效能。  
- **Maven 3.6+** – 用於相依性管理。  
- **GroupDocs.Watermark for Java 版本 24.11** – 撰寫本文時的最新穩定版。  
- **基本的 Java I/O 串流知識** – 您將為每個預覽頁面建立 `FileOutputStream` 物件。  
- **授權金鑰**（生產環境可選） – 試用版將每個文件的預覽大小限制為 5 MB。

## 如何設定 GroupDocs.Watermark（Java 版）
要設定 GroupDocs.Watermark，首先加入 Maven 倉庫，然後在專案的 `pom.xml` 中將函式庫加入為相依性。這可確保 Maven 下載正確的套件，並使類別在編譯與執行時可於 classpath 中取得。

### 添加 Maven 相依性
此函式庫透過 Maven Central 發佈。將以下程式碼片段加入 `pom.xml` 的 `<dependencies>` 區塊中：
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **專業提示：** 將版本號保留在屬性 (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) 中，以便輕鬆升級。

### 直接下載（替代方案）
如果您偏好手動安裝，可從官方發佈頁面下載 JAR： [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)。

## 如何取得與套用授權
將授權套用至 GroupDocs.Watermark 可移除試用限制，並停用預設的浮水印覆蓋。將授權檔放置於已知位置，並讓 API 指向該檔，或在任何其他呼叫之前於程式碼中直接嵌入授權路徑。載入後，所有後續操作皆以完整功能模式執行。

您可以：
- **向 GroupDocs 入口網站申請免費試用** – 可取得 30 天的授權檔。  
- **透過線上授權產生器產生臨時授權**，供評估環境使用。  
- **購買商業授權**，以獲得無限制的生產使用與優先支援。

將授權檔 (`GroupDocs.Watermark.lic`) 放置於專案根目錄，或以程式方式使用 `Watermarker.setLicense("path/to/license.file")` 指定其路徑。

## 如何初始化 Watermarker
透過提供來源文件的路徑（可選擇性加入受保護檔案的密碼）來初始化 `Watermarker`。建構子會驗證格式並準備內部解析器，使您能立即呼叫預覽或浮水印方法。建立後，若有需要，可保留該實例的參考以重複使用於多個操作。

`Watermarker` 類別是 GroupDocs.Watermark 的核心物件，負責載入文件並提供如浮水印插入與預覽產生等操作。
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – 指向來源檔案的絕對或相對路徑。  
- 建構子會驗證檔案格式並準備內部解析器。

> **定義說明：** `Watermarker` 是 GroupDocs.Watermark for Java 中所有文件處理動作的入口點。

## 如何建立頁面串流以產生預覽
透過實作 `ICreatePageStream` 介面來建立自訂頁面串流，函式庫會在渲染每一頁時呼叫此介面。您的實作應產生全新的 `OutputStream`（通常為 `FileOutputStream`），指向以頁碼命名的唯一檔案。此方式可將每頁的輸出隔離，防止資料重疊。

要 **java generate thumbnails**，必須為每一頁提供寫入渲染圖像的串流。實作 `ICreatePageStream` 介面；函式庫會在處理每頁時呼叫您的實作。
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** 讓您直接在檔名中嵌入頁碼，便於批次處理。  
- 此方法為每頁回傳全新的 `OutputStream`，確保先前的頁面不會干擾後續寫入。

> **定義說明：** `ICreatePageStream` 是回呼介面，讓您定義如何為每個預覽頁面建立輸出串流。

## 如何在產生預覽後釋放頁面串流
在寫入頁面圖像後，函式庫會呼叫 `IReleasePageStream`，讓您關閉並清理相關的輸出串流。實作此回呼以安全釋放檔案句柄、刷新緩衝區，並執行任何額外的記錄。適當的清理可避免描述符洩漏，確保後續頁面不受干擾地處理。

適當的資源清理可防止檔案句柄洩漏，並避免 JVM 用盡描述符。實作 `IReleasePageStream` 以在函式庫表示頁面完成時關閉串流。
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **定義說明：** `IReleasePageStream` 是回呼介面，讓您定義針對頁面特定輸出資源的自訂釋放邏輯。

## 如何產生文件預覽（convert document to image）
透過在 `Watermarker` 實例上呼叫 `generatePreview()`，並提供定義解析度、圖像格式與頁面範圍的 `PreviewOptions` 物件，即可產生預覽。此方法會遍歷每一頁，使用您的串流建立器寫入點陣圖，然後釋放串流。此過程會產生一組代表文件各頁的圖像檔案。

在準備好 `Watermarker`、`FeatureCreatePageStream` 與 `FeatureReleasePageStream` 後，即可呼叫預覽引擎。`generatePreview()` 方法會遍歷每一頁，呼叫您的串流建立器，寫入圖像，最後釋放串流。
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** 控制 DPI；150 DPI 為網頁縮圖的良好平衡。  
- **`ImageFormat`** 可根據下游需求設定為 PNG、JPEG、BMP 或 TIFF。  
- 此方法順序處理頁面，即使是數百頁的文件，記憶體消耗仍保持低位。

> **定義說明：** `generatePreview()` 為 API 呼叫，使用您提供的串流將已載入文件的每一頁渲染為圖像。

## convert document to image 的實務應用
產生圖像預覽可開啟許多可能性：

1. **文件瀏覽器** – 顯示 PNG 縮圖網格，讓使用者在不開啟大型 PDF 的情況下快速瀏覽。  
2. **搜尋結果摘要** – 為搜尋索引條目附加預覽圖像，以提升 UI 豐富度。  
3. **電子郵件附件** – 在郵件正文中嵌入附加 PDF 的小型預覽。  
4. **行動應用程式** – 以 200 KB PNG 預覽取代完整 PDF，降低頻寬使用。  
5. **合規門戶** – 將依法必須的浮水印合約版本渲染為圖像，以作審計追蹤。

## 在 java generate thumbnails 時的效能考量
處理大量批次時，請留意以下最佳化建議：

- **串流緩衝** – 將 `FileOutputStream` 包裝於 `BufferedOutputStream`，以減少磁碟 I/O。  
- **平行批次執行** – 使用 Java 的 `ForkJoinPool` 同時處理多個文件；每個任務應建立自己的 `Watermarker` 實例，以避免執行緒安全問題。  
- **限制縮圖 DPI** – 72–150 DPI 足以應付大多數 UI 情境；較高 DPI 應保留給列印就緒的預覽。  
- **重複使用授權物件** – 每個 JVM 僅載入一次授權檔，可減少開銷。  
- **監控記憶體** – 函式庫僅在記憶體中保留當前頁面。對於極大檔案，可適度增加 JVM 堆積（例如 `-Xmx512m`），以因應偶發的記憶體峰值。

## 常見陷阱與避免方法
| 症狀 | 可能原因 | 解決方案 |
|------|----------|----------|
| `OutOfMemoryError` 於產生預覽時 | 在 1000 頁 PDF 上使用 300 DPI 的 `ImageFormat.Jpeg` | 降低 DPI 或改用色深較低的 PNG |
| 預覽檔案為空 | `FeatureCreatePageStream` 為每頁回傳相同的 `FileOutputStream` | 確保每個 `pageNumber` 都建立新的串流 |
| 預覽圖像被旋轉 | 來源 PDF 含有未被遵守的旋轉中繼資料 | 呼叫 `previewOptions.setRotatePages(true)`（若支援） |
| 出現授權警告 | 找不到授權檔或路徑不正確 | 確認 `Watermarker.setLicense("path/to/license.file")` 在任何其他 API 呼叫之前執行 |

## 常見問答
**Q: 我能為受密碼保護的 PDF 產生預覽嗎？**  
A: 可以。將密碼傳遞給 `Watermarker` 建構子：`new Watermarker("file.pdf", "password")`。

**Q: 預覽輸出的圖像格式支援哪些？**  
A: 支援 PNG、JPEG、BMP 與 TIFF。建議使用 PNG 以獲得無損縮圖。

**Q: 單次呼叫可處理多少頁？**  
A: 函式庫沒有硬性限制；您可以預覽包含數千頁的文件，唯一受限於儲存空間與 I/O 吞吐量。

**Q: 每個伺服器實例需要單獨的授權嗎？**  
A: 只要總使用量符合授權條款，單一授權檔即可在多個實例間重複使用。

**Q: 有沒有辦法產生單一合併縮圖（例如僅第一頁）？**  
A: 有。設定 `previewOptions.setPages(new int[]{1})` 以限制僅產生第一頁的預覽。

## 結論
您現在已擁有使用 GroupDocs.Watermark 進行 **convert document to image** 與 **java generate thumbnails** 的完整、可投入生產的工作流程。透過設定自訂頁面串流處理器，您可保持低記憶體使用；調整 `PreviewOptions` 則可控制圖像品質與檔案大小。這些技巧讓您能在任何基於 Java 的應用程式中嵌入快速且高品質的預覽——無論是網頁門戶、桌面客戶端，或是雲端原生微服務。

---

**最後更新：** 2026-09-26  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## 相關教學
- [如何使用 GroupDocs.Watermark for Java 取得文件資訊&#58; 一步步指南](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [GroupDocs.Watermark Java 進階浮水印功能教學](/watermark/java/advanced-features/)
- [如何在 Java 中使用 GroupDocs.Watermark 添加圖片浮水印&#58; 一步步指南](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)