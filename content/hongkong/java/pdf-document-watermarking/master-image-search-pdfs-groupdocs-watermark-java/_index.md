---
date: '2026-02-26'
description: 學習如何使用 GroupDocs.Watermark for Java 從 PDF 中提取圖像。本指南將帶領您完成圖像提取、將 PDF 圖像另存為
  PNG，以及批量 PDF 圖像提取。
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: 如何使用 GroupDocs.Watermark Java 從 PDF 中提取圖像
type: docs
url: /zh-hant/java/pdf-document-watermarking/master-image-search-pdfs-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark Java 從 PDF 中提取圖像

處理 PDF 檔案時，通常需要 **提取圖像**——無論是重新使用圖形、執行 OCR，或套用自訂浮水印。在本教學中，你將學習如何使用 GroupDocs.Watermark Java 函式庫快速且可靠地 **提取 PDF 中的圖像**。我們將涵蓋從環境設定到將每個找到的圖像儲存為 PNG 檔案的全部步驟，甚至示範如何將解決方案擴展至批次 PDF 圖像提取。

## 快速解答
- **「how to extract images」是什麼意思？** 它指的是以程式方式定位並儲存 PDF 檔案中嵌入的圖形。  
- **哪個 Java 函式庫最適合？** GroupDocs.Watermark 提供簡單的 API 進行圖像搜尋與提取。  
- **我需要授權嗎？** 免費試用可用於開發；商業授權則需於正式環境使用。  
- **可以將圖像儲存為 PNG 嗎？** 可以——使用 `PdfImage` 物件的 `save` 方法。  
- **支援批次處理嗎？** 當然可以，只需使用相同程式碼對多個 PDF 路徑進行迴圈。

## 什麼是 PDF 圖像提取？
圖像提取是指辨識 PDF 文件中所有嵌入的點陣或向量圖形，並將其匯出為單獨的圖像檔案。此功能可用於內容再利用、品質檢查，或將圖像輸入至後續工作流程，例如機器學習管線。

## 為何在 Java 中使用 GroupDocs.Watermark？
- **高準確度** – 引擎會解析 PDF 內部結構以定位附加及內嵌圖像。  
- **簡易 API** – 只需幾行程式碼即可取得 `PdfImage` 物件集合。  
- **效能最佳化** – 即使面對大型、多頁 PDF 亦能順暢運作。  
- **可擴充** – 可依尺寸、格式過濾，或在提取後替換圖像。

## 前置條件
- Java Development Kit (JDK) 8 或更新版本。  
- 已在專案中加入 GroupDocs.Watermark for Java SDK（Maven/Gradle 或手動 JAR）。  
- 一個包含嵌入圖形的範例 PDF。  
- 具備 Java 語法與 IDE 設定的基本認識。

## 匯入必要套件
首先匯入 API 所提供的必要類別：

```java
import com.groupdocs.watermark.domain.PdfSearchableObjects;
import com.groupdocs.watermark.domain.watermarkable.PdfImage;
import com.groupdocs.watermark.domain.watermarkable.WatermarkableImageCollection;
import com.groupdocs.watermark.options.PdfLoadOptions;
import com.groupdocs.watermark.Watermarker;
```

## 步驟說明

### 步驟 1：載入 PDF 文件
在搜尋之前，需要先將 PDF 載入 `Watermarker` 實例中。

```java
// Specify the path to your PDF
String inputPdfPath = "C:\\Docs\\sample.pdf";

// Initialize load options
PdfLoadOptions loadOptions = new PdfLoadOptions();

// Create Watermarker instance
Watermarker watermarker = new Watermarker(inputPdfPath, loadOptions);
```

> **提示：** 請確認檔案路徑正確且應用程式具有讀取權限。

### 步驟 2：設定搜尋嵌入或附加圖像
指示引擎僅搜尋圖像（忽略文字或註解等其他物件）。

```java
// Set to search only for attached images
watermarker.getSearchableObjects().setPdfSearchableObjects(PdfSearchableObjects.AttachedImages);
```

> **為什麼？** 專注於圖像搜尋可縮短處理時間，並返回更精簡的集合。

### 步驟 3：在 PDF 中搜尋圖像
取得符合條件的完整圖像集合。

```java
// Retrieve all images matching the search criteria
WatermarkableImageCollection images = watermarker.getImages();

// Output the number of images found
System.out.println("Number of images found: " + images.getCount());
```

> **專業提示：** 你可以檢查 `images.getCount()` 以決定是否需要進一步處理。

### 步驟 4：處理找到的圖像 ── 將 PDF 圖像儲存為 PNG
現在已取得 `PdfImage` 物件，你可以將每個圖像儲存為單獨的 PNG 檔案——這是常見的 **save pdf images png** 需求。

```java
int index = 1;
for (PdfImage image : images) {
    // Save each image as PNG
    image.save("C:\\Output\\Image_" + index + ".png");
    index++;
}
```

> **常見陷阱：** 若未先建立輸出目錄，會拋出 `IOException`。請事先建立資料夾或在程式碼中加入檢查。

### 步驟 5：關閉資源
務必釋放 `Watermarker` 以釋放原生資源。

```java
watermarker.close();
```

## 如何執行批次 PDF 圖像提取
若需從多個 PDF 提取圖像，可將上述步驟包在迴圈中，遍歷檔案路徑清單。相同的 `Watermarker` 邏輯適用於每個文件，讓你僅需少量額外的 Java 程式碼即可構建 **batch pdf image extraction** 流程。

## 常見問題與解決方案
| 問題 | 解決方案 |
|-------|----------|
| **未找到圖像** | 確認 PDF 確實包含嵌入的圖像。可使用 PDF 檢視器的「匯出圖像」功能加以驗證。 |
| **權限錯誤** | 確保 Java 程序對輸入與輸出資料夾具有讀寫權限。 |
| **大型 PDF 造成 OutOfMemoryError** | 增加 JVM 堆積大小（`-Xmx` 參數），或使用 `PdfLoadOptions.setPageNumber` 逐頁處理 PDF。 |
| **圖像儲存為錯誤格式** | `save` 方法會遵循所提供的檔案副檔名；若需無損輸出，請使用 `.png`。 |

## 常見問答

**Q: 在使用 `extract images pdf java` 時，我可以依尺寸或格式過濾圖像嗎？**  
A: 可以。取得 `WatermarkableImageCollection` 後，檢查每個 `PdfImage` 的屬性（寬度、高度、格式），再於儲存前套用條件判斷。

**Q: 提取後可以替換圖像嗎？**  
A: 當然可以。使用 `watermarker.replace(image, newImage)`，其中 `newImage` 為你從檔案或串流建立的 `PdfImage`。

**Q: 此函式庫支援受密碼保護的 PDF 嗎？**  
A: 支援。在建立 `Watermarker` 前，於 `PdfLoadOptions.setPassword("yourPassword")` 中提供密碼。

**Q: 此方法與使用 PDF 檢視器的「匯出圖像」功能相比如何？**  
A: 透過 GroupDocs.Watermark 以程式方式提取圖像可完全自動化、適用於伺服器環境，且能整合至更大的工作流程，例如批次處理或下游 AI 管線。

**Q: 需要哪個版本的 GroupDocs.Watermark？**  
A: 任何近期版本（2024‑2025 年發行）皆支援上述 API。請查閱官方發行說明以了解細節變更。

## 結論
現在你已掌握使用 GroupDocs.Watermark for Java 從 PDF 檔案 **提取圖像** 的完整、可投入生產的方法。透過載入文件、設定搜尋、取得圖像集合，並將每張圖像儲存為 PNG，你可以自動化重複性工作、支援批次處理，並將圖像提取整合至更大型的 Java 應用程式中。

---

**最後更新：** 2026-02-26  
**測試環境：** GroupDocs.Watermark for Java 23.9（撰寫時的最新版本）  
**作者：** GroupDocs