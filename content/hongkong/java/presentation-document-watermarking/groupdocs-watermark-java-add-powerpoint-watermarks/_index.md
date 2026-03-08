---
date: '2026-03-08'
description: 學習如何使用 GroupDocs.Watermark 在 PowerPoint（Java）中加入水印，透過文字與圖片水印有效保護您的投影片。
keywords:
- GroupDocs Watermark Java
- PowerPoint watermarks
- Java presentation watermarking
title: 使用 GroupDocs.Watermark 為 PowerPoint 添加水印（Java）
type: docs
url: /zh-hant/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/
weight: 1
---

CODE_BLOCK_0}} etc. Keep as is.

Check any other shortcodes: none.

Check images: none.

Check lists: we have bullet lists and numbered list.

Make sure headings levels correct.

Now produce final content.# 使用 GroupDocs.Watermark 為 PowerPoint Java 添加水印

保護您的簡報資產是首要任務，而最直接的做法就是以 **add watermark PowerPoint Java** 風格添加水印。無論您需要品牌標誌、版權聲明或機密標籤，本教學將指導您使用 GroupDocs.Watermark for Java，將文字與圖片水印嵌入 PowerPoint 檔案的每一張投影片。

## 快速解答
- **我需要哪個函式庫？** GroupDocs.Watermark for Java  
- **我可以同時加入文字與圖片水印嗎？** Yes, the API supports both types.  
- **我需要授權嗎？** A temporary license is available for evaluation; a full license is required for production.  
- **需要哪個 Java 版本？** JDK 8 or higher.  
- **需要 Maven 嗎？** Not mandatory, but Maven simplifies dependency management.

## 使用 Java 為 PowerPoint 添加水印是什麼？
添加水印是指以程式方式在每張投影片上覆蓋半透明的文字或圖形。此技術可協助您維持品牌一致性、阻止未授權的散布，並在不改變原始內容的情況下傳達機密性。

## 為什麼要使用 GroupDocs.Watermark for Java？
- **完整功能 API：** Supports text, image, and even shape watermarks across all major Office formats.  
- **無外部相依性：** Works out‑of‑the‑box with just the JAR files.  
- **高效能：** Optimized for large presentations with batch processing capabilities.  
- **跨平台：** Runs on any OS that supports the JDK.

## 前置條件
- **Java Development Kit (JDK) 8+** – 確保 `java` 與 `javac` 已加入 PATH。  
- **Maven** – 雖非必須，但建議用於相依性管理。  
- **IDE** – IntelliJ IDEA、Eclipse，或您偏好的任何編輯器。  

## 設定 GroupDocs.Watermark for Java
### Maven 安裝
Add the repository and dependency to your `pom.xml`:

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
如果您偏好手動設定，請從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新的 JAR。

### 取得授權
可透過 [GroupDocs 的網站](https://purchase.groupdocs.com/temporary-license/) 取得臨時評估金鑰或購買正式授權。授權檔案需放置於專案的 resources 資料夾中。

### 基本初始化與設定
Create a `Watermarker` instance pointing at your PowerPoint file:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## 實作指南
以下為逐步說明，將文字與圖片水印加入每張投影片。

### 添加文字水印
**概覽：** 在每張投影片的背景圖上覆蓋自訂文字。

#### 步驟 1：建立與設定文字水印
```java
// Create a TextWatermark object
textWatermark = new TextWatermark("Protected Image", new Font("Arial", 8));
```

#### 步驟 2：設定對齊、旋轉與尺寸
```java
// Center align the watermark horizontally and vertically
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);

// Rotate the watermark by 45 degrees for better visibility
textWatermark.setRotateAngle(45);

// Scale based on parent dimensions, with no additional scaling factor
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

#### 步驟 3：將水印套用至具有背景圖的投影片
```java
PresentationContent content = watermarker.getContent(PresentationContent.class);
for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Add watermark to the slide's background image
        slide.getImageFillFormat().getBackgroundImage().add(textWatermark);
    }
}
```

### 添加圖片水印
**概覽：** 在每張投影片上放置標誌或任意 PNG/JPEG 圖片。

#### 步驟 1：載入圖片水印
```java
// Load the watermark image
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
```

#### 步驟 2：設定位置與透明度
```java
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Bottom);
imageWatermark.setOpacity(0.5f);
```

#### 步驟 3：將圖片水印插入每張投影片
```java
for (PresentationSlide slide : content.getSlides()) {
    slide.add(imageWatermark);
}
```

### 儲存已修改的簡報並釋放資源
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/presentation_output.pptx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## 實務應用
1. **品牌化：** 自動在所有面向客戶的簡報中嵌入公司標誌。  
2. **版權保護：** 顯示版權聲明以阻止未授權的複製。  
3. **機密標籤：** 為內部簡報加註「Confidential – Do Not Distribute」。  
4. **文件管理整合：** 將加水印步驟掛接至 CI/CD 流程或 DMS，以即時保護文件。

## 效能考量
- **批次處理：** 對於大型投影片檔，請分批處理以降低記憶體使用量。  
- **資源清理：** 必須關閉 `Watermarker`、`TextWatermark` 與 `ImageWatermark` 物件，以釋放原生資源。  
- **平行執行：** 若需為多個檔案加水印，可考慮使用執行緒池，但每個 `Watermarker` 實例須限制於單一執行緒。

## 常見問題與解決方案
- **Null 背景圖片：** 某些投影片可能使用純色背景而非圖片。此時，請直接將水印加入投影片 (`slide.add(textWatermark)`)。  
- **授權錯誤：** 確認臨時授權檔已正確放置，並透過 `License license = new License(); license.setLicense("path/to/license.file");` 設定路徑。  
- **大型檔案變慢：** 增加 JVM 堆積大小 (`-Xmx2g`) 或分批處理投影片。

## 常見問答

**Q: GroupDocs.Watermark 支援哪些檔案格式？**  
A: 支援 PowerPoint、Word、Excel、PDF、Visio 以及多種影像格式。

**Q: 我也可以加入圖片水印嗎？**  
A: 可以，函式庫同時支援文字與圖片水印，如上所示。

**Q: 如何有效處理大型簡報？**  
A: 以批次方式處理投影片，及時關閉資源，並考慮增大 JVM 堆積大小。

**Q: GroupDocs.Watermark Java 可以免費使用嗎？**  
A: 您可取得臨時授權進行評估；正式使用則需購買付費授權。

**Q: 加入水印後可以移除嗎？**  
A: 水印已嵌入檔案中。若要移除，需要重新開啟簡報並編輯投影片，刪除水印物件。

## 資源
- [文件說明](https://docs.groupdocs.com/watermark/java/)
- [API 參考](https://reference.groupdocs.com/watermark/java)
- [下載 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GitHub 程式庫](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/watermark/10)
- [取得臨時授權](https://purchase.groupdocs.com/temporary-license/) 

探索其他加水印情境，例如批次處理多個檔案或與雲端儲存整合，以進一步保護您的文件工作流程。

**最後更新：** 2026-03-08  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs