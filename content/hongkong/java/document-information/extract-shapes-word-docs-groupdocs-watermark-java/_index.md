---
date: '2025-12-20'
description: 學習如何使用 GroupDocs.Watermark for Java 從 Word 文件中提取圖像及形狀，完美適用於文件自動化與處理。
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: 如何在 Java 中使用 GroupDocs.Watermark 從 Word 文件提取圖片
type: docs
url: /zh-hant/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在 Java 中從 Word 文件提取圖像

在現代文件處理應用程式中，**從 Word 提取圖像** 是常見需求——無論是需要重用圖形、執行 OCR，或僅僅審核內容。本教學將一步步說明如何在 Java 中使用 GroupDocs.Watermark 載入 Word 文件，然後 **從 Word 文件提取圖像**，同時示範 **如何提取形狀**。完成後，您將擁有可直接嵌入自動化流程的可重用程式碼片段。

## 快速回答
- **什麼函式庫負責圖像提取？** GroupDocs.Watermark for Java  
- **我可以同時提取圖片與向量形狀嗎？** 是 – API 提供對圖像與形狀中繼資料的存取。  
- **需要哪個 Java 版本？** JDK 8 或更高。  
- **生產環境需要授權嗎？** 建議使用商業授權；免費試用版可用於評估。  
- **此流程對大型檔案是否具備記憶體效能？** 是，您可以即時釋放資源，並逐段處理。

## 什麼是「從 Word 提取圖像」？
從 Word 提取圖像是指以程式方式定位 `.docx` 檔案內的每張圖片、圖形或嵌入式圖形，並取得其二進位資料或中繼資料。這可支援後續的圖像分析、內容遷移或動態報告產生等工作。

## 為何在此任務中使用 GroupDocs.Watermark？
GroupDocs.Watermark 提供高階 API，抽象化 OpenXML 格式的複雜性。它讓您只需幾行程式碼即可 **在 Java 中載入 Word 文件**，同時揭露詳細的形狀資訊——非常適合需要圖像提取與形狀分析的開發者。

## 前置條件
- **Java Development Kit (JDK)** 8 或更新版本  
- **IDE** – IntelliJ IDEA、Eclipse，或任何相容 Java 的編輯器  
- 基本的 Java I/O 知識  
- 取得 GroupDocs.Watermark 授權（試用版可用於測試）

## 為 Java 設定 GroupDocs.Watermark
透過 Maven 或直接下載整合此函式庫。

### 使用 Maven
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
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 JAR。

### 取得授權
欲取得完整功能，請從 GroupDocs 入口網站取得授權金鑰。可申請臨時試用授權，以無限制探索所有功能。

## 實作指南
我們將實作分為兩個邏輯部分：

1. **如何在 Java 中載入 Word 文件**  
2. **如何提取形狀與圖像（即從 Word 提取圖像）**

### 載入 Word 文件
首先，設定載入選項並實例化 `Watermarker`。

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

> **小技巧：** 請將 `"YOUR_DOCUMENT_DIRECTORY/document.docx"` 替換為指向您欲處理檔案的絕對或相對路徑。

### 提取形狀與圖像資訊
文件載入後，您可以遍歷每個章節與每個形狀，提取向量形狀資料與嵌入圖像的詳細資訊。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

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

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
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

> **為什麼重要：** `shape.getImage()` 呼叫可直接取得每張圖片的二進位表示，讓您能將其儲存至磁碟、透過網路傳送，或輸入至圖像處理函式庫。

## 常見問題與解決方案
| 問題 | 解決方案 |
|------|----------|
| **FileNotFoundException** – 錯誤路徑 | 核對檔案路徑，並確保應用程式具有讀取權限。 |
| **OutOfMemoryError** 在大型文件上 | 每次處理單一章節，並在完成一批後立即呼叫 `watermarker.close()`。 |
| 形狀的 `getImage()` 回傳 `null` | 並非所有形狀都是圖像；有些是繪圖物件。存取圖像前請先檢查 `shape.getShapeType()`。 |
| 授權未套用 | 在建立 `Watermarker` 前加入 `License.setLicense("path/to/license/file.lic");`。 |

## 實務應用
- **自動化報告產生：** 從範本中提取圖表與標誌，以在儀表板中重用。  
- **內容稽核：** 掃描企業文件以找出禁止的圖形。  
- **遷移專案：** 在將內容搬移至新 CMS 前出嵌入的圖像。

## 效能考量
- 盡快釋放 `Watermarker` 實例（`watermarker.close()`）。  
- 對於大型檔案（>50 MB），建議串流處理章節，而非一次載入整個文件至記憶體。  
- 使用最新的 GroupDocs.Watermark 版本以獲得效能提升。

## 結論
您現在已掌握使用 GroupDocs.Watermark for Java 從 Word 文件 **提取圖像** 並取得形狀中繼資料的完整、可投入生產的方法。此功能可開啟強大的自動化情境，從產生動態報告到執行大規模文件稽核。

### 往後步驟
- 嘗試將提取的圖像儲存至磁碟（`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`）。  
- 探索其他 API，例如移除或新增浮水印。  
- 將此邏輯整合至您現有的文件管理工作流程。

## 常見問答
**Q: 什麼是 GroupDocs.Watermark for Java？**  
A: 它是一個全面的函式庫，旨在管理浮水印並提取各種文件格式的視覺元素，提升文件操作自動化任務。

**Q: 我可以從受密碼保護的 Word 文件中提取圖像嗎？**  
A: 可以。使用包含密碼的 `WordProcessingLoadOptions` 載入文件，然後使用相同的提取邏輯。

**Q: 此 API 也支援 .doc（二進位）檔案嗎？**  
A: 此函式庫主要針對 OpenXML `.docx` 格式，但在轉換後也能開啟舊版 `.doc` 檔案。

**Q: 如何將提取的圖像儲存至檔案系統？**  
A: 在 `shape.getImage()` 不為 null 的迴圈中，使用 `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());`。

**Q: 處理的形狀數量有上限嗎？**  
A: 沒有硬性上限，但記憶體使用會隨文件大小增長；對於非常大的檔案，請逐段處理。

**最後更新：** 2025-12-20  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs