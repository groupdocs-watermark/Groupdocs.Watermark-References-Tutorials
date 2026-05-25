---
date: '2026-03-17'
description: 學習如何使用 Java 與 GroupDocs.Watermark 儲存 PowerPoint 圖表影像並設定圖表背景。請依照此逐步指南，提升資料視覺化效果。
keywords:
- set chart background image PowerPoint
- Java GroupDocs.Watermark
- PowerPoint presentation enhancement
title: 使用 Java 與 GroupDocs.Watermark 儲存 PowerPoint 圖表圖片
type: docs
url: /zh-hant/java/presentation-document-watermarking/set-chart-background-image-powerpoint-java-groupdocs-watermark/
weight: 1
---

# 使用 Java 與 GroupDocs.Watermark 儲存 PowerPoint 圖表影像

在本教學中，您將學習 **如何儲存 PowerPoint 圖表** 影像並套用自訂背景，讓您的簡報呈現出精緻且符合品牌形象的外觀。我們將以 Java 與 GroupDocs.Watermark 完整示範整個流程，從設定函式庫到配置透明度與平鋪選項。

## 快速解答
- **「儲存 PowerPoint 圖表」是什麼意思？** 指在套用視覺自訂後，將圖表匯出為 PowerPoint 檔案的一部分。  
- **哪個函式庫可以為圖表加入背景影像？** GroupDocs.Watermark for Java 提供簡易的 API 來設定圖表背景影像。  
- **我需要授權嗎？** 免費試用可用於評估；正式使用則需購買完整授權。  
- **我可以平鋪背景影像嗎？** 可以 — 使用 `setTileAsTexture(true)` 方法將影像重複作為紋理。  
- **Java 8 足夠嗎？** 此函式庫支援 JDK 8 及更新版本。

## 「儲存 PowerPoint 圖表」是什麼？
儲存 PowerPoint 圖表是指將圖表嵌入投影片中，並將任何視覺變更（例如自訂背景影像）持久化至最終的 `.pptx` 檔案。這讓您能夠分發已具備所需外觀與感受的簡報。

## 為什麼要使用 GroupDocs.Watermark 設定圖表背景？
- **品牌一致性：** 直接在圖表資料後方套用公司標誌或主題紋理。  
- **提升可讀性：** 調整透明度，使資料點保持清晰，同時背景提供視覺脈絡。  
- **自動化：** 將此流程整合至後端服務、批次處理管線或 CI/CD 工作流程。  
- **效能：** GroupDocs.Watermark 能有效處理大型簡報，特別是依照本指南後續的最佳化建議時。

## 前置條件

### 必要函式庫
- **GroupDocs.Watermark for Java**（最新版本）  
- 已在您的機器上安裝 Java Development Kit（JDK）

### 環境設定
- 已配置 JDK 的 IDE，例如 IntelliJ IDEA 或 Eclipse。  
- 用於相依管理的 Maven。

### 知識前提
- 基本的 Java 程式設計與檔案 I/O。  
- 熟悉 PowerPoint 投影片與圖表結構。

## 設定 GroupDocs.Watermark for Java

### 透過 Maven 安裝
將儲存庫與相依項目加入您的 `pom.xml`：

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
或者，直接從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權
- **免費試用：** 無償探索所有功能。  
- **臨時授權：** 用於延長評估期間。  
- **購買：** 取得完整授權以無限制使用於正式環境。

## 實作指南

### 載入簡報檔案
First, load the PowerPoint file that contains the chart you want to modify:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\presentation.pptx", loadOptions);
```
- **為何這樣做：** 這會建立 `Watermarker` 實例，讓您以程式方式存取簡報內容。

### 取得並修改圖表屬性
Next, locate the chart and load the image you want to use as its background:

```java
PresentationContent content = watermarker.getContent(PresentationContent.class);

// Load image to be set as background for chart.
File imageFile = new File("YOUR_DOCUMENT_DIRECTORY\\test_image.png");
byte[] imageBytes = new byte[(int) imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
```
- **為何這樣做：** 將影像轉換為位元組陣列，使 GroupDocs.Watermark 能直接嵌入圖表的填充格式。

### 設定背景影像
Now bind the image to the first chart on the first slide:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setBackgroundImage(new PresentationWatermarkableImage(imageBytes));
```
- **為何這樣做：** 此呼叫會將預設圖表背景替換為您的自訂影像，實現 **設定圖表背景** 的效果。

### 配置透明度與平鋪
Fine‑tune the appearance with transparency and texture tiling:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTransparency(0.5);
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTileAsTexture(true);
```
- **為何這樣做：** 透明度 (`0.5`) 讓資料保持可見，而 `setTileAsTexture(true)` **平鋪圖表背景** 以產生無縫圖案。

### 儲存並關閉資源
Finally, write the modified presentation to disk and release resources:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY\\updated_presentation.pptx");
watermarker.close();
```
- **為何這樣做：** 持久化變更會產生可供分發的新檔案，關閉 `Watermarker` 則釋放系統資源。

## 實務應用
1. **企業報告：** 插入品牌標誌或企業色彩作為圖表背景。  
2. **教學投影片：** 使用主題影像（例如地圖、分子）提升資料的吸引力。  
3. **行銷簡報：** 加入紋理或浮水印風格圖形，使您的投影片與競爭者區隔。

## 效能考量
- **在嵌入前調整影像大小**，以維持檔案大小在可接受範圍。  
- **使用 try‑with‑resources** 來管理串流，確保自動清理。  
- **避免一次載入大型簡報** 至記憶體；盡可能逐張投影片增量處理。

## 常見問題與除錯

| 問題 | 解決方案 |
|-------|----------|
| `OutOfMemoryError` 在處理大型影像時 | 調整影像大小或改用基於 `InputStream` 的載入方式，而非將整個檔案讀入位元組陣列。 |
| 背景影像未顯示 | 確認圖表的 `ImageFillFormat` 在程式碼後續未被覆寫。 |
| 透明度看起來太暗 | 調整傳遞給 `setTransparency()` 的數值（範圍 0.0–1.0）。 |

## 常見問答

**Q: `setBackgroundImage` 與 `add watermark chart` 有何差異？**  
A: `setBackgroundImage` 會以影像取代圖表的填充，而加入 watermark chart 則在圖表資料上覆蓋半透明的文字或圖形。

**Q: 我可以一次為多個圖表套用相同的背景嗎？**  
A: 可以 — 迴圈遍歷 `content.getSlides().get_Item(i).getCharts()`，將相同的 `PresentationWatermarkableImage` 套用至每個圖表的 `ImageFillFormat`。

**Q: GroupDocs.Watermark 支援將動畫 GIF 作為圖表背景嗎？**  
A: 函式庫會將 GIF 視為靜態影像；僅使用第一幀。

**Q: 如何確保背景在不同投影片尺寸下正確縮放？**  
A: 使用 `setTileAsTexture(true)` 來平鋪影像，或在設定背景前根據投影片的寬高計算適當的尺寸。

**Q: 有沒有程式方式檢查圖表是否已設定背景影像？**  
A: 您可以檢查 `getImageFillFormat().getBackgroundImage()`；若回傳 `null`，則表示未設定影像。

## 資源
- **文件**： [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)
- **API 參考**： [GroupDocs.Watermark API Reference](https://reference.groupdocs.com/watermark/java)
- **下載**： [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)
- **GitHub 程式庫**： [GroupDocs.Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- **免費支援論壇**： [GroupDocs Watermark Forum](https://forum.groupdocs.com/c/watermark/10)
- **臨時授權**： [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**最後更新：** 2026-03-17  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs