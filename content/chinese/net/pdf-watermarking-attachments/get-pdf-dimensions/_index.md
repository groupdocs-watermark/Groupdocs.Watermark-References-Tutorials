---
title: 获取 PDF 尺寸
linktitle: 获取 PDF 尺寸
second_title: GroupDocs.Watermark .NET API
description: 使用 Groupdocs.Watermark for .NET 轻松保护您的文档。轻松添加水印、图章和注释。
type: docs
weight: 26
url: /zh/net/pdf-watermarking-attachments/get-pdf-dimensions/
---
## 介绍
在当今的数字时代，保护您的文档至关重要。无论您是商业专业人士、法律专家还是创意艺术家，保护您的知识产权都是至关重要的。 Groupdocs.Watermark for .NET 提供了一个强大的解决方案，可以向文档添加水印、图章和注释，确保其安全性和真实性。
## 先决条件
在深入了解 .NET 的 Groupdocs.Watermark 世界之前，请确保满足以下先决条件：
1. 安装 Groupdocs.Watermark for .NET：从以下位置下载并安装 Groupdocs.Watermark for .NET[下载链接](https://releases.groupdocs.com/Watermark/net/).
2. 许可证密钥（可选）：虽然 Groupdocs.Watermark for .NET 提供免费试用版，但您可以选择临时许可证或从以下位置购买完整许可证：[这里](https://purchase.groupdocs.com/buy)用于扩展功能。
3. 熟悉 C#：建议具备 C# 编程语言的基本知识，以理解和实现所提供的示例。
4. 要保护的文档：在本地计算机上准备好示例文档（例如 PDF、Word、Excel）以进行试验。

## 导入命名空间
要开始使用 Groupdocs.Watermark for .NET，您需要将必要的命名空间导入到您的 C# 项目中。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### 第 1 步：声明变量
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### 第 2 步：加载文档
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### 第 3 步：获取 PDF 内容
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### 第 4 步：检索尺寸
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## 结论
总之，Groupdocs.Watermark for .NET 提供了一个全面的解决方案来保护您的文档免遭未经授权的使用和分发。通过执行上述步骤并利用 Groupdocs.Watermark for .NET 的强大功能，您可以确保宝贵数字资产的安全性和完整性。
## 常见问题解答
### 我可以免费使用 Groupdocs.Watermark for .NET 吗？
是的，Groupdocs.Watermark for .NET 提供免费试用版用于评估目的。但是，对于扩展功能，您可以考虑购买完整许可证。
### Groupdocs.Watermark 支持多种文档格式吗？
是的，Groupdocs 支持多种文档格式，包括 PDF、Word、Excel、PowerPoint 等。
### 我可以使用 Groupdocs.Watermark 自定义水印和图章吗？
绝对地！ Groupdocs.Watermark 提供了广泛的水印、图章和注释自定义选项，以满足您的特定要求。
### Groupdocs.Watermark 用户可以获得技术支持吗？
是的，您可以通过以下方式获得技术援助并与 Groupdocs 社区互动：[支持论坛](https://forum.groupdocs.com/c/watermark/19).
### 如何获得 Groupdocs.Watermark 的临时许可证？
您可以从以下位置获取 Groupdocs.Watermark 的临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).