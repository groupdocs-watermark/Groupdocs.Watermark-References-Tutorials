---
title: 光栅化 PDF 文档
linktitle: 光栅化 PDF 文档
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 光栅化 PDF 文档。轻松增强文档安全性和视觉吸引力。
weight: 27
url: /zh/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# 光栅化 PDF 文档

## 介绍
在文档管理和操作领域，GroupDocs.Watermark for .NET 是一款强大的工具，提供强大的功能来添加、删除和搜索各种文档格式的水印。无论是使用版权声明保护您的文档、添加企业徽标以进行品牌推广，还是只是使用图章对文档进行注释，GroupDocs.Watermark 都可以通过其直观的 API 和广泛的功能集简化流程。
## 先决条件
在使用 GroupDocs.Watermark for .NET 深入研究水印世界之前，请确保满足以下先决条件：
### 1.安装.NET框架
确保您的开发计算机上安装了 .NET Framework。您可以从 Microsoft 网站下载它或使用您喜欢的包管理器。
#### 第 1 步：下载 .NET Framework
访问 Microsoft .NET Framework 下载页面。
#### 第 2 步：安装 .NET Framework
按照下载页面上提供的安装说明在您的系统上安装 .NET Framework。
### 2. 获取GroupDocs.Watermark许可证
要利用 GroupDocs.Watermark 的全部功能，您需要有效的许可证。您可以购买许可证或获取临时许可证以进行评估。
#### 第 1 步：获取许可证
访问 GroupDocs.Watermark 购买页面。
#### 第 2 步：购买或获取临时许可证
根据您的需求选择适当的许可选项 - 购买许可证以继续使用或获取临时许可证以进行评估。

## 导入命名空间
在开始为文档添加水印之前，请确保导入必要的命名空间以无缝访问 GroupDocs 的功能。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

现在您已完成所有设置，让我们深入研究使用 GroupDocs.Watermark for .NET 对 PDF 文档进行光栅化。光栅化将 PDF 文档的每一页转换为光栅图像格式，例如 PNG。
## 第 1 步：初始化变量
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
确保将“您的文档路径”和“您的文档目录”分别替换为 PDF 文档的实际路径和所需的输出目录。
## 第2步：加载文档并添加水印
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //初始化图像或文本水印
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    //先添加任意类型的水印
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    //光栅化所有页面
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    //所有页面的内容均替换为光栅图像
    watermarker.Save(outputFileName);
}
```
在此步骤中，我们加载 PDF 文档并使用指定属性（例如文本、字体、对齐方式、旋转角度、尺寸类型、比例因子和不透明度）初始化文本水印。然后，我们将水印添加到文档中。接下来，我们检索 PDF 文档的内容并将所有页面光栅化为分辨率为 100 DPI 的 PNG 格式。最后，我们用栅格化内容保存修改后的文档。

## 结论
GroupDocs.Watermark for .NET 提供了一个全面的解决方案，可以轻松地将水印添加到各种文档格式。通过遵循本教程中概述的步骤，您可以有效地光栅化 PDF 文档并增强其安全性和视觉吸引力。
## 常见问题解答
### GroupDocs.Watermark 是否与 PDF 以外的其他文档格式兼容？
是的，GroupDocs.Watermark 支持多种文档格式，包括 Microsoft Word、Excel、PowerPoint、Visio、Outlook 等。
### 我可以自定义使用 GroupDocs.Watermark 添加的水印的外观吗？
绝对地！ GroupDocs.Watermark 提供了用于自定义水印属性的广泛选项，例如文本、字体、颜色、大小、不透明度、旋转和位置。
### GroupDocs.Watermark 是否提供批处理支持？
是的，您可以使用 Watermark 以批处理模式轻松处理多个文档，从而节省为大量文件添加水印的时间和精力。
### GroupDocs.Watermark 是否有试用版？
是的，您可以从网站下载 GroupDocs.Watermark 的免费试用版，以在购买前评估其功能。
### 如果我遇到任何问题或对 GroupDocs.Watermark 有疑问，如何获得帮助？
您可以访问 GroupDocs.Watermark 论坛寻求社区支持或联系 GroupDocs 支持团队寻求帮助。