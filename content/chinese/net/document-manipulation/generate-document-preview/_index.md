---
title: 生成文档预览
linktitle: 生成文档预览
second_title: GroupDocs.Watermark .NET API
description: 通过本指南了解如何使用 GroupDocs.Watermark for .NET 生成文档预览。轻松增强您的文档安全性和管理。
weight: 10
url: /zh/net/document-manipulation/generate-document-preview/
---

# 生成文档预览

## 介绍
在数字文档管理领域，水印在确保文档的安全性和真实性方面发挥着至关重要的作用。 GroupDocs.Watermark for .NET 是一个功能强大的工具，允许开发人员轻松地向文档添加水印。在本教程中，我们将引导您完成使用 GroupDocs.Watermark for .NET 生成文档预览的过程。无论您是经验丰富的开发人员还是刚刚入门，本指南都将为您提供全面的分步流程来实现您的目标。
## 先决条件
在深入实施之前，让我们确保您拥有开始所需的一切：
- 对 C# 和 .NET 框架有基本了解。
- Visual Studio 安装在您的计算机上。
- .NET 库的 GroupDocs.Watermark。你可以[在这里下载](https://releases.groupdocs.com/Watermark/net/).
- GroupDocs.Watermark 的有效许可证。您可以购买[这里](https://purchase.groupdocs.com/buy)或获得[临时执照](https://purchase.groupdocs.com/temporary-license/)出于评估目的。
## 导入命名空间
要开始在项目中使用 GroupDocs.Watermark，您需要导入必要的命名空间。这可以通过在代码中添加以下 using 指令来完成：
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
这些命名空间将提供对加水印和生成文档预览所需的类和方法的访问。

让我们将生成文档预览的过程分解为简单、易于遵循的步骤。
## 第 1 步：设置您的项目
首先，在 Visual Studio 中设置 .NET 项目。如果您还没有项目，请按照以下步骤创建一个新项目：
1. 打开视觉工作室。
2. 单击“创建新项目”。
3. 选择“控制台应用程序（.NET Core）”，然后单击“下一步”。
4. 为您的项目命名并选择保存位置，然后单击“创建”。
## 步骤 2：安装适用于 .NET 的 GroupDocs.Watermark
要在项目中使用 GroupDocs.Watermark，您需要安装该库。这可以使用 NuGet 包管理器来完成：
1. 在解决方案资源管理器中右键单击您的项目。
2. 选择“管理 NuGet 包”。
3. 在“浏览”选项卡中搜索“GroupDocs.Watermark”。
4. 单击“安装”将库添加到您的项目中。
或者，您可以通过包管理器控制台安装它：
```powershell
Install-Package GroupDocs.Watermark
```
## 步骤 3：定义文档路径和输出目录
在生成预览之前，您需要指定要预览的文档的路径以及预览图像的保存目录：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
将“您的文档路径”替换为文档的路径，将“您的文档目录”替换为要保存预览图像的目录。
## 第四步：初始化水印对象
创建一个实例`Watermarker`类通过将文档路径传递给其构造函数来实现。该对象将用于执行所有水印操作：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //你的代码在这里
}
```
## 第 5 步：创建流处理的委托方法
要生成预览，您需要定义用于创建和释放流的委托方法。这些方法将处理文档每个页面的流的创建和释放：
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
这`createPageStreamDelegate`方法为文档的每个页面创建一个流，而`releasePageStreamDelegate`方法在预览生成后关闭流。
## 第 6 步：配置预览选项
接下来，通过创建一个实例来配置预览选项`PreviewOptions`班级。指定委托方法并将预览格式设置为 PNG。您还可以指定预览中包含哪些页面：
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
在此示例中，我们正在生成文档前两页的预览。
## 第 7 步：生成文档预览
最后，致电`GeneratePreview`方法上的`Watermarker`对象，传入配置的`PreviewOptions`。这将生成预览图像并将其保存到指定目录：
```csharp
watermarker.GeneratePreview(previewOptions);
```
## 结论
使用 GroupDocs.Watermark for .NET 生成文档预览是一个简单的过程，只需几行代码即可完成。通过遵循本指南中概述的步骤，您可以轻松设置项目、配置必要的选项并生成文档预览。这个强大的库不仅简化了水印过程，而且还提供了管理和操作水印的强大功能。
如果您有任何疑问或需要进一步帮助，请随时访问[GroupDocs.Watermark 支持论坛](https://forum.groupdocs.com/c/watermark/19)或参考[文档](https://tutorials.groupdocs.com/Watermark/net/).
## 常见问题解答
### GroupDocs.Watermark for .NET 支持哪些文件格式？
 GroupDocs.Watermark for .NET 支持多种文件格式，包括 PDF、DOCX、PPTX、XLSX 等。有关支持格式的完整列表，请参阅[文档](https://tutorials.groupdocs.com/Watermark/net/).
### 我可以自定义水印的外观吗？
是的，GroupDocs.Watermark 允许您完全自定义水印的外观，包括文本、图像和形状水印。您可以调整字体、颜色、大小和透明度等属性。
### 有试用版吗？
是的，您可以获得[免费试用](https://releases.groupdocs.com/)GroupDocs.Watermark for .NET 在购买前评估其功能。
### 如何购买 GroupDocs.Watermark 的许可证？
您可以购买 GroupDocs.Watermark 的许可证[这里](https://purchase.groupdocs.com/buy)。有多种许可选项可满足不同的需求。
### 我可以在商业项目中使用 GroupDocs.Watermark 吗？
是的，只要拥有有效的许可证，您就可以在商业项目中使用 GroupDocs.Watermark。请务必查看许可条款和条件[购买页面](https://purchase.groupdocs.com/buy).