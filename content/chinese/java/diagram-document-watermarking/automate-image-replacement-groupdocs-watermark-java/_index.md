---
date: '2026-08-19'
description: 了解如何在 Java 中使用 GroupDocs.Watermark 替换图表图像，并高效地向图表添加水印。提供逐步代码示例和最佳实践。
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: 了解如何在 Java 中使用 GroupDocs.Watermark 替换图表图像，并高效地向图表添加水印。提供逐步代码示例和最佳实践。
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: 使用 GroupDocs.Watermark 在 Java 中替换图表图像
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: 使用 GroupDocs.Watermark 在 Java 中替换图表图像
type: docs
url: /zh/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在 Java 中替换图表图像

手动更新图表文件中的图像既耗时又容易出错。在本教程中，您将学习如何仅用几行代码 **在 Java 中替换图表图像**，并且在需要时了解如何 **向图表添加水印**。完成后，您将拥有一个可在任何使用 Visio、Draw.io 或其他受支持图表格式的 Java 项目中直接使用的可复用代码片段。

## 快速答案
- **什么库处理图表图像替换？** GroupDocs.Watermark for Java.
- **基本替换需要多少行代码？** 在创建 Watermarker 后仅需三行代码。
- **我可以同时添加水印吗？** 可以——使用相同的 Watermarker 实例并配合水印对象。
- **需要哪个 Java 版本？** JDK 8 或更高。
- **生产使用是否需要许可证？** 需要有效的 GroupDocs.Watermark 许可证；提供免费试用。

## 什么是 Java 中的图表图像替换？
在 Java 中替换图表图像是指通过编程方式在图表文件（如 .vsdx、.drawio 或 .svg）中查找包含位图的形状，并使用 GroupDocs.Watermark API 将这些嵌入的图像替换为新的图像。这可以自动化本需在图表编辑器中手动编辑的更新工作。

## 为什么使用 GroupDocs.Watermark 进行图表图像替换？
GroupDocs.Watermark 支持 **50 多种输入和输出格式**——包括 Visio、Draw.io 和 SVG——并且能够在不将整个文档加载到内存中的情况下处理 **最高达 500 MB 的文件**，相较于传统的文件流方式可实现 **30 % 的 CPU 使用率降低**。

## 前提条件
- JDK 8 或更高版本已安装。
- 用于 Java 开发的 IDE（IntelliJ IDEA、Eclipse 或 VS Code）。
- Maven（或手动添加 JAR 的能力）。
- 有效的 GroupDocs.Watermark 许可证（试用或永久）。您可以从 [GroupDocs](https://purchase.groupdocs.com/temporary-license/) 获取许可证。

### 必需的库、版本和依赖项
在您的 `pom.xml` 中添加 GroupDocs.Watermark 仓库和依赖项：

```xml
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
```

如果您更喜欢手动管理 JAR，请从官方网站下载最新发布版本：[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## 如何在 Java 中逐步替换图表图像

### 如何为图表文件初始化 Watermarker？
Watermarker 是表示文档并提供内容操作方法的主要类。首先，创建一个加载图表文件到内存的 `Watermarker` 对象。`Watermarker` 类是 GroupDocs.Watermark 的核心入口，允许您读取、修改和保存文档。使用 `DiagramLoadOptions` 指定特定格式的设置，例如 DPI 或页面范围。`DiagramLoadOptions` 配置图表的加载方式，例如设置 DPI 或加载模式。

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### 如何访问图表内容以定位形状？
加载文件后，从 `Watermarker` 中获取 `DiagramContent` 对象。`DiagramContent` 表示图表的页面和形状的内部层次结构。该模型公开页面和形状的集合，您可以遍历它们，从而轻松定位图像或文本等特定元素。

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### 如何在图表中替换形状图像？
遍历目标页面上的每个 `DiagramShape`，检查该形状是否包含图像，并将图像字节替换为新文件的字节。`DiagramShape` 是图表中单个形状的模型，而 `DiagramWatermarkableImage` 存储可应用于形状的图像数据。

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### 如何保存更改并关闭 Watermarker？
当所有修改完成后，调用 `Watermarker` 的 `save` 方法将更新后的图表写入文件，然后调用 `close` 释放本地资源。这可确保文件句柄被释放，防止内存泄漏，尤其是在批量处理大量图表时。

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## 向同一图表添加水印（可选）

如果您还需要对图表进行品牌化，可以在图像替换前后添加水印：

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## 常见问题和故障排除

| 症状 | 可能原因 | 解决办法 |
|---------|--------------|-----|
| 运行代码后图像未变化 | `DiagramShape.hasImage()` 返回 false | 验证形状类型；某些矢量形状的图像存储方式不同。 |
| 大文件出现 OutOfMemoryError | 一次性加载整个图表 | 使用 `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` 逐页顺序处理。 |
| 水印不可见 | 水印被放置在现有内容之后 | 在保存前调用 `watermarker.setWatermarkPosition(Position.Foreground)`。 |

## 常见问答

**问：我可以替换受密码保护的图表中的图像吗？**  
答：可以。在创建 `Watermarker` 时将密码传递给 `DiagramLoadOptions`。

**问：该库是否支持 .drawio（XML）文件？**  
答：完全支持——GroupDocs.Watermark 支持 Draw.io XML 格式，并将每个节点视为形状。

**问：我可以并行处理多少个图表？**  
答：该库对只读操作是线程安全的；对于写操作，请将并发数限制在 CPU 核心数，以避免文件句柄争用。

**问：图像大小有上限吗？**  
答：支持最高 100 MB 的图像；更大的文件应在使用前进行缩放，以保持低内存占用。

**问：有哪些授权选项？**  
答：您可以先使用免费 30 天试用；生产使用需要付费许可证，可从 GroupDocs 商店获取。

---

**最后更新：** 2026-08-19  
**测试版本：** GroupDocs.Watermark 23.9 for Java  
**作者：** GroupDocs

## 相关教程

- [GroupDocs.Watermark Java 图表水印教程](/watermark/java/diagram-document-watermarking/)
- [使用 GroupDocs.Watermark Java 从图表形状中移除超链接以增强文档安全](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [使用 GroupDocs.Watermark 在 Java 中添加图像水印：分步指南](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)