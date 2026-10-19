---
date: '2025-12-19'
description: 了解如何使用 GroupDocs.Watermark Java 从图表形状中删除超链接，这是实现 Java 文档安全和批量删除超链接的关键步骤。
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: 如何使用 GroupDocs.Watermark Java 删除图表形状中的超链接
type: docs
url: /zh/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 删除图表形状中的超链接

管理数字文档通常涉及编辑图表，尤其是在出于安全或清晰度的考虑**删除超链接**时。在本教程中，您将学习如何使用 GroupDocs.Watermark for Java **删除图表形状中的超链接**，确保您的文件保持干净、安全且专业。

## 快速答案
- **主要目的是什么？** 从图表形状中剥离不需要的超链接，以提升文档安全性。  
- **使用哪个库？** GroupDocs.Watermark for Java（版本 24.11 或更高）。  
- **需要许可证吗？** 试用版可用于测试；生产环境需要有效许可证。  
- **可以一次处理多个文件吗？** 可以——相同的逻辑可以放在批处理循环中。  
- **Java 8 足够吗？** 支持 Java 8+，推荐使用更新的 JDK。

## 在图表上下文中，“如何删除超链接”是什么意思？
删除超链接是指删除附加在图表文件（例如 Visio *.vsdx）中的形状上的 URL 引用。此操作可防止意外跳转到外部站点，并有助于满足合规或内部安全策略。

## 为什么在此任务中使用 GroupDocs.Watermark Java？
- **强大的格式支持** – 兼容多种图表类型。  
- **细粒度 API** – 让您能够定位单个形状及其超链接集合。  
- **性能优化** – 适用于单文件和批量处理。

## 前置条件
- **GroupDocs.Watermark** 库版本 24.11 或更高。  
- Maven 或直接下载 JAR（请参阅下面的设置步骤）。  
- Java Development Kit（JDK 8 或更高）以及 IntelliJ IDEA 或 Eclipse 等 IDE。

## 为 Java 设置 GroupDocs.Watermark
首先，通过 Maven 或下载 JAR 将库包含到项目中。

### Maven 设置
将以下配置添加到您的 `pom.xml` 中：

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
- 先使用免费试用版评估 API。  
- 生产环境请从 GroupDocs 门户获取临时或正式许可证。

#### 基本初始化和设置
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 如何删除图表形状中的超链接
下面提供一步步指南，帮助您加载图表、定位形状并剥离不需要的超链接。

### 步骤 1：加载图表文件
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*为什么？* 加载文件可让您以编程方式访问其内部结构。

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
*为什么？* 逆向遍历可防止在删除集合项时出现索引错误。

### 步骤 4：保存并关闭
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*为什么？* 持久化更改并释放资源可避免内存泄漏和文件锁定。

## 批量删除超链接（高级用例）
如果需要一次清理大量图表，可将上述逻辑包装在遍历文件路径列表的循环中。相同的 API 调用仍然适用，只需为每次迭代更改输入和输出目录即可。此方法符合 **batch remove hyperlinks** 在大型文档库中的需求。

## 实际应用
删除图表形状中的超链接在多个真实场景中都有帮助：

1. **安全目的** – 防止外部链接导致网络遭受钓鱼或恶意软件攻击。  
2. **合规** – 符合禁止在共享文档中出现外部 URL 的公司政策。  
3. **清晰度** – 生成更简洁的演示文稿，避免不必要或分散注意力的超链接。

## 性能考虑
### 优化性能
- 使用上文展示的逆向遍历模式以保持循环高效。  
- 完成后尽快关闭 `Watermarker` 对象以释放内存。

### 资源使用指南
- 处理大型图表时监控 CPU 和内存使用情况。  
- 对于批量任务，考虑流式读取文件，而不是一次性全部加载。

### Java 内存管理最佳实践
- 避免在紧密循环中创建对象。  
- 在适用的情况下使用 try‑with‑resources 实现自动清理。

## 常见问题
1. **如何处理多个形状？**  
   遍历所有页面及其形状，对每个形状应用相同的超链接删除逻辑。  

2. **此过程能否自动化处理大量图表？**  
   可以——将代码嵌入批处理例程或与文档管理系统集成。  

3. **如果只需要从特定页面删除超链接怎么办？**  
   通过索引 (`content.getPages().get_Item(pageIndex)`) 访问所需页面，仅针对该页面的形状进行操作。  

4. **生产环境使用 GroupDocs.Watermark 是否需要许可证？**  
   试用期结束后需要有效的商业许可证。  

5. **此方法能否用于其他图表格式？**  
   GroupDocs.Watermark 支持多种图表类型；请在官方文档中确认兼容性。  

**Additional Q&A**

**Q:** *是否可以记录被删除的超链接？*  
**A:** 可以——在调用 `removeAt(i)` 之前，获取 `shape.getHyperlinks().get_Item(i).getAddress()` 并写入日志文件。

**Q:** *删除超链接会影响形状的视觉外观吗？*  
**A:** 不会。形状的几何形状保持不变，仅删除链接元数据。

**Q:** *删除后是否需要重新应用任何样式？*  
**A:** 通常不需要。超链接的删除不会改变填充、线条或文字样式。

## 结论
您现在拥有一套完整的、可用于生产环境的 **如何删除超链接** 方法，使用 GroupDocs.Watermark for Java 对图表形状进行处理。按照上述步骤操作，即可保护图表安全、符合政策要求，并保持文档的专业外观。

**资源**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**最后更新：** 2025-12-19  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  
