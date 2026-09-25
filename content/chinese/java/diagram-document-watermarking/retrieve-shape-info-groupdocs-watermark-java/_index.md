---
date: '2026-02-13'
description: 学习如何使用 GroupDocs.Watermark for Java 提取形状并从形状中提取图像，高效获取详细的图表信息。
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 如何在 Java 中使用 GroupDocs.Watermark 从图表中提取形状
type: docs
url: /zh/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark 在 Java 中提取图表形状

当您需要以编程方式 **如何提取形状** 从类似 Visio 的图表时，GroupDocs.Watermark 库提供了一种简洁、Java 优先的方式来获取所有细节——尺寸、位置、嵌入的图像，甚至每个形状内部的文本。在本教程中，您将看到 **如何提取形状**、了解其重要性，并获得可直接复制到项目中的逐步代码。

## 快速答案
- **哪个库处理形状提取？** GroupDocs.Watermark for Java  
- **需要哪个 Java 版本？** JDK 8 或更高  
- **可以从形状获取图像数据吗？** 可以——使用 `shape.getImage()`  
- **可以访问形状内部的文本吗？** 当然，可以通过 `shape.getText()`  
- **生产环境需要许可证吗？** 需要有效的 GroupDocs.Watermark 许可证  

## 介绍

管理复杂图表通常需要访问其组件的详细信息，例如形状和图像。如果您曾经需要使用 Java 编程方式检索图表形状的尺寸、位置或关联文本等数据，本教程正适合您。利用 GroupDocs.Watermark 库的强大功能，可以在 Java 应用程序中简化此过程。在本指南中，我们将演示 **如何提取形状**，并展示 **如何从形状提取图像** 与 **如何从形状提取文本**。

## 什么是 “如何提取形状”？

提取形状是指读取图表内部对象（页面、形状、图像、文本），以便您可以分析、转换或在其他应用中复用它们——这对于自动化、报告或与 CAD 工具的集成非常有用。

## 为什么使用 GroupDocs.Watermark 进行形状提取？

- **完整格式支持** – 支持 VSDX、VDX 等多种图表类型。  
- **丰富的对象模型** – 直接访问形状几何、图像和文本。  
- **无外部依赖** – 纯 Java，易于在 Maven 项目中嵌入。  

## 前置条件

- **GroupDocs.Watermark for Java**（版本 24.11 或更高）  
- Java Development Kit (JDK) 8 或更高  
- 用于依赖管理的 Maven  
- IntelliJ IDEA、Eclipse 等 IDE  

## 设置 GroupDocs.Watermark for Java

将库添加到您的 Maven `pom.xml` 中：

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

您也可以从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新二进制文件。

### 许可证获取步骤
- **免费试用：** 下载试用包以评估 API。  
- **临时许可证：** 申请临时密钥以进行扩展测试。  
- **购买：** 获取正式许可证用于生产环境。

### 基本初始化和设置

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## 如何提取形状 – 实现指南

### 加载并检索内容

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### 遍历形状

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

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

### 如何从形状提取图像

`shape.getImage()` 调用返回一个包含原始位图、其尺寸以及字节数组的对象。使用上面展示的属性可以将图像保存到磁盘，或将其传递给其他处理管道。

### 如何从形状提取文本

`shape.getText()` 方法返回形状内部的纯文本。如果形状不包含文本，方法返回 `null`。示例循环已经打印了文本，您可以进一步处理，例如构建所有形状标签的索引。

## 故障排除提示
- 验证文件路径及读取权限。  
- 确保使用受支持的图表格式（VSDX、VDX 等）。  
- 如果形状缺少预期数据，请检查库的发行说明中针对特定格式的已知问题。

## 实际应用

1. **图表分析：** 自动审计图表以检查形状大小或缺失标签，确保合规。  
2. **数据可视化：** 将提取的尺寸数据输入报表仪表盘，以可视化布局密度。  
3. **CAD 集成：** 将形状数据与 CAD API 结合，实现跨工具的设计规范同步。  

## 性能注意事项

- **关闭资源：** 完成后调用 `watermarker.close()` 以释放本机资源。  
- **内存管理：** 大型图表可能占用大量堆内存；请监控内存并在必要时增加 `-Xmx` 参数。  
- **批量处理：** 批量处理文件时尽可能复用单个 `Watermarker` 实例。

## 结论

通过本指南，您已经掌握了 **如何提取形状**、**如何从形状提取图像** 与 **如何从形状提取文本** 的方法，使用 GroupDocs.Watermark for Java 实现这些功能。这些技术为自动化图表分析、报告以及与其他工程系统的集成打开了大门。下一步，建议查阅其 [documentation](https://docs.groupdocs.com/watermark/java/) 以了解完整 API，并尝试将形状提取与自定义业务逻辑相结合。

## FAQ 部分

1. **什么是 GroupDocs.Watermark？**  
   - 一个全面的 Java 库，旨在对各种文档格式（包括图表）进行水印添加和信息提取。  

2. **我可以使用该库处理所有类型的图表文件吗？**  
   - 可以，但请通过查看 [API Reference](https://reference.groupdocs.com/watermark/java/) 确认文件格式是否受支持。  

3. **如何使用 Java 和 GroupDocs.Watermark 从图表中提取形状的尺寸和位置？**  
   - 加载图表，访问 `DiagramContent`，然后遍历形状以获取宽度、高度、X、Y 等属性。  

4. **GroupDocs.Watermark 能否使用 Java 提取嵌入在图表形状中的图像？**  
   - 能，它提供访问形状内部图像数据的方法，包括大小和像素数据，便于分析或修改。  

5. **在 Java 中提取图表形状信息的前置条件是什么？**  
   - 必须具备 Java JDK 8+、Maven 环境、GroupDocs.Watermark 库（24.11+）以及基本的 Java 编程知识。  

---

**最后更新：** 2026-02-13  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs