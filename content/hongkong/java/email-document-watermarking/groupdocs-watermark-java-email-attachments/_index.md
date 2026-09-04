---
date: '2025-12-29'
description: 了解如何使用 GroupDocs.Watermark for Java 為電郵附件添加水印。本指南提供逐步說明與最佳實踐。
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: 使用 GroupDocs.Watermark for Java 為電郵附件添加水印
type: docs
url: /zh-hant/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# 使用 GroupDocs.Watermark for Java 為電郵附件添加水印

在當今的數位環境中，保護敏感資訊至關重要——尤其是在附件離開收件箱之前 **為電郵添加水印**。無論您是想加強文件安全的開發人員，還是希望為每個外發檔案加上品牌標誌的企業，本教學將示範如何使用 GroupDocs.Watermark for Java 為電郵訊息中的所有支援附件套用文字水印。

## 快速解答
- **「為電郵添加水印」能達成什麼目的？** 它會在每個支援的附件中嵌入可見或半透明的標籤（例如「Confidential」），以阻止未經授權的散布。  
- **需要哪個函式庫？** GroupDocs.Watermark for Java（最新版本）。  
- **是否需要授權？** 試用授權可用於開發；商業授權則需於正式環境使用。  
- **可以一次處理多封電郵嗎？** 可以——將步驟包在針對 *.msg* 檔案資料夾的迴圈中。  
- **支援哪些檔案類型？** PDF、Word、Excel、PowerPoint、圖片等多種格式（詳見官方文件）。

## 什麼是「為電郵添加水印」？
為電郵添加水印指的是以程式方式開啟電郵檔案，提取每個附件，並在這些文件上蓋上自訂文字（或圖片）標記，然後再發送或儲存電郵。這可確保水印隨檔案一起傳遞，強化機密性與品牌識別。

## 為何使用 GroupDocs.Watermark for Java？
- **廣泛的格式支援** – 可處理 PDF、Office 檔案、圖片等。  
- **簡易 API** – 只需幾行程式碼即可建立、套用與儲存水印。  
- **效能導向** – 低記憶體佔用，適合伺服器端處理。  
- **企業級授權** – 提供評估用試用版，正式環境則需付費授權。

## 前置條件
- 已安裝 Java Development Kit（JDK）。  
- 使用 IntelliJ IDEA 或 Eclipse 等開發環境。  
- 已將 GroupDocs.Watermark for Java 加入專案（請參考以下設定步驟）。

## 設定 GroupDocs.Watermark for Java

### Maven 設定
若使用 Maven，請在 `pom.xml` 中加入儲存庫與相依性：

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
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

#### 取得授權
- 取得免費試用，請於 GroupDocs 官網註冊並申請臨時授權。  
- 若為商業使用，請購買完整授權。更多資訊請參閱 [purchase page](https://purchase.groupdocs.com/temporary-license/)。

### 基本初始化
載入您需要的核心類別：

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## 如何為電郵附件添加水印 – 步驟說明

### 步驟 1：建立文字水印
首先，定義水印文字及其外觀。

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### 步驟 2：設定電郵載入選項
設定載入器，使 GroupDocs 能讀取 *.msg* 檔案。

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### 步驟 3：為電郵檔案初始化 Watermarker
將 `Watermarker` 指向您要處理的電郵。

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### 步驟 4：取得電郵內容
取得電郵的內部結構，以便操作其附件。

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### 步驟 5：遍歷附件
逐一遍歷每個附件，並確認其是否可加水印。

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

### 步驟 6‑9：為支援的附件添加水印
對於每個符合條件的檔案，使用新的 `Watermarker` 開啟，套用水印，並將變更寫回電郵。

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

### 步驟 10：儲存已加水印的電郵
將修改後的電郵寫入新檔案，以免影響原始檔案。

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### 步驟 11：清理資源
關閉主要的 `Watermarker` 以釋放資源。

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## 實務應用
1. **內部文件共享** – 在內部分發前，於每個附件嵌入公司品牌或機密聲明。  
2. **客戶溝通** – 使用明顯的「Confidential」標籤保護合約、提案與財務報表。  
3. **電郵行銷活動** – 為促銷電郵附帶的 PDF 或圖片添加低調的品牌水印，提升品牌記憶。

## 效能考量
- **記憶體管理** – 一次處理一個附件，並即時關閉每個 `Watermarker`。  
- **附件大小** – 大檔案會延長處理時間；建議在加水印前先壓縮或限制檔案大小。  
- **批次處理** – 針對 *.msg* 檔案目錄進行迴圈，以分攤大量電郵的處理開銷。

## 常見問答

**Q: 可以為加密檔案添加水印嗎？**  
A: 不行。出於安全考量，GroupDocs.Watermark 不支援對加密文件加水印。

**Q: 支援哪些檔案類型的水印？**  
A: PDF、Word、Excel、PowerPoint、圖片（PNG、JPEG、BMP）以及其他多種常見格式。完整清單請參閱官方文件。

**Q: 如何自訂水印的外觀？**  
A: 您可透過 `TextWatermark` 建構子及其屬性調整字型、大小、顏色、不透明度、旋轉角度與位置。

**Q: 是否可以批次處理多封電郵？**  
A: 可以。將步驟包在 `for` 迴圈中，遍歷 *.msg* 檔案資料夾，對每封電郵套用相同邏輯。

**Q: 我的水印沒有顯示——應該檢查什麼？**  
A: 請確認附件的檔案類型受支援、確保水印尺寸符合頁面大小，且文件未設定密碼保護。

## 資源
- [文件說明](https://docs.groupdocs.com/watermark/java/)  
- [API 參考](https://reference.groupdocs.com/watermark/java)  
- [下載 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

---

**最後更新：** 2025-12-29  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

---