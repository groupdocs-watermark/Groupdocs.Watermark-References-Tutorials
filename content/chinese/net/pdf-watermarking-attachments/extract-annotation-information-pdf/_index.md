---
title: 从 PDF 中提取注释信息
linktitle: 从 PDF 中提取注释信息
second_title: GroupDocs.Watermark .NET API
description: 在此详细的分步指南中了解如何使用 GroupDocs.Watermark for .NET 从 PDF 文档中提取注释信息。
type: docs
weight: 23
url: /zh/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## 介绍
您是否经常发现自己需要从 PDF 文档中提取详细的注释信息？无论您是文档管理系统的开发人员还是处理大量 PDF 的业务专业人员，高效提取和处理注释都至关重要。借助 GroupDocs.Watermark for .NET，您可以使用强大的工具包来使此任务变得简单而高效。
## 先决条件
在我们深入研究代码之前，让我们确保您拥有开始使用所需的一切：
1. Visual Studio：确保您已安装 Visual Studio。这将是我们用于编写和运行代码的 IDE。
2.  GroupDocs.Watermark for .NET：您需要拥有 GroupDocs.Watermark for .NET 库。你可以[在这里下载](https://releases.groupdocs.com/Watermark/net/).
3. C# 基础知识：需要熟悉 C# 编程才能理解示例。
## 导入命名空间
首先，您需要将必要的命名空间导入到您的项目中。这些命名空间包含处理 PDF 文件和提取注释所需的类和方法。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## 第 1 步：设置您的项目
首先，让我们在 Visual Studio 中设置我们的项目。创建一个新的控制台应用程序（.NET Core）项目。创建项目后，您需要添加对 GroupDocs.Watermark for .NET 库的引用。
1. 打开 NuGet 包管理器。
2. 搜索`GroupDocs.Watermark`.
3. 安装`GroupDocs.Watermark`包裹。
## 第 2 步：定义文档路径
接下来，您需要指定输入 PDF 文档的路径以及保存提取信息的输出目录。这可确保您的应用程序知道在哪里可以找到 PDF 文件以及在哪里存储结果。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 第 3 步：加载 PDF 文档
要使用 PDF 文档，我们需要使用以下命令加载它`PdfLoadOptions`。此类提供了配置加载过程的选项。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //提取注释的代码将放在此处
}
```
## 第 4 步：访问 PDF 内容
加载文档后，我们就可以访问其内容。具体来说，我们想要获取 PDF 内容，以便可以迭代页面和注释。
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 第 5 步：迭代页面和注释
有了 PDF 内容，我们就可以循环浏览每个页面，然后浏览这些页面上的每个注释。这使我们能够提取我们需要的信息。
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        //在此提取注释详细信息
    }
}
```
## 第 6 步：提取注释详细信息
在嵌套循环中，我们提取有关每个注释的各种详细信息。这包括注释的类型、任何关联的图像、文本和位置数据。
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## 第 7 步：保存或处理提取的数据
最后，决定要如何处理提取的注释信息。您可以根据需要将其打印到控制台、将其保存到文件，甚至存储在数据库中。
```csharp
//将提取的数据保存到文件的示例
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## 结论
使用 GroupDocs.Watermark for .NET 从 PDF 文档中提取注释信息是一个简单的过程，可以为您节省大量时间和精力。通过遵循本指南中概述的步骤，您可以轻松地将此功能集成到您的项目中并自动提取有价值的注释数据。
无论您是管理大量 PDF 还是仅需要提取特定信息，GroupDocs.Watermark for .NET 都能提供可靠且高效的解决方案。不要忘记查看[文档](https://reference.groupdocs.com/Watermark/net/)了解更多高级功能和定制选项。
## 常见问题解答
### 什么是 .NET 的 GroupDocs.Watermark？
GroupDocs.Watermark for .NET 是一个综合库，允许开发人员从各种文档格式（包括 PDF、Word 文档和图像）添加、搜索和删除水印。
### 我可以免费试用 GroupDocs.Watermark 吗？
是的，您可以获得[免费试用](https://releases.groupdocs.com/)在购买之前测试图书馆的功能。
### 如果遇到问题，我如何获得支持？
您可以通过访问 GroupDocs 团队获得支持[支持论坛](https://forum.groupdocs.com/c/watermark/19).
### 是否可以获得临时测试许可证？
是的，您可以请求[临时执照](https://purchase.groupdocs.com/temporary-license/)用于测试目的。
### 在哪里可以购买适用于 .NET 的 GroupDocs.Watermark 的完整版本？
您可以从以下网站购买完整版本[集团文档网站](https://purchase.groupdocs.com/buy).