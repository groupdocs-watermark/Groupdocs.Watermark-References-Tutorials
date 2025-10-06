---
title: 在 Word 文档中删除具有特定文本格式的形状
linktitle: 在 Word 文档中删除具有特定文本格式的形状
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 删除 Word 文档中具有特定文本格式的形状。请遵循我们的指南来有效地处理水印。
weight: 31
url: /zh/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
type: docs
---
# 在 Word 文档中删除具有特定文本格式的形状

## 介绍
GroupDocs.Watermark for .NET 是一个功能强大的 API，允许开发人员以编程方式操作各种文档格式的水印。在本教程中，我们将重点介绍使用 GroupDocs.Watermark for .NET 删除 Word 文档中具有特定文本格式的形状。无论您是经验丰富的开发人员还是刚刚起步，本分步指南都将帮助您了解高效且有效地删除形状的过程。
## 先决条件
在我们深入学习本教程之前，请确保您具备以下先决条件：
1.  GroupDocs.Watermark for .NET：确保您的开发环境中安装了 GroupDocs.Watermark for .NET 库。您可以从[网站](https://releases.groupdocs.com/Watermark/net/).
2. 开发环境：安装 Visual Studio 或任何其他 .NET IDE，设置合适的开发环境。
3. Word 文档：准备一个 Word 文档，其中包含具有要删除的特定文本格式的形状。

## 导入命名空间
在开始实现之前，让我们导入必要的名称空间：
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：加载文档
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //实施在这里
}
```
## 第 2 步：获取内容并迭代各个部分
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    //实施在这里
}
```
## 第 3 步：迭代形状并根据文本格式删除
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## 步骤 4：保存文档
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Watermark for .NET 删除 Word 文档中具有特定文本格式的形状。通过遵循分步指南并利用提供的代码示例，开发人员可以根据自己的要求轻松操作水印。
## 常见问题解答
### GroupDocs.Watermark for .NET 是否与除 Word 之外的其他文档格式兼容？
是的，GroupDocs.Watermark for .NET 支持各种文档格式，包括 Excel、PowerPoint、PDF 等。
### 我可以根据文本格式自定义删除形状的标准吗？
绝对地！您可以修改代码以针对特定的文本属性，例如字体大小、样式、颜色等。
### GroupDocs.Watermark for .NET 是否也提供添加水印的支持？
是的，除了删除之外，您还可以使用 GroupDocs.Watermark for .NET 将文本或图像水印添加到文档中。
### 购买前是否有试用版可供测试？
是的，您可以从 GroupDocs 下载免费试用版[网站](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Watermark for .NET 的技术支持或帮助？
如需技术帮助，您可以访问支持论坛：[GroupDocs.水印论坛](https://forum.groupdocs.com/c/watermark/19).