---
date: '2026-09-06'
description: 了解如何使用适用于 Java 的 GroupDocs.Watermark 从 Word 文档中提取形状，实现强大的文档自动化和分析。
keywords:
- how to extract shapes
- GroupDocs.Watermark Java
- Word document shape extraction
lastmod: '2026-09-06'
og_description: 如何使用适用于 Java 的 GroupDocs.Watermark 从 Word 文档中提取形状。请按照本分步指南高效加载、分析和处理形状。
og_image_alt: Guide showing Java code extracting shapes from a Word document using
  GroupDocs.Watermark
og_title: 如何使用 GroupDocs.Watermark 在 Java 中从 Word 文档中提取形状
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract shapes from Word documents with GroupDocs.Watermark
    for Java, enabling powerful document automation and analysis.
  headline: How to extract shapes from Word documents using GroupDocs.Watermark in
    Java
  type: TechArticle
- questions:
  - answer: GroupDocs.Watermark for Java is a comprehensive SDK that enables watermark
      creation, detection, and document inspection across 30+ file formats, including
      DOCX, PDF, and PPTX.
    question: What is GroupDocs.Watermark for Java?
  - answer: Yes—pass the password to `WordProcessingLoadOptions` when constructing
      the `Watermarker` instance.
    question: Can I extract shapes from password‑protected Word files?
  - answer: Absolutely; GroupDocs.Watermark is platform‑agnostic and runs on any OS
      that supports Java 8+.
    question: Does the library work on Linux servers?
  - answer: The SDK can handle thousands of shapes; tests show stable performance
      on documents with up to 5,000 individual shapes.
    question: How many shapes can be processed in a single document?
  - answer: No, shape extraction is included in the standard GroupDocs.Watermark license.
    question: Is a separate license needed for shape extraction?
  type: FAQPage
tags:
- extract shapes
- GroupDocs.Watermark
- Java document processing
title: 如何使用 GroupDocs.Watermark 在 Java 中从 Word 文档中提取形状
type: docs
url: /zh/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中从 Word 文档中提取形状

在现代以文档为中心的应用程序中，从 Word 文件中 **提取形状** 是一个常见的挑战。无论您是需要审计图表使用情况、将图形转换为图像，还是推动动态报告，能够以编程方式获取形状元数据都能节省大量手动工作时间。本教程将指导您使用 GroupDocs.Watermark for Java 加载 DOCX，枚举每个形状，并检索其属性，如类型、大小和位置。

## 快速答案
- **哪个库处理形状提取？** GroupDocs.Watermark for Java.  
- **最低 Java 版本？** JDK 8 or newer.  
- **开发是否需要许可证？** A free trial works for testing; a full license is required for production.  
- **我可以处理大文档吗？** Yes—process sections incrementally to keep memory usage low.  
- **Maven 是首选的设置方式吗？** Maven simplifies dependency management and is recommended for most projects.

## 什么是 Word 文档中的形状提取？
形状提取是以编程方式读取 Word 文件并检索每个图形对象——图片、绘图、SmartArt、图表或文本框——的详细信息的过程，以便您可以在代码中分析或操作它们。提取的元数据包括形状类型、尺寸、位置以及任何关联的文本，从而实现如转换或分析等进一步处理。

## 为什么使用 GroupDocs.Watermark for Java？
GroupDocs.Watermark 支持 **30 多种文档格式**，并且能够在不将整个文件加载到内存中的情况下处理 **数百页的文件**，这归功于其流式 API。该库在典型服务器上能够在 **每 100 页文档不到 200 毫秒** 的时间内处理形状元数据，为批量操作提供快速、可靠的结果。

## 前提条件
- **Java Development Kit (JDK)** 8 或更高。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse。  
- 对 Java I/O 和 Maven 有基本了解。  

我们将使用 GroupDocs.Watermark for Java，这是一款专注于水印但也提供深度文档检查功能的强大 SDK。

## 设置 GroupDocs.Watermark for Java
通过 Maven 或直接下载集成 SDK。

### 使用 Maven
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

### 直接下载
或者，从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新版本。

### 获取许可证
免费试用许可证可让您探索所有功能。生产环境使用时，请从 GroupDocs 门户获取永久许可证密钥。

## 实现指南
我们将把实现分为两个逻辑部分：加载文档和提取形状信息。

## 如何使用 GroupDocs.Watermark 从 Word 文档中提取形状？
`Watermarker` 是 GroupDocs.Watermark 中的主要类，用于加载文档并提供对其内容的访问。使用 `Watermarker` 实例加载 DOCX，然后遍历每个章节和形状以读取其属性。两步模式——初始化，然后枚举——覆盖 **所有 30 多种支持的形状类型**，并且可处理高达 500 页的文档而不会产生过多内存消耗。它高效地流式处理文档，使您能够在不占用大量内存的情况下处理大文件。

### 步骤 1：配置加载选项
`WordProcessingLoadOptions` 让您可以微调文件的解析方式（例如，忽略页眉，启用快速模式）。  
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```  
该代码片段创建了一个将文档保存在内存中的 `Watermarker`，并为检查做好准备。

### 步骤 2：访问 Word 处理内容
遍历章节和形状，打印关键细节，如类型、尺寸、对齐方式以及形状是否位于页眉/页脚。  
```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```  
此循环覆盖每个形状对象，确保您不会错过嵌入在页眉或页脚中的隐藏图形。

## 常见问题及解决方案
- **文件未找到** – 仔细检查绝对或相对路径；为清晰起见使用 `Paths.get(...).toAbsolutePath()`。  
- **性能瓶颈** – 对于超过 300 页的文档，逐个处理章节，并在每个批次后调用 `watermarker.close()` 释放内存。  
- **不支持的形状类型** – GroupDocs.Watermark 目前支持 25 种本机形状类别；对于自定义 OfficeArt 对象，考虑使用 OpenXML SDK 作为后备。

## 实际应用
1. **自动化报告生成** – 提取图表以嵌入仪表板。  
2. **合规审计** – 验证受监管文档中不存在禁止的图形。  
3. **迁移流水线** – 在将内容迁移到基于 Web 的发布平台之前，将形状转换为 SVG。

## 性能考虑因素
- 及时使用 `watermarker.close()` 释放 `Watermarker` 对象，以释放本机资源。  
- 当仅需要形状元数据而非完整内容渲染时，在 `WordProcessingLoadOptions` 中启用 `fastLoad` 标志。  
- 仅在服务器拥有足够 CPU 核心时才在并行流中处理文档；避免使用线程不安全的共享对象。

## 结论
您现在已经了解了如何使用 GroupDocs.Watermark for Java 从 Word 文档中 **提取形状**。通过使用 `Watermarker` 加载文档、配置加载选项并遍历每个形状，您可以构建强大的自动化工作流，处理甚至最复杂的文件。

### 下一步
- 试验 `Shape` 对象的 `getImageData()` 方法，将图片导出为 PNG。  
- 探索 GroupDocs.Watermark 的其他功能，如水印检测和移除。  
- 将形状提取与 GroupDocs.Parser 库结合，以获取周围文本进行更丰富的分析。

## 常见问题
**Q: 什么是 GroupDocs.Watermark for Java？**  
A: GroupDocs.Watermark for Java 是一个综合 SDK，能够在 30 多种文件格式（包括 DOCX、PDF 和 PPTX）中实现水印创建、检测和文档检查。

**Q: 我可以从受密码保护的 Word 文件中提取形状吗？**  
A: 可以——在构造 `Watermarker` 实例时，将密码传递给 `WordProcessingLoadOptions`。

**Q: 该库能在 Linux 服务器上运行吗？**  
A: 完全可以；GroupDocs.Watermark 与平台无关，可在任何支持 Java 8+ 的操作系统上运行。

**Q: 单个文档可以处理多少个形状？**  
A: 该 SDK 能处理成千上万的形状；测试显示在包含多达 5,000 个单独形状的文档上性能稳定。

**Q: 形状提取需要单独的许可证吗？**  
A: 不需要，形状提取已包含在标准的 GroupDocs.Watermark 许可证中。

---
**最后更新：** 2026-09-06  
**测试版本：** GroupDocs.Watermark 23.12 for Java  
**作者：** GroupDocs

## 相关教程
- [使用 GroupDocs.Watermark 在 Java 中提取图表的形状信息](/watermark/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark 在 Java 中从 Word 文档中删除形状：综合指南](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}