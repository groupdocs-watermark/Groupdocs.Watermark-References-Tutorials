---
date: '2026-08-25'
description: 了解如何使用 GroupDocs.Watermark for Java 编辑图表文件并删除超链接。通过分步指导快速保护您的图表。
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: 了解如何使用 GroupDocs.Watermark for Java 编辑图表文件并删除超链接。遵循清晰的步骤来保护您的文档。
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: 如何使用 Java 编辑图表并删除超链接
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: 如何使用 Java 编辑图表并删除超链接
type: docs
url: /zh/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 Java 编辑图表并删除超链接  

管理数字文档通常涉及编辑图表，尤其是在需要 **edit diagram** 文件以去除超链接以提升安全性或视觉清晰度时。本教程将准确展示如何使用强大的 **GroupDocs.Watermark** Java 库编辑图表文件并删除图表形状中的不需要的超链接。阅读完本指南后，您将拥有一个干净、无链接的图表，可供分发。  

## 快速答案  
- **What is the main goal?** 删除图表形状中的所有超链接，以提升安全性和展示效果。  
- **Which library is required?** GroupDocs.Watermark for Java，版本 24.11 或更高。  
- **Do I need a license?** 免费试用可用于测试；生产环境需要商业许可证。  
- **Can I process many files at once?** 可以——相同的代码可以放入循环中批量处理。  
- **What Java version is supported?** Java 8 或更高（推荐使用 Java 11）。  

## 什么是 “how to edit diagram”？  
**How to edit diagram** 指的是以编程方式打开图表文件，修改其内部元素（如形状、文本或超链接），并保存结果的过程。使用 GroupDocs.Watermark，您可以在无需原始创作工具的情况下编辑图表文件。  

## 为什么使用 GroupDocs.Watermark for Java？  
GroupDocs.Watermark 支持 **30+ 图表和图像格式**（包括 VSDX、SVG 和 WMF），并且能够在不将整个文档加载到内存中的情况下处理高达 **500 MB** 的文件，提供比许多竞争对手快 **20 %** 的处理速度。  

## 前提条件  
- **GroupDocs.Watermark** 库版本 24.11 或更高。  
- 已安装 Maven（或如果您更喜欢手动设置，则使用 JAR 文件）。  
- Java Development Kit 8 或更高版本，以及 IntelliJ IDEA 或 Eclipse 等 IDE。  

### 必需的库、版本和依赖项  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+（如果您使用 Maven 方法）  

### 环境设置要求  
确保 JDK 的 `bin` 目录已加入 `PATH`，并且您的 IDE 指向正确的 JDK 版本。  

### 知识前提  
您应熟悉基本的 Java 语法、Maven 依赖管理以及文件 I/O 操作。  

## 如何为 Java 设置 GroupDocs.Watermark？  
`Watermarker` 类提供了加载和修改文档的 API 入口。  
要开始使用 GroupDocs.Watermark，请将其 Maven 坐标添加到项目的 `pom.xml` 中。这将拉取库及其依赖，使您能够实例化 Watermarker 类并直接在 Java 代码中处理图表文件。随后您可以配置许可证并在处理任何文档之前设置输出选项。  

将 GroupDocs.Watermark 依赖添加到您的 `pom.xml` 中。  

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

如果您不想使用 Maven，可以从官方发布页面下载最新的 JAR 包。  

[GroupDocs.Watermark for Java 发布](https://releases.groupdocs.com/watermark/java/)  

#### 许可证获取步骤  
- 首先使用免费试用来评估 API。  
- 对于生产环境，请从供应商门户获取临时或永久许可证。  

#### 基本初始化和设置  
`Watermarker` 类是所有文档处理操作的入口点。  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## 如何使用 GroupDocs.Watermark 编辑图表并删除超链接？  
`Watermarker` 类提供了加载和修改文档的 API 入口点。  
首先，将图表文件加载到 Watermarker 实例中。然后获取形状集合，识别包含超链接对象的形状，并以逆序遍历它们，以安全地删除每个链接而不影响集合索引。这样可确保删除所有嵌入的 URL，同时保持图表的视觉完整性。  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Why this step matters**: 加载文件后，您即可以编程方式访问每个形状及其相关属性。  

## 如何访问图表中的形状内容？  
`DiagramShape` 对象表示图表中的单个形状，公开其属性和附加元数据。  
加载图表后，在 Watermarker 上调用 `getShapes()` 以获取 `DiagramShape` 对象列表。每个形状都可以检查其超链接集合，从而精确定位要删除或修改的链接。如果需要进一步调整，还可以读取形状的文本、颜色和几何信息。  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Why this step matters**: 精确定位形状可确保仅删除不需要的链接，而不影响其他视觉元素。  

## 如何安全地遍历并删除超链接？  
`removeHyperlink(int index)` 方法删除形状超链接集合中指定位置的超链接。  
从最后一个索引向下遍历超链接列表至零。此逆向循环可防止删除项目时导致的索引移动，确保每个超链接都被处理而不会被跳过。删除后，您可以刷新形状状态或继续处理图表中的下一个形状。  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Why this step matters**: 逆向循环可保证所有超链接都被删除，不会遗漏任何条目。  

## 如何保存编辑后的图表并释放资源？  
`save(String path)` 方法将修改后的文档写入指定的文件位置，完成所有更改。  
所有超链接删除后，在 Watermarker 实例上调用 `save` 方法，提供新文件名以避免覆盖原文件。随后调用 `close()` 释放文件句柄并释放内存，这对于长时间运行的批处理过程至关重要。这样可确保文件正确关闭并可供进一步使用。  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Why this step matters**: 正确关闭资源可避免服务器上的内存泄漏和文件锁定问题。  

## 实际应用  
从图表形状中删除超链接在多种实际场景中都有益处：  

1. **Security** – 防止可能导致恶意站点的外部链接。  
2. **Compliance** – 符合禁止在共享资产中嵌入 URL 的公司政策。  
3. **Clarity** – 生成更清晰的演示文稿，避免链接分散注意力。  

您可以将此逻辑嵌入更大的自动化流水线，例如在图表发布到内部网之前的每夜批处理作业，以对所有图表进行清理。  

## 性能考虑  
### 优化性能  
- 对每个文件使用单个 `Watermarker` 实例以降低开销。  
- 优先使用逆向遍历（如示例所示），以避免代价高昂的列表重新索引。  

### 资源使用指南  
- 对于大于 200 MB 的图表，监控堆使用情况并考虑增大 JVM 的 `-Xmx` 参数。  
- 像 VisualVM 这样的分析工具可帮助识别大规模批处理运行中的瓶颈。  

### Java 内存管理最佳实践  
- 在尽可能小的作用域内声明对象。  
- 在使用流时使用 try‑with‑resources，以确保自动关闭。  

## 常见问题  
**Q: 如何处理包含成千上万形状的图表？**  
A: 逐页处理图表，并在转到下一页之前释放每页的资源，以保持低内存使用。  

**Q: 我可以仅在特定页面上限制超链接删除吗？**  
A: 可以——检索您想要的页面索引，然后仅对该页面上的形状应用删除循环。  

**Q: 批处理是否必须使用商业许可证？**  
A: 任何生产级部署都需要有效许可证；免费试用限制为 30 天和 5 份文档。  

**Q: GroupDocs.Watermark 是否支持 SVG 图表？**  
A: 当然——SVG 是 30 多种支持格式之一，可使用相同的 API 调用剥离超链接。  

**Q: 如果一个形状有多个超链接怎么办？**  
A: 逆向遍历循环会逐个删除每个超链接条目，确保所有链接都被清除。  

## 资源  
- [文档](https://docs.groupdocs.com/watermark/java/)  
- [API 参考](https://reference.groupdocs.com/watermark/java)  
- [下载](https://releases.groupdocs.com/watermark/java/)  
- [GitHub 仓库](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [免费支持论坛](https://forum.groupdocs.com/c/watermark/10)  
- [临时许可证获取](https://purchase.groupdocs.com/temporary-license/)  

---  

**最后更新：** 2026-08-25  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

## 相关教程  
- [GroupDocs.Watermark Java 图表水印教程](/watermark/java/diagram-document-watermarking/)  
- [使用 GroupDocs.Watermark 在 Java 中编辑图表页眉和页脚：综合指南](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [使用 GroupDocs.Watermark for Java 高效删除图表形状](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)