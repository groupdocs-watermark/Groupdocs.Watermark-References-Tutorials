---
title: 从流加载文档
linktitle: 从流加载文档
second_title: GroupDocs.Watermark .NET API
description: 通过本指南了解如何使用 GroupDocs.Watermark for .NET 向文档添加水印。非常适合希望增强文档安全性的开发人员。
type: docs
weight: 11
url: /zh/net/document-loadings/load-document-from-stream/
---
## 介绍
您是否希望使用 .NET 向文档无缝添加水印？别再犹豫了！ GroupDocs.Watermark for .NET 是一个功能强大且易于使用的库，允许您管理各种文档格式的水印。无论您是处理 PDF、Word 文档还是图像，此工具都能满足您的需求。在本教程中，我们将引导您逐步完成从流加载文档并添加水印的过程。那么，让我们开始吧！
## 先决条件
在我们开始之前，请确保您已进行以下设置：
1. Visual Studio：任何最新版本的 Visual Studio 都可以正常工作。
2. .NET Framework：确保您已安装 .NET Framework 4.0 或更高版本。
3.  GroupDocs.Watermark for .NET：您可以从以下位置下载：[这里](https://releases.groupdocs.com/Watermark/net/).
4. C# 基础知识：熟悉 C# 和面向对象编程概念将会有所帮助。

## 导入命名空间
要在项目中使用 GroupDocs.Watermark，您需要导入必要的命名空间。这将使您能够毫无问题地访问该库的功能。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 第 1 步：设置您的项目
首先，您需要在 Visual Studio 中设置项目。操作方法如下：
1. 创建新项目：打开 Visual Studio 并创建一个新的 C# 控制台应用程序项目。
2. 安装 GroupDocs.Watermark：通过 NuGet 包管理器安装 GroupDocs.Watermark 库。只需搜索`GroupDocs.Watermark`并安装它。
## 第 2 步：定义文档路径
接下来，您需要定义文档的路径以及将保存带水印的文档的输出文件。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
代替`"Your Document Path"`与您想要加水印的文档的实际路径和`"Your Document Directory"`与要保存带水印的文档的目录。
## 第 3 步：从流加载文档
现在，让我们从流中加载文档。这涉及以流的形式打开文档，然后使用`Watermarker`GroupDocs.Watermark 库中的类来管理它。
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    //您管理水印的代码将位于此处
}
```
此代码片段确保文档作为流打开并且`Watermarker`类是用该流初始化的。这`using`声明确保资源在使用后得到妥善处置。
## 第 4 步：创建并添加水印
使用 GroupDocs.Watermark 创建水印非常简单。在此示例中，我们将创建一个简单的文本水印。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
在这里，我们创建一个`TextWatermark`对象包含文本“测试水印”并指定字体详细信息。然后，我们使用以下命令将此水印添加到文档中`Add`的方法`Watermarker`班级。
## 第5步：保存带水印的文档
最后将加水印的文档保存到指定的输出路径。
```csharp
watermarker.Save(outputFileName);
```
此代码保存带有新添加的水印的文档`outputFileName`您之前定义的路径。

## 结论
恭喜！您已使用 GroupDocs.Watermark for .NET 成功向文档添加水印。该库使管理各种文档格式的水印变得非常容易。无论您需要添加文本、图像还是其他类型的水印，GroupDocs.Watermark 都有您需要的工具。不要忘记查看[文档](https://reference.groupdocs.com/Watermark/net/)了解更多高级功能和定制选项。
## 常见问题解答
### 我可以使用 GroupDocs.Watermark for .NET 添加哪些类型的水印？
您可以添加文本水印、图像水印，甚至复杂的形状和徽标。该库支持广泛的定制选项。
### 我可以使用 GroupDocs.Watermark 从文档中删除水印吗？
是的，GroupDocs.Watermark 还允许您从文档中删除现有的水印。
### GroupDocs.Watermark 是否有免费试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 如何购买 GroupDocs.Watermark 的许可证？
您可以直接从[集团文档网站](https://purchase.groupdocs.com/buy).
### 如果遇到问题，我可以在哪里获得支持？
如需支持，您可以访问[GroupDocs.Watermark 支持论坛](https://forum.groupdocs.com/c/watermark/19).