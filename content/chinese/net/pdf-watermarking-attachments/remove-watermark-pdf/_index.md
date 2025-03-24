---
title: 从 PDF 中删除水印
linktitle: 从 PDF 中删除水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 从 PDF 文件中删除水印。专业文档编辑的简单步骤。
weight: 34
url: /zh/net/pdf-watermarking-attachments/remove-watermark-pdf/
---

# 从 PDF 中删除水印

## 介绍
在当今的数字时代，使用水印保护敏感文档是一种常见的做法。但是，在某些情况下，您可能因各种原因需要从 PDF 文件中删除水印。无论您是在编辑文档还是只是需要一个干净的版本进行演示，GroupDocs.Watermark for .NET 都提供了从 PDF 文件中删除水印的无缝解决方案。
## 先决条件
在我们深入研究使用 GroupDocs.Watermark for .NET 从 PDF 文件中删除水印之前，请确保您满足以下先决条件：
1.  GroupDocs.Watermark for .NET 库：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/Watermark/net/).
2. 开发环境：系统上安装了 Visual Studio 或任何兼容的 IDE。
3. 带水印的文档：准备包含要删除的水印的 PDF 文档。

## 导入命名空间
在您的 C# 项目中，首先导入必要的命名空间：
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## 第 1 步：加载 PDF 文档
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
在此步骤中，指定 PDF 文档的路径以及要保存输出文件的目录。
## 第 2 步：初始化水印和搜索条件
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
使用 PDF 文档路径和加载选项初始化 Watermarker 对象。然后，定义要删除的水印的搜索条件。您可以根据图像或文本搜索水印。
## 第三步：搜索并删除水印
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    //删除所有找到的水印
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
根据定义的搜索条件在 PDF 文档的第一页上搜索可能的水印。然后，迭代可能的水印集合并将其一一删除。最后，保存修改后的无水印PDF文档。

## 结论
从文档编辑到演示文稿准备，从 PDF 文件中删除水印是各种场景中的一项关键任务。借助 GroupDocs.Watermark for .NET，您可以使用简单的 C# 代码轻松地从 PDF 文件中删除水印，确保您的文档干净且专业。
## 常见问题解答
### GroupDocs.Watermark for .NET 是否与所有版本的 Visual Studio 兼容？
是的，GroupDocs.Watermark for .NET 与所有版本的 Visual Studio 兼容，包括 Visual Studio 2019 和 Visual Studio 2022。
### 我可以使用 GroupDocs.Watermark for .NET 从单个 PDF 文档中删除多个水印吗？
是的，您可以通过指定适当的搜索条件来搜索并删除单个 PDF 文档中的多个水印。
### GroupDocs.Watermark for .NET 是否支持除 PDF 之外的其他文档格式？
是的，GroupDocs.Watermark for .NET 支持多种文档格式，包括 Word 文档、Excel 电子表格、PowerPoint 演示文稿等。
### GroupDocs.Watermark for .NET 是否有试用版？
是的，您可以从以下位置下载 GroupDocs.Watermark for .NET 的免费试用版：[这里](https://releases.groupdocs.com/).
### 在哪里可以找到针对 GroupDocs.Watermark for .NET 的其他支持和帮助？
如需更多支持，您可以访问 GroupDocs.Watermark 论坛[这里](https://forum.groupdocs.com/c/watermark/19).