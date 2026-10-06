---
date: '2025-12-31'
description: 學習如何使用 GroupDocs.Watermark for Java 搜尋電郵文字，並有效管理正文、主旨及附件。
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: 如何使用 GroupDocs.Watermark Java 搜尋電郵文字 – 完整指南
type: docs
url: /zh-hant/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 搜尋電子郵件文字

在電子郵件的主旨、內容或附件中尋找特定片語可能相當頭痛——尤其是當你要處理數十或數百封訊息時。在本教學中，你將學會 **如何搜尋電子郵件** 內容，快速且精準，使用 **GroupDocs.Watermark for Java**。我們會一步步說明設定、程式碼與最佳實踐技巧，讓你能自信地將電子郵件文字搜尋整合到自己的應用程式中。

## 快速答覆
- **哪個程式庫可以在 Java 中搜尋電子郵件文字？** GroupDocs.Watermark for Java。  
- **需要授權嗎？** 免費試用可用於測試；正式上線需購買授權。  
- **可以同時搜尋主旨與內容嗎？** 可以——設定 `EmailSearchableObjects` 以包含 Subject、HtmlBody 與 PlainTextBody。  
- **API 是否區分大小寫？** 可透過在 `TextSearchCriteria` 中設定相應旗標，執行不區分大小寫的搜尋。  
- **需要哪個 Java 版本？** JDK 8 或以上；建議使用 Maven 進行相依管理。

## 什麼是使用 GroupDocs.Watermark 的「搜尋電子郵件」？
GroupDocs.Watermark 提供統一的 API，用於定位、移除或修改多種文件類型（包括 **電子郵件訊息**（`.msg`、`.eml`））中的浮水印與純文字。透過其可搜尋物件模型，你可以精準鎖定電子郵件中關心的部分，讓大量處理既快速又可靠。

## 為什麼選擇 GroupDocs.Watermark Java 進行電子郵件搜尋？
- **統一 API** – 同一套程式碼模式即可處理 PDF、影像、Office 檔案與電子郵件。  
- **效能優化** – 搜尋操作在記憶體中執行，無需外部服務。  
- **強韌處理** – 支援 HTML 與純文字內容、附件，甚至受密碼保護的電子郵件。  
- **輕鬆整合** – 支援 Maven/Gradle，文件清晰且有活躍支援。

## 前置需求

- **Java Development Kit (JDK)** 8 或更新版本。  
- **Maven**（或 Gradle）用於相依管理。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 具備基本的 Java 語法與電子郵件檔案格式（`.msg`、`.eml`）認識。

## 設定 GroupDocs.Watermark for Java

### Maven 設定
將以下儲存庫與相依項目加入 `pom.xml`：

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
或者，你也可以從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 JAR。

### 取得授權
- **免費試用：** 無需授權金鑰即可測試核心功能。  
- **臨時授權：** 申請限時金鑰以延長評估期間。  
- **付費授權：** 購買後可無限制於正式環境使用。

#### 基本初始化
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 實作指南

### 功能 1：搜尋電子郵件內容

#### 概觀
我們將設定 API，掃描電子郵件的 **主旨**、**HTML 內容** 與 **純文字內容**，尋找指定關鍵字。

#### 步驟 1：定義文件路徑
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### 步驟 2：設定載入選項與 Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### 步驟 3：建立搜尋條件
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### 步驟 4：指定搜尋位置
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### 步驟 5：執行搜尋並清除浮水印
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### 步驟 6：儲存變更
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### 疑難排解小技巧
- **結果為空：** 確認關鍵字確實出現在所選的電子郵件部分。  
- **效能問題：** 僅保留必要的可搜尋物件（例如 Subject + PlainTextBody），可加速大量批次處理。

### 功能 2：載入電子郵件文件選項

#### 概觀
`EmailLoadOptions` 讓你控制電子郵件的解析方式——對於加密訊息或自訂編碼特別有用。

#### 步驟 1：設定載入選項
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 主要設定項目
- **密碼保護：** 使用 `loadOptions.setPassword("yourPassword")` 讀取加密的 `.msg` 檔案。  
- **編碼設定：** 當處理非標準字元集時，可使用 `loadOptions.setEncoding(Charset.forName("UTF-8"))` 進行調整。

## 實務應用

- **自動化電子郵件處理：** 大量掃描進來的客服票證，尋找「退款」或「錯誤」等關鍵字。  
- **法規遵循檢查：** 快速定位公司郵件存檔中的機密詞彙（如身分證號、信用卡號）。  
- **客服自動化：** 依偵測到的片語將郵件路由至相應的支援團隊。

## 效能考量
- **資源管理：** 完成處理後立即呼叫 `watermarker.close()`，釋放原生資源。  
- **記憶體最佳實踐：** 處理上千封訊息時，建議分批處理，並盡可能重複使用 `Watermarker` 實例。

## 結論
現在你已掌握使用 GroupDocs.Watermark Java **搜尋電子郵件** 內容的完整、可投入生產的做法。此 API 的彈性讓你能針對電子郵件的特定部位進行搜尋、清除不需要的浮水印，並將邏輯整合至更大的工作流程中。

### 後續步驟
- 嘗試 **多重搜尋條件**（例如同時搜尋「發票」 + 「逾期」）。  
- 探索 **加入浮水印**，以標記含有敏感資料的郵件。  
- 使用相同的 Watermarker 工作流程，深入其他文件類型（PDF、DOCX）。

## 常見問題

**Q1：** 如何使用 GroupDocs.Watermark 處理加密的電子郵件？  
**A1：** 在建立 `Watermarker` 實例前，使用 `EmailLoadOptions.setPassword("yourPassword")`。

**Q2：** 可以一次搜尋多個關鍵字嗎？  
**A2：** 可以——為每個關鍵字建立獨立的 `SearchCriteria` 物件，並以邏輯運算子（如 `OrSearchCriteria`）組合。

**Q3：** GroupDocs.Watermark Java 可以免費使用嗎？  
**A3：** 提供免費試用供評估使用。正式上線需購買授權。

**Q4：** 如何有效處理大量電子郵件？  
**A4：** 僅保留必要的可搜尋物件，分批處理郵件，並在完成後始終關閉 `Watermarker` 以釋放資源。

**Q5：** 哪裡可以取得更多協助或支援？  
**A5：** 前往 [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) 取得社群協助，或直接聯絡 GroupDocs 支援團隊。

## 參考資源
- **文件說明：** 前往 [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) 瀏覽詳細指南。  
- **API 參考：** 參見 [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) 取得技術細節。

---

**最後更新：** 2025-12-31  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

---