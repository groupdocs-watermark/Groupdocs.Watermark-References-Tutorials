---
date: 2026-11-20
description: 了解如何在 Java 中使用 GroupDocs.Watermark 建立不可讀字符。詳細教學涵蓋進階浮水印、保護與預覽功能。
keywords:
- create unreadable characters java
- GroupDocs.Watermark Java
- advanced watermarking Java
lastmod: 2026-11-20
og_description: 使用 GroupDocs.Watermark 在 Java 中建立不可讀字符。探索進階浮水印、文件保護與產生預覽功能。
og_image_alt: Guide showing how to create unreadable characters in Java with GroupDocs.Watermark
og_title: 使用 GroupDocs.Watermark 在 Java 中建立不可讀字符
schemas:
- author: GroupDocs
  dateModified: '2026-11-20'
  description: Learn how to create unreadable characters Java using GroupDocs.Watermark
    for Java. Detailed tutorials cover advanced watermarking, protection, and preview
    features.
  headline: Create unreadable characters Java with GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt,
      apply the transformation, and re‑encrypt automatically.
    question: Can I apply unreadable characters to password‑protected PDFs?
  - answer: The unreadable character option works on text layers; for scanned images
      you must first run OCR to create a searchable text layer.
    question: Does the feature work with scanned images?
  - answer: Processing time grows linearly; a 500‑page PDF typically finishes in under
      15 seconds on a standard server.
    question: How does performance scale with document size?
  - answer: No, the operation overwrites the original text. Keep an original copy
      if you need to restore the content later.
    question: Is it possible to revert the changes?
  - answer: GroupDocs.Watermark for Java supports JDK 8 through JDK 21, including
      all LTS releases.
    question: Which Java versions are supported?
  type: FAQPage
tags:
- watermarking
- GroupDocs
- Java tutorial
title: 使用 GroupDocs.Watermark 在 Java 中建立不可讀字符
type: docs
url: /zh-hant/java/advanced-features/
weight: 13
---

# 使用 GroupDocs.Watermark 在 Java 中建立不可讀字元

在本指南中，您將學習如何透過 GroupDocs.Watermark for Java 的進階功能 **create unreadable characters Java**（建立不可讀字元 Java）來保護機密資料、隱藏敏感文字，或遵守法規標準。本教學會逐步說明概念、使用情境以及將不可讀字元安全嵌入文件的操作步驟。

## 快速解答
- **“unreadable characters” 是什麼意思？** 這是一種將選取的文字替換為無法被一般閱讀器解讀的符號或字形的技術。  
- **為什麼要使用此功能？** 它在不改變文件版面的情況下，提供額外的保護層。  
- **支援哪些檔案類型？** 超過 70 種格式，包括 PDF、DOCX、PPTX 以及影像檔。  
- **需要授權嗎？** 是，需要有效的 GroupDocs.Watermark 授權才能在正式環境使用。  
- **能處理大型檔案嗎？** 是，能處理高達 2 GB 的檔案，同時保持低記憶體使用量。

## 什麼是 create unreadable characters Java？
Create unreadable characters Java 是使用 GroupDocs.Watermark 的 API，將一般文字替換為不可辨識字形的過程。API 會掃描文件中指定的字串，將每個字元替換為預先定義的不可讀字形集合中的字形，確保視覺版面保持不變，同時原始內容對一般檢視器變得不可讀。

## 為什麼在浮水印中使用不可讀字元？
GroupDocs.Watermark 支援 **70+ 輸入與輸出格式**，且可處理高達 **2 GB** 大小的文件，同時將記憶體消耗維持在 **150 MB** 以下。使用不可讀字元可加入防篡改層，防止隨意複製或資料挖掘，對合約、法律簡報與財務報表等特別有價值。

## 如何建立不可讀字元 Java？
`Watermark` 類別是 GroupDocs.Watermark 中用於載入、編輯與儲存文件的主要 API。  
`UnreadableCharacterOptions` 定義產生不可讀字元的設定，例如字形集合與替換規則。  

使用 `Watermark` 類別載入文件，設定 `UnreadableCharacterOptions` 物件，然後呼叫 `apply()` —— 這是不到十行程式碼的核心工作流程。API 會自動偵測文字串列，替換字元，並在不需要完整重新渲染文件的情況下儲存結果。若要批次處理，可遍歷資料夾並重複使用相同的 options 實例，以提升效能。

## 可用教學

### [使用 GroupDocs.Watermark 於 Java 產生文件預覽&#58; 進階指南](./groupdocs-watermark-java-document-previews/)
學習使用 GroupDocs.Watermark for Java 產生文件預覽。透過有效處理大量文件，簡化工作流程。

### [精通 GroupDocs.Watermark 於 Java&#58; 文件保護完整指南](./groupdocs-watermark-java-tutorial/)
了解如何將 GroupDocs.Watermark 整合至您的 Java 應用程式。使用文字與影像浮水印保護文件與圖片。

## 其他資源

- [GroupDocs.Watermark for Java 文件](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark for Java API 參考文件](https://reference.groupdocs.com/watermark/java/)
- [下載 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark 論壇](https://forum.groupdocs.com/c/watermark)
- [免費支援](https://forum.groupdocs.com/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)

## 常見問題

**Q: 我可以將不可讀字元套用於受密碼保護的 PDF 嗎？**  
**A:** 是，開啟文件時提供密碼；API 會自動解密、套用轉換，並重新加密。

**Q: 此功能能用於掃描圖像嗎？**  
**A:** 不可讀字元選項作用於文字層；對於掃描圖像，必須先執行 OCR 以建立可搜尋的文字層。

**Q: 效能如何隨文件大小而變化？**  
**A:** 處理時間呈線性增長；在一般伺服器上，500 頁的 PDF 通常在 15 秒內完成。

**Q: 可以還原變更嗎？**  
**A:** 不行，操作會覆寫原始文字。若需日後還原，請保留原始副本。

**Q: 支援哪些 Java 版本？**  
**A:** GroupDocs.Watermark for Java 支援 JDK 8 至 JDK 21，包括所有 LTS 版本。

---

**最後更新:** 2026-11-20  
**測試環境:** GroupDocs.Watermark 23.12 for Java  
**作者:** GroupDocs

## 相關教學

- [GroupDocs.Watermark 入門教學（適用於 Java 開發者）](/watermark/java/getting-started/)
- [精通 GroupDocs.Watermark 於 Java - 文件保護完整指南](/watermark/java/advanced-features/groupdocs-watermark-java-tutorial/)
- [GroupDocs.Watermark for Java：PDF 浮水印完整指南](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-pdf-watermark-guide/)