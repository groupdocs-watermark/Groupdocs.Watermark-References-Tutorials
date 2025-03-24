---
title: 删除 Word 文档中的形状
linktitle: 删除 Word 文档中的形状
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 从 Word 文档中删除形状。简单、高效、强大的文档操作。
weight: 30
url: /zh/net/word-processing-watermarkings/remove-shape-word-docs/
---
## 介绍
在文档处理和操作领域，GroupDocs.Watermark for .NET 作为一个强大的工具集出现，使开发人员能够将水印功能无缝集成到他们的 .NET 应用程序中。本文深入探讨了利用 GroupDocs.Watermark for .NET 删除 Word 文档中的形状的复杂性。通过遵循分步指南，开发人员可以轻松高效地掌握该过程。
## 先决条件
在开始使用 GroupDocs.Watermark for .NET 在 Word 文档中去除形状之前，请确保满足以下先决条件：
### 1. 获取 .NET 的 GroupDocs.Watermark
首先获取 GroupDocs.Watermark for .NET 库。您可以从以下位置下载该库[发布页面](https://releases.groupdocs.com/Watermark/net/).
### 2.熟悉.NET开发
对 .NET 开发的基本了解至关重要。确保您精通 C# 编程，并基本掌握使用 .NET 生态系统中的库和依赖项。
### 3.集成开发环境（IDE）
在系统上安装 Visual Studio 等 IDE，为 .NET 开发提供有利的环境。 
### 4.Word文档示例
准备一个包含要删除的形状的示例 Word 文档。本文档将作为您实施的试验场。

## 导入命名空间
要使用 GroupDocs.Watermark for .NET 启动 Word 文档中的形状删除过程，请将必要的命名空间导入到您的项目中：
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## 第 1 步：加载文档
首先指定要操作的 Word 文档的路径，并为处理后的文档创建输出文件名：
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 第2步：初始化水印
初始化一个`Watermarker`通过传递文档路径和可选加载选项来对象：
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 第 3 步：访问文档内容
检索 Word 文档的内容以访问其部分和形状：
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## 步骤 4：按索引删除形状
通过指定形状在文档中的索引来从文档中删除形状`Shapes`收藏：
```csharp
content.Sections[0].Shapes.RemoveAt(0);
```
## 第 5 步：通过参考删除形状
或者，通过在`Shapes`收藏：
```csharp
content.Sections[0].Shapes.Remove(content.Sections[0].Shapes[0]);
```
## 第 6 步：保存文档
将修改后的文档保存到指定的输出文件中：
```csharp
watermarker.Save(outputFileName);
```

## 结论
总之，GroupDocs.Watermark for .NET 使开发人员能够轻松操作 Word 文档。通过遵循此分步指南，您可以无缝地从 Word 文档中删除形状，从而增强文档处理工作流程。
## 常见问题解答
### GroupDocs.Watermark for .NET 可以处理除 Word 之外的其他文档格式吗？
是的，GroupDocs.Watermark for .NET 支持多种文档格式，包括 Excel、PowerPoint、PDF 等。
### GroupDocs.Watermark for .NET 是否有免费试用版？
是的，您可以从以下位置访问 GroupDocs.Watermark for .NET 的免费试用版：[发布页面](https://releases.groupdocs.com/).
### 如何获取 GroupDocs.Watermark for .NET 的临时许可证？
 GroupDocs.Watermark for .NET 的临时许可证可以从[临时许可证页面](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以找到 GroupDocs.Watermark for .NET 的文档和支持？
 GroupDocs.Watermark for .NET 的文档和支持资源可在[论坛](https://forum.groupdocs.com/c/watermark/19)和[参考页](https://tutorials.groupdocs.com/Watermark/net/).
### 哪些版本的 .NET 与 GroupDocs.Watermark 兼容？
GroupDocs.Watermark for .NET 与各种版本的 .NET 兼容，包括 .NET Framework 和 .NET Core。