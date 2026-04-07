---
date: '2026-04-07'
description: 學習如何使用 GroupDocs.Watermark 在 Java 中搜尋電郵內容，包括如何搜尋多個關鍵字的電郵以及如何移除電郵浮水印。
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 使用 GroupDocs.Watermark 在 Java 中搜尋電郵內容：完整指南
type: docs
url: /zh-hant/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# 使用 GroupDocs.Watermark 搜尋 Email 內容（Java）

如果您需要快速且可靠地 **search email body java**，您來對地方了。在本教學中，我們將說明 GroupDocs.Watermark for Java 如何讓您在電子郵件主旨、HTML 內容與純文字內容中定位特定文字，並在之後清除不需要的浮水印。完成後，您將能實作一個穩健的解決方案，支援單一或多個關鍵字，甚至在需要時移除電子郵件浮水印。

## 快速解答
- **What does “search email body java” mean?** 它指的是使用 Java 程式碼（搭配 GroupDocs.Watermark）在電子郵件內容中尋找文字。  
- **Can I search multiple keywords email at once?** 是的 – 建立獨立的 `SearchCriteria` 物件並將它們組合起來。  
- **How to remove email watermarks?** 在搜尋後使用 `PossibleWatermarkCollection.clear()` 方法。  
- **Do I need a license?** 免費試用可用於測試；正式環境需購買永久授權。  
- **Which IDE works best?** IntelliJ IDEA 或 Eclipse 均得到完整支援。

## 您將學習
- 安裝與設定 GroupDocs.Watermark for Java。  
- 設定搜尋條件以 **search email body java** 橫跨主旨與內容。  
- 在單次執行中使用 **search multiple keywords email** 的技巧。  
- 找到後執行 **how to remove email watermarks** 的具體步驟。  

## 為何使用 GroupDocs.Watermark 搜尋 Email 內容（Java）？
GroupDocs.Watermark 提供高階 API，抽象化解析 .msg 檔案、處理不同內容格式與管理浮水印的複雜性。與自行開發解析器相比，可節省時間，並確保在大量電子郵件批次中取得一致的結果。

## 先決條件
- Java Development Kit (JDK) 8 或更新版本。  
- Maven（或手動加入 JAR 的能力）。  
- 具備 Java 與電子郵件檔案格式（.msg、.eml）的基本知識。  

## 設定 GroupDocs.Watermark for Java
GroupDocs.Watermark for Java 簡化了文件（包括電子郵件）中的浮水印與文字搜尋。以下是將此函式庫加入專案的兩種最常見方式。

### Maven 設定
在 `pom.xml` 檔案中加入以下內容，以將 GroupDocs.Watermark 作為相依性加入：
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
或者，您也可以直接從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權步驟
- **Free Trial:** 開始使用免費試用以測試基本功能。  
- **Temporary License:** 取得臨時授權以獲得更長的存取與測試時間。  
- **Purchase:** 若 GroupDocs.Watermark 符合需求，請考慮購買。

#### 基本初始化
如下所示初始化 `Watermarker` 類別：
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 實作指南

### 功能 1：在 Email 內容中搜尋文字
此功能可在電子郵件的主旨與內容中搜尋特定文字。

#### 概觀
我們將示範如何使用 Java 程式碼設定 GroupDocs.Watermark，以搜尋電子郵件訊息的不同部分。

##### 步驟 1：定義文件路徑
設定處理電子郵件的輸入與輸出路徑：
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### 步驟 2：設定載入選項與 Watermarker
初始化 `EmailLoadOptions` 與 `Watermarker` 以處理您的電子郵件文件。
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### 步驟 3：建立搜尋條件
定義文字搜尋的條件。我們將使用不區分大小寫的搜尋關鍵字 **"test"**：
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### 步驟 4：指定搜尋位置
設定搜尋範圍，同時涵蓋電子郵件的主旨與內容：
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### 步驟 5：執行搜尋並清除浮水印
執行搜尋並移除所有找到的浮水印：
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### 步驟 6：儲存變更
處理完成後，將變更儲存至新文件：
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### 疑難排解提示
- **Common Issue:** 如果搜尋結果為空，請確認文字確實存在於電子郵件的內容或主旨中。  
- **Performance Tip:** 透過僅搜尋實際需要的區段來最佳化效能。

### 功能 2：載入 Email 文件選項
本節說明在使用 GroupDocs.Watermark 載入電子郵件文件進行處理時，如何設定額外的選項。

#### 概觀
設定載入選項可讓您更精細地控制文件處理方式，例如指定密碼保護或編碼設定。

##### 步驟 1：設定載入選項
以下是 `EmailLoadOptions` 的基本設定範例：
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 主要設定選項
- **Password Protection:** 如果您的電子郵件已加密，請指定密碼。  
- **Encoding Settings:** 根據需求定義特定的編碼類型。  

## 如何搜尋多個關鍵字（Email）
如果您需要一次定位多個詞彙，請建立多個 `SearchCriteria` 物件，並使用邏輯 **OR** 或 **AND** 運算子將它們組合。API 允許鏈接條件，您可以搜尋 “invoice” **or** “receipt” 而無需執行多次迴圈。

## 如何移除 Email 浮水印
在定位到浮水印（或任何符合條件的文字）後，`PossibleWatermarkCollection.clear()` 方法會將其從電子郵件文件中移除。這正是我們在上述 **Step 5** 中使用的步驟，且適用於任意數量的匹配項目。

## 實務應用

### 使用案例 1：自動化 Email 處理
自動化大量 Email 資料的篩選與處理，以高效找出特定內容。

### 使用案例 2：法律合規檢查
透過搜尋公司 Email 中的敏感資訊，確保合規性。

### 使用案例 3：客戶支援自動化
快速定位客戶詢問中的關鍵字或片語，簡化支援工作流程。

## 效能考量
使用 GroupDocs.Watermark 時，請考慮以下方式以最佳化效能：
- **Resource Management:** 有效管理記憶體與處理能力，以處理大型 Email 資料集。  
- **Java Memory Management Best Practices:** 定期監控資源使用情況，並及時釋放資源。  

## 常見問題

**Q:** 如何使用 GroupDocs.Watermark 處理加密的 Email？  
**A:** 在初始化 `Watermarker` 時，使用 `EmailLoadOptions` 指定密碼。

**Q:** 是否可以一次搜尋多個關鍵字？  
**A:** 可以，建立獨立的 `SearchCriteria` 實例，並使用邏輯運算子將它們組合。

**Q:** GroupDocs.Watermark Java 是否免費使用？  
**A:** 提供免費試用；若需擴充功能，請考慮購買授權。

**Q:** 如何有效處理大量 Email？  
**A:** 透過針對特定 Email 區段進行搜尋，並有效管理資源，以最佳化效能。

**Q:** 我可以在哪裡取得額外的協助或支援？  
**A:** 前往 [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) 取得社群支援，或聯絡他們的免費支援渠道。

## 資源
- **Documentation:** 深入指南請參考 [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/)。  
- **API Reference:** 技術細節請參考 [GroupDocs API](https://apireference.groupdocs.com/watermark/java/)。  

---

**最後更新:** 2026-04-07  
**測試環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs