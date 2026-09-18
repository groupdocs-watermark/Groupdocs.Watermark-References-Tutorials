---
date: '2026-02-13'
description: 學習如何在 Java 中加入水印，並使用 GroupDocs.Watermark 高效列出支援的檔案格式，確保各類文件的相容性。
keywords:
- GroupDocs Watermark Java
- list supported file formats GroupDocs
- Java watermarking library
title: 在 Java 中添加水印：使用 GroupDocs 列出支援的格式
type: docs
url: /zh-hant/java/document-information/groupdocs-watermark-java-list-supported-formats/
weight: 1
---

# 在 Java 中加入浮水印：使用 GroupDocs 列出支援的格式

## 快速解答
- **這個函式庫的功能是什麼？** 它讓您能在多種文件類型上 add watermark java，並取得支援的格式。  
- **哪個方法會列出格式？** `FileType.getSupportedFileTypes()` 會回傳所有可用的類型。  
- **我需要授權嗎？** 試用版可用於測試；正式環境需購買授權。  
- **可以在 Maven 中使用嗎？** 可以，只要加入 GroupDocs 的儲存庫與相依性。  
- **Java 8 足夠嗎？** 足夠，支援 JDK 8 或更高版本。

## 什麼是 “add watermark java”？
在 Java 中加入浮水印是指以程式方式在文件上覆蓋文字或圖像，以保護或加上品牌。GroupDocs.Watermark 提供簡潔的 API，能自動處理數十種檔案類型的繁雜工作。

## 為什麼要列出支援的格式？
了解確切的格式可協助您 **retrieve file types java** 相容的檔案類型，避免執行時錯誤，並能為使用者上傳建立動態驗證邏輯。

## 前置條件

- **必要的函式庫**：GroupDocs.Watermark for Java 版本 24.11 或更新版本。  
- **環境**：已安裝 JDK 8 + 與 Maven。  
- **知識需求**：基本的 Java 與 Maven 相依性管理。

## 設定 GroupDocs.Watermark for Java

### 透過 Maven 安裝

將儲存庫與相依性加入您的 `pom.xml`：

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

或者，從 [GroupDocs releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本的 GroupDocs.Watermark for Java。

#### 取得授權

若要使用 GroupDocs.Watermark，必須取得授權。可選擇先使用免費試用版或申請臨時授權。

### 初始化與設定

在加入相依性或下載函式庫後，於您的 Java 專案中進行初始化：

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.common.FileType;

public class WatermarkExample {
    public static void main(String[] args) {
        // Initialize a watermarker object for demonstration purposes
        Watermarker watermarker = new Watermarker("path/to/your/file");
        
        // Your code to list supported file formats will go here

        watermarker.close();
    }
}
```

## 如何 add watermark java 並列出支援的檔案格式

### 步驟 1：取得所有支援的檔案類型  

使用 `FileType` 類別取得函式庫可處理的所有格式：

```java
// STEP 1: Retrieve all supported file types from the GroupDocs library
FileType[] fileTypes = FileType.getSupportedFileTypes();
```

### 步驟 2：遍歷並印出檔案類型名稱  

遍歷陣列並顯示每個格式名稱：

```java
// STEP 2: Iterate over each file type and print its name
for (FileType fileType : fileTypes) {
    System.out.println(fileType);
}
```

執行此程式碼會列印出如 `PDF`、`DOCX`、`PNG` 等清單，讓您清楚了解可以 **list supported formats java** 的檔案類型。

## 常見問題與解決方案

- **相依性錯誤** – 請確認 Maven 坐標與您加入的版本相符。  
- **不支援的 Java 版本** – 此函式庫需要 JDK 8 或更新版本；若看到相容性警告請升級。  
- **效能小技巧** – 若格式數量龐大，建議將資訊寫入檔案而非使用 `System.out.println`，以避免主控台瓶頸。

## 實務應用

1. **文件管理系統** – 在套用浮水印前，根據取得的清單動態驗證上傳檔案。  
2. **內容發佈平台** – 確保只有支援的影像與 PDF 類型會加上品牌浮水印。  
3. **法律文件工作流程** – 自動保護所有函式庫支援格式的機密檔案。

## 效能考量

- **資源使用** – 及時關閉 `Watermarker` 實例（如初始化範例所示），以釋放記憶體。  
- **可擴充性** – 處理上千檔案時，批次檢查格式並盡可能重複使用單一 `Watermarker` 實例。

## 結論

在本教學中，您學會了如何使用 GroupDocs.Watermark **add watermark java**，同時 **retrieve file types java** 與 **list supported formats java**。掌握這些知識後，您即可建立可靠的文件處理流程，只處理相容的檔案，並自信地套用浮水印。

### 後續步驟

探索其他功能，例如加入文字或圖像浮水印、調整不透明度與位置。API 提供豐富選項，讓您依品牌需求客製化浮水印。

## 常見問答

1. **GroupDocs.Watermark 支援哪些檔案格式？**  
   - 此函式庫支援多種文件類型，包括 PDF、影像、Word 文件等。  
2. **如何排除 GroupDocs.Watermark 的問題？**  
   - 檢查您的 Maven 相依性，並確保與您的 Java 版本相容。  
3. **可以將 GroupDocs.Watermark 用於商業用途嗎？**  
   - 可以，但試用期結束後需購買授權。  
4. **如果列出檔案格式時應用程式變慢，我該怎麼辦？**  
   - 透過及時關閉檔案與物件來最佳化資源管理。  
5. **在哪裡可以找到更多使用 GroupDocs.Watermark 的範例？**  
   - 前往 [GroupDocs GitHub repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) 查看更多程式碼範例。

## 常見問題

**Q: 如何以程式方式檢查特定檔案類型是否受支援？**  
A: 取得 `FileType[]` 後，將 `fileType.toString()` 與目標副檔名比較即可。

**Q: 能否將清單過濾為僅影像格式？**  
A: 可以 – 遍歷陣列並使用 `fileType.isImage()`（或檢查副檔名）來挑選影像類型。

**Q: 在列出格式時，函式庫是否支援受密碼保護的 PDF？**  
A: 列出格式與檔案內容無關，密碼保護不會影響取得。

**Q: 是否可以在不初始化 `Watermarker` 實例的情況下取得清單？**  
A: 完全可以。`FileType.getSupportedFileTypes()` 為靜態方法，無需 `Watermarker`。

## 資源

- **文件說明**： [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API 參考**： [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **下載**： [Latest Release](https://releases.groupdocs.com/watermark/java/)  
- **GitHub**： [GroupDocs.Watermark Java GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **免費支援**： [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **臨時授權**： [Purchase Temporary License](https://purchase.groupdocs.com/temporary-license/)  

立即開始使用 GroupDocs.Watermark for Java，為您的應用程式解鎖強大的文件處理功能！

---

**最後更新：** 2026-02-13  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs