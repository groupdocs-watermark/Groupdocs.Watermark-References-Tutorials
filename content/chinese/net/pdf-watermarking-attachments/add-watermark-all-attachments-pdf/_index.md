---
title: 为 PDF 中的所有附件添加水印
linktitle: 为 PDF 中的所有附件添加水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 向 PDF 附件添加水印。使用自定义水印轻松保护您的文档。
type: docs
weight: 16
url: /zh/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## 介绍
向 PDF 附件添加水印可能是文档管理中的关键步骤，尤其是在确保安全或品牌时。 GroupDocs.Watermark for .NET 提供了将水印无缝嵌入 PDF 文件的全面解决方案。在本教程中，我们将指导您完成使用 GroupDocs.Watermark for .NET 向 PDF 文档中的所有附件添加水印的过程。
## 先决条件
在我们开始之前，请确保您具备以下条件：
1.  GroupDocs.Watermark for .NET：如果您还没有安装 GroupDocs.Watermark for .NET，请从[网站](https://releases.groupdocs.com/Watermark/net/).
2. 开发环境：使用 Visual Studio 或任何其他 .NET 兼容 IDE 设置合适的开发环境。
3. PDF 文档：准备要添加水印的 PDF 文档以及要添加水印的附件。

## 导入命名空间
在深入研究代码之前，请确保导入必要的命名空间以访问 GroupDocs.Watermark 的 .NET 功能：
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第1步：定义文档路径和输出目录
首先，定义输入 PDF 文档的路径以及保存带水印文档的目录：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 第2步：初始化加载选项和水印
接下来，初始化 PDF 文档的加载选项并创建文本水印：
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## 第 3 步：加载文档和附件
加载 PDF 文档并遍历其附件：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## 第 4 步：检查附件支持
检查附件是否受 GroupDocs.Watermark 支持：
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## 第 5 步：为附件添加水印
加载附件并添加水印：
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## 第 6 步：保存更改
最后，保存对带水印的 PDF 文档的更改：
```csharp
    watermarker.Save(outputFileName);
}
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Watermark for .NET 向 PDF 文档中的所有附件添加水印。通过遵循分步指南，您可以将水印无缝集成到 PDF 文件中，确保文档安全和品牌。
## 常见问题解答
### 我可以自定义水印的外观吗？
是的，您可以根据您的要求自定义水印的文本、字体、大小、颜色和位置等各个方面。
### GroupDocs.Watermark 是否支持除 PDF 之外的其他文档格式？
是的，GroupDocs.Watermark 支持多种文档格式，包括 Microsoft Word、Excel、PowerPoint、Visio、Outlook 和图像。
### GroupDocs.Watermark 是否有试用版？
是的，您可以通过从网站下载免费试用版来探索 GroupDocs.Watermark 的功能。
### 我可以在单个文档中添加多个水印吗？
当然，GroupDocs.Watermark 允许您同时添加多个水印，包括文本、图像和注释，以增强文档安全性和品牌形象。
### GroupDocs.Watermark 用户可以获得技术支持吗？
是的，GroupDocs 通过论坛和专门的支持渠道提供全面的技术支持，以帮助用户解决可能遇到的任何疑问或问题。