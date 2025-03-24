---
title: 将仅打印注释水印添加到 PDF
linktitle: 将仅打印注释水印添加到 PDF
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 将仅打印注释水印添加到 PDF。轻松增强文档安全性和品牌形象。
weight: 13
url: /zh/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## 介绍
在本教程中，我们将深入研究使用 GroupDocs.Watermark for .NET 将仅打印注释水印添加到 PDF 的过程。文档水印是文档安全和品牌塑造的一个重要方面，GroupDocs.Watermark 为 .NET 开发人员提供了实现这一目标的无缝解决方案。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
- 对 C# 编程语言有基本了解。
- Visual Studio 安装在您的计算机上。
- GroupDocs.Watermark for .NET 库安装在您的项目中。

## 导入命名空间
首先，请确保导入必要的命名空间：
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：加载文档
首先，您需要加载要加水印的PDF文档。代替`"Your Document Path"`以及您的 PDF 文件的路径和`"Your Document Directory"`与要保存输出文件的目录。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //此处将添加水印代码
}
```
## 第2步：添加水印
接下来，使用所需的文本和字体创建文本水印对象。放`isPrintOnly`到`true`确保水印仅在打印文档时可见，而不是在查看模式下可见。
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## 步骤 3：配置水印选项
定义水印的选项，例如应添加水印的页面索引并将其指定为仅打印注释。
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## 第 4 步：应用水印
使用指定的选项将水印添加到文档并保存输出文件。
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Watermark for .NET 将仅打印注释水印添加到 PDF 文档。这使开发人员能够轻松增强文档安全性和品牌化。
## 常见问题解答
### GroupDocs.Watermark 是否与 PDF 以外的其他文档格式兼容？
是的，GroupDocs 支持多种文档格式，例如 Word、Excel、PowerPoint 和图像。
### 我可以自定义水印的外观吗？
当然，GroupDocs.Watermark 提供了广泛的选项来自定义水印文本、字体、颜色、大小和位置。
### GroupDocs.Watermark 是否提供批处理功能？
当然，开发人员可以使用批处理功能同时为多个文档添加水印。
### GroupDocs.Watermark 是否有试用版？
是的，您可以从提供的链接访问 GroupDocs.Watermark 的免费试用版。
### 如何获得 GroupDocs.Watermark 的技术支持？
您可以通过提供的支持链接从 GroupDocs.Watermark 论坛寻求技术帮助。