---
date: '2026-01-03'
description: 學習如何使用 GroupDocs.Watermark 在 Java 中為電子郵件加入浮水印，涵蓋嵌入圖像的電子郵件 Java 以及讀取圖像位元組的
  Java 技術，以確保電子郵件文件的安全。
keywords:
- Java Email Watermarking
- GroupDocs Watermark for Java
- Email Document Watermarking
title: 使用 GroupDocs.Watermark 在 Java 中添加電郵水印
type: docs
url: /zh-hant/java/email-document-watermarking/java-email-watermarking-groupdocs-guide/
weight: 1
---

# 如何使用 GroupDocs.Watermark 為 Java 添加電子郵件浮水印：逐步指南

## 簡介

您是否希望 **add email watermark java** 以在不影響完整性的情況下保護您的電子郵件文件？了解如何使用 GroupDocs.Watermark for Java 無縫將浮水印整合到您的電子郵件工作流程中。本教學將指導您載入電子郵件文件、讀取圖像檔案、將圖像嵌入為浮水印，並有效地儲存修改後的文件。

**您將學到：**
- 設定與使用 GroupDocs.Watermark for Java。  
- 將電子郵件文件載入您的應用程式。  
- 讀取並嵌入圖像至電子郵件。  
- 有效地儲存帶有浮水印的電子郵件文件。

### 快速回答
- **主要函式庫？** GroupDocs.Watermark for Java  
- **主要目標？** Add email watermark java to MSG/EML files  
- **關鍵步驟？** Load email → read image bytes → embed image → save  
- **需要授權嗎？** 是，需要有效的 GroupDocs 授權才能投入生產使用  
- **支援的格式？** MSG、EML 以及其他電子郵件類型  

## 什麼是 add email watermark java？

在 Java 中添加電子郵件浮水印是指以程式方式在電子郵件檔案的正文或附件中插入視覺識別標誌（例如標誌或免責聲明）。此舉有助於保護機密資訊、加強品牌形象，並驗證文件的真實性。

## 為何使用 GroupDocs.Watermark for Java？

GroupDocs.Watermark 提供高階 API，抽象化不同電子郵件格式的複雜性。它讓您專注於業務邏輯，同時在底層處理 MIME 結構、嵌入物件與圖像渲染。

## 先決條件

- **必備函式庫與相依性**
  - GroupDocs.Watermark for Java（版本 24.11 或更新）。  
  - 支援 Maven 專案的 IDE，例如 IntelliJ IDEA 或 Eclipse。  
- **環境設定需求**
  - 已安裝 JDK 8 或更新版本。  
  - 可存取用於儲存輸入與輸出檔案的目錄。  
- **知識先備**
  - 基本的 Java 程式設計。  
  - 熟悉檔案處理與 Maven。  

## 設定 GroupDocs.Watermark for Java

### 使用 Maven
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

### 直接下載
或者，直接從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

#### 授權取得步驟
- **免費試用：** 先下載免費試用版以探索 GroupDocs.Watermark 功能。  
- **臨時授權：** 若需延長評估，可透過 [GroupDocs' purchase page](https://purchase.groupdocs.com/temporary-license) 取得臨時授權。  
- **購買：** 考慮為生產環境購買完整授權。  

### 基本初始化與設定
```java
import com.groupdocs.watermark.Watermarker;

// Initialize GroupDocs.Watermark with your document path
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
Watermarker watermarker = new Watermarker(emailFilePath);
```

## 如何 add email watermark java

以下是一個完整的逐步指南，展示如何使用 API **add email watermark java**。

### 步驟 1：載入電子郵件文件

#### Overview
載入電子郵件文件是浮水印的第一步。GroupDocs.Watermark 允許您無縫載入各種格式。

#### Implementation
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;
```

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

*說明：* `EmailLoadOptions` 讓您微調 MSG/EML 檔案的解析方式。請確保檔案路徑指向有效的電子郵件檔案。

### 步驟 2：read image bytes java

#### Overview
要將圖像嵌入為浮水印，首先需要將圖像檔案讀取為位元組陣列。這就是 **read image bytes java** 步驟。

#### Implementation
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
```

```java
File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/sample.jpg");
byte[] imageBytes = new byte[(int) imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
```

*說明：* 將圖像轉換為位元組陣列，使其與 `addEmbeddedObject` API 相容，無論圖像大小如何。

### 步驟 3：embed image email java

#### Overview
現在您將圖像嵌入電子郵件內容。這是 **embed image email java** 操作，會產生 Content‑ID（CID）參考。

#### Implementation
```java
import com.groupdocs.watermark.contents.EmailContent;
import com.groupdocs.watermark.contents.EmailEmbeddedObject;
```

```java
EmailContent content = watermarker.getContent(EmailContent.class);
content.getEmbeddedObjects().add(imageBytes, "sample.jpg");

EmailEmbeddedObject embeddedObject = content.getEmbeddedObjects().get_Item(content.getEmbeddedObjects().getCount() - 1);
content.setHtmlBody("<html><body>This is an embedded image: <img src=\"cid:" + embeddedObject.getContentId() + "\"></body></html>");
```

*說明：* `add` 方法將圖像儲存為嵌入物件。產生的 CID 隨後在 HTML 本文中使用，以顯示浮水印。

### 步驟 4：儲存帶浮水印的電子郵件文件

#### Overview
在嵌入浮水印後，將變更持久化至新檔案。

#### Implementation
```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/message.msg";
watermarker.save(outputFilePath);
watermarker.close();
```

*說明：* `save` 將修改後的電子郵件寫入磁碟，而 `close` 釋放所有本機資源。

## 實際應用

1. **內部文件安全：** 防止敏感企業通訊被未授權轉發。  
2. **電子郵件行銷活動：** 為每封外發郵件加上您的標誌，以保持一致的辨識度。  
3. **法律文件：** 為法律往來加上防篡改浮水印，以確保完整性。

## 效能考量
- **優化圖像大小：** 使用壓縮的 PNG/JPEG 檔案以降低記憶體使用。  
- **資源管理：** 始終關閉串流 (`close()`) 以避免記憶體洩漏。  
- **非同步處理：** 對於大量操作，請在背景執行緒上處理電子郵件，或使用 Java 的 `CompletableFuture` 提升吞吐量。

## 常見問題與解決方案
| 問題 | 原因 | 解決方案 |
|------|------|----------|
| 電子郵件中未顯示圖像 | CID 參考不正確 | 驗證在 `<img src="cid:...">` 標籤中正確使用 `embeddedObject.getContentId()`。 |
| 浮水印未儲存 | `watermarker.save()` 在與輸入相同的路徑上被呼叫 | 使用不同的輸出目錄或檔名。 |
| 授權例外 | 授權檔案遺失或已過期 | 將有效的 `GroupDocs.Watermark.lic` 放置於應用程式根目錄，或以程式方式設定 `License`。 |

## 常見問答

**Q: 哪些圖像格式最適合 embed image email java？**  
A: 建議使用 PNG 與 JPEG，因為它們在品質與檔案大小之間取得平衡，且皆受到 GroupDocs.Watermark 完全支援。

**Q: 如何排除 read image bytes java 的問題？**  
A: 確認檔案路徑正確、檔案未被鎖定且您具有讀取權限。同時，驗證位元組陣列長度與檔案大小相符。

**Q: 我可以在同一封電子郵件中加入多個浮水印嗎？**  
A: 可以。對每個圖像呼叫 `content.getEmbeddedObjects().add(...)`，並相應更新 HTML 本文。

**Q: 能否對電子郵件內的附件進行浮水印？**  
A: GroupDocs.Watermark 可個別處理附件文件；您需要以程式方式提取、加浮水印，然後重新附加。

**Q: 此函式庫是否同時支援 EML 與 MSG 檔案？**  
A: 當然。相同的 API 可同時用於 MSG 與 EML 格式。

## 結論

您現在已掌握使用 GroupDocs.Watermark 的完整、可投入生產的 **add email watermark java** 方法。可嘗試不同的圖像樣式、探索文字浮水印，並將此工作流程整合到更大的電子郵件處理管線中，以實現強大的文件安全性。

---

**最後更新：** 2026-01-03  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs