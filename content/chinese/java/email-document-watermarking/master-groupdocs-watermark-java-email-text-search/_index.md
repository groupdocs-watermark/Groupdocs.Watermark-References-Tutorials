---
date: '2025-12-31'
description: 了解如何使用 GroupDocs.Watermark for Java 搜索电子邮件文本，高效管理正文、主题和附件。
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: 使用 GroupDocs.Watermark Java 搜索电子邮件文本 – 综合指南
type: docs
url: /zh/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# 如何使用 GroupDocs.Watermark Java 搜索电子邮件文本

在电子邮件的主题、正文或附件中查找特定短语可能会让人头疼——尤其是当您需要处理数十甚至数百封邮件时。在本教程中，您将学习如何使用 **GroupDocs.Watermark for Java** 快速、准确地 **搜索电子邮件** 内容。我们将逐步演示设置、代码以及最佳实践技巧，帮助您自信地将电子邮件文本搜索集成到自己的应用程序中。

## 快速回答
- **什么库可以在 Java 中搜索电子邮件文本？** GroupDocs.Watermark for Java.  
- **我需要许可证吗？** 免费试用可用于测试；生产环境需要付费许可证。  
- **我可以同时搜索主题和正文吗？** 是的——配置 `EmailSearchableObjects` 以包含 Subject、HtmlBody 和 PlainTextBody。  
- **API 是否区分大小写？** 您可以通过在 `TextSearchCriteria` 中设置相应标志来进行不区分大小写的搜索。  
- **需要哪个 Java 版本？** JDK 8 或更高；推荐使用 Maven 进行依赖管理。

## 使用 GroupDocs.Watermark 的 “如何搜索电子邮件” 是什么？
GroupDocs.Watermark 提供统一的 API，用于在多种文档类型中定位、删除或修改水印和纯文本——包括 **电子邮件消息**（`.msg`、`.eml`）。通过利用其可搜索对象模型，您可以精准定位电子邮件中关心的部分，从而实现快速且可靠的批量处理。

## 为什么在电子邮件搜索中使用 GroupDocs.Watermark Java？
- **统一 API** – 可使用相同的代码模式处理 PDF、图像、Office 文件和电子邮件。  
- **性能优化** – 搜索操作在内存中执行，无需外部服务。  
- **强大处理能力** – 支持 HTML 和纯文本正文、附件，甚至受密码保护的电子邮件。  
- **易于集成** – 支持 Maven/Gradle，文档清晰且提供积极支持。

## 前置条件
- **Java Development Kit (JDK)** 8 或更高。  
- **Maven**（或 Gradle）用于依赖管理。  
- IDE，例如 **IntelliJ IDEA** 或 **Eclipse**。  
- 对 Java 语法和电子邮件文件格式（`.msg`、`.eml`）有基本了解。

## 为 Java 设置 GroupDocs.Watermark

### Maven 设置
将仓库和依赖添加到您的 `pom.xml` 中：

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
或者，您可以从 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) 下载最新的 JAR。

### 许可证获取
- **免费试用：** 在没有许可证密钥的情况下测试核心功能。  
- **临时许可证：** 请求一个限时密钥以进行更长时间的评估。  
- **付费许可证：** 购买后可在生产环境中无限制使用。

#### 基本初始化
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 实现指南

### 功能 1：在电子邮件正文中搜索文本

#### 概述
我们将配置 API，以在电子邮件的 **主题**、**HTML 正文** 和 **纯文本正文** 中扫描给定关键字。

#### 步骤 1：定义文档路径
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### 步骤 2：设置加载选项和 Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### 步骤 3：创建搜索条件
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### 步骤 4：指定搜索位置
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### 步骤 5：执行搜索并清除水印
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### 步骤 6：保存更改
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### 故障排除提示
- **空结果：** 确认关键字确实出现在所选的电子邮件部分中。  
- **性能：** 将可搜索对象限制为仅需要的部分（例如 Subject + PlainTextBody），以加快大批量处理速度。

### 功能 2：加载电子邮件文档选项

#### 概述
`EmailLoadOptions` 允许您控制电子邮件的解析方式——对加密消息或自定义编码非常有用。

#### 步骤 1：配置加载选项
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 关键配置选项
- **密码保护：** 对加密的 `.msg` 文件使用 `loadOptions.setPassword("yourPassword")` 设置密码。  
- **编码设置：** 处理非标准字符集时，使用 `loadOptions.setEncoding(Charset.forName("UTF-8"))` 进行调整。

## 实际应用
- **自动化电子邮件处理：** 批量扫描传入的支持工单，查找诸如 “refund” 或 “error” 等关键字。  
- **法律合规检查：** 在企业邮件存档中快速定位机密术语（例如 SSN、信用卡号）。  
- **客户支持自动化：** 根据检测到的短语将电子邮件路由到相应的支持团队。

## 性能注意事项
- **资源管理：** 完成处理后立即调用 `watermarker.close()` 以释放本机资源。  
- **内存最佳实践：** 处理成千上万的邮件时，分批处理并尽可能复用 `Watermarker` 实例。

## 结论
现在，您已经掌握了一套稳健、可用于生产环境的 **如何搜索电子邮件** 内容的方法，使用 GroupDocs.Watermark Java。该 API 的灵活性使您能够定位电子邮件的特定部分，清除不需要的水印，并将逻辑集成到更大的工作流中。

### 后续步骤
- 试验 **多搜索条件**（例如，组合 “invoice” + “overdue”）。  
- 探索 **添加水印** 以标记包含敏感数据的电子邮件。  
- 使用相同的 Watermarker 工作流深入其他文档类型（PDF、DOCX）。

## 常见问题

**Q1:** 如何使用 GroupDocs.Watermark 处理加密的电子邮件？  
**A1:** 在创建 `Watermarker` 实例之前，使用 `EmailLoadOptions.setPassword("yourPassword")`。

**Q2:** 我可以一次搜索多个关键字吗？  
**A2:** 可以——为每个关键字创建单独的 `SearchCriteria` 对象，并使用逻辑运算符（例如 `OrSearchCriteria`）将它们组合。

**Q3:** GroupDocs.Watermark Java 可以免费使用吗？  
**A3:** 提供免费试用供评估。生产环境使用需付费许可证。

**Q4:** 如何高效处理大量电子邮件？  
**A4:** 将可搜索对象限制为仅需要的部分，分批处理邮件，并始终关闭 `Watermarker` 以释放资源。

**Q5:** 我可以在哪里获得更多帮助或支持？  
**A5:** 访问 [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) 获取社区帮助，或直接联系 GroupDocs 支持。

## 资源
- **文档：** 在 [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) 查看详细指南。  
- **API 参考：** 在 [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) 获取技术细节。

---

**最后更新：** 2025-12-31  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

---