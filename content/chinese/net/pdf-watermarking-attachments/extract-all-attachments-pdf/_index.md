---
title: 从 PDF 中提取所有附件
linktitle: 从 PDF 中提取所有附件
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 从 PDF 中提取所有附件。请按照我们的分步指南进行无缝提取过程。
weight: 22
url: /zh/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
---
## 介绍
您是否希望轻松地从 PDF 文档中提取附件？嗯，您来对地方了！在这个综合教程中，我们将指导您完成使用 Groupdocs.Watermark for .NET 从 PDF 中提取所有附件的过程。这个强大的库允许开发人员管理各种文档格式的水印，但它还包括提取嵌入文件的强大功能。无论您是经验丰富的开发人员还是刚刚起步的开发人员，本分步指南都将使整个过程变得轻而易举。
## 先决条件
在深入研究代码之前，我们先介绍一下入门所需的基础知识。这是一个快速清单，可确保您做好准备：
1. .NET 环境：确保您已设置 .NET 开发环境。您可以使用 Visual Studio 或您选择的任何其他 .NET IDE。
2.  Groupdocs.Watermark for .NET：从以下位置下载并安装最新版本的 Groupdocs.Watermark for .NET[这里](https://releases.groupdocs.com/Watermark/net/).
3. 开发技能：对 C# 编程有基本了解，熟悉 .NET 库。
4. 示例 PDF 文档：拥有一个带有附件的示例 PDF 文档，可用于测试。
## 导入命名空间
在开始编码之前，您需要导入必要的命名空间。这有助于组织您的代码并允许您访问将要使用的类和方法。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## 第 1 步：设置您的项目
首先，让我们设置您的项目。打开您的 .NET 开发环境并创建一个新的控制台应用程序。
### 创建一个新项目
1. 打开视觉工作室。
2. 选择“创建新项目”。
3. 根据您的喜好选择“控制台应用程序（.NET Core）”或“.NET Framework”。
4. 为您的项目命名并单击“创建”。
### 为 .NET 添加 Groupdocs.Watermark
1. 在解决方案资源管理器中右键单击您的项目。
2. 选择“管理 NuGet 包”。
3. 搜索“Groupdocs.Watermark”并安装最新版本。
## 第 2 步：定义您的路径
接下来，您需要定义文档和输出目录的路径。这是您的 PDF 和提取的附件的存储位置。

在你的`Program.cs`文件中，添加以下代码来定义您的路径：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`与系统上的实际路径。
## 第 3 步：加载您的 PDF 文档
现在，让我们使用 Groupdocs.Watermark 加载 PDF 文档。此步骤涉及创建加载选项并初始化`Watermarker`班级。
### 创建加载选项
首先，创建一个实例`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### 初始化水印
接下来，使用`Watermarker`类来加载您的文档：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //您的代码将位于此处
}
```
## 第 4 步：提取附件
加载文档后，就可以提取附件了。您将使用`PdfContent`类来访问附件，然后将它们保存到指定的输出目录。
### 获取PDF内容
在 - 的里面`using`块，获取PDF内容：
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### 循环浏览附件
循环浏览 PDF 中的每个附件：
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    //将附件保存到磁盘上
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
此代码提取每个附件并将其保存到您的输出目录。它还将有关每个附件的一些基本信息打印到控制台。
## 结论
现在你就得到了它！您已使用 Groupdocs.Watermark for .NET 成功从 PDF 中提取附件。本教程将引导您逐步设置项目、加载文档以及提取附件。有了这些技能，您现在可以轻松管理和操作 .NET 应用程序中的 PDF 附件。
## 常见问题解答
### 什么是 .NET 的 Groupdocs.Watermark？
Groupdocs.Watermark for .NET 是一个综合库，用于添加、删除和管理各种文档格式（包括 PDF）的水印。它还提供提取嵌入文件的功能。
### 我可以提取 PDF 中嵌入的其他类型的文件吗？
是的，Groupdocs.Watermark for .NET 允许您提取 PDF 中嵌入的任何类型的文件，而不仅仅是附件。
### 有免费试用吗？
是的，您可以从以下位置下载 Groupdocs.Watermark for .NET 的免费试用版：[这里](https://releases.groupdocs.com/).
### 如果遇到问题，我如何获得支持？
您可以通过访问获得支持[Groupdocs.Watermark 支持论坛](https://forum.groupdocs.com/c/watermark/19).
### 我需要许可证才能使用 Groupdocs.Watermark for .NET 吗？
是的，您需要许可证才能在生产中使用该库。您可以购买许可证[这里](https://purchase.groupdocs.com/buy)或获得临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).