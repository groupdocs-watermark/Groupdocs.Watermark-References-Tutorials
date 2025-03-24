---
title: 向 PDF 中的 XObject 添加水印
linktitle: 向 PDF 中的 XObject 添加水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 将水印添加到 PDF 中的 XObject。请遵循我们的分步指南以轻松实施。
weight: 20
url: /zh/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---

# 向 PDF 中的 XObject 添加水印

## 介绍
对 PDF 添加水印是确保您的文档免遭未经授权使用的关键步骤。借助 Groupdocs.Watermark for .NET，向 PDF 中的 XObject 添加水印从未如此简单。在本教程中，我们将逐步引导您完成该过程，确保您可以自信地将水印应用到 PDF 文档。让我们开始吧！
## 先决条件
在深入学习本教程之前，让我们确保您拥有无缝学习所需的一切：
-  Groupdocs.Watermark for .NET：从以下位置下载并安装最新版本[这里](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework：确保您的开发计算机上安装了 .NET Framework。
- 开发环境：使用Visual Studio或任何其他支持.NET开发的IDE。
- 临时许可证：获得[临时执照](https://purchase.groupdocs.com/temporary-license/)如果您正在评估产品。
满足这些先决条件后，您就可以开始为 PDF 添加水印了。
## 导入命名空间
首先，您需要在项目中导入必要的命名空间。打开您的 C# 项目并添加以下 using 指令：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：设置文档路径
第一步涉及设置文档的路径。定义 PDF 所在的路径以及要保存带水印的 PDF 的位置。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`和`"Your Document Directory"`与您机器上的实际路径。
## 步骤 2：初始化 PDF 加载选项
接下来，您需要初始化 PDF 加载选项。这对于正确加载 PDF 内容至关重要。
```csharp
var loadOptions = new PdfLoadOptions();
```
## 第 3 步：加载 PDF 文档
使用加载选项，加载 PDF 文档`Watermarker`班级。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 第四步：创建水印
现在，您需要创建将添加到 PDF 的水印。在本教程中，我们将创建文本水印。
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## 第 5 步：向 XObject 添加水印
迭代 PDF 中的每个页面和每个 XObject 以应用水印。
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            //为图像添加水印
            xObject.Image.Add(watermark);
        }
    }
}
```
## 步骤 6：保存带水印的 PDF
最后，将带水印的PDF保存到指定的输出文件中。
```csharp
    watermarker.Save(outputFileName);
}
```
现在你就得到了它！现在，您的 PDF 的所有 XObject 上都包含水印。
## 结论
使用 Groupdocs for .NET 向 PDF 文档添加水印是一个简单的过程，可提供额外的安全层。通过遵循本教程中概述的步骤，您可以确保您的文档免受未经授权的使用。请记住，您可以随时参考[文档](https://tutorials.groupdocs.com/Watermark/net/)了解更多详细信息和高级功能。
## 常见问题解答
### 我可以使用图像而不是文本作为水印吗？
是的，Groupdocs.Watermark for .NET 支持文本和图像水印。
### 如何在不购买 Groupdocs.Watermark 的情况下测试它？
您可以使用[临时执照](https://purchase.groupdocs.com/temporary-license/)来评估产品。
### 是否可以自定义水印的外观？
绝对地！您可以自定义字体、大小、旋转角度等。
### Groupdocs.Watermark 支持其他文档格式吗？
是的，它支持多种格式，包括 Word、Excel 和 PowerPoint。
### 如果遇到问题，我可以在哪里获得支持？
您可以从以下方面获得支持[组文档论坛](https://forum.groupdocs.com/c/watermark/19).