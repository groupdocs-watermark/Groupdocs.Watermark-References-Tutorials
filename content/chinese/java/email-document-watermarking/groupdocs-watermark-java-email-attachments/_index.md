---
date: '2025-12-29'
description: 了解如何使用 GroupDocs.Watermark for Java 为电子邮件附件添加水印。本指南提供逐步说明和最佳实践。
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: 使用 GroupDocs.Watermark for Java 为电子邮件附件添加水印
type: docs
url: /zh/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# 使用 GroupDocs.Watermark for Java 为电子邮件附件添加水印

在当今的数字环境中，保护敏感信息至关重要——尤其是在电子邮件附件离开收件箱之前**添加水印**。无论您是希望加强文档安全的开发者，还是想为每个外发文件加上品牌标识的企业，本教程将展示如何使用 GroupDocs.Watermark for Java 为电子邮件消息中的所有受支持附件应用文本水印。

## 快速答案
- **“add watermark to email” 能实现什么？** 它在每个受支持的附件中嵌入可见或半透明的标签（例如 “Confidential”），以阻止未经授权的分发。  
- **需要哪个库？** GroupDocs.Watermark for Java（最新版本）。  
- **是否需要许可证？** 试用许可证可用于开发；生产环境需要商业许可证。  
- **可以一次处理多封邮件吗？** 可以——将步骤放入遍历 *.msg* 文件夹的循环中。  
- **支持哪些文件类型？** PDF、Word、Excel、PowerPoint、图像等（详见官方文档）。

## 什么是 “add watermark to email”？
为电子邮件添加水印指的是以编程方式打开邮件文件，提取每个附件，并在这些文档上盖上自定义文本（或图像）后再发送或存储邮件。这样可确保水印随文件一起传播，强化机密性和品牌形象。

## 为什么使用 GroupDocs.Watermark for Java？
- **广泛的格式支持** – 支持 PDF、Office 文件、图像等。  
- **简洁的 API** – 几行代码即可创建、应用并保存水印。  
- **性能导向** – 内存占用低，适合服务器端处理。  
- **企业级授权** – 试用版用于评估，付费许可证用于生产。

## 前置条件
- 已安装 Java Development Kit (JDK)。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 已在项目中添加 GroupDocs.Watermark for Java（见下文设置步骤）。

## 设置 GroupDocs.Watermark for Java

### Maven 设置
如果使用 Maven，请在 `pom.xml` 中添加仓库和依赖：

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

#### 获取许可证
- 免费试用请在 GroupDocs 网站注册并申请临时许可证。  
- 商业使用请购买完整许可证。更多信息请访问 [purchase page](https://purchase.groupdocs.com/temporary-license/)。

### 基本初始化
Import the core classes you’ll need:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## 如何为电子邮件附件添加水印 – 步骤指南

### 步骤 1：创建文本水印
First, define the watermark text and its appearance.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### 步骤 2：设置电子邮件加载选项
Configure the loader so GroupDocs can read the *.msg* file.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### 步骤 3：为电子邮件文件初始化 Watermarker
Point the `Watermarker` to the email you want to process.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### 步骤 4：检索电子邮件内容
Grab the email’s internal structure so you can work with its attachments.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### 步骤 5：遍历附件
Loop through each attachment and verify that it can be watermarked.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### 步骤 6‑9：为受支持的附件添加水印
For every eligible file, open it with a new `Watermarker`, apply the watermark, and write the changes back to the email.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### 步骤 10：保存带水印的电子邮件
Write the modified email to a new file so the original remains untouched.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### 步骤 11：清理
Release resources by closing the main `Watermarker`.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## 实际应用
1. **内部文档共享** – 在内部分发前，将公司品牌或机密声明嵌入每个附件。  
2. **客户沟通** – 使用明确的 “Confidential” 标签保护合同、提案和财务报表。  
3. **电子邮件营销活动** – 为促销邮件中附带的 PDF 或图像添加细微的品牌水印，强化品牌记忆。

## 性能考虑
- **内存管理** – 一次处理一个附件，并及时关闭每个 `Watermarker`。  
- **附件大小** – 大文件会增加处理时间；考虑在加水印前压缩或限制大小。  
- **批量处理** – 遍历 *.msg* 文件目录，以在处理大量邮件时摊销开销。

## 常见问题

**问：我可以为加密文件添加水印吗？**  
答：不可以。出于安全原因，GroupDocs.Watermark 不支持对加密文档加水印。

**问：支持哪些文件类型的水印？**  
答：PDF、Word、Excel、PowerPoint、图像（PNG、JPEG、BMP）以及许多其他常见格式。完整列表请参见官方文档。

**问：如何自定义水印的外观？**  
答：可以使用 `TextWatermark` 构造函数及其属性更改字体、大小、颜色、不透明度、旋转角度和位置。

**问：是否可以批量处理多封邮件？**  
答：可以。将步骤放入遍历 *.msg* 文件夹的 `for` 循环中，对每封邮件应用相同逻辑。

**问：我的水印没有显示——我应该检查什么？**  
答：确认附件的文件类型受支持，确保水印尺寸适合页面尺寸，并确认文档未受密码保护。

## 资源
- [文档](https://docs.groupdocs.com/watermark/java/)  
- [API 参考](https://reference.groupdocs.com/watermark/java)  
- [下载 GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

---

**最后更新：** 2025-12-29  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs