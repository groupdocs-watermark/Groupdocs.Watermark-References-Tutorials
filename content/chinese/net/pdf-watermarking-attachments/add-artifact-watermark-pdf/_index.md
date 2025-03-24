---
title: 向 PDF 添加工件水印
linktitle: 向 PDF 添加工件水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 Groupdocs.Watermark for .NET 轻松地将工件水印添加到 PDF 文件。轻松保护您的文档。
weight: 11
url: /zh/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---

# 向 PDF 添加工件水印

## 介绍
向 PDF 文件添加水印是文档管理的一个重要方面，尤其是在保护知识产权或品牌文档时。 Groupdocs.Watermark for .NET 提供了一个强大的解决方案，可以轻松地向 PDF 文件添加水印。在本教程中，我们将逐步介绍向 PDF 文件添加人工水印的过程。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1.  Groupdocs.Watermark for .NET：从以下位置下载并安装 Groupdocs.Watermark for .NET[这里](https://releases.groupdocs.com/Watermark/net/).
2. 开发环境：搭建.NET开发环境。
3. PDF文档：准备要添加水印的PDF文档。
4. 输出目录：创建一个目录来保存带水印的 PDF 文件。

## 导入命名空间
首先，在 C# 项目中导入必要的命名空间：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：加载 PDF 文档
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 第 2 步：定义水印选项
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## 第三步：添加文字水印
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## 第四步：添加图片水印
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## 第5步：保存带水印的PDF
```csharp
watermarker.Save(outputFileName);
```

## 结论
在本教程中，我们学习了如何使用 Groupdocs.Watermark for .NET 将工件水印添加到 PDF 文件。通过执行这些步骤，您可以将水印功能无缝集成到 .NET 应用程序中，从而确保文档的安全性和完整性。
## 常见问题解答
### 我可以自定义文本水印的外观吗？
是的，您可以根据自己的喜好自定义文本水印的字体、大小、颜色和对齐方式等各个方面。
### Groupdocs.Watermark 是否支持向其他文档格式添加水印？
是的，Groupdocs.Watermark 支持向多种文档格式添加水印，包括 Word、Excel、PowerPoint 等。
### Groupdocs.Watermark for .NET 是否有试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 对于与 Groupdocs.Watermark 相关的任何问题或查询，如何获得支持？
您可以从 Groupdocs 社区论坛获得支持[这里](https://forum.groupdocs.com/c/watermark/19).
### 我可以将 Groupdocs.Watermark 用于商业目的吗？
是的，您可以从以下位置购买商业用途的许可证[这里](https://purchase.groupdocs.com/buy).