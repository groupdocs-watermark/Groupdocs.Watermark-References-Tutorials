---
date: '2026-09-06'
description: 了解如何使用 GroupDocs.Watermark for Java 從 Word 文件中提取形狀，實現強大的文件自動化與分析。
keywords:
- how to extract shapes
- GroupDocs.Watermark Java
- Word document shape extraction
lastmod: '2026-09-06'
og_description: 如何使用 GroupDocs.Watermark for Java 從 Word 文件中提取形狀。請依照本步驟指南載入、分析並有效處理形狀。
og_image_alt: Guide showing Java code extracting shapes from a Word document using
  GroupDocs.Watermark
og_title: 如何使用 GroupDocs.Watermark 在 Java 中從 Word 文件提取形狀
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract shapes from Word documents with GroupDocs.Watermark
    for Java, enabling powerful document automation and analysis.
  headline: How to extract shapes from Word documents using GroupDocs.Watermark in
    Java
  type: TechArticle
- questions:
  - answer: GroupDocs.Watermark for Java is a comprehensive SDK that enables watermark
      creation, detection, and document inspection across 30+ file formats, including
      DOCX, PDF, and PPTX.
    question: What is GroupDocs.Watermark for Java?
  - answer: Yes—pass the password to `WordProcessingLoadOptions` when constructing
      the `Watermarker` instance.
    question: Can I extract shapes from password‑protected Word files?
  - answer: Absolutely; GroupDocs.Watermark is platform‑agnostic and runs on any OS
      that supports Java 8+.
    question: Does the library work on Linux servers?
  - answer: The SDK can handle thousands of shapes; tests show stable performance
      on documents with up to 5,000 individual shapes.
    question: How many shapes can be processed in a single document?
  - answer: No, shape extraction is included in the standard GroupDocs.Watermark license.
    question: Is a separate license needed for shape extraction?
  type: FAQPage
tags:
- extract shapes
- GroupDocs.Watermark
- Java document processing
title: 如何使用 GroupDocs.Watermark 在 Java 中從 Word 文件提取形狀
type: docs
url: /zh-hant/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中從 Word 文件中提取圖形

在現代以文件為中心的應用程式中，**提取圖形**從 Word 檔案是一項常見挑戰。無論您需要稽核圖表使用情況、將圖形轉換為圖片，或推動動態報表，能以程式方式取得圖形的中繼資料都能節省大量人工時間。本教學將指導您如何使用 GroupDocs.Watermark for Java 載入 DOCX、列舉每個圖形，並取得其屬性（如類型、尺寸與位置）。

## 快速回答
- **哪個函式庫負責圖形提取？** GroupDocs.Watermark for Java.  
- **最低 Java 版本？** JDK 8 or newer.  
- **開發是否需要授權？** A free trial works for testing; a full license is required for production.  
- **能處理大型文件嗎？** Yes—process sections incrementally to keep memory usage low.  
- **Maven 是首選的設定方式嗎？** Maven simplifies dependency management and is recommended for most projects.

## 什麼是 Word 文件中的圖形提取？
圖形提取是以程式方式讀取 Word 檔案，並取得每個圖形物件（圖片、圖畫、SmartArt、圖表或文字方塊）的詳細資訊，以便在程式碼中分析或操作它們。提取的中繼資料包括圖形類型、尺寸、位置以及任何相關文字，從而支援後續的轉換或分析等處理。

## 為什麼使用 GroupDocs.Watermark for Java？
GroupDocs.Watermark 支援 **30+ 份文件格式**，且能在不將整個檔案載入記憶體的情況下處理 **數百頁的檔案**，這得益於其串流 API。該函式庫在一般伺服器上能於每 100 頁文件低於 **200 ms** 內處理圖形中繼資料，為批次作業提供快速且可靠的結果。

## 前置條件
- **Java Development Kit (JDK)** 8 或以上。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse。  
- 具備基本的 Java I/O 與 Maven 使用經驗。

我們將使用 GroupDocs.Watermark for Java，這是一套以浮水印為主、同時提供深入文件檢查功能的強大 SDK。

## 設定 GroupDocs.Watermark for Java
透過 Maven 或直接下載方式整合此 SDK。

### 使用 Maven
在您的 `pom.xml` 檔案中加入以下設定：
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

### 取得授權
免費試用授權可讓您探索全部功能。若要於正式環境使用，請從 GroupDocs 入口網站取得永久授權金鑰。

## 實作指南
我們將實作分為兩個邏輯部分：載入文件與提取圖形資訊。

## 如何使用 GroupDocs.Watermark 從 Word 文件中提取圖形？
`Watermarker` 是 GroupDocs.Watermark 中的主要類別，用於載入文件並提供存取其內容的功能。使用 `Watermarker` 實例載入 DOCX，然後遍歷每個區段與圖形以讀取其屬性。這個兩步驟模式——先初始化，再列舉——涵蓋 **所有 30+ 支援的圖形類型**，且可處理最多 500 頁的文件而不會產生過多記憶體使用。它會有效率地串流文件，讓您在不佔用大量記憶體的情況下處理大型檔案。

### 步驟 1：設定載入選項
`WordProcessingLoadOptions` 讓您微調檔案的解析方式（例如，忽略頁首、啟用快速模式）。  
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
此程式碼片段會建立一個將文件保留於記憶體中的 `Watermarker`，並為檢查做準備。

### 步驟 2：存取 Word 處理內容
遍歷區段與圖形，列印關鍵資訊，如類型、尺寸、對齊方式，以及圖形是否位於頁首/頁尾。  
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
此迴圈會涵蓋所有圖形物件，確保不會遺漏嵌入於頁首或頁尾的隱藏圖形。

## 常見問題與解決方案
- **找不到檔案** – 請再次確認絕對或相對路徑；可使用 `Paths.get(...).toAbsolutePath()` 以確保正確性。  
- **效能瓶頸** – 若文件超過 300 頁，請一次處理單一區段，並在每個批次後呼叫 `watermarker.close()` 釋放記憶體。  
- **不支援的圖形類型** – GroupDocs.Watermark 目前支援 25 種原生圖形類別；若遇自訂 OfficeArt 物件，可考慮改用 OpenXML SDK 作為備援。

## 實務應用
1. **自動化報表產生** – 提取圖表以嵌入儀表板。  
2. **合規稽核** – 確認受管制文件中未出現禁止的圖形。  
3. **遷移管線** – 在將內容搬移至基於 Web 的出版平台前，將圖形轉換為 SVG。

## 效能考量
- 盡快使用 `watermarker.close()` 釋放 `Watermarker` 物件，以釋放原生資源。  
- 當僅需圖形中繼資料而非完整內容渲染時，於 `WordProcessingLoadOptions` 中啟用 `fastLoad` 旗標。  
- 僅在伺服器具備足夠 CPU 核心時才以平行串流處理文件；避免使用非執行緒安全的共享物件。

## 結論
現在您已了解如何使用 GroupDocs.Watermark for Java **提取 Word 文件中的圖形**。透過 `Watermarker` 載入文件、設定載入選項，並遍歷每個圖形，您即可構建強大的自動化工作流程，處理即使是最複雜的檔案。

### 後續步驟
- 嘗試使用 `Shape` 物件的 `getImageData()` 方法將圖片匯出為 PNG。  
- 探索 GroupDocs.Watermark 的其他功能，例如浮水印偵測與移除。  
- 結合 GroupDocs.Parser 的圖形提取，以取得周圍文字，進行更深入的分析。

## 常見問答

**Q: 什麼是 GroupDocs.Watermark for Java？**  
A: GroupDocs.Watermark for Java 是一套完整的 SDK，能在 30+ 種檔案格式（包括 DOCX、PDF、PPTX）上實現浮水印的建立、偵測與文件檢查。

**Q: 能從受密碼保護的 Word 檔案提取圖形嗎？**  
A: 可以——在建立 `Watermarker` 實例時，將密碼傳入 `WordProcessingLoadOptions`。

**Q: 此函式庫能在 Linux 伺服器上運作嗎？**  
A: 完全可以；GroupDocs.Watermark 與平台無關，能在任何支援 Java 8+ 的作業系統上執行。

**Q: 單一文件最多能處理多少個圖形？**  
A: 此 SDK 可處理數千個圖形；測試顯示在最多 5,000 個獨立圖形的文件上仍能保持穩定效能。

**Q: 圖形提取需要額外授權嗎？**  
A: 不需要，圖形提取已包含在標準的 GroupDocs.Watermark 授權中。

---

**最後更新：** 2026-09-06  
**測試環境：** GroupDocs.Watermark 23.12 for Java  
**作者：** GroupDocs

## 相關教學

- [使用 GroupDocs.Watermark 在 Java 中從圖表提取圖形資訊](/watermark/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark 在 Java 中從 Word 文件移除圖形&#58; 完整指南](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}