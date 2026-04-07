---
date: '2026-04-07'
description: 學習如何使用 GroupDocs.Watermark for Java 為電郵附件建立文字水印，保護電郵附件及機密資料。
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: 使用 GroupDocs Java 為電郵附件建立文字浮水印
type: docs
url: /zh-hant/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# 如何使用 GroupDocs.Watermark for Java 為電郵附件添加水印

在本教學中，您將**建立文字水印**物件，並將其套用至電郵訊息中的每個支援的附件。添加水印是一種有效的方式，可**保護電郵附件**、顯示機密性，並加強品牌識別——只需幾行 Java 程式碼即可完成。

## 簡介

在電郵傳送敏感資訊時的保護需求比以往任何時候都更為重要。無論您是需要為內部報告貼標、為法律合約加註，或僅僅為行銷資產加上品牌標識，文字水印都能提供輕量且防篡改的保護層。本指南將逐步說明如何使用 **GroupDocs.Watermark for Java** 為 Outlook `.msg` 檔案中的每個附件加入自訂水印。

### 您將學習
- 如何使用自訂字型與顏色**建立文字水印**物件。  
- 在 Java 電郵處理工作流程中逐步整合加水印的方式。  
- 處理大型附件時的效能優化技巧。  
- 真實案例：在電郵附件上加水印如何提升價值。

在深入之前，先確認您已具備所有必要條件。

## 快速答疑
- **「建立文字水印」是什麼意思？** 即實例化 `TextWatermark` 物件，定義要覆蓋於文件上的可見文字、字型、大小與樣式。  
- **我可以為加密的附件加水印嗎？** 不行 – 為了安全考量，GroupDocs.Watermark 不支援加密檔案。  
- **支援哪些檔案類型？** PDF、Word、Excel、PowerPoint、圖片等多種格式 – 請參考官方文件取得完整清單。  
- **需要授權嗎？** 開發階段可使用試用授權；正式上線需購買商業授權。  
- **處理速度如何？** 在現代硬體上，對一個 2 MB 附件加水印通常不到一秒。

## 前置條件

- **Java Development Kit (JDK)** – 8 版或更新。  
- IntelliJ IDEA、Eclipse 等任一 IDE。  
- 已將 **GroupDocs.Watermark for Java** 加入專案（請見下方設定步驟）。  
- 可取得包含欲保護附件的電郵檔案（`.msg`、`.eml` 等）。

## 設定 GroupDocs.Watermark for Java

### Maven 設定

若使用 Maven 管理相依性，請在 `pom.xml` 中加入以下儲存庫與相依性：

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

### 直接下載

或是直接從官方網站下載最新 JAR：  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### 取得授權
- **試用版：** 在 GroupDocs 官網註冊並申請臨時授權。  
- **商業版：** 前往此處購買完整授權：[purchase page](https://purchase.groupdocs.com/temporary-license/).

### 基本初始化

在 Java 原始檔中匯入所需的核心類別：

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## 什麼是文字水印？

**文字水印**是一段半透明文字，會渲染於文件每一頁的上方。使用 GroupDocs.Watermark，您可以控制字型、大小、顏色、旋轉角度與不透明度，彈性打造符合品牌或機密性需求的標示，且自然融合於原始內容。

## 為何在電郵附件上使用 GroupDocs.Watermark？

- **保護電郵附件**，以明顯方式標示為機密。  
- **維持品牌一致性**，於所有外發文件上加上統一標識。  
- **批次處理**多封電郵，只需一次迴圈即可，省時且減少人工錯誤。  
- **跨格式支援** – 同一段程式碼同時適用於 PDF、Word、圖片等多種檔案。

## 實作指南

以下將逐步說明每個步驟，並解釋程式碼背後的 *why*，方便您自行客製化。

### 步驟 1：建立文字水印

先以欲顯示的文字與字型設定，實例化 `TextWatermark`。

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **專業提示：** 調整字型大小或顏色以符合公司樣式指南。若需較淡的效果，可透過 `watermark.setOpacity(0.5)` 設定不透明度。

### 步驟 2：設定 Email 載入選項

`EmailLoadOptions` 告訴函式庫如何解析輸入的電郵檔案。

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### 步驟 3：為電郵檔案初始化 Watermarker

將 `Watermarker` 建構子指向欲處理的 `.msg`（或 `.eml`）檔案。

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### 步驟 4：取得電郵內容

擷取電郵的內部結構，以便遍歷其附件。

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### 步驟 5：遍歷附件

對每個附件檢查檔案類型是否受支援，且未加密。

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### 步驟 6‑9：為受支援的附件加水印

在條件判斷內部，為附件建立專屬 `Watermarker`，套用水印，然後將修改後的內容寫回電郵。

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### 步驟 10：儲存加水印後的電郵

將更新後的電郵寫入新檔案，保留原始檔不變。

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### 步驟 11：清理資源

務必釋放資源，以避免記憶體洩漏。

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## 常見問題與解決方案

| 問題 | 原因 | 解決方式 |
|------|------|----------|
| **水印未顯示** | 不透明度設定過低或字體顏色與背景相同。 | 提高不透明度 (`watermark.setOpacity(0.7)`) 或改用對比色。 |
| **不支援的附件類型** | 檔案格式未列於 GroupDocs 支援清單。 | 先將檔案轉為支援格式（例如 PDF），或以記錄訊息跳過。 |
| **大型 PDF 發生 OutOfMemoryError** | 載入過大的附件佔用過多堆疊記憶體。 | 增加 JVM 堆疊大小 (`-Xmx2g`) 或分批處理附件。 |

## 常見問答

**Q: 我可以為加密檔案加水印嗎？**  
A: 不行，GroupDocs.Watermark 因安全限制不支援對加密檔案加水印。

**Q: 支援哪些檔案類型進行加水印？**  
A: 支援的類型包括 PDF、Word 文件、Excel 工作表、PowerPoint 簡報以及常見影像格式。完整清單請參考官方文件。

**Q: 如何自訂水印外觀？**  
A: 使用 `Font` 類別設定大小、樣式與顏色，並在 `TextWatermark` 實例上呼叫 `setOpacity`、`setRotationAngle` 等方法。

**Q: 能否批次處理多封電郵？**  
A: 能。將整個工作流程包在迴圈中，遍歷資料夾內的檔案，重複使用同一 `TextWatermark` 實例以提升效能。

**Q: 我的水印在最後一頁被裁切，怎麼辦？**  
A: 確認水印尺寸在頁面邊界內。可使用 `watermark.setHorizontalAlignment` 與 `watermark.setVerticalAlignment` 調整位置。

## 實務應用

1. **內部文件共享：** 在向公司內部分發報告前嵌入品牌或機密標示。  
2. **客戶溝通：** 為合約與提案加上「機密」標記，提醒收件人遵守資料處理政策。  
3. **電郵行銷：** 在附於電子報的推廣 PDF 上加入細微品牌水印，提升品牌回想度且不影響設計。

## 效能考量

- **記憶體管理：** 如步驟 9 所示，及時關閉每個 `attachedWatermarker`，釋放本機資源。  
- **檔案大小上限：** 超過 10 MB 的附件建議使用串流方式或提升 JVM 堆疊大小。  
- **平行處理：** 可利用 Java `ExecutorService` 同時為多封電郵加水印，但需監控 CPU 使用率以免資源爭用。

## 結論

您現在已掌握完整、可投入生產環境的作法，能使用 **GroupDocs.Watermark for Java** 為電郵檔案中的每個支援附件**建立文字水印**並套用。將此工作流程整合至現有的電郵處理管線，即可提升文件安全、落實品牌一致性，且以最小的額外開銷達到合規需求。

準備好進一步行動了嗎？試著將程式碼擴充至處理整個 `.msg` 檔案資料夾，或探索圖像與 QR Code 等其他水印類型。

---

**最後更新：** 2026-04-07  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

**資源**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)