---
date: '2025-12-20'
description: 学习如何使用 GroupDocs.Watermark for Java 从 Word 文档中提取图像和形状，完美适用于文档自动化和处理。
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: 如何使用 GroupDocs.Watermark 在 Java 中从 Word 文档中提取图像
type: docs
url: /zh/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中提取 Word 文档中的图片

在现代文档处理应用中，**从 Word 文档中提取图片** 是一个常见需求——无论是需要复用图形、进行 OCR，还是仅仅审计内容。本教程将一步步演示如何在 Java 中使用 GroupDocs.Watermark 加载 Word 文档，并 **从 Word 文件中提取图片**，同时展示 **如何提取形状**。完成后，你将拥有一段可直接嵌入自动化流水线的可复用代码片段。

## 快速回答
- **哪个库负责图片提取？** GroupDocs.Watermark for Java  
- **我可以同时提取图片和矢量形状吗？** 可以——API 提供对图片和形状元数据的访问。  
- **需要哪个 Java 版本？** JDK 8 或更高。  
- **生产环境需要许可证吗？** 建议使用商业许可证；免费试用可用于评估。  
- **该过程对大文件是否内存友好？** 是的，你可以及时释放资源并增量处理章节。

## 什么是 “从 Word 中提取图片”？
从 Word 中提取图片指的是以编程方式定位 `.docx` 文件内部的每个图片、绘图或嵌入式图形，并获取其二进制数据或元数据。这为后续的图像分析、内容迁移或动态报表生成等任务提供了可能。

## 为什么选择 GroupDocs.Watermark 来完成此任务？
GroupDocs.Watermark 提供了一个高级 API，抽象了 OpenXML 格式的复杂性。它让你只需几行代码即可 **在 Java 项目中加载 Word 文档**，同时还能暴露详细的形状信息——非常适合需要同时进行图片提取和形状分析的开发者。

## 前置条件
- **Java Development Kit (JDK)** 8 或更新版本  
- **IDE** – IntelliJ IDEA、Eclipse 或任意支持 Java 的编辑器  
- 基础的 Java I/O 知识  
- 拥有 GroupDocs.Watermark 许可证（试用版可用于测试）

## 为 Java 配置 GroupDocs.Watermark
通过 Maven 或直接下载方式集成库。

### 使用 Maven
在 `pom.xml` 中添加仓库和依赖：

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
或者，从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新的 JAR 包。

### 获取许可证
要获得完整功能，请从 GroupDocs 门户获取许可证密钥。也可以申请临时试用许可证，以无限制地探索所有特性。

## 实现指南
我们将实现分为两个逻辑部分：

1. **如何在 Java 中加载 Word 文档**  
2. **如何提取形状和图片（即从 Word 中提取图片）**

### 加载 Word 文档
首先，配置加载选项并实例化 `Watermarker`。

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

> **小贴士：** 将 `"YOUR_DOCUMENT_DIRECTORY/document.docx"` 替换为指向你要处理文件的绝对路径或相对路径。

### 提取形状和图片信息
文档加载完成后，你可以遍历每个章节和每个形状，提取矢量形状数据以及嵌入的图片细节。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

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

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
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

> **为何重要：** `shape.getImage()` 调用直接返回每张图片的二进制表示，你可以将其保存到磁盘、通过网络发送，或喂入图像处理库。

## 常见问题及解决方案
| 问题 | 解决方案 |
|---------|----------|
| **FileNotFoundException** – 路径错误 | 核实文件路径并确保应用拥有读取权限。 |
| **OutOfMemoryError** 在大文档上出现 | 一次处理一个章节，完成批次后立即调用 `watermarker.close()`。 |
| 形状的 `getImage()` 返回 `null` | 并非所有形状都是图片；有些是绘图对象。访问图片前请检查 `shape.getShapeType()`。 |
| 许可证未生效 | 在创建 `Watermarker` 前添加 `License.setLicense("path/to/license/file.lic");`。 |

## 实际应用场景
- **自动化报表生成：** 从模板中提取图表和徽标，复用于仪表盘。  
- **内容审计：** 扫描企业文档，查找违规图形。  
- **迁移项目：** 在将内容迁移至新 CMS 前导出嵌入的图片。

## 性能考量
- 及时释放 `Watermarker` 实例 (`watermarker.close()`)。  
- 对于超过 50 MB 的超大文件，建议流式处理章节，而不是一次性加载整个文档。  
- 使用最新的 GroupDocs.Watermark 版本以获得性能提升。

## 结论
现在，你已经掌握了使用 GroupDocs.Watermark for Java **从 Word 文档中提取图片** 并获取形状元数据的完整、可投入生产的方案。这一能力可解锁强大的自动化场景，从生成动态报表到执行大规模文档审计。

### 后续步骤
- 试着将提取的图片保存到磁盘（`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`）。  
- 探索其他 API，如水印移除或添加。  
- 将此逻辑集成到现有的文档管理工作流中。

## FAQ 区域
**问：GroupDocs.Watermark for Java 是什么？**  
答：它是一个全面的库，旨在管理水印并提取各种文档格式中的可视元素，提升文档操作任务的自动化水平。

**问：我可以从受密码保护的 Word 文件中提取图片吗？**  
答：可以。使用包含密码的 `WordProcessingLoadOptions` 加载文档，然后按相同的提取逻辑操作。

**问：API 是否也支持 .doc（二进制）文件？**  
答：库主要面向 OpenXML `.docx` 格式，但在转换后也能打开传统的 `.doc` 文件。

**问：如何将提取的图片保存到文件系统？**  
答：在 `shape.getImage()` 不为 null 的循环中使用 `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());`。

**问：处理的形状数量有限制吗？**  
答：没有硬性限制，但内存消耗会随文档大小增长；对超大文件请顺序处理章节。

---

**最后更新：** 2025-12-20  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs