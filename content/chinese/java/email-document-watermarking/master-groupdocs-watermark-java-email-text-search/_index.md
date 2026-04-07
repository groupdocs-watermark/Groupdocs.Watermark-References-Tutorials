---
date: '2026-04-07'
description: 学习如何使用 GroupDocs.Watermark 在 Java 中搜索电子邮件正文，包括如何搜索多个关键字的电子邮件以及如何删除电子邮件水印。
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 使用 GroupDocs.Watermark 在 Java 中搜索电子邮件正文：全面指南
type: docs
url: /zh/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# 使用 GroupDocs.Watermark 搜索电子邮件正文（Java）

如果您需要快速且可靠地 **search email body java**，您来对地方了。在本教程中，我们将演示 GroupDocs.Watermark for Java 如何帮助您定位电子邮件主题、HTML 正文和纯文本正文中的特定文本，以及如何在之后清除不需要的水印。完成后，您将能够实现一个强大的解决方案，支持单个或多个关键字，并在需要时删除电子邮件水印。

## 快速答案
- **What does “search email body java” mean?** 它指的是使用 Java 代码（配合 GroupDocs.Watermark）在电子邮件内容中查找文本。  
- **Can I search multiple keywords email at once?** 是的——创建单独的 `SearchCriteria` 对象并将它们组合起来。  
- **How to remove email watermarks?** 在搜索后使用 `PossibleWatermarkCollection.clear()` 方法移除电子邮件水印。  
- **Do I need a license?** 免费试用可用于测试；生产环境需要永久许可证。  
- **Which IDE works best?** IntelliJ IDEA 或 Eclipse 都得到完整支持。

## 您将学习的内容
- 安装并配置 GroupDocs.Watermark for Java。  
- 设置搜索条件，以 **search email body java** 跨主题和正文进行搜索。  
- 在一次运行中实现 **search multiple keywords email** 的技术。  
- 定位后执行 **how to remove email watermarks** 的确切步骤。  

## 为什么使用 GroupDocs.Watermark 搜索电子邮件正文（Java）？
GroupDocs.Watermark 提供了高级 API，抽象了解析 .msg 文件、处理不同正文格式以及管理水印的复杂性。与自行构建解析器相比，这为您节省了时间，并确保在大批量电子邮件中获得一致的结果。

## 前提条件
- Java Development Kit (JDK) 8 或更高版本。  
- Maven（或手动添加 JAR 的能力）。  
- 对 Java 和电子邮件文件格式（.msg、.eml）有基本了解。  

## 为 Java 设置 GroupDocs.Watermark
GroupDocs.Watermark for Java 简化了在文档（包括电子邮件）中添加水印和文本搜索的过程。以下是将该库添加到项目中的两种最常见方式。

### Maven 设置
在您的 `pom.xml` 文件中加入以下内容，以将 GroupDocs.Watermark 添加为依赖项：
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
或者，您可以直接从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新版本。

### 获取许可证的步骤
- **Free Trial:** 开始使用免费试用以测试基本功能。  
- **Temporary License:** 获取临时许可证以获得更长的访问权限和测试。  
- **Purchase:** 如果 GroupDocs.Watermark 满足您的需求，请考虑购买。

#### 基本初始化
按如下方式初始化 `Watermarker` 类：
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 实施指南

### 功能 1：在电子邮件正文中搜索文本
此功能可在电子邮件的主题和正文中搜索特定文本。

#### 概述
我们将演示如何使用 Java 代码配置 GroupDocs.Watermark，以搜索电子邮件消息的不同部分。

##### 步骤 1：定义文档路径
为处理电子邮件设置输入和输出路径：
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### 步骤 2：设置加载选项和 Watermarker
初始化 `EmailLoadOptions` 和 `Watermarker` 以处理您的电子邮件文档。
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### 步骤 3：创建搜索条件
定义搜索文本的条件。我们将对关键字 **"test"** 使用不区分大小写的搜索：
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### 步骤 4：指定搜索位置
配置搜索以覆盖电子邮件的主题和正文：
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### 步骤 5：执行搜索并清除水印
执行搜索并移除所有找到的水印：
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### 步骤 6：保存更改
处理完成后，将更改保存为新文档：
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### 故障排除提示
- **Common Issue:** 如果搜索结果为空，请确保文本出现在电子邮件正文或主题中。  
- **Performance Tip:** 通过仅限制搜索到实际需要的部分来优化性能。

### 功能 2：加载电子邮件文档选项
本节讨论在使用 GroupDocs.Watermark 加载电子邮件文档进行处理时，如何设置额外选项。

#### 概述
配置加载选项可更好地控制文档的处理方式，例如指定密码保护或编码设置。

##### 步骤 1：配置加载选项
以下是 `EmailLoadOptions` 的基本设置：
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 关键配置选项
- **Password Protection:** 如果您的电子邮件被加密，请指定密码。  
- **Encoding Settings:** 根据需要定义特定的编码类型。

## 如何搜索多个关键字电子邮件
如果您需要一次性定位多个词汇，请创建多个 `SearchCriteria` 对象并使用逻辑 **OR** 或 **AND** 运算符将它们组合。API 允许链式连接条件，这样您可以在不运行单独循环的情况下搜索 “invoice” **or** “receipt”。

## 如何移除电子邮件水印
定位到水印（或任何匹配您条件的文本）后，`PossibleWatermarkCollection.clear()` 方法会将其从电子邮件文档中移除。这正是我们在上文 **Step 5** 中使用的步骤，适用于任意数量的匹配项。

## 实际应用

### 用例 1：自动化电子邮件处理
自动过滤和处理大量电子邮件数据，以高效查找特定内容。

### 用例 2：法律合规检查
通过在公司电子邮件中搜索敏感信息来确保合规性。

### 用例 3：客户支持自动化
通过快速定位客户询问中的关键字或短语，简化支持工作流。

## 性能考虑因素
使用 GroupDocs.Watermark 时，请考虑以下因素以优化性能：

- **Resource Management:** 高效管理内存和处理能力，以处理大型电子邮件数据集。  
- **Java Memory Management Best Practices:** 定期监控资源使用情况并及时释放资源。

## 常见问题

**Q:** 如何使用 GroupDocs.Watermark 处理加密的电子邮件？  
**A:** 在初始化 `Watermarker` 时使用 `EmailLoadOptions` 指定密码。

**Q:** 我可以一次搜索多个关键字吗？  
**A:** 可以，创建单独的 `SearchCriteria` 实例并使用逻辑运算符将它们组合。

**Q:** GroupDocs.Watermark Java 可以免费使用吗？  
**A:** 提供免费试用；如需扩展功能，请考虑购买许可证。

**Q:** 如何高效处理大量电子邮件？  
**A:** 通过针对特定电子邮件部分进行搜索并有效管理资源来优化处理。

**Q:** 我可以在哪里找到更多帮助或支持？  
**A:** 访问 [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) 获取社区支持，或联系他们的免费支持渠道。

## 资源
- **Documentation:** 在 [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) 查看详细指南。  
- **API Reference:** 在 [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) 获取技术细节。  

---

**最后更新:** 2026-04-07  
**测试环境:** GroupDocs.Watermark 24.11 for Java  
**作者:** GroupDocs