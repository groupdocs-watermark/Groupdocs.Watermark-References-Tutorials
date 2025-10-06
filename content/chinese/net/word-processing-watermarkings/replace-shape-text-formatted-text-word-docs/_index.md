---
title: 在 Word 文档中将形状文本替换为格式化文本
linktitle: 在 Word 文档中将形状文本替换为格式化文本
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 将 Word 文档中的形状文本替换为格式化文本。您的文档编辑功能毫不费力。
weight: 34
url: /zh/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
type: docs
---
# 在 Word 文档中将形状文本替换为格式化文本

## 介绍
在本教程中，我们将指导您完成使用 GroupDocs.Watermark for .NET 将 Word 文档中的形状文本替换为格式化文本的过程。该库提供了处理水印的强大功能，包括替换形状中的文本。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1.  GroupDocs.Watermark for .NET：确保您已安装并设置 GroupDocs.Watermark for .NET。您可以从以下位置下载：[这里](https://releases.groupdocs.com/Watermark/net/).
2. 文档路径：您应该拥有要替换文本的 Word 文档的路径。

## 导入命名空间
在编写代码之前，导入必要的命名空间：
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：加载文档
使用以下命令加载 Word 文档`Watermarker`班级：
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //您的代码在这里继续...
}
```
## 第 2 步：获取内容并替换文本
加载文档后，获取内容并替换形状中的文本：
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## 第 3 步：保存文档
替换文本后，保存修改后的文档：
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 结论
使用 GroupDocs for .NET，可以轻松地用 Word 文档中的格式化文本替换形状文本。通过遵循本教程中概述的步骤，您可以有效地管理和操作文档中的文本。

## 常见问题解答
### 我可以使用 GroupDocs.Watermark for .NET 替换其他类型文档中的文本吗？
是的，GroupDocs 支持多种文档格式，例如 PDF、Excel、PowerPoint 等。
### GroupDocs.Watermark 与 .NET Core 兼容吗？
是的，GroupDocs.Watermark 同时支持 .NET Framework 和 .NET Core。
### GroupDocs.Watermark 是否支持添加图像作为水印？
当然，GroupDocs.Watermark 允许您向文档添加文本和图像水印。
### 我可以自定义使用 GroupDocs.Watermark 添加的水印的外观吗？
是的，您可以完全控制水印的外观、位置和其他属性。
### GroupDocs.Watermark for .NET 是否有试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).