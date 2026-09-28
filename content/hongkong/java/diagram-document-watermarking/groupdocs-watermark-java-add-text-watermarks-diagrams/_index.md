---
date: '2025-12-19'
description: 學習如何使用 GroupDocs.Watermark for Java 為圖表添加文字浮水印。有效保護您的視覺內容，確保文件完整性。
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: 使用 GroupDocs.Watermark for Java 為圖表添加文字水印 – 完整指南
type: docs
url: /zh-hant/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# 使用 GroupDocs.Watermark for Java 為圖表添加文字浮水印：完整指南

## 介紹
保護圖表文件免於未授權使用至關重要，而 **添加文字浮水印** 提供了一個簡單且有效的解決方案。在本教學中，你將學會如何載入圖表檔案、建立可自訂的文字浮水印，並使用 **GroupDocs.Watermark for Java** 將其套用於背景頁面或特定圖形。完成本指南後，你將能在保持原始外觀的同時，保護你的視覺資產。

### 快速回答
- **「添加文字浮水印」是什麼意思？**  
  意指在文件中嵌入半透明的文字覆蓋層，以表明所有權或機密性。  
- **哪個函式庫支援圖表浮水印？**  
  GroupDocs.Watermark for Java 原生支援圖表格式（例如 Visio、VSDX）。  
- **我需要授權嗎？**  
  生產環境使用需取得臨時或正式授權；亦提供免費試用版供評估。  
- **我可以將浮水印放在背景頁面上嗎？**  
  可以 – 使用 `DiagramWatermarkPlacementType.SeparateBackgrounds` 選項即可實現 **背景頁面浮水印**。  
- **程式碼是否相容於 Java 8+？**  
  完全相容 – 此函式庫支援 JDK 8 及更新版本。

## 什麼是圖表的文字浮水印？
文字浮水印是一段可讀的文字（通常為半透明），會渲染在圖表元素的上方或下方。它可用於品牌宣傳、版權保護，或標示機密草稿。

## 為什麼使用 GroupDocs.Watermark for Java？
- **廣泛的格式支援** – 可處理 Visio、VSDX 以及其他多種圖表類型。  
- **精細的放置控制** – 可選擇前景、背景或特定圖形的浮水印。  
- **簡易的 API** – 只需幾行 Java 程式碼即可建立並套用浮水印。  

## 前置條件
- **GroupDocs.Watermark for Java**（v24.11 或更新版本）  
- **Java Development Kit (JDK)** 8 或以上  
- Maven（或手動加入 JAR）  

## 設定 GroupDocs.Watermark for Java
### Maven 設定
將以下設定加入你的 `pom.xml` 檔案：

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
從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權
- **免費試用** – 無需授權金鑰即可評估全部功能。  
- **臨時授權** – 開發期間使用，可解鎖完整功能。  
- **購買正式授權** – 用於商業專案的正式授權。  

### 基本初始化與設定
確保你的 Java 類別中已匯入以下程式碼：

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## 步驟實作

### 步驟 1：載入圖表文件
首先，指向圖表檔案並初始化載入選項。

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*說明*：`DiagramLoadOptions` 讓你在加入浮水印前控制圖表的解析方式。

### 步驟 2：建立文字浮水印
接著建立浮水印文字並定義其視覺樣式。

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*說明*：此程式碼會建立一個文字浮水印 **「Test watermark 1」**，使用 Calibri 字型，字型大小 19。

### 步驟 3：配置放置方式 – 背景頁面浮水印
選擇浮水印的顯示位置。若要建立 **背景頁面浮水印**，使用以下選項：

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*說明*：`DiagramShapeWatermarkOptions` 控制精確位置。將放置類型設定為 `SeparateBackgrounds` 後，浮水印會加到圖表的每個背景頁面。

### 步驟 4：套用浮水印並儲存
最後，將浮水印加入文件、儲存結果，並釋放資源。

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*說明*：`add` 方法使用配置好的 `textWatermark` 及放置選項，然後將修改後的圖表儲存至 `outputPath`。

## 實務應用
- **智慧財產保護** – 防止競爭對手重複使用專有圖表。  
- **品牌強化** – 在所有匯出圖表上嵌入公司名稱或標誌作為文字浮水印。  
- **法律文件** – 為工程圖紙的機密草稿加上標記。  
- **學術提交** – 在圖表上附加學號或課程代碼，以便追蹤抄襲情況。

## 效能考量
- **記憶體管理** – 關閉 `Watermarker` 實例 (`watermarker.close()`) 以釋放原生資源，尤其在處理大型檔案時。  
- **批次處理** – 迭代處理多個圖表路徑時，盡可能重複使用同一個 `Watermarker` 實例，以降低開銷。  

## 常見問題與解決方案
| 問題 | 解決方案 |
|------|----------|
| **大型圖表導致 OutOfMemoryError** | 增加 JVM 堆積大小（`-Xmx2g`），並一次處理單一檔案。 |
| **浮水印未顯示** | 確認浮水印顏色具備足夠對比度；可透過 `textWatermark.setOpacity(0.5)` 設定不透明度。 |
| **不支援的圖表格式** | 確認該格式已列於 GroupDocs.Watermark 支援格式文件中。 |

## 常見問答

**Q: 文字浮水印的最佳字型大小是多少？**  
A: 最適字型大小取決於圖表尺寸；大多數情況下 12‑20 pt 表現良好。

**Q: 我可以自訂浮水印顏色嗎？**  
A: 可以，使用 `textWatermark.setColor(Color.GRAY)`（或任意 `java.awt.Color`）。

**Q: 如何處理大量文件的批次作業？**  
A: 可利用函式庫的批次 API，或撰寫迴圈重複使用 `Watermarker` 物件以降低開銷。

**Q: GroupDocs.Watermark 有什麼限制嗎？**  
A: 此函式庫支援大多數常見圖表格式，但某些專有擴充功能可能無法完整呈現。詳情請參閱 [documentation](https://docs.groupdocs.com/watermark/java/)。

**Q: 若遇到問題該如何取得支援？**  
A: 前往 [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) 尋求社群協助，或直接聯繫 GroupDocs 客服。

## 其他資源
- **文件說明**： [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API 參考**： [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **下載**： [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub 程式庫**： [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **免費支援論壇**： [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **臨時授權**： [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**最後更新：** 2025-12-19  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs