---
date: '2026-08-25'
description: 了解如何使用 GroupDocs.Watermark for Java 編輯圖表檔案並移除超連結。快速保護您的圖表，提供逐步指引。
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: 了解如何使用 GroupDocs.Watermark for Java 編輯圖表檔案並移除超連結。遵循清晰步驟保護您的文件。
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: 如何使用 Java 編輯圖表並移除超連結
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: 如何使用 Java 編輯圖表並移除超連結
type: docs
url: /zh-hant/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 Java 編輯圖表並移除超連結  

管理數位文件時常需要編輯圖表，特別是當您需要 **edit diagram** 檔案以去除超連結以提升安全性或視覺清晰度時。本教學將向您展示如何使用功能強大的 **GroupDocs.Watermark** Java 函式庫編輯圖表檔案並移除圖表形狀中不需要的超連結。完成本指南後，您將擁有一個乾淨、無超連結的圖表，可供發佈使用。  

## 快速回答  
- **What is the main goal?** 移除圖表形狀中的所有超連結，以提升安全性與呈現效果。  
- **Which library is required?** GroupDocs.Watermark for Java，版本 24.11 或更新。  
- **Do I need a license?** 免費試用可用於測試；正式環境需購買商業授權。  
- **Can I process many files at once?** 可以——相同程式碼可放入迴圈以批次處理。  
- **What Java version is supported?** Java 8 或以上（建議使用 Java 11）。  

## 「how to edit diagram」是什麼？  
**How to edit diagram** 指的是以程式方式開啟圖表檔案、修改其內部元素（例如形狀、文字或超連結），並儲存結果的過程。使用 GroupDocs.Watermark，您可以在不需要原始編輯工具的情況下編輯圖表檔案。  

## 為何使用 GroupDocs.Watermark for Java？  
GroupDocs.Watermark 支援 **30+ 圖表與影像格式**（包括 VSDX、SVG 與 WMF），且可處理高達 **500 MB** 的檔案而無需將整個文件載入記憶體，提供比多數競爭對手快 **20 %** 的處理速度。  

## 前置條件  
- **GroupDocs.Watermark** 函式庫版本 24.11 或更新。  
- 已安裝 Maven（或若偏好手動設定則使用 JAR 檔案）。  
- Java Development Kit 8 或更新，並搭配如 IntelliJ IDEA 或 Eclipse 等 IDE。  

### 必要的函式庫、版本與相依性  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+（若使用 Maven 方式）  

### 環境設定需求  
確保 JDK 的 `bin` 目錄已加入 `PATH`，且您的 IDE 指向正確的 JDK 版本。  

### 知識前置條件  
您應熟悉基本的 Java 語法、Maven 相依性管理，以及檔案 I/O 操作。  

## 如何設定 GroupDocs.Watermark for Java？  
`Watermarker` 類別提供載入與修改文件的 API 入口。  
要開始使用 GroupDocs.Watermark，請將其 Maven 坐標加入專案的 `pom.xml`。此舉會下載函式庫及其相依性，讓您能實例化 Watermarker 類別，直接在 Java 程式碼中處理圖表檔案。之後即可設定授權並在處理文件前設定輸出選項。  

將 GroupDocs.Watermark 的相依性加入您的 `pom.xml`。  

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

如果不想使用 Maven，請從官方發行頁面下載最新的 JAR 檔案。  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### 取得授權步驟  
- 先使用免費試用版評估 API。  
- 正式環境請從供應商入口網站取得臨時或永久授權。  

#### 基本初始化與設定  
`Watermarker` 類別是所有文件處理操作的入口點。  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## 如何使用 GroupDocs.Watermark 編輯圖表並移除超連結？  
`Watermarker` 類別提供載入與修改文件的 API 入口點。  
首先，將圖表檔案載入 Watermarker 實例。接著取得形狀集合，找出包含超連結物件的形狀，並以逆向順序遍歷，以安全地刪除每個連結而不影響集合索引。此作法確保移除所有嵌入的 URL，同時保留圖表的視覺完整性。  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Why this step matters**: 載入檔案可讓您以程式方式存取每個形狀及其相關屬性。  

## 如何在圖表中存取形狀內容？  
`DiagramShape` 物件代表圖表中的單一形狀，提供其屬性與附加的中繼資料。  
載入圖表後，於 Watermarker 呼叫 `getShapes()` 以取得 `DiagramShape` 物件的清單。每個形狀皆可檢查其超連結集合，從而精確定位要移除或修改的連結。若需進一步調整，亦可讀取形狀的文字、顏色與幾何資訊。  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Why this step matters**: 精準鎖定形狀可確保只移除不需要的連結，而不影響其他視覺元素。  

## 如何安全地遍歷並移除超連結？  
`removeHyperlink(int index)` 方法會刪除形狀超連結集合中指定位置的超連結。  
從最後一個索引向零遞減遍歷超連結清單。此逆向迴圈可避免刪除項目時產生的索引移位，確保每個超連結皆被處理且不會被跳過。移除後，您可以刷新形狀狀態或繼續處理圖表中的下一個形狀。  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Why this step matters**: 逆向迴圈可保證所有超連結皆被移除，且不會遺漏任何項目。  

## 如何儲存編輯後的圖表並釋放資源？  
`save(String path)` 方法會將修改後的文件寫入指定的檔案位置，完成所有變更。  
所有超連結移除後，於 Watermarker 實例呼叫 `save` 方法，提供新檔名以避免覆寫原始檔案。接著呼叫 `close()` 釋放檔案句柄並釋放記憶體，這對長時間執行的批次處理至關重要。此步驟確保檔案正確關閉，並可供後續使用。  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Why this step matters**: 正確關閉資源可避免記憶體洩漏與伺服器上的檔案鎖定問題。  

## 實務應用  
從圖表形狀中移除超連結在多種實務情境中皆有益處：  

1. **Security** – 防止可能導向惡意網站的外部連結。  
2. **Compliance** – 符合禁止在共享資產中嵌入 URL 的公司政策。  
3. **Clarity** – 產生更乾淨的簡報，避免連結分散注意力。  

您可以將此邏輯嵌入更大的自動化流程，例如每晚的批次作業，於圖表發佈至內部網路前先進行清理。  

## 效能考量  

### 優化效能  
- 每個檔案使用單一 `Watermarker` 實例以降低開銷。  
- 偏好使用逆向迭代（如示範）以避免昂貴的清單重新索引。  

### 資源使用指導原則  
- 圖表若大於 200 MB，請監控堆積使用情況，並考慮提升 JVM `-Xmx` 參數。  
- 如 VisualVM 等效能分析工具可協助找出大規模批次執行的瓶頸。  

### Java 記憶體管理最佳實踐  
- 在最小可能的範圍內宣告物件。  
- 使用 try‑with‑resources 處理串流，以確保自動關閉。  

## 常見問題  

**Q: How do I handle diagrams that contain thousands of shapes?**  
A: 逐頁處理圖表，並在移至下一頁前釋放該頁的資源，以降低記憶體使用量。  

**Q: Can I limit hyperlink removal to specific pages only?**  
A: 可以——取得目標頁面的索引，然後僅對該頁的形狀執行移除迴圈。  

**Q: Is a commercial license mandatory for batch processing?**  
A: 任何正式環境的部署皆需有效授權；免費試用僅限 30 天與 5 份文件。  

**Q: Does GroupDocs.Watermark support SVG diagrams?**  
A: 當然支援——SVG 為 30+ 支援格式之一，且可使用相同的 API 呼叫移除超連結。  

**Q: What if a shape has multiple hyperlinks?**  
A: 逆向迭代迴圈會逐一移除每個超連結項目，確保所有連結皆被清除。  

## 資源  

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)  

---  

**最後更新:** 2026-08-25  
**測試環境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs  

## 相關教學

- [Diagram Watermarking Tutorials for GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Edit Diagram Headers & Footers in Java Using GroupDocs.Watermark: A Comprehensive Guide](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)
- [Efficiently Remove Shapes from Diagrams Using GroupDocs.Watermark for Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)