---
date: '2026-10-27'
description: 了解如何使用 GroupDocs.Watermark for Java 从 diagram 文件中删除 text watermark 并高效
  detect image watermark。面向开发者的逐步指南。
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: 使用 GroupDocs.Watermark for Java 从 diagram 文件中删除 text watermark。了解如何
  detect image watermark、search 并使用 code snippets remove watermarks。
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: 快速使用 Java 删除 diagram 文件中的 text watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: 如何使用 Java 删除图表中的 text watermark
type: docs
url: /zh/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# 如何使用 Java 删除图表中的文字水印

在文档中管理水印对于保护知识产权和维护文档完整性至关重要。在本教程中，您将学习如何使用 GroupDocs.Watermark for Java 从 `.vsdx` 等图表文件中**删除文字水印**，以及在需要时**检测图像水印**。无论是构建企业级文档流水线还是自动化简单的批处理任务，这些技术都能让您对图表水印进行细粒度控制。

**您将学习的内容**
- 设置 GroupDocs.Watermark 库
- 使用特定选项加载图表文档
- 搜索并删除文字水印
- 检测图像水印并将其移除
- 大规模处理的最佳实践技巧

准备好深入学习了吗？让我们先准备好您的环境。

## 快速答案
- **我能一次性删除文字和图像水印吗？** 是的 – 将 `TextSearchCriteria` 和 `ImageDctHashSearchCriteria` 与 `or()` 条件组合使用。  
- **库是否会将整个图表加载到内存中？** 不会 – 它会流式读取页面，允许文件大小最高达 500 MB 而不会占用全部内存。  
- **支持哪些图表格式？** 超过 20 种格式，包括 `.vsdx`、`.vdx` 和 `.drawio`。  
- **生产环境是否需要许可证？** 需要有效的 GroupDocs.Watermark 许可证才能用于非试用。  
- **我可以在 CI/CD 流水线中运行它吗？** 当然可以 – API 是无头的，支持 Windows、Linux 和 macOS。

## 什么是删除文字水印？
删除文字水印是指移除文档中添加的基于文本的覆盖对象，这些对象用于标示所有权、机密性或草稿状态。在 GroupDocs.Watermark 中，此操作通过使用搜索条件定位水印对象，然后对得到的集合调用 `clear()` 来完成。

## 为什么要检测图像水印？
检测图像水印可以帮助您识别嵌入到图表中的图形徽标或印章。这对于合规检查、品牌保护以及自动化内容审核至关重要。GroupDocs.Watermark 使用感知哈希（DCT）快速且高效地比较图像。

## 前提条件
在开始之前，请确保您具备：
1. **Java Development Kit (JDK)** 8 或更高版本。  
2. **IDE** – IntelliJ IDEA、Eclipse 或您喜欢的任何编辑器。  
3. **GroupDocs.Watermark for Java** – 必须将库的 JAR 放入类路径。

### 必需的库和依赖项
您可以通过 Maven 添加该库，或手动下载 JAR。

#### Maven 设置
Add the following configuration to your `pom.xml` file:

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

#### 直接下载
或者，从 [GroupDocs.Watermark for Java 发布](https://releases.groupdocs.com/watermark/java/) 下载最新版本。

### 许可证获取
- **免费试用** – 在没有许可证密钥的情况下测试所有功能。  
- **临时许可证** – 请求一个限时密钥用于评估。  
- **购买** – 获取永久或订阅许可证用于生产环境。

## 为 Java 设置 GroupDocs.Watermark
1. **安装库** – 确保 Maven 仓库和依赖项已配置，或将 JAR 文件放入 `libs/` 并添加到项目的构建路径。  
2. **初始化 API** – 创建 `Watermarker` 实例；该对象是加载图表并执行水印操作的入口。

## 如何使用 Java 删除图表中的文字水印
要删除文字水印，使用 `Watermarker` 加载图表，创建匹配水印文本的 `TextSearchCriteria`，获取匹配的 `PossibleWatermarkCollection`，并对其调用 `clear()`。这仅删除指定的文字覆盖层，而保持图表的其他部分不变。

`Watermarker` 类在内存中表示单个文档，并提供加载、搜索和修改水印的方法。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```
- **参数：**  
  - `inputFilePath`：指向您的 `.vsdx` 文件的路径。  
  - `loadOptions`：配置文档的加载方式（例如页面范围、密码）。

## 如何在图表文件中检测图像水印？
检测图像水印的过程包括使用参考图像创建 `ImageDctHashSearchCriteria`，然后使用 `Watermarker` 对图表进行搜索。API 为每个嵌入的图像生成感知哈希，并将其与参考图像比较，返回带有相似度分数的匹配项，以便您识别并移除不需要的徽标或印章。

`ImageDctHashSearchCriteria` 为参考图像生成哈希，并将其与图表中嵌入的图像进行比较，返回带有相似度分数的匹配。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```
- **关键方法：**  
  - `TextSearchCriteria` – 创建针对基于文本的水印的搜索条件。  
  - `PossibleWatermarkCollection` – 保存任何搜索操作的结果。

## 找到水印后如何移除？
一旦识别出水印，您可以通过对搜索返回的 `PossibleWatermarkCollection` 调用 `clear()` 方法来移除它们。此操作会删除水印对象，同时保留图表的其他所有元素，确保原始内容保持完整不变。

`clear()` 会删除集合中的所有水印，同时保留图表的其余内容。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```
- **关键方法：** `clear()` – 删除提供的集合中的所有水印，而不影响其他图表元素。

## 实际应用
1. **企业软件集成** – 将水印管理嵌入以文档为中心的业务应用中，以保护专有图表。  
2. **内容管理系统 (CMS)** – 在发布用户生成的图表前自动检测未经授权的徽标。  
3. **法律文档处理** – 在案件文件工作流的不同阶段添加或删除水印，确保符合保密政策。

## 常见陷阱与故障排除
- **大文件** – 如果遇到 `OutOfMemoryError`，请在 `LoadOptions` 中增加 `maxMemory` 设置。  
- **受密码保护的图表** – 在 `LoadOptions` 中提供密码以打开文件。  
- **缺少图像哈希匹配** – 确保参考图像分辨率足够；低分辨率图像可能产生弱哈希。

## 常见问题

**问：我能同时搜索文字和图像吗？**  
答：可以 – 将 `TextSearchCriteria` 与 `ImageDctHashSearchCriteria` 使用 `or()` 运算符组合，以在一次扫描中定位两种类型。

**问：是否可以在不损坏图表的情况下删除水印？**  
答：完全可以。API 会隔离水印对象并将其移除，保持原始图表结构完整。

**问：GroupDocs.Watermark 是否支持多种图表格式？**  
答：是的 – 支持超过 20 种格式，包括 `.vsdx`、`.vdx`、`.drawio` 和 `.svg`，实现广泛的图表管理。

**问：如何高效处理大量文档？**  
答：使用批处理循环，尽可能复用单个 `Watermarker` 实例，并调优 `LoadOptions` 以流式读取页面，而不是一次性加载整个文件。

**问：我能将水印检测集成到 CI/CD 流水线吗？**  
答：可以 – 该库是无头的，可从 Maven、Gradle 或任何构建脚本调用，自动验证图表资产。

---

**最后更新:** 2026-10-27  
**测试环境:** GroupDocs.Watermark 23.6 for Java  
**作者:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## 相关教程

- [如何使用 GroupDocs.Watermark 在 Java 中为图表添加文字水印](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark for Java 为图表添加水印的指南](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [使用 GroupDocs.Watermark for Java 检索文档信息：一步步指南](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)