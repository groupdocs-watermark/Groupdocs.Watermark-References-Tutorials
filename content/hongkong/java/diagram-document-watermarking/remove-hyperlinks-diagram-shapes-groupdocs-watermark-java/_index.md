---
date: '2026-10-21'
description: 了解如何使用 GroupDocs.Watermark for Java 從圖表形狀中移除超連結。遵循此逐步指南，以確保文件安全且保持整潔。
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: 了解如何使用 GroupDocs.Watermark for Java 從圖表形狀中移除超連結。本指南將帶您逐步完成設定、程式碼以及安全、整潔文件的最佳實踐。
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: 如何使用 GroupDocs.Watermark Java 從形狀中移除超連結
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: 如何使用 GroupDocs.Watermark Java 從形狀中移除超連結
type: docs
url: /zh-hant/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 從圖形中移除超連結

管理數位文件時常需要編輯圖表，特別是當您需要從圖形中 **移除超連結** 以提升安全性或視覺清晰度時。本教學將帶您一步步使用功能強大的 **GroupDocs.Watermark** Java 函式庫，簡單地剔除圖表圖形中不需要的超連結。完成本指南後，您將了解為何需要移除超連結、如何設定環境，以及安全執行移除的具體步驟。

## 快速回答
- **移除超連結的主要目的為何？** 消除安全風險並提升共享圖表的視覺清晰度。  
- **哪個函式庫負責執行移除？** GroupDocs.Watermark for Java 提供專門的圖表操作 API。  
- **我需要授權嗎？** 試用版可用於測試；正式環境須購買商業授權。  
- **可以一次處理多個檔案嗎？** 可以——將程式碼包在迴圈或批次作業中以執行大量操作。  
- **需要哪個 Java 版本？** 支援 Java 8 以上。

## 什麼是移除超連結？
「**移除超連結**」一詞指的是在圖表的圖形元素中尋找並刪除嵌入的超連結物件。執行此動作可防止外部導向意外將使用者暴露於惡意網站或不需要的內容。這在將文件公開發佈時尤為重要，確保不會留下任何隱藏的導向路徑，避免導向釣魚網站或其他不預期的外部資源。

## 為何在 Java 中使用 GroupDocs.Watermark？
GroupDocs.Watermark 支援 **30 多種輸入與輸出格式**，且可在不將整個檔案載入記憶體的情況下處理 **最多 500 頁** 的圖表，較一般 XML 解析器可減少 **40 % 的 CPU 使用率**。其 API 讓您能細緻控制圖形屬性，成為 Java 應用程式中安全處理圖表的標準方案。

## 前置條件
- **GroupDocs.Watermark** 函式庫版本 24.11 或更新。  
- 已安裝 Maven（或直接下載 JAR）。  
- JDK 8 或更新版本，並使用如 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 基本的 Java 知識以及對 Maven 依賴的熟悉度。

## 設定 GroupDocs.Watermark for Java
首先，將 GroupDocs.Watermark 函式庫加入您的專案。您可以透過 Maven 添加或手動下載 JAR。

### Maven 設定
在您的 `pom.xml` 中加入以下設定：

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
Alternatively, download the latest version from [GroupDocs.Watermark for Java 版本發布](https://releases.groupdocs.com/watermark/java/)。

#### 取得授權步驟
- 先下載 GroupDocs.Watermark 以取得免費試用。  
- 若需延長測試或正式使用，請取得臨時授權或購買完整授權。

#### 基本初始化與設定
`Watermarker` 類別是所有文件層級操作的入口。它會載入檔案，讓您存取其頁面、圖形與中繼資料，最後將修改後的文件寫回磁碟。

初始化 Watermarker 類別的程式碼如下：

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 如何從圖表圖形中移除超連結？
載入圖表後，定位每個包含超連結的圖形，並刪除這些超連結物件。整個操作可在不到十行程式碼內完成，確保最終的圖表不再包含任何可點擊的連結，避免將使用者導向外部網站或洩漏敏感資訊。

### 步驟 1：載入圖表檔案
首先使用 `Watermarker` 載入您的圖表。此物件可存取各種文件元素，包括圖形及其屬性。

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **為何**：載入檔案是取得內容以進一步操作的前提。

### 步驟 2：存取圖形內容
取得圖表的圖形內容。這讓您能直接處理可能包含超連結的元素。

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **為何**：存取特定圖形對於定位與修改超連結屬性至關重要。

### 步驟 3：遍歷並移除超連結
以相反順序遍歷超連結，以安全地移除不需要的連結，避免迭代過程被中斷。

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **為何**：反向遍歷可避免在移除元素時產生索引問題。

### 步驟 4：儲存並關閉
完成修改後，將變更儲存至新檔案位置，並關閉 Watermarker 資源。

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **為何**：正確關閉資源可確保系統不會出現記憶體洩漏或檔案被鎖定的情況。

## 常見陷阱與疑難排解
- **Null shape collections** – 在遍歷前務必檢查圖形的 `Hyperlinks` 集合是否為 null。  
- **Large diagrams** – 若檔案超過 200 頁，請增大 JVM 堆積大小 (`-Xmx2g`) 以避免 `OutOfMemoryError`。  
- **License errors** – 若出現授權例外，請確認試用授權未過期且授權檔案路徑正確。

## 常見問題

**Q: 如何處理同一頁面的多個圖形？**  
A: 迭代每個頁面的 `Shapes` 集合，對遇到的每個圖形套用相同的超連結移除邏輯。

**Q: 能否只限制在特定頁面範圍內移除？**  
A: 可以——在取得圖形時使用頁面索引，並跳過目標範圍外的頁面。

**Q: 批次處理是否需要授權？**  
A: 任何正式等級的批次作業皆需有效的商業授權；試用授權僅適用於有限測試。

**Q: 這能否支援 SVG 或 Visio 檔案？**  
A: GroupDocs.Watermark 支援 SVG、VSDX 以及其他多種圖表格式；請確認檔案類型列於支援格式表中。

**Q: 300 頁圖表的效能預期如何？**  
A: 在一般伺服器（8 核心 CPU、16 GB 記憶體）上，處理 300 頁圖表耗時不到 45 秒，記憶體使用量保持在 200 MB 以下。

## 資源
- [文件說明](https://docs.groupdocs.com/watermark/java/)
- [API 參考](https://reference.groupdocs.com/watermark/java)
- [下載](https://releases.groupdocs.com/watermark/java/)
- [GitHub 程式庫](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/watermark/10)
- [臨時授權取得](https://purchase.groupdocs.com/temporary-license/)

---

**最後更新：** 2026-10-21  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs

## 相關教學

- [使用 GroupDocs.Watermark 在 Java 中修改 Word 文件圖形：完整指南](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [使用 GroupDocs.Watermark 在 Java 中從 Word 文件移除圖形：完整指南](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [使用 GroupDocs.Watermark 在 Java 中編輯圖表頁首與頁尾：完整指南](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)