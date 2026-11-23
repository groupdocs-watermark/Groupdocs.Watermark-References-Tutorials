---
date: 2026-09-16
description: 了解如何使用 GroupDocs.Watermark for Java 为 pdf 添加水印、从各种来源加载文档以及保存加水印的文件。
keywords:
- add watermark to pdf
- load password protected document
- load document from disk
- load document from stream
- java load password protected
lastmod: 2026-09-16
og_description: 使用 GroupDocs.Watermark for Java 快速为 pdf 添加水印。了解加载文档、处理密码以及保存加水印的文件。
og_image_alt: Guide showing how to add watermark to pdf using GroupDocs.Watermark
  Java SDK
og_title: 使用 GroupDocs.Watermark for Java 为 pdf 添加水印
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to add watermark to pdf, load documents from various sources,
    and save watermarked files using GroupDocs.Watermark for Java.
  headline: How to add watermark to pdf with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark`
      or `ImageWatermark` objects; each will be layered in the order added.
    question: Can I add multiple watermarks to the same PDF?
  - answer: Absolutely. All original PDF objects, including annotations, form fields,
      and metadata, remain untouched unless you explicitly modify them.
    question: Does the library preserve existing annotations?
  - answer: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method
      to limit the watermark to specific pages.
    question: Is it possible to watermark only selected pages?
  - answer: The SDK can handle files up to **2 GB** without loading the entire document
      into memory, thanks to its streaming architecture.
    question: What is the maximum file size supported?
  - answer: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier
      returned when you initially added the watermark.
    question: How do I remove a watermark after it has been added?
  type: FAQPage
tags:
- watermark pdf
- GroupDocs.Watermark
- Java document processing
- add watermark to pdf
- load document
title: 如何使用 GroupDocs.Watermark for Java 为 pdf 添加水印
type: docs
url: /zh/java/document-loading-saving/
weight: 2
---

# 在 Java 中使用 GroupDocs.Watermark 为 PDF 添加水印

在本指南中，您将学习如何使用 GroupDocs.Watermark Java SDK **向 PDF 添加水印**。我们将演示如何从磁盘、流或受密码保护的源加载文档，应用文本或图像水印，最后保存更新后的 PDF。无论您是构建批处理器还是单文件服务，这些步骤都能为您提供可靠的生产就绪解决方案。

## 快速答案
- **我可以向受密码保护的 PDF 添加水印吗？** 是的 – 在加载文档时传入密码，然后正常应用水印。  
- **哪些格式可以添加水印？** 超过 30 种格式，包括 PDF、DOCX、PPTX 和图像。  
- **开发是否需要许可证？** 临时许可证可用于测试；生产环境需要正式许可证。  
- **需要哪个 Java 版本？** 支持 Java 8 或更高版本。  
- **是否支持流式处理？** 当然可以 – 您可以从 `InputStream` 加载并保存到 `OutputStream`，无需触及文件系统。

## 什么是向 PDF 添加水印？
*向 PDF 添加水印* 是指在 PDF 文档的每一页上覆盖半透明的文本或图像，以传达所有权、机密性或品牌信息。GroupDocs.Watermark for Java 提供单调用 API，自动处理定位、不透明度和页面范围选择。

## 为什么使用 GroupDocs.Watermark for Java？
GroupDocs.Watermark 支持 **35+ 种文件格式**，并且在普通服务器级 CPU 上可在 **2 秒以内处理 500 页的 PDF**。该库完全在内存中工作，无需安装 Microsoft Office 或 Adobe Acrobat。其 API 线程安全，非常适合高吞吐量的 Web 服务。

## 前提条件
- 已安装 Java 8 或更高版本。  
- 已在 Maven 或 Gradle 项目中配置 `groupdocs-watermark` 依赖。  
- 有效的 GroupDocs.Watermark 许可证（评估用临时许可证）。  
- 您想要保护的 PDF 文件，可选地带有密码。

## 如何向 PDF 添加水印 – 步骤详解

加载源文档，应用水印，然后保存结果。以下章节直接回答每个子任务。

### 如何从磁盘加载文档？

`Watermarker` 是用于加载和操作文档以进行水印处理的主要类。向 `Watermarker` 构造函数提供完整的文件路径；SDK 会自动检测文件格式，验证内容，并将文档加载到内存中，准备进行任何水印操作。这种方法适用于 PDF、Word 文件、图像以及许多其他受支持的类型。  
```java
Watermarker watermarker = new Watermarker("C:/files/input.pdf");
```

此行之后，PDF 已完全加载到内存中，随时可以进行任何水印操作。

### 如何从流加载文档？

`Watermarker` 也可以接受 `InputStream` 直接从内存加载文档。当您通过 HTTP 或消息队列接收文件时，可将字节数组包装在 `ByteArrayInputStream` 中，并传递给接受 `InputStream` 的 `Watermarker` 构造函数。SDK 在不写入磁盘的情况下读取流，保持性能和安全性，并通过分块处理支持大文件。此方法非常适合 Web 服务和微服务架构。  
```java
InputStream pdfStream = new ByteArrayInputStream(pdfBytes);
Watermarker watermarker = new Watermarker(pdfStream);
```

SDK 在不写入磁盘的情况下读取流，保持性能和安全性。

### 如何加载受密码保护的文档？

`Watermarker` 支持通过将密码作为第二个参数来加载受密码保护的 PDF。向构造函数提供第二个参数即密码。SDK 会在运行时解密 PDF，随后您可以像处理其他文档一样使用它。如果密码正确，所有页面都可用于添加水印；否则库会抛出明确的异常，您可以捕获并记录以进行故障排除。  
```java
Watermarker watermarker = new Watermarker("C:/files/secure.pdf", "mySecretPwd");
```

如果密码不正确，SDK 会抛出信息丰富的异常，您可以捕获并记录。

### 如何应用文本水印？

`TextWatermark` 表示可应用于页面的文本水印，具有可自定义的样式。使用您想要的文本、字体、大小和颜色创建 `TextWatermark` 对象。然后在 `Watermarker` 实例上调用 `add`，可选地指定页面范围。水印将以指定的不透明度和旋转角度渲染，并可使用预定义位置或自定义坐标进行定位，确保在所有页面上保持一致的外观。  
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 36));
watermark.setColor(Color.RED);
watermark.setTransparency(0.5);
watermarker.add(watermark);
```

此调用默认在每页放置水印；如有需要，可使用 `new PageRange(1, 5)` 限制范围。

### 如何应用图像水印？

`ImageWatermark` 表示基于图像的水印，例如徽标或印章。使用徽标的路径或流实例化 `ImageWatermark`，然后像文本水印一样添加。SDK 会自动按比例缩放图像以适应页面，同时保持其宽高比，您可以调整不透明度、旋转和位置，以实现所需的视觉效果而不扭曲原始内容。  
```java
ImageWatermark imgWatermark = new ImageWatermark("C:/images/logo.png");
imgWatermark.setTransparency(0.3);
watermarker.add(imgWatermark);
```

SDK 会在保持宽高比的同时将图像缩放以适应页面。

### 如何保存带水印的文档？

`save` 将修改后的文档写入指定位置并使用所选格式。使用输出路径和所需格式调用 `save`。如果省略格式参数，则使用与源相同的格式。该方法将修改后的 PDF 写入磁盘，保留所有原始内容，仅添加新的水印层，并支持保存到流以便进一步处理。  
```java
watermarker.save("C:/files/output.pdf");
```

该方法将修改后的 PDF 写入磁盘，保留所有原始内容，仅添加新的水印层。

## 可用教程

### [如何在 Java 中使用 GroupDocs.Watermark 加载受密码保护的文档](./groupdocs-watermark-java-password-protected-documents/)
了解如何使用 GroupDocs.Watermark for Java 加载和管理受密码保护文档中的水印。本指南提供逐步说明、实用示例和故障排除技巧。

### [如何在 Java 中使用 GroupDocs.Watermark 加载并为受密码保护的 Word 文档添加水印](./groupdocs-watermark-java-password-protected-word-docs/)
了解如何使用 GroupDocs.Watermark 与 Java 高效加载、管理并为受密码保护的 Word 文档添加水印。

## 其他资源

- [GroupDocs.Watermark for Java 文档](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark for Java API 参考](https://reference.groupdocs.com/watermark/java/)
- [下载 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark 论坛](https://forum.groupdocs.com/c/watermark)
- [免费支持](https://forum.groupdocs.com/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)

## 常见问题及解决方案
- **密码错误** – 再次检查密码字符串；必须为 UTF‑8 编码。  
- **大 PDF 导致内存不足** – 通过使用接受 `InputStream` 和 `OutputStream` 的 `Watermarker` 构造函数来启用流式模式。  
- **水印不可见** – 确保水印的不透明度设置高于 0.1，并且颜色与页面背景形成对比。

## 常见问答

**Q: 我可以在同一个 PDF 中添加多个水印吗？**  
A: 是的。重复调用 `watermarker.add()`，使用不同的 `TextWatermark` 或 `ImageWatermark` 对象；每个都会按添加顺序叠加。

**Q: 该库会保留现有的批注吗？**  
A: 当然会。所有原始 PDF 对象，包括批注、表单字段和元数据，除非您显式修改，否则保持不变。

**Q: 能否仅对选定页面添加水印？**  
A: 可以。将 `PageRange`（例如 `new PageRange(2, 4)`）传递给 `add` 方法，以限制水印仅在特定页面上。

**Q: 支持的最大文件大小是多少？**  
A: 得益于流式架构，SDK 可处理高达 **2 GB** 的文件，而无需将整个文档加载到内存中。

**Q: 添加水印后如何移除？**  
A: 使用 `watermarker.remove(watermarkId)`，其中 `watermarkId` 是最初添加水印时返回的标识符。

---

**最后更新：** 2026-09-16  
**测试环境：** GroupDocs.Watermark 23.9 for Java  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Watermark for Java 为 PDF 添加文本水印（2023 指南）](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)
- [如何使用 GroupDocs.Watermark for Java 为特定 PDF 页面添加文本和图像水印](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [如何在 Java 中使用 GroupDocs.Watermark 加载受密码保护的文档](/watermark/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/)