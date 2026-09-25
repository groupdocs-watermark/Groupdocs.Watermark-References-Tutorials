---
date: '2026-09-11'
description: 了解如何使用 GroupDocs.Watermark for Java 提取 slide background java 並讀取 PowerPoint
  幻燈片尺寸。可在數分鐘內取得 image size、file size 與 metadata。
keywords:
- extract slide background java
- read powerpoint slide dimensions
- slide background details java
lastmod: '2026-09-11'
og_description: 使用 GroupDocs.Watermark for Java 提取 slide background java 並讀取 PowerPoint
  幻燈片尺寸。提供包含 setup、code 與 troubleshooting 的詳細指南。
og_image_alt: Guide showing Java code extracting slide background information from
  PowerPoint
og_title: 使用 GroupDocs.Watermark 提取 slide background java
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  headline: How to extract slide background java
  type: TechArticle
- description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  name: How to extract slide background java
  steps:
  - name: create load options
    text: '`PresentationLoadOptions` defines loading preferences such as password
      handling and memory usage.'
  - name: open the PowerPoint document
    text: Instantiate `Watermarker` with the path to your `.pptx` file and the load
      options created earlier.
  - name: access slide content
    text: '`PresentationContent` is the entry point for retrieving slide‑level objects,
      including background images.'
  - name: iterate over slides and read background details
    text: Slide represents an individual slide within the presentation and provides
      access to its visual elements. For each `Slide` object, call `getBackground()`
      to obtain the image, then read its dimensions and size.
  - name: close the watermarker
    text: Always close the `Watermarker` instance to free native resources and avoid
      memory leaks.
  type: HowTo
- questions:
  - answer: Java 11 or newer is required; earlier versions lack the necessary language
      features for the library.
    question: What is the minimum Java version required?
  - answer: Yes—set the password in `PresentationLoadOptions` before opening the file.
    question: Can I extract backgrounds from password‑protected presentations?
  - answer: The trial imposes a watermark on output files but does not restrict slide
      count for metadata extraction.
    question: Does the trial mode limit the number of slides I can process?
  - answer: Absolutely—use `ImageInfo.save("output.png")` after retrieving the `ImageInfo`
      object.
    question: Is it possible to save the extracted background image to disk?
  - answer: The API supports PNG, JPEG, BMP, and GIF for background image export.
    question: Which formats can I export the extracted image to?
  type: FAQPage
tags:
- extract slide background
- GroupDocs.Watermark
- Java PowerPoint
- document processing
title: 如何提取 slide background java
type: docs
url: /zh-hant/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# 如何提取投影片背景 Java

## 介紹

提取投影片背景 Java 是在分析、重新利用或記錄 PowerPoint 檔案內視覺資產時的常見需求。使用 GroupDocs.Watermark for Java，您可以在不開啟 PowerPoint 的情況下，以程式方式取得圖像尺寸、檔案大小及其他中繼資料。本教學將帶您完成完整工作流程——從環境設定到提取與解讀背景細節，讓您能將此功能整合至任何基於 Java 的自動化管線。

### 快速回答
- **哪個函式庫處理投影片背景提取？** GroupDocs.Watermark for Java。  
- **哪個方法返回圖像尺寸？** `getBackground().getImageInfo().getWidth()` 和 `getHeight()`。  
- **我可以取得背景圖像的檔案大小嗎？** 可以，透過 `getBackground().getImageInfo().getSize()`。  
- **此功能需要授權嗎？** 臨時或完整授權可解鎖全部功能；試用模式在有限制下仍可使用。  
- **支援 Maven 嗎？** 當然可以——將 GroupDocs.Watermark 相依性加入 `pom.xml`。

## 什麼是提取投影片背景 Java？

提取投影片背景 Java 指的是使用 Java 程式碼以程式方式讀取 PowerPoint 簡報中每張投影片的視覺背景。此操作會產生圖像寬度、高度與檔案大小等中繼資料，方便後續進行品牌檢查或資產再利用等處理。

## 為什麼在此任務中使用 GroupDocs.Watermark？

GroupDocs.Watermark 支援 **30+ 輸入與輸出格式**，可在不將整個檔案載入記憶體的情況下處理最多 **500 張投影片**，並提供專門的 API 來存取投影片背景。這些量化的能力使其成為企業級自動化的可靠選擇。

## 前置條件
- **Java 11+** 已安裝於開發機器上。  
- **Maven** 用於相依性管理。  
- **GroupDocs.Watermark 24.11**（或更新版本）——此函式庫包含本指南中使用的 `PresentationLoadOptions` 與 `PresentationContent` 類別。  
- **有效授權**（臨時或完整）以解鎖全部功能。

## 設定 GroupDocs.Watermark（Java）

### Maven 設定
將 GroupDocs.Watermark 相依性加入您的 `pom.xml` 檔案：

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
如果您偏好手動安裝，請從官方發行頁面取得最新的 JAR： [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)。

### 取得授權
臨時授權可讓您評估 API，完整授權則移除所有試用限制。請於授權入口取得授權： [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license/)。

#### 基本初始化與設定
第一步是建立指向 PowerPoint 檔案的 `Watermarker` 實例：

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## 如何提取投影片背景 Java？

此流程從使用 Watermarker 實例載入 PowerPoint 檔案開始，接著建立適當的載入選項。開啟文件後，您可以存取每張投影片的內容、取得背景圖像，並提取其尺寸與檔案大小等中繼資料。最後，關閉 Watermarker 以釋放資源。以下步驟說明了完整的執行順序，程式碼佔位符顯示了您現有片段應放置的位置。

### 步驟 1：建立載入選項
`PresentationLoadOptions` 定義載入偏好，例如密碼處理與記憶體使用方式。

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### 步驟 2：開啟 PowerPoint 文件
以檔案路徑與先前建立的載入選項實例化 `Watermarker`。

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### 步驟 3：存取投影片內容
`PresentationContent` 是取得投影片層級物件（包括背景圖像）的入口。

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### 步驟 4：遍歷投影片並讀取背景資訊
Slide 代表簡報中的單一投影片，提供對其視覺元素的存取。對每個 `Slide` 物件呼叫 `getBackground()` 取得圖像，然後讀取其尺寸與大小。

```java
import com.groupdocs.watermark.contents.PresentationSlide;
import com.groupdocs.watermark.options.PresentationLoadOptions;

for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Extract width, height, and size of the background image.
        int width = slide.getImageFillFormat().getBackgroundImage().getWidth();
        int height = slide.getImageFillFormat().getBackgroundImage().getHeight();
        long imageSize = slide.getImageFillFormat().getBackgroundImage().getBytes().length;
        
        System.out.println("Width: " + width + ", Height: " + height + ", Image Size: " + imageSize);
    }
}
```

### 步驟 5：關閉 Watermarker
務必關閉 `Watermarker` 實例以釋放原生資源，避免記憶體泄漏。

```java
watermarker.close();
```

## 如何使用 GroupDocs.Watermark 讀取 PowerPoint 投影片尺寸？

API 透過附屬於投影片背景的 `ImageInfo` 物件公開寬度與高度。使用 `getWidth()` 與 `getHeight()` 取得像素值，可用於版面計算或與品牌指引進行驗證。

## 常見問題與故障排除
- **找不到檔案** – 請確認檔案路徑為絕對路徑或相對於專案根目錄正確。  
- **不支援的格式** – GroupDocs.Watermark 支援 PPTX、PPT 與 ODP；較舊的二進位 PPT 可能需要先轉換。  
- **授權未套用** – 請確保在使用任何其他 API 前先呼叫 `License.setLicense("path/to/license.file")`。

## 實務應用
1. **自動化品牌合規** – 掃描投影片背景以確認其符合企業色彩調色盤或標誌尺寸。  
2. **資產清點** – 建立文件庫中背景圖像的目錄，以便在行銷資產中重複使用。  
3. **內容遷移** – 提取背景圖像，存入數位資產管理系統，並以程式方式重新套用於新投影片。  
4. **效能監控** – 記錄圖像大小統計，以偵測可能導致投影片渲染緩慢的過大資產。

## 效能考量
- **資源清理** – 立即關閉 `Watermarker` 可釋放原生記憶體，對於處理大型投影片集尤為重要。  
- **記憶體占用** – 函式庫以串流方式處理投影片資料；可改為一次處理單張投影片，以降低記憶體使用。  
- **批次處理技巧** – 處理多個檔案時，重複使用單一 `License` 實例，並為每個檔案建立新的 `Watermarker`，以維持 JVM 堆積穩定。

## 結論
您現在擁有一套完整、可投入生產環境的指南，能使用 GroupDocs.Watermark 提取投影片背景 Java。依照上述步驟，您可以取得圖像尺寸、檔案大小與其他中繼資料，並將這些資訊應用於品牌檢查、資產管理或任何自訂工作流程。

**下一步**
- 嘗試不同的 `PresentationLoadOptions`（例如受密碼保護的檔案）。  
- 探索浮水印 API，以自動新增或取代背景。  
- 將此提取邏輯與 REST 服務結合，提供投影片中繼資料端點。

## 常見問答

**問：最低需要哪個 Java 版本？**  
答：需要 Java 11 或更新版本；較舊版本缺少函式庫所需的語言功能。

**問：能從受密碼保護的投影片中提取背景嗎？**  
答：可以——在開啟檔案前於 `PresentationLoadOptions` 設定密碼。

**問：試用模式會限制可處理的投影片數量嗎？**  
答：試用模式會在輸出檔案加上浮水印，但不會限制用於中繼資料提取的投影片數量。

**問：能將提取的背景圖像儲存至磁碟嗎？**  
答：當然可以——在取得 `ImageInfo` 物件後使用 `ImageInfo.save("output.png")`。

**問：可以將提取的圖像匯出為哪些格式？**  
答：API 支援 PNG、JPEG、BMP 與 GIF 作為背景圖像的匯出格式。

## 資源
- **文件說明：** [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/)  
- **文件說明：** [GroupDocs Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API 參考：** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **下載：** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **GitHub 倉庫：** [GroupDocs GitHub Page](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **支援論壇：** [GroupDocs Support Forum](https://forum.groupdocs.com/c/watermark/10)

---

**最後更新：** 2026-09-11  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs

## 相關教學

- [如何使用 GroupDocs.Watermark Java API 取得 PowerPoint 投影片尺寸](/watermark/java/presentation-document-watermarking/retrieve-slide-dimensions-powerpoint-groupdocs-watermark-java/)
- [在 Java 中使用 GroupDocs.Watermark 套件移除 PowerPoint 投影片背景](/watermark/java/watermark-removal/remove-ppt-slide-background-groupdocs-watermark-java/)
- [如何使用 GroupDocs.Watermark for Java 取得文件資訊：逐步指南](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)