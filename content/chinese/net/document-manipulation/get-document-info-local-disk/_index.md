---
title: 从本地磁盘获取文档信息
linktitle: 从本地磁盘获取文档信息
second_title: GroupDocs.Watermark .NET API
description: 通过这份全面的分步指南，了解如何使用 GroupDocs for .NET 在文档中添加、删除和提取水印。
type: docs
weight: 11
url: /zh/net/document-manipulation/get-document-info-local-disk/
---
## 介绍
欢迎阅读有关使用 GroupDocs.Watermark for .NET 的终极指南！无论您是经验丰富的开发人员还是刚刚入门，本文都将引导您了解使用这个强大的工具为文档添加水印的基本知识。最后，您将成为在文档中嵌入水印的专家，确保它们受到保护并按照您的规格进行标记。
## 先决条件
在深入了解分步指南之前，您需要满足一些先决条件：
1.  .NET Framework：确保您的系统上安装了 .NET Framework。 GroupDocs.Watermark for .NET 与各种版本的 .NET Framework 兼容，因此请检查[文档](https://reference.groupdocs.com/Watermark/net/)有关兼容性详细信息。
2.  GroupDocs.Watermark for .NET Library：从以下位置下载并安装最新版本[下载页面](https://releases.groupdocs.com/Watermark/net/).
3. 开发环境：您应该设置一个开发环境。 Visual Studio 是 .NET 开发的热门选择。
4. 基本 C# 知识：了解 C# 编程的基础知识将帮助您理解示例。
## 导入命名空间
在使用 GroupDocs.Watermark for .NET 之前，您需要将必要的命名空间导入到您的项目中。这是一个简单的过程，对于访问库的功能至关重要。
```csharp
using System;
using GroupDocs.Watermark.Common;
```
让我们将文档加水印的过程分解为清晰、可管理的步骤。每个步骤旨在帮助您轻松理解和实现功能。
## 第 1 步：加载您的文档
第一步是加载要加水印的文档。这是使用以下方法完成的`Watermarker`类，它允许您访问和操作您的文档。
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    //文档现已加载并准备好添加水印
}
```
在此步骤中，替换`"Your Document Path"`与文档的实际路径。这会初始化`Watermarker`对象，使您可以访问各种水印功能。
## 第2步：获取文档信息
在添加水印之前，您可能需要收集有关文档的一些信息。这对于根据文档属性自定义水印非常有用。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
在这一步中，`GetDocumentInfo`方法检索文件类型、页数和文档大小等详细信息。此信息将打印到控制台，但您可以根据需要在应用程序中使用它。
## 第 3 步：添加文本水印
现在您已加载文档并掌握其信息，是时候添加水印了。我们将从简单的文本水印开始。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
在这里，您创建一个`TextWatermark`具有您想要的文本、字体和样式的对象。调整颜色、不透明度和旋转角度等属性以满足您的需求。最后将水印添加到文档中并保存到指定路径。
## 第四步：添加图像水印
文本水印很棒，但如果您想添加徽标或其他图像怎么办？此步骤介绍如何添加图像水印。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
代替`"Path to Your Image"`以及水印图像的路径。设置不透明度和旋转角度等属性来自定义图像水印的外观。添加和保存水印的过程与文本水印类似。
## 第 5 步：删除现有水印
有时，您可能需要从文档中删除现有的水印。这可以使用以下方法完成`Remove`提供的方法`Watermarker`班级。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
在这里，`Remove`方法用于从文档中删除文本水印。您可以根据需要指定要删除的不同类型的水印，例如图像或文本。将文档保存到新路径以查看更改。
## 第6步：提取水印
如果您需要从文档中提取和检查水印，GroupDocs.Watermark for .NET 可以轻松实现这一点。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        //每个水印的附加属性和逻辑
    }
}
```
此步骤涉及使用`GetWatermarks`检索文档中所有水印的方法。然后，您可以遍历水印列表并检查其属性或根据需要执行其他操作。
## 结论
恭喜！您现在已经了解了如何使用 GroupDocs.Watermark for .NET 在文档中添加、删除和提取水印。借助这些技能，您可以有效地保护您的文档并为其打造品牌。请记住，[文档](https://reference.groupdocs.com/Watermark/net/)如果您需要更详细的信息或高级功能，总是在那里。
## 常见问题解答
### 我可以将 GroupDocs.Watermark for .NET 与任何 .NET 版本一起使用吗？
是的，GroupDocs.Watermark for .NET 与各种 .NET Framework 版本兼容。检查[文档](https://reference.groupdocs.com/Watermark/net/)了解具体情况。
### 在哪里可以下载 .NET 版 GroupDocs.Watermark？
您可以从以下位置下载最新版本[下载页面](https://releases.groupdocs.com/Watermark/net/).
### 我如何获得临时许可证？
您可以从以下机构获得临时许可证[临时许可证页面](https://purchase.groupdocs.com/temporary-license/).
### 有免费试用吗？
是的，您可以访问以下网站开始免费试用[免费试用页面](https://releases.groupdocs.com/).
### 如果遇到问题，我可以在哪里获得支持？
支持可在[GroupDocs 水印论坛](https://forum.groupdocs.com/c/watermark/19).