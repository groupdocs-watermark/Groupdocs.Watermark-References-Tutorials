---
date: '2026-04-04'
description: 學習如何使用 GroupDocs.Watermark for Java 在 Visio 圖表上建立文字浮水印。包括設定、程式碼及實際案例。
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: 使用 GroupDocs.Watermark Java 為圖表建立文字浮水印
type: docs
url: /zh-hant/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# 在圖表上使用 GroupDocs.Watermark Java 建立文字浮水印

在當今的協作環境中，保護圖表免於未經授權的重用是必須的。在本教學中，您將使用 **GroupDocs.Watermark for Java** 在 Visio 風格的圖表上 **建立文字浮水印**。我們將從 Maven 設定到儲存加浮水印的檔案全程示範，讓您能自信地為每個圖表頁面加入品牌或安全標記。

## 快速回答
- **需要哪個函式庫？** GroupDocs.Watermark for Java (Maven artifact `groupdocs-watermark`).
- **支援哪些檔案類型？** Visio (`.vsdx`, `.vsd`)，以及許多其他圖表格式。
- **需要授權嗎？** 臨時試用授權可用於開發；正式授權則需於生產環境使用。
- **可以自訂字型、顏色與旋轉角度嗎？** 可以 – `TextWatermark` 類別允許設定所有這些屬性。
- **處理時間多久？** 為一般圖表加入文字浮水印在現代硬件上不到一秒。

## 什麼是「建立文字浮水印」操作？
建立文字浮水印指的是以程式方式在文件頁面上覆蓋半透明文字。浮水印可放置於前景或背景，並可旋轉、著色與設定樣式，以符合品牌或安全需求。

## 為何使用 GroupDocs.Watermark for Java？
- **廣泛的格式支援** – 可處理 Visio、PDF、Word、Excel 等多種格式。
- **細緻的控制** – 可選擇放置位置、不透明度、旋轉角度，以及背景/前景渲染。
- **易於整合** – 基於 Maven 的設定與簡潔的 API 呼叫讓程式碼保持乾淨。
- **效能最佳化** – 關閉 `Watermarker` 時會自動釋放資源。

## 前置條件
- Java Development Kit (JDK) 8 或以上。
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。
- 用於相依管理的 Maven。

## 設定 GroupDocs.Watermark for Java
將以下儲存庫與相依項目加入您的 `pom.xml`：

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

如果您偏好手動下載，可從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 取得二進位檔，並將其加入專案的 classpath。

### 取得授權
先從 [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/) 取得免費試用授權。於任何浮水印操作之前載入授權檔案：

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## 步驟實作

### 步驟 1：載入圖表檔案
使用 `DiagramLoadOptions` 開啟 Visio 檔案（或任何支援的圖表格式）。

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### 步驟 2：建立文字浮水印
設定浮水印文字、字型、顏色、背景標誌與旋轉角度。

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### 步驟 3：定義圖表的放置位置
選擇浮水印在每個圖表頁面的背景或前景顯示。

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### 步驟 4：儲存加浮水印的圖表
將結果寫入新檔案並釋放資源。

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## 常見問題與解決方案

| 問題 | 解決方案 |
|---------|----------|
| **找不到檔案** | 確認絕對/相對路徑，並確保 Java 程序能讀取該檔案。 |
| **授權未套用** | 確認授權檔案路徑正確且檔案未損壞。 |
| **浮水印未顯示** | 檢查 `setBackground(false)` 以及旋轉角度；嘗試不同的顏色或不透明度。 |
| **不支援的圖表版本** | 使用最新的 GroupDocs.Watermark 版本（24.11），該版本已支援更新的 Visio 格式。 |

## 實務使用案例
1. **文件安全** – 防止競爭者重複使用專有流程圖。
2. **品牌一致性** – 自動在所有匯出的圖表中嵌入公司名稱或標誌。
3. **協作追蹤** – 加入使用者縮寫作為浮水印，以辨識誰編輯了每個圖表。

## 效能建議
- 在完成後盡快關閉 `Watermarker`，以釋放本機資源。
- 若進行批次處理，盡可能重複使用同一個 `Watermarker` 實例。
- 保持浮水印文字簡潔；過大的字型會增加渲染時間。

## 結論
現在您已了解如何使用 GroupDocs.Watermark for Java 在 Visio 圖表上 **建立文字浮水印**。此方法讓您全面掌控外觀、放置與樣式，協助您有效保護與品牌化視覺資產。

### 後續步驟
- 嘗試使用影像浮水印（`ImageWatermark`）進行標誌品牌化。
- 透過遍歷 `watermarker.getPages()` 並有條件套用選項，探索選擇性頁面浮水印。
- 將此邏輯整合至 CI/CD 流程，自動在發佈前保護圖表。

## 常見問答
1. **我可以將 GroupDocs.Watermark 用於其他檔案格式嗎？**  
   是的，它支援 PDF、Word 文件、Excel 工作表、PowerPoint 簡報等多種格式。
2. **我可以加入的浮水印數量有限制嗎？**  
   沒有硬性限制，但加入大量複雜浮水印可能會影響效能。
3. **如何從圖表中移除浮水印？**  
   GroupDocs.Watermark 提供偵測與移除的 API，您可以像加入浮水印的流程一樣呼叫。
4. **文字浮水印可以加在所有頁面或僅選取的頁面嗎？**  
   您可以為每頁設定 `DiagramShapeWatermarkOptions`，或在呼叫 `add` 前套用過濾條件。
5. **如果浮水印未如預期顯示，該怎麼辦？**  
   再次檢查放置設定、顏色對比，並確保圖表在儲存後未被平面化。

## 常見問題
**Q: 此函式庫支援 Visio 2003（`.vsd`）檔案嗎？**  
A: 支援 – `DiagramLoadOptions` 同時支援 `.vsdx` 與舊版 `.vsd` 格式。

**Q: 我可以變更文字浮水印的不透明度嗎？**  
A: 當然可以。使用 `textWatermark.setOpacity(0.5);` 設定 50 % 透明度。

**Q: 能否在不同的圖表頁面加入不同的浮水印？**  
A: 可以。遍歷 `watermarker.getPages()`，為每頁套用不同的 `TextWatermark` 實例與自訂選項。

**Q: 商業使用有授權限制嗎？**  
A: 生產環境部署需購買完整的商業授權；試用授權僅供評估使用。

**Q: 如何在一次執行中批次處理多個圖表？**  
A: 將上述步驟包在迴圈中，依序載入每個檔案、套用浮水印、儲存，並在處理下一個檔案前關閉 `Watermarker`。

**最後更新：** 2026-04-04  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

## 資源
- [文件說明](https://docs.groupdocs.com/watermark/java/)
- [API 參考文件](https://reference.groupdocs.com/watermark/java)
- [下載最新版本](https://releases.groupdocs.com/watermark/java/)
- [GitHub 程式庫](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/watermark/10)