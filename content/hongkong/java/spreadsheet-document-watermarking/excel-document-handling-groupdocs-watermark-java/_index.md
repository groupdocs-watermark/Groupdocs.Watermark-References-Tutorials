---
date: '2026-04-01'
description: 學習如何使用 GroupDocs.Watermark for Java 為 Excel 檔案加上浮水印。本教學涵蓋設定、載入、從 Excel
  中提取圖片，以及實務應用案例。
keywords:
- how to watermark excel
- extract images from excel
- GroupDocs.Watermark Java
- Excel document handling
title: 如何使用 GroupDocs.Watermark Java 為 Excel 文件加上浮水印
type: docs
url: /zh-hant/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 為 Excel 文件添加水印

## 簡介
在本指南中，您將學習 **如何為 Excel** 檔案使用 GroupDocs.Watermark Java 程式庫添加水印。有效管理與處理 Excel 文件對於水印應用或內容提取等任務至關重要。本教學示範如何在 Java 中利用 **GroupDocs.Watermark** 程式庫簡化這些流程。

## 快速回答
- **什麼程式庫可以用來為 Excel 添加水印？** GroupDocs.Watermark for Java.  
- **我可以使用相同的 API 從 Excel 中提取圖像嗎？** 是 – 您可以直接讀取形狀圖像。  
- **生產環境需要授權嗎？** 需要商業授權；提供免費試用版。  
- **支援哪個 Java 版本？** JDK 8 或更高。  
- **Maven 是唯一添加此程式庫的方式嗎？** 不是，您也可以手動下載 JAR。

## 什麼是「如何為 Excel 添加水印」？
為 Excel 添加水印是指以程式方式在 Excel 活頁簿上加入文字、圖像或形狀的覆蓋層，使水印在每一張列印或檢視的工作表上顯示。這可保護智慧財產權並傳達文件狀態（例如草稿、機密）。

## 為什麼要使用 GroupDocs.Watermark 處理 Excel？
- **功能完整的 API** – 支援 .xlsx、.xls 以及更舊的格式。  
- **無需 Microsoft Office 依賴** – 可在任何伺服器端 Java 環境中執行。  
- **內建形狀處理** – 讓您讀取、修改或提取 Excel 工作表中的圖像。  
- **效能優化** – 以最小記憶體佔用處理大型活頁簿。

## 先決條件
- 已安裝 JDK 8 或更新版本。  
- Maven（或手動 JAR 處理）用於相依管理。  
- 基本的 Java 程式設計知識。  

### 所需程式庫與相依性
在您的專案中加入 GroupDocs.Watermark 作為相依性。您可以透過 Maven 或直接下載：

**Maven**
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
**直接下載**  
或者，從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 環境設定需求
- 確保已安裝並配置 JDK 8 或更高版本。  
- 如果您偏好相依管理，請設定 Maven。

### 知識先決條件
- 對 Java 程式設計的基本了解。  
- 熟悉 Java 中的檔案處理。

## 設定 GroupDocs.Watermark for Java
首先，您必須透過 Maven 或從官方網站直接下載來安裝程式庫。GroupDocs 提供免費試用版以測試功能，亦提供授權供延伸使用：
- **Free Trial** – 功能受限，適合評估使用。  
- **Temporary License** – 在短期間內解鎖所有功能。  
- **Purchase License** – 商業部署必須購買授權。  

安裝完成後，請如下初始化以處理 Excel 文件：

## 如何為 Excel 添加水印
本節將說明如何載入試算表、提取圖像（或任何形狀），以及為加水印做準備。

### 功能 1：載入與存取試算表內容

#### 步驟 1：為試算表定義載入選項
```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
```
- **目的**: 配置載入試算表時所需的特定選項。

#### 步驟 2：使用文件路徑初始化 Watermarker  
將 `"YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx"` 替換為實際檔案路徑。
```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```
- **說明**: 建立 `Watermarker` 實例，讓您完整控制活頁簿。

#### 步驟 3：存取試算表內容
```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```
- **功能**: 取得代表工作表、儲存格與形狀的完整物件模型。

### 功能 2：從 Excel（形狀）提取圖像  

#### Overview
Excel 將圖片、圖表與文字方塊儲存為 *形狀*。以下程式碼會提取這些形狀，讓您 **從 Excel 提取圖像** 或在套用水印前檢查其屬性。

#### 步驟 4：遍歷每個工作表
```java
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
```
- **目的**: 迭代所有工作表以存取個別形狀。

#### 步驟 5：遍歷工作表內的每個形狀
```java
for (SpreadsheetShape shape : worksheet.getShapes()) {
    // Display various properties of the shape
    System.out.println(shape.getAutoShapeType());
    System.out.println(shape.getMsoDrawingType());
    System.out.println(shape.getText());

    if (shape.getImage() != null) {
        System.out.println(shape.getImage().getWidth());
        System.out.println(shape.getImage().getHeight());
        System.out.println(shape.getImage().getBytes().length);
    }

    // Display other properties of the shape
    System.out.println(shape.getId());
    System.out.println(shape.getAlternativeText());
    System.out.println(shape.getX());
    System.out.println(shape.getY());
    System.out.println(shape.getWidth());
    System.out.println(shape.getHeight());
    System.out.println(shape.getRotateAngle());
    System.out.println(shape.isWordArt());
    System.out.println(shape.getName());
}
```
- **說明**: 提取詳細的形狀資訊，包括類型、文字內容以及（若有）圖像屬性。此處可 **從 Excel 提取圖像** 以進一步處理或存檔。

#### 步驟 6：關閉 Watermarker 實例
```java
watermarker.close();
```
- **重要性**: 在操作完成後關閉 `Watermarker` 實例以釋放資源。

## 實務應用
這些功能可應用於實際情境：

1. **Document Automation** – 自動提取並處理 Excel 報告中的資料，以簡化工作流程。  
2. **Data Integrity Checks** – 驗證財務試算表中的形狀與嵌入圖像以符合合規要求。  
3. **Integration with BI Tools** – 將提取的形狀資料輸入商業智慧平台，以獲得更豐富的分析。  

## 效能考量
處理大型 Excel 檔案時：

- 僅處理必要的工作表或形狀，以降低記憶體使用量。  
- 若僅需 **從 Excel 提取圖像**，可跳過儲存格與公式。  
- 在實際負載條件下測試，並對程式碼進行效能分析以找出瓶頸。

## 結論
透過精通 GroupDocs.Watermark for Java 的這些功能，您可以高效地 **為 Excel 添加水印** 活頁簿、提取嵌入圖像，並將 Excel 處理整合至更大的自動化流程中。探索其他功能，如加入文字水印、旋轉水印，或根據工作表內容有條件地套用水印。

### 下一步
- 深入探索水印 API，以加入自訂文字或圖像水印。  
- 結合形狀提取與 OCR，讀取圖片內的文字。  
- 探索適用於 PDF、Word 與影像格式的 GroupDocs SDK，構建統一的文件處理解決方案。

## 常見問答
1. **什麼是 GroupDocs.Watermark？**  
   - 一個強大的 Java 程式庫，用於在文件中處理水印及其他內容。  
2. **我可以將 GroupDocs.Watermark 用於其他檔案類型嗎？**  
   - 是的，支援 PDF、影像、Word 檔等。  
3. **如何排除常見問題？**  
   - 查看官方 [GroupDocs forums](https://forum.groupdocs.com/c/watermark/10) 取得支援或參考文件。  
4. **使用 GroupDocs.Watermark 的最佳實踐是什麼？**  
   - 總是關閉 `Watermarker` 實例、僅處理必要的工作表，並在處理大型檔案時監控記憶體使用。  
5. **在哪裡可以找到更多範例？**  
   - [GitHub repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) 提供大量程式碼範例與專案。

## 常見問題

**Q: 如何為 Excel 活頁簿的每個工作表添加文字水印？**  
A: 載入活頁簿後，建立 `TextWatermark` 物件，並對每個工作表呼叫 `watermarker.add(watermark, new SpreadsheetWatermarkOptions())`。

**Q: 我可以只從 Excel 檔案中提取 PNG 圖像嗎？**  
A: 可以。處理前先檢查 `shape.getImage().getBytes()`，並透過 `shape.getImage().getImageFormat()` 判斷圖像格式。

**Q: 是否能只對包含特定關鍵字的工作表套用水印？**  
A: 完全可以。遍歷 `content.getWorksheets()`，檢查儲存格值，並在符合條件的工作表上有條件呼叫 `watermarker.add(...)`。

**Q: 程式庫是否支援受密碼保護的 Excel 檔案？**  
A: 支援。於建立 `Watermarker` 前，使用 `SpreadsheetLoadOptions` 的 `setPassword("yourPassword")` 設定密碼。

**Q: 本教學使用的 GroupDocs.Watermark 版本為何？**  
A: 範例針對 GroupDocs.Watermark **24.11**。

## 資源
- **文件**: [GroupDocs Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API 參考**: [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **下載**: [Latest Release](https://releases.groupdocs.com/watermark/java/)

---

**最後更新：** 2026-04-01  
**測試版本：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}