---
date: '2026-07-30'
description: 了解如何在 Java 中為 GroupDocs.Watermark 設定授權，有效保護文件並高效管理使用情況。
keywords:
- how to set license
- GroupDocs Watermark Java
- metered licensing Java
lastmod: '2026-07-30'
og_description: 如何在 Java 中為 GroupDocs.Watermark 設定授權。本指南將帶您完成 SDK 安裝、取得 metered key
  以及配置授權以保護文件的步驟。
og_image_alt: 'Guide: Set license for GroupDocs Watermark in Java'
og_title: 如何在 Java 中為 GroupDocs Watermark 設定授權
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  headline: How to Set License for GroupDocs Watermark in Java
  type: TechArticle
- description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  name: How to Set License for GroupDocs Watermark in Java
  steps:
  - name: Define the public and private keys
    text: Enter the keys you received after registering for a temporary license. `Metered`
      is the GroupDocs.Watermark class that handles metered licensing and usage tracking.
      *Place your keys in a secure location (environment variables, encrypted config,
      etc.) before using them in code.*
  - name: Create an instance of the Metered class
    text: Instantiate the `Metered` object with your keys. This object will be passed
      to the watermark engine during initialization.
  - name: Set the metered license using the provided keys
    text: Call the `setLicense` method (or the equivalent API call) with your public
      and private keys. Once set, all subsequent watermark operations will be billed
      according to your usage. > **Pro tip:** Keep the keys out of source control.
      Use a secrets manager or encrypted properties file to avoid accidenta
  type: HowTo
- questions:
  - answer: A temporary license is time‑limited and ideal for evaluation, while a
      perpetual license provides unlimited use without recurring fees.
    question: What is the difference between a temporary and a perpetual license?
  - answer: Yes—replace the metered key initialization with a call to `engine.setLicense("path/to/license/file")`.
    question: Can I switch from a metered license to a perpetual one without code
      changes?
  - answer: The SDK falls back to offline mode; watermarking continues but usage won’t
      be reported until connectivity is restored.
    question: What happens if the metered service is unreachable?
  - answer: The SDK can handle files up to 1 GB; larger files should be split or processed
      in streaming mode.
    question: Are there file‑size limits for watermarking?
  - answer: It works on any platform that supports Java 8+, including Windows, Linux,
      and macOS.
    question: Does the metered license work on all operating systems?
  type: FAQPage
tags:
- set license
- GroupDocs Watermark
- Java licensing
- metered license
- document security
title: 如何在 Java 中為 GroupDocs Watermark 設定授權
type: docs
url: /zh-hant/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# 如何在 Java 中為 GroupDocs Watermark 設定授權

## 快速解答

- **什麼是計量授權？** 這是一種基於使用量的授權，會記錄每一次 API 呼叫，讓您只為實際消耗付費。  
- **我需要先取得試用嗎？** 是的，您可以向 GroupDocs 網站申請臨時授權以評估產品。  
- **需要哪個版本的 Java？** Java 8 或更新版本；SDK 為 JDK 8+ 編譯。  
- **我可以之後改為永久授權嗎？** 當然可以，只要將計量金鑰換成永久授權檔案即可。  
- **此設定與 Maven 相容嗎？** 是的，已提供 Maven 坐標以便無縫管理相依性。

## GroupDocs Watermark 的計量授權是什麼？

計量授權是由 GroupDocs 提供的雲端授權，會記錄 SDK 執行的每一次加水印操作。每個 API 呼叫都會在 GroupDocs 的授權伺服器上記錄，讓您能依實際使用量採取即付即用的計費方式。此模式讓開發者即時掌握消耗情況，協助控制成本，同時確保完整功能存取。

## 為什麼在 GroupDocs Watermark 使用計量授權？

GroupDocs.Watermark 支援超過五十種輸入與輸出格式，包括 PDF、DOCX、PPTX 以及各種影像類型，且可在不將整個文件載入記憶體的情況下處理高達 1 GB 的檔案，從而維持效能。使用計量授權只需為實際執行的操作付費，使解決方案能以成本效益的方式擴展，同時保有全部功能的完整存取。

## 前置條件

- **GroupDocs.Watermark for Java** 版本 24.11 或更新。  
- 已安裝並設定 Java Development Kit (JDK) 8 或更新版本。  
- 具備 Maven 或手動 JAR 管理的基本知識。  
- 從 GroupDocs 入口網站取得的臨時或永久授權金鑰。

## 如何在 Java 中為 GroupDocs Watermark 設定計量授權？

載入您的公鑰與私鑰，建立 `Metered` 實例，並套用授權——只需三個簡潔步驟。此方法確保每一次加水印請求都會計入您的帳戶，讓您完整掌握消耗情況。

### 步驟 1：定義公鑰與私鑰

輸入您在註冊臨時授權後收到的金鑰。

`Metered` 是處理計量授權與使用量追蹤的 GroupDocs.Watermark 類別。  
*在程式碼中使用金鑰前，請將金鑰放置於安全位置（環境變數、加密設定檔等）。*

### 步驟 2：建立 Metered 類別的實例

使用您的金鑰實例化 `Metered` 物件。此物件會在初始化時傳遞給水印引擎。

```text
Metered metered = new Metered(System.getenv("GROUPDOCS_PUBLIC_KEY"),
                               System.getenv("GROUPDOCS_PRIVATE_KEY"));
```

### 步驟 3：使用提供的金鑰設定計量授權

呼叫 `setLicense` 方法（或等效的 API 呼叫）並傳入您的公鑰與私鑰。設定完成後，所有後續的加水印操作都會依照您的使用量計費。

```text
WatermarkEngine engine = new WatermarkEngine();
engine.setMeteredLicense(metered);
```

> **專業提示：** 請將金鑰從原始碼管理中排除。使用機密管理服務或加密屬性檔，以避免意外洩漏。

## 設定 GroupDocs.Watermark for Java

### 安裝資訊

使用 Maven 或直接下載 JAR，將 GroupDocs.Watermark 整合至您的專案中。

**Maven 設定：**  
在您的 `pom.xml` 檔案中加入以下設定：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>watermark</artifactId>
    <version>24.11</version>
</dependency>
```

**直接下載：**  
從 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下載最新版本。

### 取得授權

欲解鎖完整功能，請取得免費試用或臨時授權：

- 在 [GroupDocs 網站](https://purchase.groupdocs.com/temporary-license/) 註冊以開始使用。  
- 取得金鑰後，依實作指南將其整合至您的專案中。

### 基本初始化與設定

將 SDK 加入專案後，匯入必要的命名空間，並依上述程式碼片段建立水印引擎實例。

## 疑難排解技巧

- **金鑰無效：** 請再次確認公鑰與私鑰完全相符，任何一個錯字都會導致授權失效。  
- **授權檔案路徑錯誤：** 若使用檔案型授權，請確保檔案路徑為絕對路徑或正確相對於工作目錄解析。  
- **網路問題：** 計量授權需要向外發出 HTTPS 請求；請確認防火牆允許連線至 `api.groupdocs.com`。

## 實務應用

1. **文件安全性：** 為 PDF、Word 文件與影像加入可見或隱形水印，以保護機密企業資料。  
2. **使用量追蹤：** 產生每日加水印文件數量的報告，協助預算編列與合規性。  
3. **CMS 整合：** 在內容發布工作流程中自動插入水印，授權會自動套用。

## 效能考量

**效能最佳化：**  
- 僅在必要時加水印；對已受保護的檔案跳過處理。  
- 大量批次時，重複使用相同的 `WatermarkEngine` 實例，以避免重複初始化的開銷。  

**最佳實踐：**  
- 處理數百頁 PDF 時監控 JVM 堆積使用情況；若記憶體成為瓶頸，請考慮使用串流 API。  
- 將日誌等級設為 `INFO`，以捕捉授權呼叫，同時避免過多輸出至主控台。

## 結論

本指南說明了在 Java 中為 GroupDocs.Watermark **設定授權** 的方法，從 Maven 安裝到計量金鑰配置。依循步驟即可取得精確的使用量追蹤、彈性的計費方式與強大的文件保護，且不影響效能。

**後續步驟：**  
- 嘗試不同的水印樣式（文字、影像、斜線）。  
- 探索進階功能，例如依使用者角色套用條件式水印。  
- 檢視 GroupDocs 分析儀表板，以監控消耗趨勢。

準備好保護您的文件了嗎？立即實作此解決方案，讓您安心資產受到保護，且授權成本透明可見。

## 常見問題

**Q: 臨時授權與永久授權有何差異？**  
A: 臨時授權有時間限制，適合評估使用；永久授權則提供無限使用，且無需定期付費。

**Q: 我可以在不更改程式碼的情況下，從計量授權切換為永久授權嗎？**  
A: 可以——只需將計量金鑰的初始化改為呼叫 `engine.setLicense("path/to/license/file")`。

**Q: 若無法連線至計量服務會怎樣？**  
A: SDK 會切換至離線模式；加水印仍會繼續，但使用量會等到連線恢復後再回報。

**Q: 加水印是否有檔案大小限制？**  
A: SDK 可處理最高 1 GB 的檔案；較大的檔案應分割或以串流模式處理。

**Q: 計量授權能在所有作業系統上使用嗎？**  
A: 只要支援 Java 8+，皆可使用，包括 Windows、Linux 與 macOS。

---

**最後更新：** 2026-07-30  
**測試環境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

資源

- [文件說明](https://docs.groupdocs.com/watermark/java/)
- [API 參考](httpshttps://reference.groupdocs.com/watermark/java)
- [下載](https://releases.groupdocs.com/watermark/java/)
- [GitHub 程式庫](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/watermark/10)
- [臨時授權取得](https://purchase.groupdocs.com/temporary-license/)

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

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```

```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```

```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```

## 相關教學

- [GroupDocs.Watermark for Java 授權與設定教學](/watermark/java/licensing-configuration/)
- [如何在 Java 中設定 GroupDocs.Watermark 授權：完整指南](/watermark/java/licensing-configuration/groupdocs-watermark-licensing-java-guide/)
- [Java 加水印指南：使用 GroupDocs.Watermark API 保護文件](/watermark/java/getting-started/java-watermark-groupdocs-guide/)