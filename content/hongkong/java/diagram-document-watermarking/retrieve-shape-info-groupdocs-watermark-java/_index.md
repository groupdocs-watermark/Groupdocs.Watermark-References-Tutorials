---
date: '2026-02-13'
description: 學習如何使用 GroupDocs.Watermark for Java 提取形狀及從形狀中提取圖像，並高效取得詳細的圖表資訊。
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 如何於 Java 中使用 GroupDocs.Watermark 從圖表提取形狀
type: docs
url: /zh-hant/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中從圖表提取形狀

當你需要以程式方式從類似 Visio 的圖表 **提取形狀** 時，GroupDocs.Watermark 函式庫提供了一個乾淨、以 Java 為先的方式，取得所有細節——尺寸、位置、嵌入的影像，甚至每個形狀內的文字。在本教學中，你將看到確切的 **提取形狀** 方法、其重要性，以及可直接複製到專案中的逐步程式碼。

## 快速解答
- **哪個函式庫負責形狀提取？** GroupDocs.Watermark for Java  
- **需要哪個 Java 版本？** JDK 8 或更高  
- **可以從形狀取得影像資料嗎？** 可以 – 使用 `shape.getImage()`  
- **可以取得形狀內的文字嗎？** 當然可以，透過 `shape.getText()`  
- **生產環境需要授權嗎？** 需要有效的 GroupDocs.Watermark 授權  

## 介紹

管理複雜的圖表通常需要存取其元件的詳細資訊，例如形狀與影像。如果你曾需要以 Java 程式方式取得圖表形狀的尺寸、位置或文字等資料，本教學正適合你。利用 GroupDocs.Watermark 函式庫的強大功能，可在 Java 應用程式中簡化此流程。在本指南中，我們將逐步說明如何 **提取形狀**，同時示範如何 **從形狀提取影像** 以及 **從形狀提取文字**。

## 「提取形狀」是什麼？

提取形狀是指讀取圖表內部的物件（頁面、形狀、影像、文字），讓你能夠分析、轉換或在其他應用程式中重複使用——非常適合自動化、報告或與 CAD 工具整合。

## 為何使用 GroupDocs.Watermark 進行形狀提取？

- **完整格式支援** – 支援 VSDX、VDX 以及許多其他圖表類型。  
- **豐富的物件模型** – 直接存取形狀幾何、影像與文字。  
- **無外部相依性** – 純 Java，易於嵌入 Maven 專案。  

## 前置條件

- **GroupDocs.Watermark for Java**（版本 24.11 或更新）  
- Java Development Kit (JDK) 8 或更高  
- Maven（用於相依性管理）  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE  

## 設定 GroupDocs.Watermark for Java

將函式庫加入你的 Maven `pom.xml`：

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

你也可以從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的二進位檔。

### 取得授權步驟
- **免費試用：** 下載試用套件以評估 API。  
- **臨時授權：** 申請臨時金鑰以進行延長測試。  
- **購買：** 取得正式授權以供生產環境使用。  

### 基本初始化與設定

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## 如何提取形狀 – 實作指南

### 載入並取得內容

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### 迭代形狀

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

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

### 如何從形狀提取影像

`shape.getImage()` 呼叫會回傳一個包含原始位圖、其尺寸以及位元組陣列的物件。使用上述屬性可將影像儲存至磁碟，或輸入至其他處理管線。

### 如何從形狀提取文字

`shape.getText()` 方法會回傳形狀內的純文字。若形狀未包含文字，該方法會回傳 `null`。範例迴圈已經會印出文字，你亦可進一步操作，例如建立所有形狀標籤的索引。

## 疑難排解技巧
- 核對檔案路徑與讀取權限。  
- 確認使用受支援的圖表格式（VSDX、VDX 等）。  
- 若形狀缺少預期資料，請檢查函式庫的發行說明，以了解格式特定的差異。  

## 實務應用

1. **圖表分析：** 透過檢查形狀尺寸或缺失標籤，自動稽核圖表是否符合規範。  
2. **資料視覺化：** 將提取的尺寸輸入報表儀表板，以視覺化版面密度。  
3. **CAD 整合：** 結合形狀資料與 CAD API，以同步各工具間的設計規格。  

## 效能考量

- **關閉資源：** 完成後呼叫 `watermarker.close()` 以釋放原生資源。  
- **記憶體管理：** 大型圖表可能佔用大量堆積記憶體；請監控記憶體使用，必要時增加 `-Xmx`。  
- **批次處理：** 以批次方式處理檔案，並盡可能重複使用單一 `Watermarker` 實例。  

## 結論

透過本指南，你現在已了解如何使用 GroupDocs.Watermark for Java **提取形狀**、**從形狀提取影像**，以及 **從形狀提取文字**。這些技巧為自動化圖表分析、報告與與其他工程系統的整合開啟大門。下一步，請透過查看其 [documentation](https://docs.groupdocs.com/watermark/java/) 來探索完整 API，並嘗試將形狀提取與自訂業務邏輯結合。

## 常見問答

1. **什麼是 GroupDocs.Watermark？**  
   - 一個全面的 Java 函式庫，設計用於為各種文件格式（包括圖表）加上浮水印與提取資訊。  

2. **我可以使用此函式庫處理所有類型的圖表檔案嗎？**  
   - 可以，但請透過檢查 [API Reference](https://reference.groupdocs.com/watermark/java/) 以確認檔案格式受支援。  

3. **如何使用 Java 與 GroupDocs.Watermark 從圖表提取形狀的尺寸與位置？**  
   - 載入圖表，存取 `DiagramContent`，然後迭代形狀以取得寬度、高度、X 與 Y 等屬性。  

4. **GroupDocs.Watermark 能以 Java 提取圖表形狀中嵌入的影像嗎？**  
   - 可以，它提供存取形狀內影像資料的方法，包括尺寸與像素資料，適用於分析或修改。  

5. **在 Java 中提取圖表形狀資訊的前置條件是什麼？**  
   - 必須具備 Java JDK 8+、Maven 設定、GroupDocs.Watermark 函式庫（24.11+）以及基本的 Java 知識。  

---

**最後更新：** 2026-02-13  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs