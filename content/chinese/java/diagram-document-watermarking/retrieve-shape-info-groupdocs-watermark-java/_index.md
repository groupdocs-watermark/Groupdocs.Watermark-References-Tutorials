---
date: '2025-12-20'
description: 学习如何使用 GroupDocs.Watermark for Java 提取形状信息。高效地从图表文件中获取尺寸、位置和文本。
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 提取形状信息（Java）：使用 GroupDocs.Watermark 处理图表
type: docs
url: /zh/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在图表中提取形状信息（Java）

当您需要从复杂的图表文件中**extract shape information java**时，手动操作很快变得不切实际。本教程展示如何利用 GroupDocs.Watermark for Java 以编程方式提取每个形状的尺寸、位置、旋转角度、嵌入图像和文本等详细信息。完成后，您将拥有一个清晰、可复用的模式，可直接嵌入任何使用 Visio 风格图表的 Java 项目中。

## 介绍

管理复杂的图表通常需要访问其组件的详细信息，例如形状和图像。如果您曾需要使用 Java 编程方式检索与图表形状相关的尺寸、位置或文本等数据，本教程适合您。利用 GroupDocs.Watermark 库的强大功能可以在 Java 应用程序中简化此过程。在本指南中，我们将演示如何使用 GroupDocs.Watermark **extract shape information java** 从图表文件中提取形状信息。

## 快速答案
- **我应该使用哪个库？** GroupDocs.Watermark for Java (v24.11+).  
- **支持哪些文件格式？** Visio (.vsdx, .vsd) and other diagram types listed in the API docs.  
- **我需要许可证吗？** A free trial works for development; a commercial license is required for production.  
- **我可以从形状中获取图像数据吗？** Yes – the API exposes image width, height, and raw byte data.  
- **需要 Maven 吗？** Maven is the recommended way to manage the GroupDocs.Watermark dependency.

## 什么是 “extract shape information java”

extract shape information java 指的是使用 Java 代码以编程方式读取图表文件并提取每个形状的属性——尺寸、位置、旋转、文本以及任何嵌入的图像。这使得自动化分析、报告或与其他系统（如 CAD 工具或数据可视化流水线）的集成成为可能。

## 为什么在此任务中使用 GroupDocs.Watermark？

GroupDocs.Watermark 为图表格式提供了高级抽象，帮助您处理底层解析工作。它让您专注于业务逻辑，而无需处理 XML 或二进制规范，并且在所有受支持的图表类型上表现一致。

## 前提条件

- **GroupDocs.Watermark for Java**（版本 24.11 或更高）  
- Java Development Kit (JDK) 8 或更高  
- 用于依赖管理的 Maven  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE  

## 设置 GroupDocs.Watermark for Java

将仓库和依赖添加到您的 Maven `pom.xml` 中：

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

或者，您也可以直接从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新版本。

### 获取许可证的步骤
- **免费试用：** Download a trial package to test the library.  
- **临时许可证：** Obtain a temporary key for extended evaluation.  
- **购买：** Acquire a full license for production use.

### 基本初始化

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## 实现指南

现在让我们逐步演示如何从图表文档中**extract shape information java**。

### 加载并检索内容

#### 概述
我们首先加载图表文件并获取 `DiagramContent` 对象，该对象提供对页面和形状的访问。

#### 步骤

**加载图表文档**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **原因：** This initializes the `Watermarker` object, allowing access to the document's content.

**访问图表内容**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **原因：** `DiagramContent` 类提供方法以交互图表的不同方面，例如页面和形状。

### 遍历形状

#### 概述
拥有 `DiagramContent` 后，我们遍历每个页面，然后遍历每个形状以提取所需的属性。

#### 步骤

**遍历页面**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **原因：** 图表由多个页面组成；我们需要检查每个页面的形状。

**提取形状信息**

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

- **原因：** 此循环提取并打印每个形状的属性，包括尺寸、位置、旋转以及任何嵌入的图像或文本。这些属性对于了解图表中形状的配置至关重要。

### 故障排除提示
- 确认文件路径正确且指向可读取的 `.vsdx`（或受支持）文件。  
- 确保应用程序对图表文件具有读取权限。  
- 如果遇到“Unsupported format”错误，请确认您的 GroupDocs.Watermark 版本支持该特定图表类型。

## 实际应用

拥有**extract shape information java**的能力，您可以驱动多种实际场景：

1. **Diagram Analysis（图表分析）：** 自动生成报告，列出每个形状的尺寸、位置和文本——对质量保证审计非常有用。  
2. **Data Visualization（数据可视化）：** 将形状指标输入仪表板，以可视化布局密度或识别过大的元素。  
3. **CAD Integration（CAD 集成）：** 将图表数据桥接到 CAD 流程中，实现自动化重新设计或验证步骤。

## 性能考虑

处理大型图表时，请牢记以下最佳实践：

- **及时关闭资源：** 调用 `watermarker.close()`（或依赖 try‑with‑resources）以释放内存。  
- **监控堆使用情况：** 大型图表可能消耗大量内存；根据需要调整 JVM 堆（`-Xmx`）。  
- **批量处理：** 将文件分批处理，而不是一次加载数十个。

## 结论

通过本指南，您现在了解如何使用 GroupDocs.Watermark for Java **extract shape information java**。您可以从任何受支持的图表文件中检索尺寸、位置、旋转角度、嵌入图像和文本，从而开启自动化分析、报告以及与更大系统集成的大门。准备好下一步了吗？请在官方[文档](https://docs.groupdocs.com/watermark/java/)中探索库的全部功能，并尝试水印、编辑或自定义形状操作。

## 常见问题

**Q: 什么是 GroupDocs.Watermark？**  
A: 一个全面的 Java 库，旨在对各种文档格式（包括图表）进行水印和信息提取。

**Q: 我可以使用此库处理所有类型的图表文件吗？**  
A: 可以，但请确保文件格式在[API Reference](https://reference.groupdocs.com/watermark/java/)中列为受支持。

**Q: 如何使用 Java 和 GroupDocs.Watermark 从图表中提取形状的尺寸和位置？**  
A: 加载图表，获取 `DiagramContent`，然后遍历每个 `DiagramShape` 读取宽度、高度、X 和 Y 等属性。

**Q: GroupDocs.Watermark 能否使用 Java 提取图表形状中嵌入的图像？**  
A: 可以，它提供访问形状内图像数据的方法，包括尺寸和原始字节数组，您可以用于分析或修改。

**Q: 在 Java 中提取图表形状信息的前提条件是什么？**  
A: Java JDK 8+、Maven 环境、GroupDocs.Watermark 库（24.11+）以及基本的 Java 编程知识。

---

**最后更新：** 2025-12-20  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs