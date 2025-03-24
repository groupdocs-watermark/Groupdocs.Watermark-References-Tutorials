---
title: 添加附件到 PDF
linktitle: 添加附件到 PDF
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs.Watermark 增强您的 .NET 文档管理功能，实现无缝水印和附件处理。
weight: 12
url: /zh/net/pdf-watermarking-attachments/add-attachment-pdf/
---

# 添加附件到 PDF

## 介绍
在 .NET 开发领域，GroupDocs.Watermark 作为管理各种文档格式中的水印、注释等的强大工具而脱颖而出。无论您使用 PDF、Word 文档还是图像，GroupDocs.Watermark for .NET 都提供无缝集成，使开发人员能够轻松操作文档。
## 先决条件
在深入了解使用 GroupDocs.Watermark for .NET 的复杂性之前，请确保满足以下先决条件：
1. 安装：确保您已安装 GroupDocs.Watermark for .NET。您可以从[发布页面](https://releases.groupdocs.com/Watermark/net/).
2. 文档准备：准备好要对其执行水印或其他操作的文档。
3. C# 基础知识：熟悉 C# 编程语言基础知识，因为我们将使用它与 GroupDocs.Watermark API 进行交互。

## 导入命名空间
在开始实施之前，导入必要的命名空间以访问 GroupDocs.Watermark 的功能至关重要。以下是所需的命名空间：
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## 第 1 步：加载文档
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
在此步骤中，我们指定要使用的文档的路径并创建一个`PdfLoadOptions`用于加载 PDF 文档的对象。然后，我们初始化一个`Watermarker`具有文档路径和加载选项的对象。
## 第2步：获取PDF内容
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
在这里，我们使用以下方法获取 PDF 文档的内容`GetContent<PdfContent>()`方法。
## 第 3 步：添加附件
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
此步骤涉及向 PDF 文档添加附件。您需要提供附件文件字节、名称和说明。
## 第 4 步：保存更改
```csharp
watermarker.Save(outputFileName);
```
最后，我们保存对文档所做的更改以及添加的附件。

## 结论
GroupDocs.Watermark for .NET 提供了一个强大的解决方案，用于无缝管理文档水印和附件。通过执行上述步骤，您可以轻松地将水印和附件功能集成到您的 .NET 应用程序中。
## 常见问题解答
### GroupDocs.Watermark 是否与所有 .NET 框架兼容？
是的，GroupDocs.Watermark 支持 .NET Framework 2.0 及更高版本。
### 我可以删除使用 GroupDocs.Watermark 添加的水印吗？
是的，GroupDocs.Watermark 提供了从文档中删除水印的方法。
### GroupDocs.Watermark 支持文档加密吗？
是的，GroupDocs.Watermark 允许您使用加密文档。
### 我可以自定义水印的外观吗？
当然，GroupDocs.Watermark 提供了各种水印自定义选项。
### 是否有可用于测试目的的试用版？
是的，您可以从以下位置访问试用版：[发布页面](https://releases.groupdocs.com/).