---
date: '2026-02-03'
description: 了解如何使用 GroupDocs.Watermark for Java 预览文档——为文档预览 Java 开发者准备的快速指南。
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 如何使用 GroupDocs.Watermark for Java 预览文档
type: docs
url: /zh/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# 使用 GroupDocs.Watermark 在 Java 中预览文档

创建 **how to preview documents** 功能对于处理大量文件的任何应用程序都至关重要。使用 GroupDocs.Watermark for Java，您可以在不将整个文档加载到内存中的情况下快速生成高质量的预您将一步步了解如何设置库、管理页面流以及为文档的每一页生成预览的库是什么？** GroupDocs.Watermarkhow to preview documents*  
- **我需要用版  
- **我可以自定义输出格式吗？** 可以——您可以在 page‑stream 模板中更改文件扩展名。  
- **代码是线程安全的吗？** Watermarker 实例不是线程安全的；请为每个线程创建单独的实例。

## 在页内容。浏览 进行预览生成？
- **性能导向**：在不渲染整个文档的情况下生成页面图像。  
- **跨格式支持**：支持 PDF、Office 文件、Visio 等多种格式IRelease. **GroupDocs.Watermark Java v24.11** – 最新稳定版。  
2. Eclipse 等  

##使用 Maven 将库添加到项目中：

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

或者直接从官方页面下载 JAR：  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### 获取许可证

- **Free Trial** – 功能受限，适合测试。  
- **Temporary License** – 完整功能，适用于提供优 实指向源文档的 `Watermarker` 实例。

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

> **提示：** 将 `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` 替换为您想要预览的文件的实际路径。

### 为预览生成创建页面流

实现 `ICreatePageStream`，告诉库每个页面图像的存储位置和方式。

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

`page%s.png` 是一种 **page stream java** 模式览文件命名（例如 `page1.png`、`page2.png`）。

### 释放页面流

正确关闭流可防止内存泄漏。

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

### 生成用 `generatePreview`。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

- `createPageStream` 负责为每个预览图像创建 **page stream java**。  
- `releasePageStream` 确保在每页写入后释放资源。  

## 实际应用

- **PDF Viewer Apps** – 在打开完整文件之前显示缩略图预览。  
- **Content Management Systems** – 让编辑快速浏览文档内容。  
- **Cloud Storage Services** – 为任何上传的文件即时生成缩略图。  

## 性能考虑

- **Memory以避免将整个文档加载到 RAM 中。  
页面Batch其自己的 `Watermarker` 实例。  

## 常见问题与解决方案

| 问题 | 原因 | 解决方案 |
|------|------|----------|
| **OutOfMemoryError** | 大型文档被完整加载 | 使用流接口（如示例所示）逐页处理。 |
| **FileNotFoundException** | 输出目录路径不正确 | 确认 `YOUR_OUTPUT_DIRECTORY` 存在且可写。 |
| **Preview images are blank** | 不支持的文件格式 | 确保文档类型受 GroupDocs.Watermark 支持（例如 PDFQ: 我可以为受密码保护的文档生成预览吗？**  
A: 可以。将密码传递给接受密码字符串: 默认是 PNG，但您可以在 `FeatureCreatePageStream` 中将文件扩展名改为否PageNumber 该库在 Linux/macOS 上可用吗？**  
A: 完全可以。只要有 Java 运行时，GroupDocs.Watermark 就是跨平台的。

**Q: 批处理后如何清理临时文件？**  
A: 手动删除生成的预览文件，或实现定时清理任务。

---

**最后更新：** 2026-02-03  
**测试环境：** GroupDocs.Watermark Java 24.11  
**作者：** GroupDocs