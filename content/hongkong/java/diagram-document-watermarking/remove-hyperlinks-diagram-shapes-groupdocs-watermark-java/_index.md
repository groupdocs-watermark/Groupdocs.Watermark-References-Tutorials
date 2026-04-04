---
date: '2026-04-04'
description: 學習如何使用 GroupDocs.Watermark Java 從圖表形狀中移除連結，確保文件的安全性與清晰度。
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: 如何使用 GroupDocs.Watermark Java 從圖表形狀中移除連結
type: docs
url: /zh-hant/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 從圖表形狀中移除連結

管理數位文件時常需要編輯圖表，特別是當您需要 **如何移除連結** 以提升安全性或清晰度時。在本教學中，您將學習一個簡單、逐步的方式，使用功能強大的 **GroupDocs.Watermark** Java 函式庫，從圖表形狀中移除不需要的超連結。完成後，您將擁有乾淨、無連結的圖表，安全可分享。

## 快速解答
- **「如何移除連結」是什麼意思？** 它指的是移除嵌入於圖表形狀中的超連結物件。  
- **哪個函式庫負責此操作？** GroupDocs.Watermark for Java（版本 24.11 或更新）。  
- **我需要授權嗎？** 免費試用可用於測試；正式環境需有效授權。  
- **我可以一次處理多個檔案嗎？** 可以——將程式碼包在迴圈或批次作業中。  
- **此方法是否限定於特定語言？** 範例使用 Java，但相同概念適用於其他 .NET/Java API。  

## 在圖表編輯中「如何移除連結」是什麼？
移除連結是指在圖表（例如 Visio *.vsdx）中尋找附加於形狀的超連結物件並將其刪除。這可消除可能洩漏敏感資訊或中斷簡報流程的外部 URL。

## 為什麼使用 GroupDocs.Watermark for Java？
- **精確度** – 直接存取形狀物件及其超連結集合。  
- **效能** – 為大型圖表優化，無需將整個文件載入記憶體。  
- **跨格式支援** – 支援多種圖表格式（Visio、Draw.io 等）。  

## 前置條件
- **GroupDocs.Watermark** 函式庫 ≥ 24.11。  
- Maven（或手動加入 JAR）。  
- Java JDK 8 或更新版本。  
- 任何 IDE，例如 IntelliJ IDEA 或 Eclipse。

## 設定 GroupDocs.Watermark for Java
### Maven 設定
將儲存庫與相依性加入您的 `pom.xml`：

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
如果您不想使用 Maven，可從官方網站取得最新的 JAR：  
[GroupDocs.Watermark for Java 版本下載](https://releases.groupdocs.com/watermark/java/).

#### 取得授權步驟
- 先下載免費試用版。  
- 正式環境請從 GroupDocs 入口網站取得臨時或完整授權。

#### 基本初始化與設定
建立指向您圖表所在資料夾的 `Watermarker` 實例：

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 如何從圖表形狀中移除連結
以下是一個簡潔的四步驟流程，示範 **remove hyperlinks java** 的實作。

### 步驟 1：載入圖表檔案
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*為什麼？* 載入檔案可讓您以程式方式存取其頁面、形狀與超連結集合。

### 步驟 2：存取形狀內容
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*為什麼？* 您需要取得可能包含超連結的特定形狀參考。

### 步驟 3：遍歷並移除超連結
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*為什麼？* 反向迴圈可避免在刪除集合項目時產生索引移位問題。

### 步驟 4：儲存與關閉
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*為什麼？* 儲存會將清理後的圖表寫入磁碟，關閉則釋放檔案句柄以避免記憶體洩漏。

## 移除連結的實務應用
1. **安全性** – 移除可能導致網路釣魚或資料外洩的外部 URL。  
2. **合規性** – 確保圖表在分發前符合內部政策。  
3. **簡報清晰度** – 消除不必要的可點擊區域，避免分散觀眾注意力。

## 效能考量
- **迴圈效率** – 使用上述的反向迭代模式。  
- **資源管理** – 優先使用 `try‑with‑resources` 或明確的 `close()` 呼叫。  
- **大型檔案** – 監控 CPU/記憶體；可考慮批次處理頁面。

## 常見問題與解決方案
- **未找到超連結** – 確認圖表實際包含超連結物件；某些格式的儲存方式不同。  
- **IndexOutOfBoundsException** – 移除集合項目時務必使用反向迭代。  
- **授權錯誤** – 確認授權檔正確放置或傳入 `Watermarker` 建構子。

## 常見問答

**Q: 如何處理多頁面上的多個形狀？**  
A: 迭代 `content.getPages()`，再遍歷每頁的 `getShapes()` 集合，對每個形狀套用相同的移除邏輯。

**Q: 我可以依網域而非完整 URL 來篩選連結嗎？**  
A: 可以——將 `contains` 檢查改為搜尋網域字串（例如 `"example.com"`）。

**Q: 有辦法記錄被移除的連結嗎？**  
A: 在迴圈內，於移除前取得 `shape.getHyperlinks().get_Item(i).getAddress()`，並寫入日誌檔案。

**Q: 這能處理嵌入於其他文件中的 PDF 圖表嗎？**  
A: GroupDocs.Watermark 支援多種格式；請確保檔案類型被辨識為圖表（Visio、VDX 等）。

**Q: 批次處理需要什麼授權？**  
A: 任何非試用的高量作業皆需完整的正式授權。

## 結論
您現在已擁有一套完整、可投入生產的 **how to strip links** 方法，使用 GroupDocs.Watermark for Java 從圖表形狀中移除連結。將此整合至文件處理流程，可提升安全性、合規性與視覺品質。

### 後續步驟
- 探索其他操作功能，例如加入浮水印或文字蓋章。  
- 將此例程與檔案監看服務結合，於上傳時自動清理圖表。

---

**最後更新：** 2026-04-04  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

## 資源
- [文件說明](https://docs.groupdocs.com/watermark/java/)
- [API 參考](https://reference.groupdocs.com/watermark/java)
- [下載](https://releases.groupdocs.com/watermark/java/)
- [GitHub 程式庫](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/watermark/10)
- [臨時授權取得](https://purchase.groupdocs.com/temporary-license/)