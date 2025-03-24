---
title: 加载受密码保护的文档
linktitle: 加载受密码保护的文档
second_title: GroupDocs.Watermark .NET API
description: 通过我们的分步指南，了解如何使用 Groupdocs for .NET 将水印添加到受密码保护的文档。轻松保护您的文件并为其打造品牌。
weight: 13
url: /zh/net/document-loadings/load-password-protected-document/
---
## 介绍
您是否希望通过添加水印来保护您的文档，即使它们受密码保护？ Groupdocs.Watermark for .NET 是一个功能强大的工具，可以让您做到这一点。在本教程中，我们将指导您完成加载受密码保护的文档并使用 Groupdocs.Watermark for .NET 添加水印的过程。让我们深入了解吧！
## 先决条件
在我们开始之前，请确保您具备以下条件：
1. Visual Studio：计算机上安装的任何版本的 Visual Studio。
2. .NET Framework：确保您拥有 .NET Framework 4.6.1 或更高版本。
3. Groupdocs.Watermark for .NET：从以下位置下载并安装 Groupdocs.Watermark for .NET 库：[下载链接](https://releases.groupdocs.com/Watermark/net/).
## 导入命名空间
首先，我们需要将必要的命名空间导入到我们的项目中。这确保了我们可以访问 Groupdocs.Watermark for .NET 提供的所有方法和属性。
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
现在，让我们将该过程分解为简单、易于遵循的步骤。
## 第 1 步：设置您的项目
首先，在 Visual Studio 中创建一个新的 C# 控制台应用程序。设置项目后，通过 NuGet 包管理器安装 Groupdocs.Watermark for .NET 库。
1. 打开 Visual Studio 并创建一个新的控制台应用程序 (.NET Framework)。
2. 去`Tools`>`NuGet Package Manager`>`Manage NuGet Packages for Solution`.
3. 搜索`GroupDocs.Watermark`并安装该软件包。
## 第 2 步：定义文档路径
接下来，您需要定义受密码保护的文档的路径以及保存带水印的文档的输出文件路径。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`与您机器上的实际路径。
## 第 3 步：使用密码设置加载选项
要打开受密码保护的文档，您必须在加载选项中提供密码。
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
代替`"P@$w0rd"`使用您文档的实际密码。
## 第 4 步：加载文档
现在，让我们使用以下命令加载文档`Watermarker`班级。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //添加水印的代码将位于此处
}
```
## 第 5 步：创建水印
我们将创建一个可以添加到文档中的文本水印。您可以根据需要自定义文本、字体、大小和其他属性。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
随意改变`"Test watermark"`, `"Arial"`， 和`12`您喜欢的文本、字体和大小。
## 第6步：添加水印
使用以下命令将水印添加到文档中`Add`的方法`Watermarker`班级。
```csharp
watermarker.Add(watermark);
```
## 第7步：保存带水印的文档
最后将加水印的文档保存到指定的输出文件路径。
```csharp
watermarker.Save(outputFileName);
```
## 结论
使用 Groupdocs for .NET，向受密码保护的文档添加水印的过程非常简单。通过执行这些简单的步骤，您可以确保您的文档根据您的要求受到保护和标记。无论是出于安全、品牌还是合规性的考虑，为文档添加水印从未如此简单。
## 常见问题解答
### 我可以使用 Groupdocs.Watermark for .NET 添加图像水印吗？
是的，您可以添加文本和图像水印。只需使用`ImageWatermark`类而不是`TextWatermark`.
### 是否可以从文档中删除水印？
是的，Groupdocs.Watermark for .NET 提供了搜索和删除水印的方法。
### Groupdocs.Watermark for .NET 是否支持除 PDF 之外的其他文档格式？
是的，它支持多种格式，包括 Word、Excel、PowerPoint 等。
### 我可以自定义水印的外观吗？
绝对地！您可以自定义字体、大小、颜色、不透明度等。
### 如果遇到问题，我可以在哪里获得支持？
您可以访问[Groupdocs 支持论坛](https://forum.groupdocs.com/c/watermark/19)寻求帮助和指导。