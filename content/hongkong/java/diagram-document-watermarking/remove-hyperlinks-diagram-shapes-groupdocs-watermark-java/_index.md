---
date: '2025-12-19'
description: 學習如何使用 GroupDocs.Watermark Java 從圖表形狀中移除超連結，這是 Java 文件安全的重要步驟，同時亦可批次移除超連結。
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: 如何使用 GroupDocs.Watermark Java 從圖表形狀中移除超連結
type: docs
url: /zh-hant/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 從圖表形狀中移除超連結

管理數位文件時常需要編輯圖表，特別是為了安全或清晰度而**移除超連結**。在本教學中，您將學習如何使用 GroupDocs.Watermark for Java 從圖表形狀中**移除超連結**，確保您的檔案保持乾淨、安全且專業。

## 快速解答
- **主要目的為何？** 為了提升文件安全性，從圖表形狀中剔除不需要的超連結。  
- **使用哪個函式庫？** GroupDocs.Watermark for Java（版本 24.11 或更新）。  
- **需要授權嗎？** 試用版可用於測試；正式環境需使用有效授權。  
- **可以一次處理多個檔案嗎？** 可以——將相同邏輯放入批次迴圈即可。  
- **Java 8 足夠嗎？** 支援 Java 8 以上；建議使用較新版本的 JDK。

## 在圖表情境下，什麼是「移除超連結」？
移除超連結指的是刪除附加在圖表檔案（例如 Visio *.vsdx）內形狀上的 URL 參考。此操作可防止意外導向外部網站，並協助符合合規或內部安全政策。

## 為何使用 GroupDocs.Watermark Java 來執行此任務？
- **強大的格式支援** – 可處理多種圖表類型。  
- **細緻的 API** – 讓您能針對單一形狀及其超連結集合操作。  
- **效能最佳化** – 適用於單一檔案與批次處理。  

## 前置條件
- **GroupDocs.Watermark** 函式庫版本 24.11 或更新。  
- Maven 或直接下載 JAR（請參考以下設定步驟）。  
- Java Development Kit（JDK 8 或更新）以及 IntelliJ IDEA 或 Eclipse 等 IDE。  

## 設定 GroupDocs.Watermark for Java
首先，透過 Maven 或下載 JAR 將函式庫加入專案中。

### Maven 設定
將以下設定加入您的 `pom.xml`：

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
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

#### 取得授權步驟
- 先使用免費試用版評估 API。  
- 正式環境請從 GroupDocs 入口網站取得臨時或正式授權。  

#### 基本初始化與設定
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 如何從圖表形狀中移除超連結
以下為逐步說明，帶您完成載入圖表、定位形狀，並剔除不需要的超連結。

### 步驟 1：載入圖表檔案
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*為什麼？* 載入檔案後即可以程式方式存取其內部結構。

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
*為什麼？* 反向迴圈可避免在刪除集合項目時產生索引錯誤。

### 步驟 4：儲存並關閉
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*為什麼？* 儲存變更並釋放資源可防止記憶體洩漏與檔案被鎖定。

## 批次移除超連結（進階案例）
若需一次清理多個圖表，可將上述邏輯包在遍歷檔案路徑清單的迴圈中。API 呼叫相同，只需在每次迭代時更改輸入與輸出目錄。此方式符合大型文件庫的**批次移除超連結**需求。

## 實務應用
在多種實務情境中，移除圖表形狀的超連結皆有其好處：

1. **安全目的** – 防止外部連結可能使您的網路遭受釣魚或惡意軟體攻擊。  
2. **合規** – 符合公司政策，禁止在共享文件中包含外部 URL。  
3. **清晰度** – 產生更乾淨的簡報，避免不必要或分散注意力的超連結。  

## 效能考量
### 效能最佳化
- 使用上述的反向迭代模式，以提升迴圈效能。  
- 完成後立即關閉 `Watermarker` 物件以釋放記憶體。

### 資源使用指引
- 處理大型圖表時監控 CPU 與記憶體使用情況。  
- 大量作業時，考慮以串流方式處理檔案，而非一次全部載入。

### Java 記憶體管理最佳實踐
- 避免在緊密迴圈內建立物件。  
- 在適用情況下使用 try‑with‑resources 以自動清理。

## 常見問題
1. **如何處理多個形狀？**  
   迭代所有頁面及其形狀，對每個形狀套用相同的超連結移除邏輯。  

2. **此流程能否自動化處理大量圖表？**  
   可以——將程式碼嵌入批次處理例行或與文件管理系統整合。  

3. **如果只想從特定頁面移除超連結該怎麼做？**  
   透過索引取得目標頁面（`content.getPages().get_Item(pageIndex)`），僅針對該頁面的形狀執行。  

4. **正式使用 GroupDocs.Watermark 是否需要授權？**  
   試用期結束後需購買有效的商業授權。  

5. **此方法能否支援其他圖表格式？**  
   GroupDocs.Watermark 支援多種圖表類型，請於官方文件確認相容性。  

**其他問答**

**問：** *能否記錄被移除的超連結？*  
**答：** 可以——在呼叫 `removeAt(i)` 前，取得 `shape.getHyperlinks().get_Item(i).getAddress()`，並寫入日誌檔案。

**問：** *移除超連結會影響形狀的視覺外觀嗎？*  
**答：** 不會。形狀的幾何形狀保持不變，僅移除連結的中繼資料。

**問：** *移除後需要重新套用樣式嗎？*  
**答：** 通常不需要。移除超連結不會改變填色、線條或文字樣式。

## 結論
現在您已掌握使用 GroupDocs.Watermark for Java 從圖表形狀中**移除超連結**的完整、可投入生產的做法。依照上述步驟，您可以保護圖表安全、符合政策，並讓文件保持精緻。

**資源**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  
