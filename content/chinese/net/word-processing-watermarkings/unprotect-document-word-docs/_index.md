---
title: 取消保护 Word 文档中的文档
linktitle: 取消保护 Word 文档中的文档
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 轻松取消对 Word 文档的保护。请遵循我们的分步指南。
type: docs
weight: 38
url: /zh/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## 介绍
GroupDocs.Watermark for .NET 是一个功能强大的 API，允许开发人员使用各种文档格式（包括 Word 文档）的水印。在本教程中，我们将指导您完成使用 GroupDocs.Watermark for .NET 取消保护 Word 文档的过程。无论您是经验丰富的开发人员还是刚刚开始 .NET 开发，本分步指南都将帮助您高效地完成任务。
## 先决条件
在我们开始之前，请确保您具备以下先决条件：
1.  GroupDocs.Watermark for .NET：您需要在开发环境中安装 GroupDocs.Watermark for .NET API。您可以从以下位置下载：[这里](https://releases.groupdocs.com/Watermark/net/).
2. 开发环境：确保您为 .NET 开发设置了合适的开发环境，包括 Visual Studio 或任何其他兼容的 IDE。
3. Word 文档：在文件系统中准备好要取消保护的 Word 文档。

## 导入命名空间
在深入研究代码之前，您需要将必要的命名空间导入到您的 .NET 项目中。这使您可以无缝访问 GroupDocs.Watermark for .NET 提供的功能。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## 第1步：指定文档路径
定义要取消保护的 Word 文档的路径。
```csharp
string documentPath = "Your Document Path";
```
代替`"Your Document Path"`与 Word 文档的实际路径。
## 第2步：设置输出文件名
指定要保存未受保护文档的目录并提供输出文件的名称。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
代替`"Your Document Directory"`与要保存输出文件的目录路径。
## 第 3 步：加载带有选项的文档
创建一个实例`WordProcessingLoadOptions`使用特定选项加载 Word 文档。
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 步骤 4：取消文档保护
实例化`Watermarker`具有文档路径和加载选项的类。然后，获取文档内容作为 WordProcessingContent 并取消保护。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## 结论
通过执行以下步骤，您可以使用 GroupDocs.Watermark for .NET 轻松取消对 Word 文档的保护。此 API 提供了一种简单的方法来操作水印并有效地保护您的文档。
## 常见问题解答
### GroupDocs.Watermark for .NET 是否与所有版本的 .NET 兼容？
是的，GroupDocs.Watermark for .NET 与 .NET Framework 2.0 及更高版本兼容，包括 .NET Core 和 .NET Standard。
### 我可以为除 Word 之外的其他格式的文档添加水印吗？
绝对地！ GroupDocs.Watermark for .NET 支持多种文档格式，包括 PDF、Excel、PowerPoint 等。
### GroupDocs.Watermark for .NET 是否有试用版？
是的，您可以从以下位置获取免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Watermark for .NET 的技术支持？
您可以访问[GroupDocs.Watermark 论坛](https://forum.groupdocs.com/c/watermark/19)寻求技术援助和社区支持。
### 我可以购买 GroupDocs.Watermark for .NET 的临时许可证吗？
是的，您可以从以下位置购买临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).