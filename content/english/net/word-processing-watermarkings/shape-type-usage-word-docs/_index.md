---
title: Shape Type Usage in Word Docs
linktitle: Shape Type Usage in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to manipulate shapes in Word documents using GroupDocs.Watermark for .NET. This tutorial provides guidance for efficient document processing.
weight: 37
url: /net/word-processing-watermarkings/shape-type-usage-word-docs/
type: docs
---
# Shape Type Usage in Word Docs

## Introduction
In this tutorial, we will explore how to utilize shape types in Word documents using GroupDocs.Watermark for .NET. Shapes in Word documents can vary, and understanding how to manipulate them can be crucial for various document processing tasks.
## Prerequisites
Before we begin, ensure you have the following prerequisites in place:
1. GroupDocs.Watermark for .NET Library: Download and install the GroupDocs.Watermark for .NET library from the [download link](https://releases.groupdocs.com/Watermark/net/).
2. Document Path: Have a Word document ready for processing.
3. Development Environment: Set up a suitable development environment with .NET framework support.

## Import Namespaces
To get started, you need to import the necessary namespaces into your project. These namespaces will provide access to the required classes and methods for working with Word documents.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Step 1: Load the Document
Begin by loading the Word document into the Watermarker object. Ensure to specify the document path and any additional options required during the loading process.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Document processing code goes here
}
```
## Step 2: Access Document Content
Access the content of the loaded Word document using the `GetContent<WordProcessingContent>()` method. This will provide access to sections, paragraphs, and shapes present in the document.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Step 3: Iterate Through Sections and Shapes
Iterate through each section and shape within the document to inspect and manipulate them as required.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Shape manipulation code goes here
    }
}
```
## Step 4: Check Shape Types
Within the loop, check for specific shape types using the `ShapeType` property. This example demonstrates identifying and handling Diagonal Corners Rounded shapes.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Shape-specific manipulation code goes here
}
```
## Step 5: Manipulate Shapes
Perform actions such as adding text, modifying formatting, or applying visual changes to the identified shapes.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Step 6: Save the Document
Once all necessary modifications are made, save the document with the applied changes to the specified output file.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
Manipulating shapes in Word documents can be essential for various document processing tasks. With GroupDocs.Watermark for .NET, you can easily identify, modify, and manipulate shapes to meet your requirements efficiently.
## FAQ's
### Can GroupDocs.Watermark for .NET handle other document formats besides Word?
Yes, GroupDocs.Watermark for .NET supports a wide range of document formats, including PDF, Excel, PowerPoint, and more.
### Is there a free trial available for GroupDocs.Watermark for .NET?
Yes, you can access a free trial version from the [releases page](https://releases.groupdocs.com/).
### Does GroupDocs.Watermark for .NET provide technical support?
Yes, you can seek assistance and engage with the community through the [support forum](https://forum.groupdocs.com/c/watermark/19).
### Can I customize the watermarking process for specific document requirements?
Absolutely, GroupDocs.Watermark for .NET offers extensive customization options to tailor the watermarking process according to your needs.
### How can I obtain a temporary license for GroupDocs.Watermark for .NET?
You can acquire a temporary license from the [temporary license purchase page](https://purchase.groupdocs.com/temporary-license/) for testing and evaluation purposes.
