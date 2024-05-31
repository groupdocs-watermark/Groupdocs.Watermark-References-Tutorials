---
title: 在 Word 文档中获取形状信息
linktitle: 在 Word 文档中获取形状信息
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs for .NET 轻松从 Word 文档中获取有价值的见解。无缝提取形状信息以增强数据分析。
type: docs
weight: 24
url: /zh/net/word-processing-watermarkings/get-shapes-information-word-docs/
---
## 介绍
在数据为王的数字环境中，从文档中提取有意义的见解至关重要。 GroupDocs.Watermark for .NET 使开发人员能够深入研究文档结构，轻松提取有价值的信息。在本教程中，我们将逐步探索如何利用这个强大的工具从Word文档中获取形状信息。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
1.  GroupDocs.Watermark for .NET：从以下位置下载并安装该库[网站](https://releases.groupdocs.com/Watermark/net/).
2. 开发环境：设置 .NET 开发环境，包括 Visual Studio 或任何首选的文本编辑器。
3. 访问 Word 文档：可以访问您希望从中提取形状信息的 Word 文档。

## 导入必要的命名空间
在继续编写代码之前，必须导入所需的命名空间：
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
```
## 第 1 步：加载文档
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
确保更换`"Your Document Path"`与 Word 文档的实际路径。
## 第 2 步：提取形状信息
```csharp
	WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
	foreach (WordProcessingSection section in content.Sections)
	{
		foreach (WordProcessingShape shape in section.Shapes)
		{
```
此代码片段获取 Word 文档的内容并迭代其中的每个部分和形状。
## 第 3 步：分析形状属性
```csharp
			if (shape.HeaderFooter != null)
			{
				Console.WriteLine("In header/footer");
			}
			Console.WriteLine(shape.ShapeType);
			Console.WriteLine(shape.Width);
			Console.WriteLine(shape.Height);
			Console.WriteLine(shape.IsWordArt);
			Console.WriteLine(shape.RotateAngle);
			Console.WriteLine(shape.AlternativeText);
			Console.WriteLine(shape.Name);
			Console.WriteLine(shape.X);
			Console.WriteLine(shape.Y);
			Console.WriteLine(shape.Text);
			if (shape.Image != null)
			{
				Console.WriteLine(shape.Image.Width);
				Console.WriteLine(shape.Image.Height);
				Console.WriteLine(shape.Image.GetBytes().Length);
			}
			Console.WriteLine(shape.HorizontalAlignment);
			Console.WriteLine(shape.VerticalAlignment);
			Console.WriteLine(shape.RelativeHorizontalPosition);
			Console.WriteLine(shape.RelativeVerticalPosition);
		}
	}
}
```
这部分代码片段检索每个形状的各种属性，例如其类型、尺寸、位置、文本等。

## 结论
GroupDocs.Watermark for .NET 简化了从 Word 文档中提取形状信息的过程，为开发人员提供了一个无缝的解决方案，可以轻松地深入研究文档结构。通过遵循本教程中概述的步骤，您可以从文档中获得有价值的见解，从而增强您的数据分析能力。
## 常见问题解答
### GroupDocs.Watermark 是否与其他文档格式兼容？
是的，GroupDocs 支持各种文档格式，包括 PDF、Excel、PowerPoint 等。
### 我可以使用 GroupDocs.Watermark 将水印应用到文档吗？
当然，GroupDocs.Watermark 使您能够轻松地以编程方式向文档添加水印。
### GroupDocs.Watermark 是否提供对自定义文档解析的支持？
事实上，GroupDocs.Watermark 为自定义文档解析提供了灵活的选项，以适应不同的用例。
### GroupDocs.Watermark适合企业级文档处理吗？
是的，GroupDocs.Watermark 旨在满足企业级文档处理的需求，提供强大的功能和可扩展性。
### 我可以将 GroupDocs.Watermark 集成到我现有的 .NET 项目中吗？
当然，GroupDocs.Watermark 可以无缝集成到 .NET 项目中，为文档操作提供全面的解决方案。