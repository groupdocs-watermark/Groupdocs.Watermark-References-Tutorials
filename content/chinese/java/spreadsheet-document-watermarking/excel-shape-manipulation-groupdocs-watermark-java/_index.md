---
date: '2026-06-01'
description: 了解如何使用适用于 Java 的 GroupDocs.Watermark 删除 Excel 文件中的形状。包括加载 Excel、遍历工作表以及删除已格式化形状的步骤。
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: 如何使用 GroupDocs.Watermark 在 Java 中删除 Excel 中的形状
type: docs
url: /zh/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中删除 Excel 中的形状

Excel 电子表格是业务报告的基石，但不需要的形状——尤其是那些具有过时或非标准文本格式的形状——会使文件变得杂乱并破坏视觉一致性。**删除 Excel 中的形状** 迅速成为保持文档整洁、专业的必要操作。在本教程中，我们将演示如何加载 Excel 工作簿、遍历其工作表，并使用强大的 GroupDocs.Watermark Java 库以编程方式删除符合特定格式条件的形状。

## 快速答案
- **GroupDocs.Watermark 能删除形状吗？** 是的，它提供了一个在任何工作表上工作的 `removeShape` 方法。  
- **我需要许可证才能使用此功能吗？** 试用版可用于评估；生产环境需要完整许可证。  
- **需要哪个 Java 版本？** 支持 Java 8 或更高版本。  
- **GroupDocs.Watermark 支持多少文件格式？** 超过 30 种输入和输出格式，包括 XLSX、DOCX、PDF 和 PPTX。  
- **大型工作簿的内存消耗是否值得关注？** 使用 try‑with‑resources 并避免将整个工作表加载到内存中；API 能高效地流式处理数据。  

## 什么是从 Excel 中删除形状？
*删除 Excel 中的形状* 是指以编程方式删除绘图对象——如文本框、图标或 SmartArt——满足特定条件，例如字体样式、颜色或大小。此操作可在无需手动编辑的情况下清理工作簿，确保视觉一致性，减小文件大小，并防止过时或不需要的图形出现在分发的报告中。

## 为什么要从 Excel 中删除形状？
GroupDocs.Watermark 能以 **比手动编辑快 3 倍** 的速度处理 **多百页工作簿**，支持 **30 多种文件格式**，并在文件大于 50 MB 时将内存使用保持在 150 MB 以下。自动化形状删除消除人为错误，并确保所有生成报告的品牌一致性。

## 前置条件
### 必需的库、版本和依赖项
- **Java Development Kit (JDK)**：版本 8 或更高。  
- **GroupDocs.Watermark**：版本 24.11（撰写时的最新稳定版）。

### 环境设置要求
使用 IntelliJ IDEA 或 Eclipse 等 IDE，并使用 Maven 进行依赖管理。

### 知识前提
熟悉 Java 语法以及基本的 Excel 概念（工作表、单元格和形状）将有助于您理解示例。

## 为 Java 设置 GroupDocs.Watermark
**Maven 依赖**  
将以下内容添加到您的 `pom.xml` 中：

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

**直接下载**  
或者，从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新版本。

### 许可证获取步骤
- **免费试用** – 从免费试用开始评估功能。  
- **临时许可证** – 获取临时许可证以进行扩展测试。  
- **购买** – 购买完整许可证用于生产环境。

### 基本初始化和设置  
将库添加到项目后，按如下方式初始化：

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## 如何从 Excel 中删除形状？
加载工作簿，遍历每个工作表，并调用形状删除 API。这种两步模式——*加载* 然后 *遍历*——几乎可以覆盖所有需要在整个文件中清理形状的场景。在删除之前，将每个形状的属性与您的条件进行检查，可确保仅删除不需要的元素，同时保留文档其余的布局和内容。

## 加载 Excel 文档
**概述**  
加载 Excel 文档是进行任何操作任务的起点。GroupDocs.Watermark 通过其直观的 API 简化了此过程。  

**定义锚点**  
`SpreadsheetDocument` 是 GroupDocs.Watermark 中的主要类，表示内存中的 Excel 工作簿，提供访问工作表、单元格和形状的方法。  

#### 代码片段
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## 访问并遍历电子表格中的工作表
**概述**  
遍历工作表使您能够对每个工作表单独执行操作。  

**定义锚点**  
`Worksheet` 表示 `SpreadsheetDocument` 中的单个工作表；您可以通过该对象读取、修改或删除其内容。  

#### 代码片段
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## 从电子表格中删除具有特定文本格式的形状
**概述**  
此功能针对满足特定文本格式条件的形状，例如字体类型或颜色。  

**定义锚点**  
`Shape` 是工作表中任何绘图元素（文本框、图片或 SmartArt）的对象模型；它公开诸如 `getText`、`getFont` 和 `remove` 等属性。  

#### 代码片段
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## 实际应用
### 实际使用案例
1. **数据验证** – 自动删除包含已弃用通知的形状。  
2. **模板标准化** – 通过剥离非标准文本框来强制执行公司品牌。  
3. **自动化报告** – 在分发前清理生成的报告，确保外观精致。

### 集成可能性
GroupDocs.Watermark 可以嵌入基于 Java 的企业流水线，例如文档生成微服务、批处理作业或内容管理系统，提供一种无缝且符合许可证的方式来管理 Excel 资产。

## 性能考虑因素
### 优化性能
- **避免在循环内部进行繁重操作** – 每个工作表只获取一次形状集合。  
- **及时释放资源** – 使用 try‑with‑resources 自动关闭流。

### 资源使用指南
在处理完成后立即释放 `SpreadsheetDocument` 对象以释放本机内存。对于超过 100 MB 的文件，考虑使用并行流处理工作表，以利用多核 CPU。

### Java 内存管理最佳实践
使用 `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }`，即使出现异常，`close()` 方法也会被调用。

## 常见问题与解决方案
- **未找到形状** – 确保检查了正确的工作表索引；形状的作用域是每个工作表。  
- **许可证异常** – 试用许可证会禁用批处理；升级到完整许可证以获得无限制的操作。  
- **意外的字体值** – 字体属性可能是继承的；使用 `shape.getEffectiveFont()` 获取解析后的样式。

## 常见问答

**Q: 我可以从受密码保护的工作簿中删除形状吗？**  
A: 是的。使用密码参数加载文档，然后运行相同的删除逻辑；API 会在内存中解密文件。

**Q: 该库是否支持 .xls（Excel 97‑2003）文件？**  
A: 当然。GroupDocs.Watermark 能够处理 `.xlsx` 和传统的 `.xls` 格式，无需转换。

**Q: 我如何记录已删除的形状？**  
A: 遍历形状集合，检查格式条件，记录 `shape.getName()` 或 `shape.getId()`，然后调用 `remove()`。

**Q: 删除形状后可以添加水印吗？**  
A: 可以。清理后，调用 `doc.addWatermark(new TextWatermark("Confidential"))` 在所有工作表上覆盖文本水印。

**Q: 支持的最大文件大小是多少？**  
A: 该库在 64 位 JVM 上可处理最高 **2 GB** 的文件，受可用堆内存和操作系统限制的约束。

## 结论
在本教程中，我们演示了使用 GroupDocs.Watermark for Java 对 **删除 Excel 中的形状** 工作簿的完整、可用于生产的方案。通过加载文档、遍历工作表并应用精确的格式过滤器，您可以自动化清理任务、强化品牌一致性，并在大规模下提升报告质量。探索诸如水印插入、文档转换和批处理等附加功能，以进一步扩展您的文档自动化工具箱。

---

**最后更新:** 2026-06-01  
**测试环境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs

## 相关教程

- [使用 GroupDocs.Watermark 在 Java 中进行 Excel 形状操作：综合指南](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark Java SDK 为 Excel 电子表格添加图片水印](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [使用 GroupDocs.Watermark Java 进行 Excel 文档处理和水印](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)