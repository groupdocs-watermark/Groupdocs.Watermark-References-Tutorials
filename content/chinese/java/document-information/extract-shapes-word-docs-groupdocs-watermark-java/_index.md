---
date: '2026-02-05'
description: 了解如何使用 GroupDocs.Watermark for Java 从 Word 文档中提取形状，包括如何在 Java 中加载 Word
  文档并操作形状数据。
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: 如何使用 GroupDocs.Watermark Java 从 Word 文档中提取形状
type: docs
url: /zh/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark 在 Java 中从 Word 文档中提取形状

在本教程中，您将了解如何使用 GroupDocs.Watermark Java 库从 Word 文档中 **提取形状**。无论您是需要分析图表、提取嵌入的图像，还是自动化报告生成，提取形状元数据都能让您构建更智能的文档处理流水线。我们将演示如何设置库、加载 Word 文档以及获取详细的形状信息——全部使用清晰的逐步 Java 代码。

## 快速回答
- **“提取形状”是什么意思？** 检索 Word 文件中每个绘图对象的元数据（类型、大小、位置、文本、图像）。  
- **哪个库负责此功能？** GroupDocs.Watermark for Java。  
- **我需要许可证吗？** 试用版可用于开发；完整许可证可移除使用限制。  
- **我还能从形状中获取图像吗？** 可以——API 会公开图片形状的图像字节。  
- **需要哪个 Java 版本？** JDK 8 或更高版本。

## 在 Word 文档上下文中，“提取形状”是什么？
提取形状是指以编程方式访问每个绘图元素——图片、WordArt、自动形状、图表，甚至嵌入在页眉或页脚中的形状。此信息可用于验证、迁移或基于内容的分析。

## 为什么在 Java 中使用 GroupDocs.Watermark？
GroupDocs.Watermark 提供了高级且内存高效的 API，抽象了底层 Office Open XML 格式的复杂性。它让您能够：
- 快速加载文档（`WordProcessingLoadOptions`）。  
- 在不处理低层 XML 的情况下遍历章节和形状。  
- 在一次调用中检索图像数据、文本、对齐方式和旋转角度。  
- 无缝集成到现有的 Java 服务或微服务中。

## 前提条件
- **Java Development Kit (JDK)** 8 或更高版本。  
- **IDE**，如 IntelliJ IDEA 或 Eclipse。  
- 基本的 Java I/O 知识。  
- 获取 **GroupDocs.Watermark for Java** 许可证或试用版的访问权限。

## 设置 GroupDocs.Watermark（Java）
通过 Maven 或直接下载方式集成该库。

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
或者，从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新的 JAR。

### 获取许可证
免费试用版足以进行测试。生产环境请申请永久许可证以解锁全部功能。

## 实现指南
我们将实现分为两个明确的步骤：**加载 Word 文档** 和 **提取形状信息**。

### 步骤 1：加载 Word 文档（load word document java）
首先，配置加载选项并创建 `Watermarker` 实例。这将为后续检查准备文档。

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

> **技巧提示：** 尽可能将 `Watermarker` 实例的作用域限制得很小；及时关闭它可以释放本机资源并避免内存泄漏。

### 步骤 2：提取形状信息（extract images from shapes）
现在我们将获取每个形状的详细信息，包括任何嵌入的图像。代码会遍历每个章节和每个形状，打印有用的元数据。

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

**此代码的功能：**  
- 获取每个形状的 **type**（例如 picture、WordArt）。  
- 打印 **size**、**position** 和 **rotation** 值。  
- 显示 **alternative text** 和 **name**，这对可访问性检查很有用。  
- 如果形状包含图像，则打印图像的 **pixel dimensions** 和 **byte size**——非常适合从形状中提取图像。

### 常见陷阱及解决方案
| 问题 | 原因 | 解决方案 |
|-------|-------|----------|
| `FileNotFoundException` | 文件路径错误或缺少权限 | 验证绝对/相对路径并确保文件可读。 |
| Null `shape.getImage()` | 形状不是图片（例如 auto‑shape） | 如示例所示，用 `if (shape.getImage() != null)` 进行检查。 |
| 大型文档内存使用高 | 一次性加载整个文档 | 一次处理一个章节或增加 JVM 堆大小（`-Xmx`）。 |
| 缺少页眉/页脚形状 | 未检查 `shape.getHeaderFooter()` | 示例已在形状属于页眉/页脚时记录日志。 |

## 实际应用
1. **自动化报告生成** – 提取图表和示意图以嵌入下游 PDF。  
2. **合规审计** – 验证所有形状是否包含适当的替代文本以满足可访问性要求。  
3. **内容迁移** – 将旧版 Word 文件中的嵌入图像导出到数字资产管理系统。  

## 性能考虑
- **释放资源**：始终在 `finally` 块中调用 `watermarker.close()`，或在使用 API 时采用 try‑with‑resources。  
- **分块处理**：对于超过 50 MB 的文档，考虑逐章节处理以保持低内存占用。  
- **线程安全**：`Watermarker` 实例不是线程安全的；每个线程应创建新的实例。

## 结论
您现在已经了解如何使用 GroupDocs.Watermark for Java **提取 Word 文档中的形状**，从加载文件到读取每个形状的元数据和嵌入的图像数据。这一能力为高级文档分析、自动化内容流水线和可访问性验证打开了大门。

### 后续步骤
- 尝试修改形状属性（例如调整大小或重新定位）。  
- 将此方法与 **GroupDocs.Parser** 结合，以提取周围文本。  
- 将提取逻辑集成到 REST 服务中，实现按需处理。

## 常见问题解答
**问：GroupDocs.Watermark for Java 是什么？**  
A: 它是一个综合库，旨在跨格式管理水印和文档内容，支持形状提取、图像检索和文本操作等任务。

**问：没有许可证可以提取形状中的图像吗？**  
A: 试用版允许提取，但完整许可证可移除使用限制并支持商业部署。

**问：这适用于 `.doc`（二进制）文件吗？**  
A: 是的，API 同时支持 `.docx` 和传统的 `.doc` 格式。

**问：如何处理受密码保护的文档？**  
A: 在创建 `Watermarker` 之前，通过 `WordProcessingLoadOptions.setPassword("yourPassword")` 提供密码。

**问：有没有办法将提取的形状数据导出为 JSON？**  
A: 您可以将打印的值映射到 POJO，并使用任意 JSON 库（例如 Jackson）对集合进行序列化。

---

**最后更新：** 2026-02-05  
**测试版本：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs