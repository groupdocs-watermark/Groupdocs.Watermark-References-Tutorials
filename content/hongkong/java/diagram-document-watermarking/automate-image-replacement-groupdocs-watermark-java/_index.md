---
date: '2026-02-18'
description: 了解如何使用 GroupDocs.Watermark for Java 取代圖表圖片——自動化更新、提升效率，確保工作流程的準確性。
keywords:
- GroupDocs Watermark Java
- automate image replacement
- Java diagram watermarking
title: 如何使用 GroupDocs.Watermark 替換 Java 圖表圖像
type: docs
url: /zh-hant/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# 用 GroupDocs.Watermark for Java 替換 Java 圖表圖片

更新 Visio 風格圖表中的圖片可能是一項繁瑣且易出錯的工作——尤其是當你需要同步數十個檔案以符合品牌指南或產品修訂時。在本教學中，你將學習 **如何在 Java 程式中替換圖表圖片**，使用功能強大的 GroupDocs.Watermark 函式庫。我們將逐步說明環境設定、存取圖表形狀、交換圖片以及儲存結果，全部以清晰、對話式的方式呈現。

## 快速解答
- **哪個函式庫可以在 Java 中替換圖表圖片？** GroupDocs.Watermark for Java.  
- **我需要授權嗎？** 免費試用可用於開發；商業使用則需正式授權。  
- **支援哪些檔案格式？** Visio (.vsdx, .vsd) 以及函式庫支援的其他圖表類型。  
- **實作需要多長時間？** 基本的替換圖片腳本大約 15 分鐘即可完成。  
- **我可以批次處理多個圖表嗎？** 可以——只需使用相同的 Watermarker 邏輯迴圈處理檔案。

## 什麼是「replace diagram images java」？
「replace diagram images java」指的是透過程式自動在圖表檔案中定位含有圖片的形狀，並以新圖取代內嵌的位圖，全部使用 Java 程式碼完成。此方式可免除在 Visio 或類似工具中手動編輯，確保大量文件集合的一致性。

## 為何使用 GroupDocs.Watermark 來完成此任務？
- **自動化優先**：只需少量程式碼即可處理數千個檔案。  
- **不需 UI**：可在伺服器、CI 流程或桌面應用程式上無頭執行。  
- **豐富的內容模型**：提供強大的抽象層 (DiagramContent、DiagramShape)，讓你精確定位所需的形狀。  
- **跨平台**：可在任何相容 JVM 的環境上執行（Windows、Linux、macOS）。

## 前置條件
- 已安裝 JDK 8 或更新版本。  
- 使用 Maven（或手動管理 JAR）進行相依管理。  
- 具備基礎 Java 知識與檔案 I/O 經驗。  

### 必要的函式庫、版本與相依性
將 GroupDocs 儲存庫與 Watermark 相依性加入你的 `pom.xml`：

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

你也可以直接從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 JAR。

可取得免費試用授權，永久授權可於 [GroupDocs](https://purchase.groupdocs.com/temporary-license/) 購買。

## 步驟式實作

### 1. 初始化 Watermarker
首先，建立指向欲編輯圖表的 `Watermarker` 實例。

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

*為什麼這很重要*：使用 `DiagramLoadOptions` 載入檔案，讓函式庫將來源視為圖表，從而支援形狀層級的存取。

### 2. 取得圖表內容
取得內部表示 (`DiagramContent`)，以便列舉頁面與形狀。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

*小技巧*：在使用 `DiagramContent` 時保持 `Watermarker` 實例存活；過早關閉會使內容物件失效。

### 3. 替換形狀圖片
遍歷第一頁的形狀（可擴展至所有頁面），將任何現有圖片替換為新的 PNG。

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

*說明*：  
- `shape.getImage()` 檢查形狀是否已包含圖片。  
- 我們將替換用的 PNG 讀入位元組陣列，並以 `DiagramWatermarkableImage` 包裝。  
- `shape.setImage(...)` 將舊圖片換成新圖片。

### 4. 儲存變更並清理
完成所有替換後，將圖表寫入磁碟並釋放資源。

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

儲存會將更新後的圖表寫入磁碟，`close()` 可防止檔案句柄洩漏——對批次處理至關重要。

## 實務應用
- **企業品牌** – 使用單一腳本更新所有組織圖的標誌。  
- **產品文件** – 當新硬體發布時，更新元件圖片。  
- **教育資源** – 將過時的圖表換成最新的科學插圖。

## 效能與最佳實踐
- **一次處理單一檔案**：面對大型圖表時，保持記憶體使用量低。  
- **及時釋放串流**（如範例所示），避免檔案鎖定問題。  
- **分析 I/O 效能**：若處理數百個檔案，可考慮使用受控併發的執行緒池。

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方法 |
|------|----------|----------|
| `shape.getImage()` 時出現 `NullPointerException` | 圖表頁面索引超出範圍 | 在迴圈前確認頁面存在（`content.getPages().size() > 0`）。 |
| 替換後的圖片顯示失真 | 輸入圖片的 DPI 不同 | 使用與原圖尺寸/DPI 相近的 PNG，或在載入前先調整大小。 |
| 執行時出現 LicenseException | 試用期已過或缺少授權 | 在建立 `Watermarker` 前，使用 `License.setLicense("path/to/license.json");` 套用有效的授權檔案。 |

## 常見問答

**Q: 我可以替換圖表所有頁面的圖片嗎？**  
A: 可以——遍歷 `content.getPages()`，對每一頁套用相同的替換邏輯。

**Q: 函式庫支援其他圖片格式嗎（例如 JPEG、BMP）？**  
A: 當然支援。提供任意支援格式的圖片位元組，API 會自行處理轉換。

**Q: 能否只替換特定形狀（例如具有特定名稱的形狀）？**  
A: 可以。每個 `DiagramShape` 都有 `getName()` 等屬性或自訂中繼資料，可在交換圖片前進行篩選。

**Q: 如何在沒有 GUI 的 Linux 伺服器上執行此程式碼？**  
A: GroupDocs.Watermark 完全無頭執行；不需要 GUI 元件。只需確保 JDK 與必要的 JAR 已加入 classpath。

**Q: 需要哪個版本的 GroupDocs.Watermark？**  
A: 本範例使用 24.11 版，為撰寫時的最新穩定版。

## 結論
現在你已擁有使用 GroupDocs.Watermark 進行 **replace diagram images java** 的完整、可投入生產的工作流程。將這些程式碼片段整合至建置管線、批次處理圖表資料夾，或透過 REST 服務公開此邏輯，以自動化整個組織的品牌更新。

---

**最後更新：** 2026-02-18  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs