---
date: '2026-02-05'
description: 學習如何使用 GroupDocs.Watermark for Java 從 Word 文件中提取形狀，包括如何在 Java 中載入 Word
  文件以及操作形狀資料。
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: 如何使用 GroupDocs.Watermark Java 從 Word 文件中提取圖形
type: docs
url: /zh-hant/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在 Java 中從 Word 文件提取形狀

在本教學中，您將了解 **如何從 Word 文件提取形狀**，使用 GroupDocs.Watermark Java 函式庫。無論您是需要分析圖表、提取嵌入的圖片，或是自動化報告產生，提取形狀的中繼資料都能讓您建立更智慧的文件處理流程。我們將逐步說明如何設定函式庫、載入 Word 文件，以及取得詳細的形狀資訊——全部以清晰的 Java 程式碼示範。

## 快速答覆
- **「extract shapes」是什麼意思？** 取得 Word 檔案中每個繪圖物件的中繼資料（類型、大小、位置、文字、圖片）。  
- **哪個函式庫負責此功能？** GroupDocs.Watermark for Java。  
- **我需要授權嗎？** 試用版可用於開發；完整授權可解除使用限制。  
- **我也能從形狀取得圖片嗎？** 可以——API 會公開圖片形狀的位元組資料。  
- **需要哪個 Java 版本？** JDK 8 或更新版本。

## 在 Word 文件的情境下，「如何提取形狀」是什麼意思？
提取形狀是指以程式方式存取每個繪圖元素──圖片、WordArt、自動圖形、圖表，甚至嵌入於頁首或頁尾的形狀。這些資訊可用於驗證、遷移或內容驅動的分析。

## 為什麼要使用 GroupDocs.Watermark for Java？
GroupDocs.Watermark 提供高階且記憶體效能佳的 API，抽象化底層 Office Open XML 的複雜性。它讓您可以：
- 快速載入文件（`WordProcessingLoadOptions`）。  
- 在不處理低階 XML 的情況下遍歷節與形狀。  
- 只需一次呼叫即可取得圖片資料、文字、對齊方式與旋轉角度。  
- 無縫整合至現有的 Java 服務或微服務。

## 前置條件
- **Java Development Kit (JDK)** 8 或以上。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse。  
- 基本的 Java I/O 知識。  
- 取得 **GroupDocs.Watermark for Java** 授權或試用版。

## 設定 GroupDocs.Watermark for Java
透過 Maven 或直接下載方式整合此函式庫。

### 使用 Maven
在 `pom.xml` 中加入儲存庫與相依性：

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
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 JAR。

### 取得授權
免費試用版足以進行測試。若要正式上線，請申請永久授權以解鎖全部功能。

## 實作指南
我們將實作分為兩個清晰步驟：**載入 Word 文件** 與 **提取形狀資訊**。

### 步驟 1：載入 Word 文件（load word document java）
首先，設定載入選項並建立 `Watermarker` 實例。此步驟會為後續檢查做好文件的準備。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **小技巧：** 盡量將 `Watermarker` 實例的作用域限制在最小範圍；及時關閉可釋放原生資源，避免記憶體洩漏。

### 步驟 2：提取形狀資訊（extract images from shapes）
現在我們將取得每個形狀的詳細資訊，包括任何嵌入的圖片。程式碼會遍歷每個節與每個形狀，並輸出有用的中繼資料。

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**此程式碼的功能：**  
- 取得每個形狀的 **type**（例如 picture、WordArt）。  
- 輸出 **size**、**position** 與 **rotation** 的數值。  
- 顯示 **alternative text** 與 **name**，有助於可及性檢查。  
- 若形狀包含圖片，則輸出圖片的 **pixel dimensions** 與 **byte size**——非常適合從形狀中提取圖片。

### 常見陷阱與解決方法
| 問題 | 原因 | 解決方案 |
|-------|-------|----------|
| `FileNotFoundException` | 檔案路徑錯誤或缺少權限 | 確認絕對或相對路徑正確，且檔案可讀取。 |
| Null `shape.getImage()` | 形狀不是圖片（例如 auto‑shape） | 如範例所示，以 `if (shape.getImage() != null)` 進行檢查。 |
| 大型文件記憶體使用過高 | 一次載入整個文件 | 一次處理單一節，或提升 JVM 堆積大小（`-Xmx`）。 |
| 缺少頁首/頁尾形狀 | 未檢查 `shape.getHeaderFooter()` | 範例已在形狀屬於頁首/頁尾時記錄。 |

## 實務應用
1. **自動化報告產生** – 提取圖表與示意圖，嵌入後續的 PDF。  
2. **合規稽核** – 驗證所有形狀是否具備適當的 alternative text，以符合可及性要求。  
3. **內容遷移** – 將舊版 Word 檔案中的嵌入圖片匯出至數位資產管理系統。  

## 效能考量
- **釋放資源**：務必在 `finally` 區塊中呼叫 `watermarker.close()`，或在使用 API 時採用 try‑with‑resources。  
- **分段處理**：對於超過 50 MB 的文件，建議分別處理每個節，以降低記憶體佔用。  
- **執行緒安全**：`Watermarker` 實例非執行緒安全，請為每個執行緒建立新實例。

## 結論
您現在已掌握使用 GroupDocs.Watermark for Java **提取 Word 文件形狀** 的方法，從載入檔案到讀取每個形狀的中繼資料與嵌入圖片資料。此功能為進階文件分析、自動化內容管線與可及性驗證開啟了新可能。

### 後續步驟
- 嘗試修改形狀屬性（例如調整大小或重新定位）。  
- 結合 **GroupDocs.Parser** 以提取相鄰文字。  
- 將提取邏輯整合至 REST 服務，以提供即時處理。

## 常見問答
**Q: 什麼是 GroupDocs.Watermark for Java？**  
A: 它是一套完整的函式庫，旨在管理跨格式的浮水印與文件內容，支援形狀提取、圖片取得與文字操作等工作。

**Q: 沒有授權能提取形狀中的圖片嗎？**  
A: 試用版允許提取，但完整授權可解除使用限制，並支援商業部署。

**Q: 這能用於 `.doc`（二進位）檔案嗎？**  
A: 可以，API 同時支援 `.docx` 與舊版 `.doc` 格式。

**Q: 如何處理受密碼保護的文件？**  
A: 在建立 `Watermarker` 前，使用 `WordProcessingLoadOptions.setPassword("yourPassword")` 提供密碼。

**Q: 有辦法將提取的形狀資料匯出為 JSON 嗎？**  
A: 您可以將列印的值映射為 POJO，並使用任意 JSON 函式庫（例如 Jackson）序列化該集合。

---

**最後更新：** 2026-02-05  
**測試版本：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs