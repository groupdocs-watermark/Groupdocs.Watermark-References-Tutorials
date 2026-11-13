---
date: 2026-11-13
description: 了解如何使用 GroupDocs.Watermark for Java 提取元資料、列出支援的格式以及取得文件資訊。
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: 如何使用 GroupDocs.Watermark for Java 提取元資料。了解如何在數分鐘內列出支援的格式、取得文件資訊，以及提取投影片背景。
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: 如何使用 GroupDocs.Watermark for Java 提取元資料
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: 如何使用 GroupDocs.Watermark for Java 提取元資料
type: docs
url: /zh-hant/java/document-information/
weight: 14
---

# 使用 GroupDocs.Watermark for Java 提取元資料

在本指南中，您將會發現 **如何提取元資料**，適用於各種文件類型，使用 GroupDocs.Watermark for Java。無論您需要讀取檔案類型、頁數、作者資訊或自訂屬性，該函式庫皆提供程式化存取，以便您對浮水印放置、文件路由或合規性檢查作出智慧決策。教學亦示範如何列出支援的格式、取得投影片背景資料，以及取得其他有用的文件特徵。

## 快速答案
- **我可以從 PDF 和 Word 檔案提取元資料嗎？** 是的，API 可從超過 70 種常見格式讀取元資料。  
- **開發時需要授權嗎？** 免費的臨時授權可用於測試；正式環境需要完整授權。  
- **需要哪個 Java 版本？** 支援 Java 8 或更高版本。  
- **此函式庫是執行緒安全的嗎？** 核心提取類別設計為可同時使用。  
- **支援多少種格式？** 開箱即支援超過 70 種輸入與輸出格式。

## 什麼是元資料提取？
元資料提取是指在不改變文件內容的前提下，讀取嵌入的資訊——例如作者、建立日期、頁數與自訂屬性——的過程。它可支援依賴文件屬性的自動化工作流程。通常會包含標題、關鍵字與修改時間戳記等屬性，可用於索引與合規報告。

## 為什麼使用 GroupDocs.Watermark for Java？
GroupDocs.Watermark for Java 支援 **70+ 檔案格式**，包括 PDF、DOCX、PPTX、XLSX 以及各種影像類型，且可在不將整個檔案載入記憶體的情況下處理高達 500 MB 的文件。其 API 以單一且一致的物件回傳元資料，減少格式特定解析器的需求，開發時間可縮短最高 40 %。

## 前置條件
- 已在開發機器上安裝 Java 8 或更新版本。  
- 使用 Maven 或 Gradle 管理 `groupdocs-watermark` 相依性。  
- 具備臨時或完整的 GroupDocs.Watermark 授權檔。

## 如何逐步提取元資料

### 如何取得基本文件資訊？
`Watermark` 類別代表一個文件，並提供存取其元資料的功能。`getDocumentInfo()` 方法會從已載入的文件中提取元資料物件。先以 `Watermark` 類別載入文件，然後呼叫 `getDocumentInfo()` 取得包含檔案類型、大小、頁數與建立日期的物件。此單一呼叫在一般小於 100 MB 的檔案上可於一秒內回傳所有核心元資料。回傳的 `DocumentInfo` 物件亦包含文件的作者、最後修改日期以及任何嵌入的自訂屬性，提供完整概覽。

### 如何列出所有支援的檔案格式？
`SupportedFormats` 工具提供 SDK 可處理的所有檔案類型目錄。使用 SDK 所提供的 `SupportedFormats` 工具，可取得格式識別碼的集合，您可以在上傳檔案前顯示或驗證，以確保相容性並避免執行時錯誤。每筆條目包含格式名稱、常見副檔名以及其功能的簡短說明，協助開發者在處理前驗證輸入。

### 如何從 PowerPoint 檔案提取投影片背景資訊？
`SlideInfo` 物件描述投影片的視覺屬性，例如背景影像與尺寸。`getSlides()` 會回傳每張投影片的 `SlideInfo` 物件集合。`SlideInfo` 物件公開背景影像尺寸、檔案大小與色深。透過 `getSlides()` 集合存取，然後遍歷每張投影片以讀取其背景屬性——對於動態樣式或縮圖產生非常有用。這些細節可用於產生縮圖、套用一致樣式，或在多個簡報中以程式方式替換背景。

## 常見問題與解決方案
- **Missing metadata:** 某些較舊的檔案可能不含標準屬性。此時，請啟用 `extractCustomProperties` 旗標以擷取任何使用者自訂欄位。  
- **Large files cause timeouts:** 增加 SDK 的 `maxMemory` 設定或以串流模式處理文件，以避免將整個檔案載入記憶體。  
- **Unsupported format error:** 在嘗試提取前，先以 `SupportedFormats` 回傳的清單驗證格式。

## 常見問答

**Q: 我可以從受密碼保護的文件提取元資料嗎？**  
A: 可以，開啟文件時提供密碼；API 會在記憶體中解密後再讀取元資料。

**Q: 此函式庫能在 Android 上使用嗎？**  
A: 核心提取功能相容於 Android API 21+，只要以標準 JAR 包裝即可。

**Q: 我該如何處理自訂元資料欄位？**  
A: 使用 `DocumentInfo` 物件的 `getCustomProperties()` 方法；它會回傳鍵值對映射，您可以遍歷使用。

**Q: 有沒有辦法批次處理多個檔案？**  
A: 將提取邏輯包在迴圈中，並重複使用單一 `Watermark` 實例；SDK 設計支援高吞吐量情境。

**Q: 有哪些授權選項？**  
A: GroupDocs.Watermark 提供永久、訂閱與臨時授權；臨時授權特別適合評估與 CI 流程。

## 可用教學

### [使用 GroupDocs.Watermark for Java 提取文件資訊：完整指南](./extract-document-info-groupdocs-watermark-java/)
了解如何使用 GroupDocs.Watermark for Java 高效提取文件元資料，如檔案類型、頁數與大小。本教學涵蓋設定、實作與實務應用。

### [使用 GroupDocs.Watermark 在 Java 中提取 PDF 頁面尺寸：完整指南](./get-pdf-page-dimensions-groupdocs-watermark-java/)
了解如何使用 GroupDocs.Watermark for Java 提取 PDF 頁面尺寸。本教學涵蓋設定、程式碼範例與實務應用。

### [使用 GroupDocs.Watermark 在 Java 中提取 Word 文件中的圖形](./extract-shapes-word-docs-groupdocs-watermark-java/)
了解如何使用 GroupDocs.Watermark for Java 提取並分析 Word 文件中的圖形，提升文件自動化與操作能力。

### [如何使用 GroupDocs.Watermark for Java 提取投影片背景資訊](./groupdocs-watermark-java-extract-slide-backgrounds/)
了解如何使用 GroupDocs.Watermark for Java 提取投影片背景細節，如影像尺寸與檔案大小。適用於自訂、分析或文件化。

### [如何使用 GroupDocs.Watermark for Java 列出支援的檔案格式：完整指南](./groupdocs-watermark-java-list-supported-formats/)
了解如何使用 GroupDocs.Watermark in Java 高效列出支援的檔案格式，確保各種文件類型的相容性。

### [如何使用 GroupDocs.Watermark for Java 取得文件資訊：逐步指南](./retrieve-document-info-groupdocs-watermark-java/)
了解如何使用 GroupDocs.Watermark for Java 高效取得文件資訊，如檔案類型、頁數與大小。跟隨我們的詳細教學與程式碼範例。

### [如何使用 GroupDocs.Watermark for Java 取得 Word 文件的章節屬性](./groupdocs-java-word-section-properties-retrieval/)
了解如何使用 GroupDocs.Watermark for Java 高效取得並操作 Word 文件的章節屬性。適合想提升文件處理能力的開發者。

## 其他資源

- [GroupDocs.Watermark for Java 文件](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark for Java API 參考](https://reference.groupdocs.com/watermark/java/)
- [下載 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark 論壇](https://forum.groupdocs.com/c/watermark)
- [免費支援](https://forum.groupdocs.com/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)

---

**最後更新:** 2026-11-13  
**測試環境:** GroupDocs.Watermark 23.12 for Java  
**作者:** GroupDocs

## 相關教學

- [如何使用 GroupDocs.Watermark for Java 列出支援的檔案格式：完整指南](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [如何使用 GroupDocs.Watermark for Java 取得文件資訊：逐步指南](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark for Java 提取文件資訊：完整指南](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)