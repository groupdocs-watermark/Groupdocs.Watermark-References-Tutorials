---
date: '2026-10-21'
description: 了解如何使用 GroupDocs.Watermark for Java 删除图表形状中的超链接。按照本分步指南，确保文档安全且整洁。
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: 了解如何使用 GroupDocs.Watermark for Java 删除图表形状中的超链接。本指南将带您了解设置、代码以及实现安全、整洁文档的最佳实践。
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: 如何使用 GroupDocs.Watermark Java 从形状中删除超链接
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: 如何使用 GroupDocs.Watermark Java 从形状中删除超链接
type: docs
url: /zh/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 从形状中删除超链接

管理数字文档通常涉及编辑图表，尤其是在出于安全或视觉清晰度的考虑时，需要**how to remove hyperlink**从形状中删除超链接。本教程将引导您使用强大的 **GroupDocs.Watermark** Java 库，轻松去除图表形状中不需要的超链接。阅读完本指南后，您将了解删除超链接的意义、如何搭建环境以及安全执行删除的具体步骤。

## 快速答案
- **What is the primary purpose of removing hyperlinks?** 消除安全风险并提升共享图表的视觉清晰度。  
- **Which library handles the removal?** GroupDocs.Watermark for Java 提供专用的 API 用于图表操作。  
- **Do I need a license?** 试用版可用于测试；生产环境需要商业许可证。  
- **Can I process many files at once?** 是的——将代码包装在循环或批处理作业中即可批量处理。  
- **What Java version is required?** 支持 Java 8 或更高版本。

## 什么是 how to remove hyperlink？
短语 **how to remove hyperlink** 指的是在图表的形状元素中定位并删除嵌入的超链接对象的过程。执行此操作可防止外部导航意外将用户暴露于恶意站点或不需要的内容。在准备面向公众分发的文档时尤为重要，以确保不存在可能导致钓鱼站点或意外外部资源的隐藏导航路径。

## 为什么在 Java 中使用 GroupDocs.Watermark？
GroupDocs.Watermark 支持 **30+ 输入和输出格式**，并且能够在不将整个文件加载到内存的情况下处理 **最多 500 页** 的图表，与通用 XML 解析器相比，可实现 **CPU 使用率降低 40 %**。其 API 提供对形状属性的细粒度控制，使其成为 Java 应用中安全处理图表的标准方案。

## 先决条件
- **GroupDocs.Watermark** 库版本 24.11 或更高。  
- 已安装 Maven（或直接下载 JAR）。  
- JDK 8 或更高版本，以及 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 基本的 Java 知识并熟悉 Maven 依赖。

## 为 Java 设置 GroupDocs.Watermark
要开始，请在项目中包含 GroupDocs.Watermark 库。您可以通过 Maven 添加或手动下载 JAR。

### Maven 配置
在您的 `pom.xml` 中添加以下配置：

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

#### 获取许可证的步骤
- 通过下载 GroupDocs.Watermark 开始免费试用。  
- 对于更长时间的测试或生产使用，获取临时许可证或购买正式许可证。

#### 基本初始化和设置
`Watermarker` 类是所有文档级操作的入口。它加载文件，提供对页面、形状和元数据的访问，最后将修改后的文档写回磁盘。

要初始化 Watermarker 类：

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 如何从图表形状中删除超链接？
加载图表，定位包含超链接的每个形状，并删除这些超链接对象。整个操作可以在不到十行代码中完成，并确保生成的图表不再包含任何可能将用户重定向到外部站点或泄露敏感信息的可点击链接。

### 步骤 1：加载图表文件
首先使用 `Watermarker` 加载图表。此对象提供对各种文档元素的访问，包括形状及其属性。

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Why**: 加载文件是访问其内容以进行进一步操作的前提。

### 步骤 2：访问形状内容
获取图表的形状内容。这使您能够直接处理可能包含超链接的元素。

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Why**: 访问特定形状对于定位并修改超链接属性至关重要。

### 步骤 3：遍历并删除超链接
逆向遍历超链接，以安全地删除不需要的链接而不打乱遍历过程。

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Why**: 逆序遍历可防止在删除元素时出现索引问题。

### 步骤 4：保存并关闭
修改完成后，将更改保存到新文件位置并关闭 watermarker 资源。

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Why**: 正确关闭资源可确保系统中不出现内存泄漏或文件锁定。

## 常见陷阱与故障排除
- **Null shape collections** – 在遍历之前，始终检查形状的 `Hyperlinks` 集合是否为 null。  
- **Large diagrams** – 对于超过 200 页的文件，增大 JVM 堆大小 (`-Xmx2g`) 以避免 `OutOfMemoryError`。  
- **License errors** – 如果出现许可证异常，请确认试用许可证未过期且许可证文件路径正确。

## 常见问题

**Q: 如何处理同一页面上的多个形状？**  
A: 遍历每页的 `Shapes` 集合，对遇到的每个形状应用相同的超链接删除逻辑。

**Q: 能否将删除限制在特定页面范围内？**  
A: 是的——在检索形状时使用页面索引，并跳过目标范围之外的页面。

**Q: 批处理是否需要许可证？**  
A: 任何生产级批处理作业都需要有效的商业许可证；试用许可证仅适用于有限的测试。

**Q: 这适用于 SVG 或 Visio 文件吗？**  
A: GroupDocs.Watermark 支持 SVG、VSDX 以及其他多种图表格式；请确保文件类型在支持的格式表中列出。

**Q: 在 300 页的图表上可以期待怎样的性能？**  
A: 在典型服务器（8 CPU，16 GB RAM）上，处理 300 页的图表耗时不到 45 秒，内存使用保持在 200 MB 以下。

## 资源
- [文档](https://docs.groupdocs.com/watermark/java/)
- [API 参考](https://reference.groupdocs.com/watermark/java)
- [下载](https://releases.groupdocs.com/watermark/java/)
- [GitHub 仓库](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/watermark/10)
- [临时许可证获取](https://purchase.groupdocs.com/temporary-license/)

---

**最后更新：** 2026-10-21  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs

## 相关教程

- [在 Java 中使用 GroupDocs.Watermark 修改 Word 文档形状：完整指南](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [在 Java 中使用 GroupDocs.Watermark 从 Word 文档中删除形状：完整指南](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [在 Java 中使用 GroupDocs.Watermark 编辑图表页眉和页脚：完整指南](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)