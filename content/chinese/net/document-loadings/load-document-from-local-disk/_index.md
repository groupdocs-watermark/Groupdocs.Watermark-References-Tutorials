---
title: 从本地磁盘加载文档
linktitle: 从本地磁盘加载文档
second_title: GroupDocs.Watermark .NET API
description: 使用 Groupdocs for .NET 保护和管理您的文档。按照我们的详细指南无缝添加水印。
type: docs
weight: 10
url: /zh/net/document-loadings/load-document-from-local-disk/
---
## 介绍
在当今的数字时代，为文档添加水印对于确保内容保护、所有权声明和机密性至关重要。 Groupdocs.Watermark for .NET 是一个功能强大的库，允许开发人员添加、搜索和管理各种文档格式的水印。在本教程中，我们将通过详细的分步说明逐步介绍使用 Groupdocs.Watermark for .NET 向文档添加水印的过程。
## 先决条件
在深入实施之前，请确保您具备以下条件：
1. 已安装 Visual Studio：您需要 Visual Studio 或其他兼容的 .NET IDE。
2.  Groupdocs.Watermark for .NET：从以下位置下载该库[下载链接](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework：确保安装了 .NET Framework 4.6.1 或更高版本。
4. 示例文档：准备示例文档来测试水印过程。
## 导入命名空间
首先，您需要在项目中导入必要的命名空间。这些对于访问水印所需的类和方法至关重要。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 步骤一：从本地磁盘加载文档
首先，您需要从本地磁盘加载文档。您将在该文档中添加水印。
定义要加水印的文档的路径。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 第 2 步：初始化加载选项
接下来，初始化加载选项。例如，如果您正在处理 Word 文档，您将使用`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 第 3 步：创建并配置水印
现在，您将创建一个实例`Watermarker`班级。该实例将用于管理水印并将其应用到您的文档。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //该块将包含添加和保存水印的进一步步骤
}
```
## 第 4 步：创建水印
创建文本水印。该水印可以包含您选择的任何文本。在这里，我们将使用“测试水印”。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## 第5步：向文档添加水印
使用以下命令将创建的水印添加到文档中`Add`的方法`Watermarker`班级。
```csharp
watermarker.Add(watermark);
```
## 步骤 6：保存带水印的文档
最后将带水印的文档保存到指定路径。
```csharp
watermarker.Save(outputFileName);
```

## 结论
使用 Watermark for .NET 向文档添加水印既简单又高效。本指南引导您完成从设置环境到保存带水印的文档的整个过程。借助这个强大的工具，您可以确保您的文档受到保护并确保您的知识产权安全。 
欲了解更多详情，请查看[文档](https://reference.groupdocs.com/Watermark/net/)，如果您遇到任何问题，[支持论坛](https://forum.groupdocs.com/c/watermark/19)是寻求帮助的绝佳场所。 
## 常见问题解答
### 我可以使用自定义字体作为水印吗？
是的，Groupdocs 支持自定义字体。您可以指定系统上安装的任何字体。
### 支持哪些类型的文档？
Groupdocs.Watermark 支持多种文档格式，包括 Word、Excel、PDF、PowerPoint 等。
### 如何从文档中删除水印？
您可以使用`Remove`提供的方法`Watermarker`类来删除水印。
### 可以添加图片水印吗？
是的，您可以使用以下命令添加图像水印`ImageWatermark`班级。
### 我可以免费试用 Groupdocs.Watermark 吗？
绝对可以，你可以下载一个[免费试用](https://releases.groupdocs.com/)在购买之前评估图书馆。