---
date: '2026-10-27'
description: 了解如何使用 GroupDocs.Watermark for Java 從 diagram files 刪除 text watermark，並高效偵測
  image watermark。開發人員的逐步指南。
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: 使用 GroupDocs.Watermark for Java 從 diagram files 刪除 text watermark。了解如何偵測
  image watermark、搜尋及使用 code snippets 移除 watermarks。
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: 快速使用 Java 刪除 diagram files 中的 text watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: 如何使用 Java 刪除圖表中的 text watermark
type: docs
url: /zh-hant/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# 如何在 Java 中刪除圖表的文字浮水印

管理文件中的浮水印對於保護智慧財產權與維持文件完整性至關重要。在本教學中，您將學會如何使用 GroupDocs.Watermark for Java 從 `.vsdx` 等圖表檔案中 **刪除文字浮水印**，以及在需要時 **偵測圖片浮水印**。無論是建置企業級文件管線或是自動化簡易批次工作，這些技巧都能讓您對圖表浮水印進行精細控制。

**您將學到的內容**
- 設定 GroupDocs.Watermark 函式庫
- 使用特定選項載入圖表文件
- 搜尋並刪除文字浮水印
- 偵測圖片浮水印並將其移除
- 大規模處理的最佳實踐技巧

準備好深入了解了嗎？先把環境建好吧。

## 快速解答
- **我可以一次刪除文字與圖片浮水印嗎？** 可以 – 只要將 `TextSearchCriteria` 與 `ImageDctHashSearchCriteria` 以 `or()` 條件結合即可。  
- **函式庫會將整個圖表載入記憶體嗎？** 不會 – 它會串流頁面，支援最高 500 MB 的檔案而不會一次佔用全部記憶體。  
- **支援哪些圖表格式？** 超過 20 種格式，包括 `.vsdx`、`.vdx`、`.drawio`。  
- **正式環境需要授權嗎？** 非試用使用時必須擁有有效的 GroupDocs.Watermark 授權。  
- **可以在 CI/CD 管線中執行嗎？** 完全可以 – API 為無頭模式，支援 Windows、Linux 與 macOS。

## 什麼是刪除文字浮水印？
刪除文字浮水印指的是移除文件中以文字形式呈現的覆蓋物，這類浮水印通常用於標示所有權、機密性或草稿狀態。於 GroupDocs.Watermark 中，此操作透過搜尋條件定位浮水印物件，然後對取得的集合呼叫 `clear()` 來完成。

## 為什麼要偵測圖片浮水印？
偵測圖片浮水印可讓您找出嵌入圖表中的商標或印章圖形。這對於合規檢查、品牌保護與自動化內容審核相當重要。GroupDocs.Watermark 採用感知雜湊（DCT）快速且精確地比對圖像。

## 前置條件
在開始之前，請確認您已具備以下項目：
1. **Java Development Kit (JDK)** 8 或更新版本。  
2. **IDE** – IntelliJ IDEA、Eclipse，或您慣用的任何編輯器。  
3. **GroupDocs.Watermark for Java** – 必須將函式庫 JAR 加入 classpath。  

### 必要的函式庫與相依性
您可以透過 Maven 加入函式庫，或手動下載 JAR。

#### Maven 設定
在 `pom.xml` 檔案中加入以下設定：

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

#### 直接下載
或是從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 授權取得
- **免費試用** – 無需授權金鑰即可測試全部功能。  
- **臨時授權** – 申請限時金鑰以供評估使用。  
- **購買授權** – 取得永久或訂閱授權以供正式環境使用。

## 設定 GroupDocs.Watermark for Java
1. **安裝函式庫** – 確認 Maven 套件庫與相依性已正確設定，或將 JAR 放置於 `libs/` 並加入專案建置路徑。  
2. **初始化 API** – 建立 `Watermarker` 實例；此物件是載入圖表與執行浮水印操作的入口。

## 如何在 Java 中刪除圖表的文字浮水印
要刪除文字浮水印，先以 `Watermarker` 載入圖表，建立匹配浮水印文字的 `TextSearchCriteria`，取得 `PossibleWatermarkCollection`，然後對其呼叫 `clear()`。此動作只會移除指定的文字覆蓋層，其他圖表內容保持不變。

`Watermarker` 類別代表記憶體中的單一文件，提供載入、搜尋與修改浮水印的方法。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```
- **參數：**  
  - `inputFilePath`：您的 `.vsdx` 檔案路徑。  
  - `loadOptions`：設定文件載入方式（例如頁面範圍、密碼）。

## 如何在圖表檔案中偵測圖片浮水印？
偵測圖片浮水印的流程是先以參考圖建立 `ImageDctHashSearchCriteria`，再使用 `Watermarker` 搜尋圖表。API 會為每個嵌入的圖像產生感知雜湊，並與參考圖比較，回傳相似度分數，讓您辨識並移除不需要的商標或印章。

`ImageDctHashSearchCriteria` 會產生參考圖的雜湊，並與圖表中嵌入的圖像進行比對，回傳相似度分數。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```
- **關鍵方法：**  
  - `TextSearchCriteria` – 建立文字浮水印的搜尋條件。  
  - `PossibleWatermarkCollection` – 保存任何搜尋操作的結果集合。

## 如何在找到浮水印後將其移除？
一旦定位到浮水印，只需對搜尋返回的 `PossibleWatermarkCollection` 呼叫 `clear()` 即可。此操作會刪除浮水印物件，同時保留圖表的其他元素，確保原始內容完整不變。

`clear()` 會移除集合中的所有浮水印，同時保留圖表其餘內容。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```
- **關鍵方法：** `clear()` – 在不改變其他圖表元素的前提下，刪除提供集合中的全部浮水印。

## 實務應用
1. **企業軟體整合** – 將浮水印管理嵌入以文件為中心的業務應用，保護專有圖表。  
2. **內容管理系統 (CMS)** – 在發佈使用者產生的圖表前，自動偵測未授權的商標。  
3. **法律文件處理** – 在案件流程的不同階段加入或刪除浮水印，確保符合機密政策。

## 常見問題與除錯
- **大型檔案** – 若遇到 `OutOfMemoryError`，請在 `LoadOptions` 中提升 `maxMemory` 設定。  
- **受密碼保護的圖表** – 在 `LoadOptions` 中提供密碼即可開啟檔案。  
- **找不到圖片雜湊匹配** – 確認參考圖的解析度足夠；低解析度圖像可能產生弱雜湊。

## 常見問答

**Q: 我可以同時搜尋文字與圖片嗎？**  
A: 可以 – 只要將 `TextSearchCriteria` 與 `ImageDctHashSearchCriteria` 以 `or()` 運算子結合，即可在一次搜尋中定位兩種浮水印。

**Q: 能否在不損壞圖表的前提下刪除浮水印？**  
A: 完全可以。API 會隔離浮水印物件並將其移除，保留原始圖表結構不變。

**Q: GroupDocs.Watermark 支援多種圖表格式嗎？**  
A: 支援超過 20 種格式，包括 `.vsdx`、`.vdx`、`.drawio`、`.svg`，可廣泛管理各類圖表。

**Q: 如何有效處理大量文件？**  
A: 使用批次處理迴圈，盡可能重複利用單一 `Watermarker` 實例，並調整 `LoadOptions` 以串流頁面而非一次載入整個檔案。

**Q: 能將浮水印偵測整合到 CI/CD 管線嗎？**  
A: 能 – 函式庫為無頭模式，可從 Maven、Gradle 或任何建置腳本呼叫，自動驗證圖表資產。

---

**最後更新：** 2026-10-27  
**測試環境：** GroupDocs.Watermark 23.6 for Java  
**作者：** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## 相關教學

- [How to Add Text Watermarks to Diagrams Using GroupDocs.Watermark in Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [Guide to Adding Watermarks to Diagrams Using GroupDocs.Watermark for Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [How to Retrieve Document Information Using GroupDocs.Watermark for Java: A Step-by-Step Guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)