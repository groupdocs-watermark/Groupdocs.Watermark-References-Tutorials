---
date: '2025-12-19'
description: 学习如何使用 GroupDocs Watermark Maven 在 Java 中管理 .vsdx 等图表文件的水印，提升文档完整性并保护知识产权。
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – 使用 Java 管理图表水印
type: docs
url: /zh/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – 使用 Java 管理图表水印

在文档中管理水印对于保护知识产权和维护文档完整性至关重要。**在本教程中，我们将展示如何使用 groupdocs watermark maven 高效地加载、搜索和删除 `.vsdx` 等图表文件中的水印**。无论您是在构建企业软件还是自动化文档工作流，掌握这些技术都能让您全面掌控图表水印管理。

## 快速答案
- **需要哪个库？** GroupDocs.Watermark for Java（通过 Maven 可获取）。  
- **支持哪些图表格式？** `.vsdx`、`.vdx` 以及其他 Visio 格式。  
- **可以同时搜索文本和图片水印吗？** 是的 – 使用 `or()` 组合搜索条件。  
- **生产环境需要许可证吗？** 需要有效的 GroupDocs.Watermark 许可证。  
- **如何将其集成到 Maven 中？** 添加下面显示的仓库和依赖。

## 什么是 groupdocs watermark maven？
`groupdocs watermark maven` 指的是基于 Maven 的 GroupDocs.Watermark Java 库集成。通过在 `pom.xml` 中声明该库，Maven 会自动解析所有必需的二进制文件，让您专注于加载图表、搜索水印并以编程方式删除它们的代码。

## 为什么在图表水印管理中使用 GroupDocs.Watermark？
- **功能完整的 API** – 支持多种图表类型的文本、图片和形状水印。  
- **精准删除** – 在不破坏原始图表布局的情况下消除水印。  
- **可扩展** – 适用于批量处理大量图表。  
- **Maven 友好** – 简单的依赖管理，使项目保持整洁。

## 前置条件
1. **Java Development Kit (JDK) 8+** – 确保与库兼容。  
2. **IDE** – IntelliJ IDEA、Eclipse 或任何兼容 Java 的编辑器。  
3. **GroupDocs.Watermark for Java** – 通过 Maven（推荐）或直接下载 JAR 添加。  

### 必需的库和依赖
#### Maven 设置
将以下配置添加到您的 `pom.xml` 文件中：

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

#### 直接下载
或者，从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新版本。

### 许可证获取
- **免费试用：** 使用试用许可证测试库。  
- **临时许可证：** 申请短期密钥进行评估。  
- **购买：** 获取用于无限制使用的生产许可证。

## 使用 groupdocs watermark maven 加载图表文档
加载图表文档是进行任何水印操作的第一步。下面是一个最小示例，创建了带有 `DiagramLoadOptions` 的 `Watermarker` 实例。

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

- **参数：**  
  - `inputFilePath` – 您的 `.vsdx` 文件路径。  
  - `loadOptions` – 允许您控制图表的解析方式（例如，密码保护）。

## 使用 groupdocs watermark maven 搜索水印
### 文本水印
要定位基于文本的水印，定义 `TextSearchCriteria` 并查询图表的第一页。

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

- **关键方法：**  
  - `TextSearchCriteria` – 指定要查找的确切文本。  
  - `PossibleWatermarkCollection` – 存储找到的所有匹配项。

### 图片水印
如果您的图表包含徽标或图片水印，请使用 `ImageDctHashSearchCriteria` 与参考图像进行比较。

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

- **关键方法：**  
  - `ImageDctHashSearchCriteria` – 为参考图像创建感知哈希，以实现稳健匹配。

## 删除水印
一旦识别出不需要的水印，您可以将其清除并保存图表的干净副本。

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

- **关键方法：** `clear()` 删除通过组合条件找到的所有水印，保持图表完整。

## 实际应用
1. **企业软件集成** – 将水印管理嵌入业务应用，以保护专有图表。  
2. **内容管理系统（CMS）** – 在发布前自动检测并删除未授权的徽标。  
3. **法律文档工作流** – 在合同处理的不同阶段添加或去除水印。  

## 常见问题与故障排除
- **许可证错误：** 在创建 `Watermarker` 之前，确保正确引用许可证文件。  
- **大文件：** 对于大于 100 MB 的图表，使用流式 API 或增加 JVM 堆大小（`-Xmx2g`）。  
- **未检测到水印：** 确认搜索条件（文本大小写、图像相似度阈值）与实际水印内容匹配。

## 常见问答

**问：我可以同时搜索文本和图片吗？**  
答：可以。像删除示例中那样使用 `or()` 组合条件。

**问：删除水印是否会影响图表布局？**  
答：完全不会。API 精准定位水印对象，保留所有其他图表元素。

**问：GroupDocs.Watermark 支持哪些图表格式？**  
答：支持 Visio 格式，如 `.vsdx`、`.vdx`，以及其他矢量图表类型。

**问：如何高效处理数百个图表？**  
答：实现批处理循环，尽可能复用单个 `Watermarker` 实例，并考虑使用 Java 的 `ExecutorService` 进行并行处理。

**问：我可以将水印检测集成到 CI/CD 流水线吗？**  
答：可以。将 Java 代码片段加入构建脚本（如 Maven 插件或 Gradle 任务），在部署前验证图表。

## 结论
通过使用 **groupdocs watermark maven**，您可以获得一种强大且由 Maven 管理的方式，使用 Java 加载、搜索和删除图表文件中的水印。这一能力提升了文档安全性，简化了内容工作流，并能轻松在大型文档集合中扩展。

---

**最后更新：** 2025-12-19  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

---