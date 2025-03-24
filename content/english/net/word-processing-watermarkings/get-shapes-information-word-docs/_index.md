---
title: Get Shapes Information in Word Docs
linktitle: Get Shapes Information in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Unlock valuable insights from Word documents effortlessly with GroupDocs.Watermark for .NET. Extract shape information seamlessly for enhanced data analysis.
weight: 24
url: /net/word-processing-watermarkings/get-shapes-information-word-docs/
---
## Introduction
In the digital landscape where data is king, extracting meaningful insights from documents is paramount. GroupDocs.Watermark for .NET empowers developers to delve into document structures, extracting valuable information effortlessly. In this tutorial, we will explore how to leverage this powerful tool to obtain shapes information from Word documents step by step.
## Prerequisites
Before diving into the tutorial, ensure you have the following prerequisites in place:
1. GroupDocs.Watermark for .NET: Download and install the library from the [website](https://releases.groupdocs.com/Watermark/net/).
2. Development Environment: Set up a .NET development environment, including Visual Studio or any preferred text editor.
3. Access to Word Documents: Have access to the Word documents from which you wish to extract shape information.

## Importing Necessary Namespaces
Before proceeding with the code, it's essential to import the required namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
```
## Step 1: Load the Document
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
Ensure to replace `"Your Document Path"` with the actual path to your Word document.
## Step 2: Extract Shapes Information
```csharp
	WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
	foreach (WordProcessingSection section in content.Sections)
	{
		foreach (WordProcessingShape shape in section.Shapes)
		{
```
This snippet fetches the content of the Word document and iterates over each section and shape within.
## Step 3: Analyze Shape Attributes
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
This part of the code snippet retrieves various attributes of each shape, such as its type, dimensions, position, text, and more.

## Conclusion
GroupDocs.Watermark for .NET simplifies the extraction of shapes information from Word documents, providing developers with a seamless solution to delve into document structures effortlessly. By following the steps outlined in this tutorial, you can unlock valuable insights from your documents, enhancing your data analysis capabilities.
## FAQ's
### Is GroupDocs.Watermark compatible with other document formats?
Yes, GroupDocs.Watermark supports various document formats, including PDF, Excel, PowerPoint, and more.
### Can I apply watermarks to documents using GroupDocs.Watermark?
Absolutely, GroupDocs.Watermark enables you to add watermarks to documents programmatically with ease.
### Does GroupDocs.Watermark offer support for custom document parsing?
Indeed, GroupDocs.Watermark provides flexible options for custom document parsing to suit diverse use cases.
### Is GroupDocs.Watermark suitable for enterprise-level document processing?
Yes, GroupDocs.Watermark is designed to meet the needs of enterprise-level document processing, offering robust features and scalability.
### Can I integrate GroupDocs.Watermark into my existing .NET projects?
Certainly, GroupDocs.Watermark seamlessly integrates into .NET projects, providing a comprehensive solution for document manipulation.
