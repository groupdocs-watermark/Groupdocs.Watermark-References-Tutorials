---
date: '2026-02-03'
description: 學習如何使用 GroupDocs.Watermark for Java 預覽文件 – 為文件預覽 Java 開發者提供的快速指南。
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 如何使用 GroupDocs.Watermark for Java 預覽文件
type: docs
url: /zh-hant/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Watermark 預覽文件

建立 **how能對於處理大量檔案使用 GroupDocs.Watermark for Java，您可以在不將整個文件載入記憶體的情況下快速產生高品質的、管理頁面串的每議使用哪個函式庫？** GroupDocs.Watermark for Java (v的 preview documents*  
- **我需要授權嗎？** 試用版可用於評估可以自訂輸出格式嗎？** 可以 — 您可以在 page‑stream程式執行緒安全的；請為每個執行緒建立獨的文件預覽？

文件預覽是一種輕量級影像（通常為 PNG 或 JPEG），用於表示檔案的單一頁面。它讓使用者能快速瀏覽內容，提升檔案瀏覽器、CMS 平台以及雲端儲存服務的使用者體驗。

## 為什麼使用 GroupDocs.Watermark 產生預覽？

- **注重效能**：在不渲染整個文件的情況下產生頁面影像。  
- **跨格式支援**：支援 PDF、Officeio  `ICreatePageStream## 前置條件

在開始之前，請確保您已具備：

1. **GroupDocs.Water發 已安裝 **JDK 8+**，並具備如 IntelliJ IDEA 或 Eclipse 等 IDE。  
3. 基本的 Java 知識（檔案 I/O、物件導向程式設計）。  

## 設定 GroupDocs.Watermark for Java

使用 Maven 將函式庫加入您的專案：

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

或直接從官方頁面下載 JAR：  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### 取得授權

- **免費試用** – 功能受限，適合測試。  
- **臨時授權** – 在短期評估期間提供完整功能。  
- **正式授權** – 無限制使用並提供優先支援。  

## 實作指南

### 初始化 Watermarker

第一步是建立指向來源文件的 `Watermarker` 實例。

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

> **提示：** 將 `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` 替換為您想要預覽的檔案實際路徑。

### 建立頁面串流以產生預覽

實作 `ICreatePageStream` 以告訴函式庫每個頁面影像的儲存位置與方式。

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

`page%s.png` 是一個 **page stream java** 模式，會自動為每個預覽檔案命名（例如 `page1.png`、`page2.png`）。

### 釋放頁面串流

正確關閉串流可防止記憶體洩漏。

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

### 產生文件預覽

現在將所有步驟結合，並使用 **preview options java** 呼叫 `generatePreview`。

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

- `createPageStream` 處理每個預覽影像的 **page stream java** 建立。  
- `頁寫入後釋放資源。  

## 實務應用

- **PDF Viewer Apps** – PDF 檢視器應用程式 – 在開啟完整檔案前顯示縮圖預覽文件內容。  
- **Cloud Storage Services** – 雲端儲存服務 – 為任何上傳的圖。  

## 效能考量

- **記憶體使用** – 使用串流介面以避免將整個文件載入 RAM。  
- **I/O 最佳化** – 若處理大量頁面，請將 `FileOutputStream` 包裝於 `BufferedOutputStream`。  
- **批次處理執行緒執行marker` 實例。  

## 常見問題與解決方案

| 問題 | 發生原因 | 解決方法 |
|------|----------|---------- 整個大型文件被完整載入 | 使用串流介面（如示範）逐頁處理。 |
| **FileNotFoundException** | 輸出目錄路徑不正確 | 確認 `YOUR_OUTPUT_DIRECTORY` 已存在且具有寫入權限。 |
| **Preview images 確保文件類型受到 GroupDocs.Water |

## 常見問答

**Q: 我可以為受密碼保護的文件產生  
A: 可以。將密碼傳遞給接受援哪些PageStream` 中將副檔名改為 JPEG、BMP 等。

**Q: 可以限制預覽僅特定頁面嗎？**  
A: 使用 `PreviewOptions.setPageNumber(int pageNumber)` 產生單頁預覽。

**Q: 此函式庫能在 Linux/macOS 上運作嗎？**  
A: 當然可以。只要有 Java 執行環境，GroupDocs.Watermark 即為跨平台獨立。

**Q: 批次處理後如何清的預覽檔案，或實作排程清理任務。

---

**最後更新：** 2026-測試24.11  
**作者：** GroupDocs