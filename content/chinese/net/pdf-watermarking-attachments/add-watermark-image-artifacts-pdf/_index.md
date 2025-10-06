---
title: 向 PDF 中的图像工件添加水印
linktitle: 向 PDF 中的图像工件添加水印
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs.Watermark for .NET 使用个性化水印保护您的 PDF 文件。轻松将文本或图像水印添加到 PDF 文档中的图像工件。
weight: 18
url: /zh/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
type: docs
---
# 向 PDF 中的图像工件添加水印

## 介绍
在本教程中，我们将指导您完成使用 GroupDocs.Watermark for .NET 向 PDF 文档中的图像工件添加水印的过程。通过执行以下步骤，您可以使用个性化水印有效保护您的 PDF 文件。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1.  GroupDocs.Watermark for .NET：下载并安装 GroupDocs.Watermark for .NET 库[这里](https://releases.groupdocs.com/Watermark/net/).
2. 文档路径：包含要添加水印的 PDF 文档的路径。
3. 输出目录：创建保存带水印文档的目录。

## 导入命名空间
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：加载文档并初始化 Watermarker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 第2步：获取PDF内容并添加水印
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	//初始化图像或文本水印
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				//为图像添加水印
				artifact.Image.Add(watermark);
			}
		}
	}
```
## 步骤 3：保存带水印的文档
```csharp
	watermarker.Save(outputFileName);
}
```

## 结论
借助 GroupDocs.Watermark for .NET，向 PDF 文档中的图像工件添加水印成为一个无缝过程。通过遵循本教程，您可以使用自定义水印有效保护您的PDF文件，确保其安全性和真实性。
## 常见问题解答
### 我可以在 PDF 文档中添加图像和文本水印吗？
是的，GroupDocs.Watermark for .NET 支持同时添加图像和文本水印。
### 我可以添加到文档中的水印数量有限制吗？
不，您可以在文档中添加多个水印，没有任何限制。
### 我可以自定义水印的外观和位置吗？
当然，您可以完全控制水印的外观、位置和属性。
### GroupDocs.Watermark for .NET 是否支持除 PDF 之外的其他文档格式？
是的，它支持多种文档格式，包括 Word、Excel、PowerPoint 等。
### 有没有办法从文档中删除水印？
是的，GroupDocs.Watermark for .NET 提供了根据需要从文档中删除水印的方法。