---
title: Add Text Watermark
linktitle: Add Text Watermark
second_title: GroupDocs.Watermark .NET API
description: Learn how to add text watermarks to your documents using Groupdocs.Watermark for .NET with this step-by-step guide.
weight: 11
url: /net/watermarking-basics/add-text-watermark/
---
## Introduction
GroupDocs.Watermark for .NET is a powerful library that allows developers to add, search, and remove watermarks from various document formats in .NET applications. In this tutorial, we'll focus on adding a text watermark to a document using GroupDocs.Watermark.
## Prerequisites
Before we begin, make sure you have the following prerequisites:
1. Basic knowledge of C# programming language.
2. Visual Studio installed on your system.
3. GroupDocs.Watermark for .NET library installed. You can download it from [here](https://releases.groupdocs.com/Watermark/net/).

## Import Namespaces
First, you need to import the necessary namespaces into your C# project.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Step 1: Define Document Path and Output Directory
Define the path to your input document and the output directory where the watermarked document will be saved.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` with the absolute or relative path to your input document, for example: `@"C:\Docs\document.pdf"`. Also, specify the directory where you want to save the watermarked document.
## Step 2: Add Text Watermark
Instantiate the `Watermarker` class with the input document path. Then, create a `TextWatermark` object with the desired text and font settings.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Conclusion
In this tutorial, we have learned how to add a text watermark to a document using GroupDocs.Watermark for .NET. With its intuitive API, developers can easily manipulate watermarks in various document formats.
## FAQ's
### Is GroupDocs.Watermark for .NET compatible with all document formats?
GroupDocs.Watermark supports a wide range of document formats including PDF, Microsoft Word, Excel, PowerPoint, and many more.
### Can I customize the appearance of the text watermark?
Yes, you can customize various properties such as font, color, alignment, and opacity of the text watermark.
### Does GroupDocs.Watermark provide support for removing watermarks from documents?
Yes, GroupDocs.Watermark offers functionality to search for and remove watermarks from documents.
### Can I try GroupDocs.Watermark for .NET before purchasing?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Watermark?
You can get technical support by visiting the [GroupDocs.Watermark forum](https://forum.groupdocs.com/c/watermark/19).
