---
date: '2025-12-21'
description: 學習如何在 GroupDocs.Watermark for Java 中使用水印，列出所有支援的檔案格式，確保文件之間的無縫相容性。
keywords:
- GroupDocs Watermark Java
- list supported file formats GroupDocs
- Java watermarking library
title: 如何使用水印 – 列出 Java 支援的格式
type: docs
url: /zh-hant/java/document-information/groupdocs-watermark-java-list-supported-formats/
weight: 1
---

# 如何使用 Watermark – 列出 Java 支援的格式

在處理多種文件類型時可能會很具挑戰性，特別是當您需要在應用程式中可靠地使用 **how to use watermark** 功能時。本指南將逐步說明如何列出 GroupDocs.Watermark for Java 支援的所有檔案格式。完成後，您將了解如何整合此函式庫、取得格式清單，並將此知識應用於實務情境，例如文件管理系統或內容發布管線。

## 快速解答
- **在 Java 中「how to use watermark」是什麼意思？** 這表示呼叫 GroupDocs.Watermark API 以操作支援的檔案類型。  
- **需要哪個版本的函式庫？** GroupDocs.Watermark Java 24.11 或更新版本。  
- **需要授權嗎？** 開發階段可使用試用版；正式環境必須取得永久授權。  
- **可以在 JDK 8+ 上執行嗎？** 可以，函式庫相容於 JDK 8 及以上版本。  
- **格式清單是靜態的嗎？** 清單會依您使用的函式庫版本而定；較新版本可能會加入新格式。

## 如何使用 Watermark – 列出支援的格式

### 介紹

在開始撰寫程式碼之前，請先確保您的開發環境符合以下前置條件。此步驟可節省時間，並避免許多開發者在首次學習 **how to use watermark** 功能時常見的「class not found」錯誤。

## 前置條件

- **必需函式庫**：GroupDocs.Watermark for Java 24.11 或更新版本。  
- **環境**：JDK 8 或更高版本，Maven 3.6 以上。  
- **知識**：基本的 Java 語法與 Maven 依賴管理。

## 設定 GroupDocs.Watermark for Java

### 透過 Maven 安裝

將儲存庫與依賴項目加入您的 `pom.xml` 檔案：

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

或者，從 [GroupDocs releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 GroupDocs.Watermark for Java 版本。

#### 取得授權

若要在正式環境使用 GroupDocs.Watermark，必須取得授權。您可以先使用免費試用版，或申請臨時授權以進行評估。

### 初始化與設定

在加入依賴或下載函式庫後，於 Java 專案中初始化它：

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

## 實作指南

### 列出支援的檔案格式

此功能可讓您取得並顯示 GroupDocs.Watermark 所支援的所有檔案類型。

#### 步驟 1：取得所有支援的檔案類型

使用 `FileType` 類別的方法取得支援格式的陣列：

```java
// STEP 1: Retrieve all supported file types from the GroupDocs library
FileType[] fileTypes = FileType.getSupportedFileTypes();
```

#### 步驟 2：遍歷並列印檔案類型名稱

遍歷取得的檔案類型，並列印其名稱：

```java
// STEP 2: Iterate over each file type and print its name
for (FileType fileType : fileTypes) {
    System.out.println(fileType);
}
```

### 疑難排解技巧

- **常見問題**：確認 Maven 依賴已正確定義。不相容的 JDK 版本常會導致 `NoClassDefFoundError`。  
- **效能考量**：若格式清單非常龐大，請將輸出導向日誌檔案而非直接印到主控台，以免造成 UI 卡頓。

## 實務應用

了解 GroupDocs.Watermark 支援的檔案格式可在多種情境中發揮效益：

1. **文件管理系統** – 僅對支援的類型自動套用浮水印，避免執行時錯誤。  
2. **內容發布平台** – 在發佈前為 PDF、影像與 Office 文件加上安全浮水印。  
3. **法律文件處理** – 透過浮水印確保所有支援的法律檔案格式保持機密。

## 效能考量

大量處理檔案時，請遵守以下最佳實踐：

- **資源管理** – 必須在使用完畢後關閉 `Watermarker` 物件，以釋放記憶體。  
- **記憶體監控** – 使用 Java 效能分析工具監測大量作業期間的堆積使用情形。

## 結論

我們已說明 **how to use watermark** 以列出 GroupDocs.Watermark for Java 所支援的全部格式。此知識可協助您設計具彈性的浮水印工作流程，讓程式自動依函式庫功能調整。

### 後續步驟

- 探索使用相同的 `Watermarker` 例項加入文字或影像浮水印。  
- 嘗試自訂浮水印的位置與不透明度設定。

準備好實作了嗎？將上述程式碼片段加入您的專案，立即開始打造更智慧、更安全的文件管線吧！

## 常見問答

1. **GroupDocs.Watermark 支援哪些檔案格式？**  
   - 函式庫支援 PDF、常見影像類型（PNG、JPEG、BMP、GIF、TIFF）、Microsoft Office 檔案（DOCX、PPTX、XLSX）以及其他多種格式。  
2. **如何排除 GroupDocs.Watermark 的問題？**  
   - 確認 Maven 依賴正確，且使用相容的 JDK 版本。  
3. **可以將 GroupDocs.Watermark 用於商業用途嗎？**  
   - 可以，但正式環境必須擁有有效授權。  
4. **若列出檔案格式時應用程式變慢，該怎麼辦？**  
   - 立即關閉 `Watermarker` 物件以釋放資源，並考慮將輸出寫入檔案。  
5. **哪裡可以找到更多 GroupDocs.Watermark 的範例？**  
   - 前往 [GroupDocs GitHub repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) 取得更多程式碼範例。

## 其他常見問題

**Q: 格式清單會隨函式庫新版本自動更新嗎？**  
A: 清單會反映您所使用版本內建的格式；升級函式庫即可取得新加入的支援類型。

**Q: 能否只篩選出影像格式的清單？**  
A: 可以，取得 `FileType[]` 後，檢查每個 `FileType` 並比對已知的影像副檔名即可。

**Q: 是否能在處理前程式化檢查特定檔案是否受支援？**  
A: 可使用 `FileType.isSupported(filePath)`（或類似工具）驗證檔案相容性。

---

**最後更新：** 2025-12-21  
**測試環境：** GroupDocs.Watermark Java 24.11  
**作者：** GroupDocs  

**資源**

- **文件說明**：[GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API 參考**：[GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **下載**：[Latest Release](https://releases.groupdocs.com/watermark/java/)  
- **GitHub**：[GroupDocs.Watermark Java GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **免費支援**：[GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **臨時授權**：[Purchase Temporary License](https://purchase.groupdocs.com/temporary-license/)