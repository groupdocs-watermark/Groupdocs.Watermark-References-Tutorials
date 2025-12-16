---
date: '2025-12-16'
description: 了解如何使用 GroupDocs.Watermark for Java 預覽文件，並透過 Maven 整合的 GroupDocs Watermark
  輕鬆產生縮圖。
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 如何在 Java 中使用 GroupDocs.Watermark 預覽文件：進階指南
type: docs
url: /zh-hant/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Watermark 預覽文件：進階指南

## 介紹

在本指南中，您將學習 **如何有效預覽文件**，使用 GroupDocs.Watermark Java 函式庫。建立文件預覽是管理大量檔案的應用程式的重要功能，讓使用者能在不開啟完整文件的情況下快速瀏覽內容。依照以下步驟，您還會看到如何 **java 產生縮圖** 圖片，以及如何透過 **maven groupdocs watermark** 整合函式庫。讓我們先準備開發環境吧。

## 快速回答
- **主要目的為何？** 產生任何支援文件的輕量級逐頁預覽（縮圖）。  
- **需要哪個函式庫？** GroupDocs.Watermark for Java（版本 24.11）。  
- **如何加入函式庫？** 使用設定章節提供的 Maven 片段。  
- **可以產生所有頁面的預覽嗎？** 可以——API 會將每一頁串流為圖像檔。  
- **需要授權嗎？** 試用版可用於基本測試；正式環境需購買完整授權。

## 什麼是文件預覽產生？
文件預覽產生會將來源檔案（PDF、DOCX、VDX 等）的每一頁轉換為 PNG 等圖像格式。這些預覽圖像可作為縮圖，顯示於檔案瀏覽器、Web 入口網站或行動應用程式中，顯著提升使用者體驗並降低載入時間。

## 為何使用 GroupDocs.Watermark for Java？
- **速度與可擴充性** – 經過優化的原生程式碼能快速處理大型文件。  
- **廣泛格式支援** – 開箱即支援超過 100 種檔案類型。  
- **內建浮水印** – 產生預覽時可同時加入浮水印，保護您的資產。  
- **簡易 API** – 只需少量程式碼即可產生高品質縮圖。

## 前置條件

1. **Java Development Kit (JDK)** – 已安裝 JDK 8 或更新版本。  
2. **IDE** – IntelliJ IDEA、Eclipse，或您慣用的任何編輯器。  
3. **Maven** – 用於相依性管理（請參考下方 Maven 設定）。  
4. **基本的 Java 知識** – 熟悉檔案 I/O 與物件導向程式設計。

## 設定 GroupDocs.Watermark for Java

要在專案中使用 GroupDocs.Watermark，請將其加入 Maven 相依性：

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

或者，您也可以直接從官方發布頁面下載最新的 JAR 檔案：  
[GroupDocs.Watermark for Java 版本發布頁面](https://releases.groupdocs.com/watermark/java/)

### 授權取得

- **免費試用** – 以受限功能測試函式庫。  
- **臨時授權** – 取得短期金鑰以完整評估功能。  
- **正式授權** – 購買後可無限制使用並獲得優先支援。

## 實作指南

### 初始化 Watermarker

#### 概觀
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

*重點說明：* 請將 `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` 替換為您實際想要預覽的檔案路徑。

### 建立頁面串流以產生預覽

#### 概觀
自訂串流建立器告訴 API 每一頁的預覽圖像要寫入哪裡。

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

`fileNameTemplate` 使用佔位符（`%s`），API 會以目前的頁碼取代它，產生 `page1.png`、`page2.png` 等檔案。

### 釋放頁面串流

#### 概觀
預覽圖寫入完成後，必須關閉串流以釋放系統資源。

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

正確釋放串流可防止記憶體洩漏，尤其在處理大量文件時更為重要。

### 產生文件預覽

#### 概觀
當 `Watermarker`、串流建立器與釋放處理程式都已就緒，即可為每一頁產生預覽。

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

*關鍵物件說明：*  
- `createPageStream` – 決定每個 PNG 檔案的儲存位置。  
- `releasePageStream` – 確保寫入後關閉檔案句柄。  
- `previewOptions` – 將上述兩個處理程式封裝，供 `generatePreview` 呼叫使用。

## 實務應用

產生文件預覽在許多真實情境中都非常有用：

1. **PDF 閱讀器應用程式** – 在不載入完整 PDF 的情況下顯示縮圖列。  
2. **內容管理系統 (CMS)** – 讓編輯者快速瀏覽文件。  
3. **雲端儲存服務** – 為已儲存的檔案提供視覺縮圖，提升導覽效率。

## 效能考量

- **記憶體管理** – 使用上述的串流釋放模式以降低記憶體佔用。  
- **I/O 最佳化** – 使用緩衝串流可進一步減少處理千頁文件時的磁碟延遲。  
- **平行處理** – 大量作業時，可考慮使用 Java 的 `ExecutorService` 同時處理多個文件。

## 常見問題與解決方案

| 問題 | 原因 | 解決方式 |
|------|------|----------|
| 未產生預覽檔案 | 輸出目錄路徑錯誤或缺乏寫入權限 | 確認 `YOUR_OUTPUT_DIRECTORY` 已存在且可寫入 |
| 大型 PDF 發生記憶體不足 | 串流未即時釋放 | 確保正確實作 `FeatureReleasePageStream` |
| 不支援的檔案格式 | 文件類型未被 GroupDocs.Watermark 支援 | 查閱函式庫的格式支援清單；必要時先轉換為支援的類型 |

## 常見問答

**Q: 能否為受密碼保護的文件產生預覽？**  
A: 能。使用接受密碼參數的 `Watermarker` 建構子載入文件，然後照範例進行預覽產生。

**Q: 函式庫是否支援除 PNG 之外的影像格式？**  
A: 預覽 API 預設輸出 PNG，但您可以使用標準的 Java 影像函式庫將產生的串流轉換為 JPEG 或 BMP。

**Q: 單次執行能預覽多少頁？**  
A: 沒有硬性上限；但處理極大型文件時，建議分批或調整 JVM 堆積大小。

**Q: 產生預覽是否必須購買授權？**  
A: 試用授權可用於評估，正式環境則需購買完整授權以移除浮水印並解鎖全部功能。

**Q: 能否自訂預覽圖的解析度？**  
A: 能。`PreviewOptions` 提供 `setResolution` 等屬性，您可在呼叫 `generatePreview` 前設定 DPI。

## 結論

現在您已掌握使用 GroupDocs.Watermark 在 Java 中 **預覽文件** 的完整、可投入生產的工作流程。透過初始化 `Watermarker`、管理頁面串流以及正確釋放資源，您可以大規模產生高品質縮圖。將這些技巧套用於任何文件密集型應用程式，提升使用者體驗。

---

**最後更新：** 2025-12-16  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs