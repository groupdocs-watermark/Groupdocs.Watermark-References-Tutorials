---
date: '2026-01-21'
description: 了解如何在 Java 中为 GroupDocs Watermark 设置许可证，包括如何为 PDF 添加水印以及如何使用计量许可证管理使用情况。
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: 如何在 Java 中为 GroupDocs Watermark（计量版）设置许可证
type: docs
url: /zh/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# 如何在 Java 中为 GroupDocs Watermark（计量）设置许可证

保护知识产权是现代企业的首要任务，水印是行之有效的方式。在本教程中，您将学习**如何设置许可证**，使用计量方式为 GroupDocs.Watermark 设置许可证，从而能够**为 PDF 文件添加水印**，并全面控制使用情况。我们将从前置条件到实际使用场景逐步讲解，并准确展示在何处**使用公私钥**来激活许可证。

## 快速答案
- **什么是计量许可证？** 基于使用量的授权模型，会跟踪每一次 API 调用。  
- **我需要许可证文件吗？** 不需要——您可以使用公钥和私钥进行激活。  
- **需要哪个 Java 版本？** Java 8 或更高版本。  
- **我可以为 PDF 文档添加水印吗？** 可以，API 支持 PDF、DOCX、PPTX 和图像。  
- **此方法安全吗？** 安全，密钥通过 HTTPS 传输，且从不以明文形式存储。  

## 什么是计量许可证以及为何使用它？
计量许可证让您仅为实际消耗的资源付费，非常适合 SaaS 或微服务架构。它提供**文档安全水印**功能，无需管理传统许可证文件的负担，并且可以即时上下扩展使用量。

## 前置条件
在开始之前，请确保您拥有：

1. **GroupDocs.Watermark for Java** ≥ 24.11（最新发布）。  
2. 已安装 **JDK 8+** 并配置 `JAVA_HOME`。  
3. 从您的 GroupDocs 账户获取的 **公钥和私钥**（将在代码中使用）。  

## 设置 GroupDocs.Watermark for Java

### 安装信息
将 GroupDocs.Watermark 集成到您的 Maven 项目中：

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

> **提示：** 相同的仓库 URL 也用于下面的直接下载选项。

#### 直接下载
从官方发布页面获取最新的 JAR： [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)。

### 许可证获取
要解锁高级功能，您需要临时或试用许可证。请在 [GroupDocs 网站](https://purchase.groupdocs.com/temporary-license/) 注册，并复制他们提供的公钥/私钥。

### 基本初始化
将库加入类路径后，您可以进行初始化：

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **为何重要：** 即使使用计量许可证，初始化 `License` 对象也能确保 SDK 在后续工作流中准备好接受基于密钥的激活。

## 实施指南

### 设置计量许可证

#### 第一步：定义公钥和私钥
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
这些密钥**使用公私钥**来安全地标识您的账户。

#### 第二步：创建 Metered 类的实例
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
`Metered` 类在后台处理所有使用量跟踪。

#### 第三步：使用提供的密钥设置计量许可证
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
调用此方法后，SDK 完全获得许可证，您即可开始**为 PDF 文件添加水印**或**创建带水印的文档**。

### 为何使用公私钥而非许可证文件？
- **安全性：** 密钥从不以明文形式写入磁盘。  
- **灵活性：** 在不同环境（开发、测试、生产）之间切换，无需复制文件。  
- **可扩展性：** 适用于容器不可变的云原生部署。  

## 实际应用

1. **文档安全：** 在 PDF 中嵌入可见或不可见的水印，以阻止未经授权的分发。  
2. **使用量跟踪：** 监控每月处理的文档数量，帮助您保持在计量配额范围内。  
3. **CMS 集成：** 自动在内容管理系统中对每个上传的文件**应用 PDF 水印**。  

## 性能考虑

- **仅在需要时应用水印**——避免不必要的大批量处理。  
- **在请求之间复用 `Metered` 实例**，以降低对象创建开销。  
- **监控内存**，在处理高分辨率图像时；SDK 提供流式 API 以保持占用低。  

## 常见问题及解决方案
| 问题 | 解决方案 |
|------|----------|
| 密钥被拒绝 | 再次检查字符串中是否没有多余的空格或换行。 |
| 许可证未激活 | 确保在任何水印操作 **之前** 调用 `metered.setMeteredKey(...)`。 |
| 大 PDF 导致内存不足错误 | 使用 `WatermarkOptions.setUseMemoryCache(true)` 将处理卸载到磁盘。 |

## 常见问答

**问：什么是计量许可证，为什么要使用它？**  
A: 计量许可证会跟踪每一次 API 调用，让您仅为实际使用付费，并且可以轻松扩展应用程序。

**问：我可以在试用许可证文件和计量密钥之间切换吗？**  
A: 可以。只需对试用调用 `license.setLicense("path/to/file.lic")`，随后再用 `metered.setMeteredKey(...)` 替换即可。

**问：如果我的公钥或私钥输入错误会怎样？**  
A: SDK 将抛出身份验证异常，阻止访问高级功能。

**问：每月可以添加多少水印有限制吗？**  
A: 限制取决于您与 GroupDocs 的协议；请在仪表盘查看具体配额。

**问：这是否同样适用于图像文件而不仅是 PDF？**  
A: 当然。相同的 API 支持 JPEG、PNG、BMP 以及其他常见图像格式。

## 资源

- [文档](https://docs.groupdocs.com/watermark/java/)
- [API 参考](https://reference.groupdocs.com/watermark/java)
- [下载](https://releases.groupdocs.com/watermark/java/)
- [GitHub 仓库](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/watermark/10)
- [临时许可证获取](https://purchase.groupdocs.com/temporary-license/)

---

**最后更新：** 2026-01-21  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs