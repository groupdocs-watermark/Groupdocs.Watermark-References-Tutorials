---
date: '2025-12-20'
description: 學習如何使用 GroupDocs.Watermark for Java 提取形狀資訊。高效地從圖表檔案中取得尺寸、位置及文字。
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 提取形狀資訊（Java）：使用 GroupDocs.Watermark 處理圖表
type: docs
url: /zh-hant/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在圖表中提取形狀資訊（Java）

當您需要從複雜的圖表檔案中**extract shape information java**時，手動操作很快就變得不切實際。本教學將示範如何利用 GroupDocs.Watermark for Java 以程式方式取得每個形狀的尺寸、位置、旋轉角度、嵌入圖像及文字等詳細資訊。完成後，您將擁有一套清晰、可重用的範本，可直接套用於任何使用 Visio 風格圖表的 Java 專案。

## 介紹

管理複雜的圖表通常需要取得其元件（如形狀和圖像）的詳細資訊。如果您曾需要使用 Java 程式化取得圖表形狀的尺寸、位置或文字等資料，本教學即為您而設。利用 GroupDocs.Watermark 函式庫的強大功能，可在 Java 應用程式中簡化此流程。在本指南中，我們將逐步說明如何使用 GroupDocs.Watermark 從圖表檔案中**extract shape information java**。

## 快速答覆
- **我應該使用哪個函式庫？** GroupDocs.Watermark for Java (v24.11+)。  
- **支援哪些檔案格式？** Visio (.vsdx, .vsd) 以及 API 文件中列出的其他圖表類型。  
- **需要授權嗎？** 免費試用版可用於開發；正式環境需購買商業授權。  
- **可以取得形狀的圖像資料嗎？** 可以——API 提供圖像寬度、高度以及原始位元組資料。  
- **需要 Maven 嗎？** Maven 是管理 GroupDocs.Watermark 相依性的推薦方式。

## 什麼是「extract shape information java」？

「extract shape information java」指的是使用 Java 程式碼程式化讀取圖表檔案，並擷取每個形狀的屬性——尺寸、位置、旋轉、文字以及任何嵌入的圖像。此功能可支援自動化分析、報告，或與 CAD 工具、資料視覺化管線等其他系統整合。

## 為何使用 GroupDocs.Watermark 來完成此任務？

GroupDocs.Watermark 為圖表格式提供高層抽象，為您處理底層解析。它讓您專注於業務邏輯，而不必面對 XML 或二進位規格，且在所有支援的圖表類型上皆能一致運作。

## 前置條件

- **GroupDocs.Watermark for Java**（版本 24.11 或更新）  
- Java Development Kit（JDK）8 或以上  
- Maven（相依性管理）  
- IDE（如 IntelliJ IDEA 或 Eclipse）  

## 設定 GroupDocs.Watermark for Java

在 Maven 的 `pom.xml` 中加入儲存庫與相依性：

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

或者，您也可以直接從 [GroupDocs.Watermark for Java 版本發布](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權步驟
- **免費試用：** 下載試用套件以測試函式庫。  
- **臨時授權：** 取得臨時金鑰以延長評估時間。  
- **購買：** 取得正式授權以供生產環境使用。

### 基本初始化

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## 實作指南

現在讓我們逐步說明如何從圖表文件中**extract shape information java**。

### 載入與取得內容

#### 概觀
我們首先載入圖表檔案，取得 `DiagramContent` 物件，藉此存取頁面與形狀。

#### 步驟

**載入圖表文件**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **為何：** 這會初始化 `Watermarker` 物件，讓您能存取文件內容。

**取得圖表內容**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **為何：** `DiagramContent` 類別提供方法，可與圖表的不同層面（如頁面與形狀）互動。

### 迭代形狀

#### 概觀
取得 `DiagramContent` 後，我們會遍歷每個頁面，再遍歷每個形狀，以擷取所需的屬性。

#### 步驟

**遍歷頁面**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **為何：** 圖表由多個頁面組成，我們需要檢查每個頁面的形狀。

**擷取形狀資訊**

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

- **為何：** 此迴圈會擷取並列印每個形狀的屬性，包括尺寸、位置、旋轉角度以及任何嵌入的圖像或文字。這些屬性對於了解圖表中形狀的配置至關重要。

### 疑難排解技巧
- 確認檔案路徑正確且指向可讀取的 `.vsdx`（或支援）檔案。  
- 確保應用程式對圖表檔案具有讀取權限。  
- 若遇到「不支援的格式」錯誤，請確認您使用的 GroupDocs.Watermark 版本支援該圖表類型。

## 實務應用

具備**extract shape information java**的能力後，您可以支援各種實務情境：

1. **圖表分析：** 自動產生列出每個形狀尺寸、位置與文字的報告——對品質保證稽核很有幫助。  
2. **資料視覺化：** 將形狀指標輸入儀表板，以視覺化版面密度或辨識過大元件。  
3. **CAD 整合：** 將圖表資料串接至 CAD 流程，實現自動化重新設計或驗證步驟。

## 效能考量

處理大型圖表時，請留意以下最佳實踐：

- **及時關閉資源：** 呼叫 `watermarker.close()`（或使用 try‑with‑resources）釋放記憶體。  
- **監控堆積使用量：** 大型圖表可能佔用大量記憶體，必要時調整 JVM 堆積大小（`-Xmx`）。  
- **批次處理：** 將檔案分批處理，而非一次載入多個。

## 結論

透過本指南，您現在已了解如何使用 GroupDocs.Watermark for Java **extract shape information java**。您可以從任何支援的圖表檔案中取得尺寸、位置、旋轉角度、嵌入圖像與文字，為自動化分析、報告以及與大型系統的整合開啟大門。準備好進一步探索了嗎？請前往官方[文件](https://docs.groupdocs.com/watermark/java/)了解函式庫的完整功能，並嘗試水印、遮蔽或自訂形狀操作。

## 常見問題

**Q: 什麼是 GroupDocs.Watermark？**  
A: 一套完整的 Java 函式庫，專為在各種文件格式（包括圖表）上加水印與擷取資訊而設計。

**Q: 我可以使用此函式庫處理所有類型的圖表檔案嗎？**  
A: 可以，但請確認檔案格式已列於[API 參考文件](https://reference.groupdocs.com/watermark/java/)中為支援格式。

**Q: 如何使用 Java 與 GroupDocs.Watermark 從圖表中擷取形狀的尺寸與位置？**  
A: 載入圖表，取得 `DiagramContent`，然後遍歷每個 `DiagramShape`，讀取寬度、高度、X、Y 等屬性。

**Q: GroupDocs.Watermark 能否使用 Java 擷取圖表形狀中嵌入的圖像？**  
A: 能，它提供存取形狀內圖像資料的方法，包括尺寸與原始位元組陣列，您可用於分析或修改。

**Q: 在 Java 中擷取圖表形狀資訊的前置條件是什麼？**  
A: Java JDK 8 以上、Maven 設定、GroupDocs.Watermark 函式庫（24.11 以上），以及基本的 Java 程式開發知識。

---

**最後更新：** 2025-12-20  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs