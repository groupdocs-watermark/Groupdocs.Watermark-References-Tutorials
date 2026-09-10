---
date: '2026-03-08'
description: 學習如何使用 GroupDocs.Watermark for Java 為 PowerPoint 添加水印，保護母片、版面、備註及講義投影片的內容。
keywords:
- GroupDocs.Watermark for Java
- PowerPoint Watermarks
- Java Slide Watermarking
- Protect Presentation Content
- Master Slides Watermark
title: 使用 GroupDocs.Watermark 為 PowerPoint 加上水印（Java）
type: docs
url: /zh-hant/java/presentation-document-watermarking/groupdocs-watermark-java-powerpoint-watermarks/
weight: 1
---

# 使用 GroupDocs.Watermark 為 PowerPoint Java 加上浮水印

## 快速解答
- **哪個函式庫可以讓您在 PowerPoint Java 中加入浮水印？** GroupDocs.Watermark for Java.  
- **我可以為所有投影片加上浮水印，包括母片與備註頁嗎？** 可以 — API 支援母片、版面配置、備註、講義母片以及備註母片。  
- **正式環境需要授權嗎？** 需要付費授權；可使用免費試用版進行評估。  
- **需要哪個 Java 版本？** JDK 8 或以上。  
- **是否建議使用 Maven 來加入相依性？** 絕對建議 — Maven 會自動處理傳遞相依性。

## 什麼是「在 PowerPoint Java 中加入浮水印」？

在 Java 中為 PowerPoint 檔案加入浮水印，指的是以程式方式在投影片上插入半透明的文字或圖片覆蓋層。此技術常用於 **保護 PowerPoint 內容** 防止被複製、標示「機密」或在整個簡報中嵌入品牌標誌。

## 為什麼要使用 GroupDocs.Watermark for Java？

GroupDocs.Watermark 提供高階、易用的 API，將複雜的 OpenXML 結構封裝成幾個直觀的類別。它讓您能夠：

* **為所有投影片加上浮水印** — 包含平常不易手動編輯的隱藏母片與版面配置。  
* **自訂外觀** — 字型、大小、顏色、旋轉角度與透明度皆可完整設定。  
* **保持效能** — 函式庫以串流方式處理大型檔案，降低記憶體使用量。  

## 前置條件

- **Java Development Kit (JDK)** 8 或更新版本。  
- **Maven** 用於相依性管理。  
- 具備基本的 Java 程式開發經驗。  

## 設定 GroupDocs.Watermark for Java

您可以透過 Maven 或直接下載 JAR 檔的方式加入函式庫。

### 使用 Maven

在 `pom.xml` 中加入以下儲存庫與相依性：

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

亦可從官方發行頁面下載最新的 JAR： [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### 取得授權

正式環境必須使用完整功能授權。您可以先使用免費試用版，或申請臨時授權以進行測試。

## 實作指南

以下提供逐步程式碼範例，說明 **如何在 PowerPoint Java 中加入浮水印** 至各種投影片類型。程式碼區塊保持原樣，說明文字已加強說明。

### 如何在所有母片上加入浮水印

母片決定簡報的整體外觀。於母片加入浮水印，可確保每張衍生投影片皆繼承此標記。

#### 概觀
我們將在每張母片上放置簡單的文字浮水印「Test watermark」。

#### 實作步驟

1. **載入簡報** — 使用 `Watermarker` 初始化您的 PPTX 檔案。

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

2. **建立浮水印** — 設定文字、字型與大小。

```java
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 8));
```

3. **套用至母片** — 使用負索引 (`-1`) 目標所有母片。

```java
PresentationContent content = watermarker.getContent(PresentationContent.class);
PresentationWatermarkMasterSlideOptions masterSlideOptions = new PresentationWatermarkMasterSlideOptions();
masterSlideOptions.setMasterSlideIndex(-1);
watermarker.add(watermark, masterSlideOptions);
```

4. **儲存結果** — 將加了浮水印的檔案寫入磁碟。

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/presentation_watermarked.pptx");
watermarker.close();
```

### 如何在所有版面配置投影片上加入浮水印

版面配置投影片是內容投影片的模板。為它們加上浮水印可保證整份簡報的一致性。

#### 概觀
同樣的「Test watermark」文字將加入每張版面配置投影片。

#### 實作步驟

1. **載入簡報**（同前）。

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

2. **建立浮水印並確認版面配置投影片是否存在**。

```java
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 8));
PresentationContent content = watermarker.getContent(PresentationContent.class);

if (content.getLayoutSlides() != null) {
    PresentationWatermarkLayoutSlideOptions layoutSlideOptions = new PresentationWatermarkLayoutSlideOptions();
    layoutSlideOptions.setLayoutSlideIndex(-1);
    watermarker.add(watermark, layoutSlideOptions);
}
```

3. **儲存並關閉**。

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/presentation_watermarked.pptx");
watermarker.close();
```

### 如何在所有備註投影片上加入浮水印

備註投影片儲存講者備註，通常包含敏感資訊。

#### 概觀
我們會遍歷每張投影片，檢查是否有備註投影片，若有則套用浮水印。

#### 實作步驟

1. **載入簡報**。

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

2. **遍歷並加入浮水印**。

```java
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 8));
PresentationContent content = watermarker.getContent(PresentationContent.class);

for (int i = 0; i < content.getSlides().getCount(); i++) {
    if (content.getSlides().get_Item(i).getNotesSlide() != null) {
        PresentationWatermarkNoteSlideOptions noteSlideOptions = new PresentationWatermarkNoteSlideOptions();
        noteSlideOptions.setSlideIndex(i);
        watermarker.add(watermark, noteSlideOptions);
    }
}
```

3. **儲存並關閉**。

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/presentation_watermarked.pptx");
watermarker.close();
```

### 如何在講義母片上加入浮水印

講義母片控制投影片列印或匯出為講義時的版面。

#### 概觀
先確認是否存在講義母片，然後再套用浮水印。

#### 實作步驟

1. **載入簡報**。

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

2. **若講義母片存在則加入浮水印**。

```java
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 8));
PresentationContent content = watermarker.getContent(PresentationContent.class);

if (content.getMasterHandoutSlide() != null) {
    PresentationWatermarkMasterHandoutSlideOptions handoutSlideOptions = new PresentationWatermarkMasterHandoutSlideOptions();
    handoutSlideOptions.setMasterHandoutSlideIndex(-1);
    watermarker.add(watermark, handoutSlideOptions);
}

// Save and close the Watermarker as done in previous sections.
```

## 常見問題與解決方案

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **某些投影片看不到浮水印** | 可能只針對母片/版面配置投影片，個別投影片未被處理。 | 加入額外的迭代，遍歷 `content.getSlides()`，使用 `PresentationWatermarkSlideOptions` 為每張投影片套用浮水印。 |
| **大型 PPTX 檔案效能下降** | 整個簡報一次載入記憶體會較重。 | 使用 `PresentationLoadOptions.setLoadAllSlides(false)`，分批處理投影片。 |
| **執行時拋出 LicenseException** | 試用授權過期或未正確設定。 | 在建立 `Watermarker` 前先註冊授權：`License license = new License(); license.setLicense("path/to/license.lic");` |

## 常見問答

**Q: 可以用相同的程式碼為 PDF 檔案加浮水印嗎？**  
A: API 為 PDF 提供類似的類別，但需改用 `PdfWatermark...` 選項取代 `Presentation...`。

**Q: GroupDocs.Watermark 支援圖片浮水印嗎？**  
A: 支援 — 只要將 `TextWatermark` 換成 `ImageWatermark`，並提供圖片串流即可。

**Q: 如何控制浮水印的透明度？**  
A: 在浮水印物件上呼叫 `setOpacity(double)`，值介於 0.0 到 1.0 之間。

**Q: 能否為不同的投影片區段加上不同的浮水印？**  
A: 可以。建立多個 `TextWatermark` 實例，並以特定的投影片索引選項分別套用。

**Q: 儲存後浮水印在 PowerPoint 中仍可編輯嗎？**  
A: 浮水印會成為投影片內容的一部份，使用者可以手動選取並移除，但它不會以獨立可編輯物件的形式存在。

## 結論

依照上述步驟，您現在已掌握 **如何在 PowerPoint Java 中為每個角落加入浮水印** — 包括母片、版面配置、備註、講義與備註母片。此方法能協助您 **保護 PowerPoint 內容**，並在整份簡報中保持一致的品牌或機密標示。欲進一步客製化，請參考官方 API 文件中的其他選項。

欲取得更多資訊，請造訪官方 [GroupDocs 文件](https://docs.groupdocs.com/watermark/java/)。

---

**最後更新：** 2026-03-08  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs