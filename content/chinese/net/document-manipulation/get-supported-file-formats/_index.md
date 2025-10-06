---
title: 获取支持的文件格式
linktitle: 获取支持的文件格式
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs.Watermark for .NET 轻松向文档添加水印。请遵循我们全面的分步指南来保护您的数字资产。
weight: 13
url: /zh/net/document-manipulation/get-supported-file-formats/
type: docs
---
# 获取支持的文件格式

## 介绍
对文档加水印是保护数字资产的关键一步。无论是为了保护知识产权、确保机密性还是仅仅为了品牌宣传，水印都起着至关重要的作用。如果您是一名 .NET 开发人员，希望将水印功能集成到您的应用程序中，那么 GroupDocs.Watermark for .NET 是您应该考虑的一个强大且多功能的工具。本教程将指导您了解使用 GroupDocs.Watermark 的基本知识，从安装到应用第一个水印，分解每个步骤以确保您可以轻松地遵循。
## 先决条件
在我们深入了解具体细节之前，让我们确保您已具备开始使用所需的一切：
1.  Visual Studio：确保您的计算机上安装了 Visual Studio。您可以从[视觉工作室网站](https://visualstudio.microsoft.com/).
2. .NET Framework：GroupDocs.Watermark 支持各种版本的 .NET Framework。确保您的项目面向兼容版本。
3. GroupDocs.Watermark for .NET：您可以从以下位置下载最新版本：[发布页面](https://releases.groupdocs.com/Watermark/net/).
4. C# 基础知识：本教程假设您对 C# 和 .NET 开发有基本的了解。
## 导入命名空间
首先，让我们在项目中导入必要的命名空间。打开 C# 文件并在顶部添加以下 using 指令：
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
导入这些命名空间后，您就可以开始向文档添加水印了。

## 第 1 步：初始化水印引擎
第一步是初始化水印引擎。这涉及到创建一个实例`Watermarker`类与您想要加水印的文档。
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
此代码片段设置`Watermarker`对象，您将使用该对象将水印应用到文档。
## 第2步：添加文本水印
现在，让我们向您的文档添加一个简单的文本水印。文本水印非常适合添加“机密”或“草稿”等标签。
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
在这里，我们创建了一个`TextWatermark`文本为“机密”的对象，设置其字体和颜色，并将其与文档的中心对齐。
## 步骤 3：添加图像水印
如果您喜欢使用图像作为水印，GroupDocs.Watermark 可以轻松实现这一点。
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
在这个例子中，我们创建一个`ImageWatermark`对象，设置其尺寸，并将其与文档的右上角对齐。
## 步骤 4：保存文档
添加所需的水印后，最后一步是保存修改后的文档。
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
这会将带水印的文档保存到指定路径并释放其使用的所有资源`Watermarker`实例。
## 第 5 步：获取支持的文件格式
要查看 GroupDocs.Watermark 支持哪些文件格式，您可以使用以下代码片段：
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
这将打印出 GroupDocs.Watermark 可以处理的所有文件类型，让您全面了解其功能。
## 结论
使用 GroupDocs for .NET 对文档添加水印既简单又高效。通过学习本教程，您已了解如何初始化水印引擎、添加文本和图像水印、保存带水印的文档以及列出支持的文件格式。借助这些工具，您可以放心地保护您的文档。
如果您有任何疑问或需要进一步帮助，请随时访问[GroupDocs.Watermark 支持论坛](https://forum.groupdocs.com/c/watermark/19).
## 常见问题解答
### 如何安装 GroupDocs.Watermark for .NET？
您可以从[发布页面](https://releases.groupdocs.com/Watermark/net/)并将 DLL 添加到您的项目中。
### 我可以免费试用 GroupDocs.Watermark 吗？
是的，您可以请求[免费试用](https://releases.groupdocs.com/)在购买前评估软件。
### GroupDocs.Watermark 支持哪些文件格式？
您可以使用提供的代码片段列出所有支持的文件格式。
### 如何购买 GroupDocs.Watermark 的许可证？
许可证可以直接从[购买页面](https://purchase.groupdocs.com/buy).
### 有适用于 GroupDocs.Watermark 的任何文档吗？
是的，提供全面的文档[这里](https://tutorials.groupdocs.com/Watermark/net/).