---
date: '2026-02-18'
description: 了解如何使用 GroupDocs.Watermark for Java 在 .vsdx 等图表文件中添加水印和移除水印。使用 GroupDocs
  Watermark Java 保护文档完整性。
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: 如何使用 GroupDocs.Watermark for Java 为图表添加水印
type: docs
url: /zh/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# 如何使用 GroupDocs.Watermark for Java 为图表添加水印

在图表文件中管理水印是保护知识产权和保持文档在公开分发时整洁的核心工作。在本指南中，您将学习 **如何为 Visio 图表添加水印**，以及 **在不再需要时如何删除水印**，全部使用 **groupdocs watermark java** 库。无论您是在构建企业级文档流水线，还是编写快速实用脚本，这些步骤都能让您全面掌控图表水印。

## 快速答案
- **哪个库在 Java 中处理图表水印？** GroupDocs.Watermark for Java。  
- **可以在同一次运行中同时添加和删除水印吗？** 可以 – 只需加载一次图表，即可执行添加和删除操作。  
- **支持哪些文件格式？** Visio 格式，如 `.vsdx`、`.vdx`，以及其他图表类型。  
- **需要许可证吗？** 试用许可证可用于开发；生产环境需要正式许可证。  
- **需要哪个 Java 版本？** JDK 8 或更高。

## 在图表上下文中，“如何添加水印”是什么意思？
添加水印是指在图表文件中嵌入可见或不可见的标记——文本、徽标或图片。该标记随文件一起保存，便于证明所有权或标记草稿版本。

## 为什么选择 GroupDocs.Watermark for Java？
* **丰富的 API** – 只需几行代码即可搜索、添加和删除文本及图片水印。  
* **跨格式支持** – 支持 Visio（`.vsdx`、`.vdx`）以及许多其他图表类型。  
* **性能导向** – 仅加载进行水印操作所需的图表部分，保持内存占用低。

## 前置条件
1. **Java Development Kit (JDK) 8+** – 确认 `java -version` 显示 1.8 或更高。  
2. **IDE** – IntelliJ IDEA、Eclipse 或您喜欢的任意编辑器。  
3. **GroupDocs.Watermark for Java** – 通过 Maven 或直接下载 JAR 添加到项目中。  

### 必需的库和依赖
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

*如果您不想使用 Maven，也可以从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新的 JAR。*

### 许可证获取
- **免费试用：** 在没有许可证密钥的情况下测试所有功能。  
- **临时许可证：** 申请限时密钥用于评估。  
- **正式许可证：** 购买订阅以获得无限制的生产使用权限。

## 设置 GroupDocs.Watermark for Java
1. **将库添加** 到项目（Maven 或手动 JAR）。  
2. **创建 `Watermarker` 实例** – 该对象是加载图表、搜索、添加和删除水印的入口。

## 实现指南

### 加载图表文档
加载是进行 **添加水印** 或 **删除水印** 之前的第一步。下面的代码演示了如何使用自定义加载选项打开 `.vsdx` 文件。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### 搜索文本水印
在添加新水印之前，您可能想确认是否已经存在文本水印。此代码片段搜索短语 “Company Name”。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### 搜索图片水印
如果需要定位作为水印使用的徽标或其他图片，请使用 `ImageDctHashSearchCriteria`。当您想 **删除水印** 并且已知徽标时，这非常便利。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### 删除水印
一旦识别出水印——文本、图片或两者兼有——即可将其从图表中清除。下面的示例展示了组合删除操作。

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## 实际应用场景
1. **企业软件集成** – 将水印管理嵌入 ERP 或文档生成平台，以强制品牌统一。  
2. **内容管理系统 (CMS)** – 自动扫描上传的图表，检测未授权徽标并将其剔除。  
3. **法律文档处理** – 在草稿阶段添加 “Confidential” 文本水印，随后在最终归档前 **删除水印**。

## 常见问题与解决方案
| 症状 | 可能原因 | 解决办法 |
|---------|--------------|-----|
| 未发现任何水印 | 搜索的文本/图片与实际不完全匹配 | 使用 `or()` 组合条件或调整大小写敏感设置。 |
| 大文件出现 `OutOfMemoryError` | 图表被完整加载到内存中 | 使用 `DiagramLoadOptions.setLoadPages()` 仅加载所需页面。 |
| 保存的文件损坏 | 在清除所有水印之前调用了 `watermarker.save()` | 确保 `possibleWatermarks.clear()` 完成后，再调用 `watermarker.close()` 保存。 |

## 常见问答

**问：我可以同时搜索文本和图片水印吗？**  
答：可以。将 `TextSearchCriteria` 与 `ImageDctHashSearchCriteria` 通过 `or()` 方法组合，如删除示例所示。

**问：是否可以在不损坏图表的情况下删除水印？**  
答：完全可以。库会隔离水印对象，调用 `clear()` 只会移除水印层，保留原始图表内容。

**问：GroupDocs.Watermark 支持多种图表格式吗？**  
答：支持。`.vsdx`、`.vdx` 以及其他兼容 Visio 的文件格式均可使用。

**问：如何高效处理大量文档？**  
答：实现批处理循环，尽可能复用单个 `Watermarker` 实例，并使用 `DiagramLoadOptions` 限制页面加载。

**问：是否可以在 CI/CD 流水线中自动检测水印？**  
答：可以将提供的 Java 代码片段嵌入构建脚本（如 Maven 或 Gradle），在发布制品前验证不存在未授权水印。

---

**最后更新：** 2026-02-18  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs