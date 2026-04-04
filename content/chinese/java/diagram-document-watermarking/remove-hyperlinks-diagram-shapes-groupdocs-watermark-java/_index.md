---
date: '2026-04-04'
description: 了解如何使用 GroupDocs.Watermark Java 从图表形状中去除链接，确保文档安全和清晰。
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: 如何使用 GroupDocs.Watermark Java 从图表形状中剥离链接
type: docs
url: /zh/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 从图表形状中剥离链接

管理数字文档通常涉及编辑图表，尤其是当您需要**剥离链接**以提升安全性或清晰度时。在本教程中，您将学习一种简单、逐步的方式，使用强大的 **GroupDocs.Watermark** 库（Java）从图表形状中删除不需要的超链接。完成后，您将拥有干净、无链接的图表，安全可共享。

## 快速答案
- **“how to strip links” 是什么意思？** 它指的是删除嵌入在图表形状中的超链接对象。  
- **哪个库处理此操作？** GroupDocs.Watermark for Java (version 24.11 or newer)。  
- **我需要许可证吗？** 免费试用可用于测试；生产环境需要有效许可证。  
- **我可以一次处理多个文件吗？** 可以——将代码包装在循环或批处理作业中。  
- **此方法是否特定于某种语言？** 示例使用 Java，但相同概念适用于其他 .NET/Java API。

## 在图表编辑中，“剥离链接”是什么？
剥离链接是指定位附加在图表（例如 Visio *.vsdx）形状上的超链接对象并将其删除。这可以消除可能泄露敏感信息或破坏演示流程的外部 URL。

## 为什么使用 GroupDocs.Watermark for Java？
- **Precision** – 直接访问形状对象及其超链接集合。  
- **Performance** – 为大型图表优化，无需将整个文档加载到内存中。  
- **Cross‑format support** – 支持多种图表格式（Visio、Draw.io 等）。

## 前置条件
- **GroupDocs.Watermark** 库 ≥ 24.11。  
- Maven（或手动 JAR 引入）。  
- Java JDK 8 或更高版本。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。

## 设置 GroupDocs.Watermark for Java
### Maven 设置
将仓库和依赖添加到您的 `pom.xml`：

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
如果您不想使用 Maven，可从官方网站获取最新的 JAR：  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### 获取许可证步骤
- 开始下载免费试用版。  
- 生产环境请从 GroupDocs 门户获取临时或完整许可证。

#### 基本初始化和设置
创建指向包含图表的文件夹的 `Watermarker` 实例：

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 如何从图表形状中剥离链接
下面是一个简洁的四步流程，展示了 **remove hyperlinks java** 的实际操作。

### 步骤 1：加载图表文件
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*为什么？* 加载文件后，您可以以编程方式访问其页面、形状和超链接集合。

### 步骤 2：访问形状内容
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*为什么？* 您需要获取可能包含超链接的特定形状的引用。

### 步骤 3：遍历并删除超链接
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*为什么？* 逆向遍历可防止在从集合中删除项目时出现索引偏移问题。

### 步骤 4：保存并关闭
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*为什么？* 保存将清理后的图表写入磁盘，关闭则释放文件句柄以避免内存泄漏。

## 剥离链接的实际应用
1. **Security** – 删除可能导致网络钓鱼或数据泄露的外部 URL。  
2. **Compliance** – 确保图表在分发前符合内部政策。  
3. **Presentation Cleanliness** – 消除分散观众注意力的不必要可点击区域。

## 性能考虑因素
- **Loop Efficiency** – 使用上面展示的逆向遍历模式。  
- **Resource Management** – 优先使用 `try‑with‑resources` 或显式的 `close()` 调用。  
- **Large Files** – 监控 CPU/内存；考虑批量处理页面。

## 常见问题及解决方案
- **No hyperlinks found** – 验证图表确实包含超链接对象；某些格式的存储方式不同。  
- **IndexOutOfBoundsException** – 删除集合项时始终逆向遍历。  
- **License errors** – 确保许可证文件放置正确或传递给 `Watermarker` 构造函数。

## 常见问答
**Q: 如何处理多页上的多个形状？**  
A: 遍历 `content.getPages()`，然后遍历每页的 `getShapes()` 集合，对每个形状应用相同的删除逻辑。

**Q: 我可以按域名而非完整 URL 过滤链接吗？**  
A: 可以——将 `contains` 检查改为匹配域名字符串（例如 `"example.com"`）。

**Q: 有办法记录被删除的链接吗？**  
A: 在循环中，在删除前获取 `shape.getHyperlinks().get_Item(i).getAddress()` 并写入日志文件。

**Q: 这适用于嵌入其他文档的 PDF 图表吗？**  
A: GroupDocs.Watermark 支持多种格式；请确保文件类型被识别为图表（Visio、VDX 等）。

**Q: 批量处理需要什么许可证？**  
A: 任何非试用的高容量操作都需要完整的生产许可证。

## 结论
您现在拥有使用 GroupDocs.Watermark for Java 从图表形状中 **剥离链接** 的完整、可投入生产的方法。将其整合到文档处理流水线中，可提升安全性、合规性和视觉质量。

### 接下来的步骤
- 探索其他操作功能，例如添加水印或盖章文本。  
- 将此例程与文件监视服务结合，实现图表上传时自动清理。

---

**最后更新：** 2026-04-04  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

## 资源
- [文档](https://docs.groupdocs.com/watermark/java/)
- [API 参考](https://reference.groupdocs.com/watermark/java)
- [下载](https://releases.groupdocs.com/watermark/java/)
- [GitHub 仓库](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/watermark/10)
- [临时许可证获取](https://purchase.groupdocs.com/temporary-license/)