---
title: 添加文字水印
linktitle: 添加文字水印
second_title: GroupDocs.Watermark .NET API
description: 通过此分步指南，了解如何使用 Groupdocs for .NET 将文本水印添加到文档中。
type: docs
weight: 11
url: /zh/net/watermarking-basics/add-text-watermark/
---
## 介绍
GroupDocs.Watermark for .NET 是一个功能强大的库，允许开发人员在 .NET 应用程序中的各种文档格式中添加、搜索和删除水印。在本教程中，我们将重点介绍如何使用 GroupDocs.Watermark 将文本水印添加到文档中。
## 先决条件
在我们开始之前，请确保您具备以下先决条件：
1. C# 编程语言的基础知识。
2. Visual Studio 安装在您的系统上。
3. 安装了 .NET 库的 GroupDocs.Watermark。您可以从以下位置下载：[这里](https://releases.groupdocs.com/Watermark/net/).

## 导入命名空间
首先，您需要将必要的命名空间导入到您的 C# 项目中。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 第1步：定义文档路径和输出目录
定义输入文档的路径和保存带水印文档的输出目录。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`输入文档的绝对或相对路径，例如：`@"C:\Docs\document.pdf"`。另外，指定要保存带水印的文档的目录。
## 第2步：添加文字水印
实例化`Watermarker`带有输入文档路径的类。然后，创建一个`TextWatermark`具有所需文本和字体设置的对象。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Watermark for .NET 将文本水印添加到文档中。凭借其直观的 API，开发人员可以轻松操作各种文档格式的水印。
## 常见问题解答
### GroupDocs.Watermark for .NET 是否与所有文档格式兼容？
GroupDocs.Watermark 支持多种文档格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以自定义文本水印的外观吗？
是的，您可以自定义文本水印的各种属性，例如字体、颜色、对齐方式和不透明度。
### GroupDocs.Watermark 是否支持从文档中删除水印？
是的，GroupDocs.Watermark 提供了搜索和删除文档水印的功能。
### 我可以在购买前试用 GroupDocs.Watermark for .NET 吗？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Watermark 的技术支持？
您可以通过访问获得技术支持[GroupDocs.Watermark 论坛](https://forum.groupdocs.com/c/watermark/19).