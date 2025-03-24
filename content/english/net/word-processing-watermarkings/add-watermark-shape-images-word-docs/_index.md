---
title: Add Watermark to Shape Images in Word Docs
linktitle: Add Watermark to Shape Images in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to add watermarks to shape images in Word documents using GroupDocs.Watermark for .NET. Enhance document security with this tutorial.
weight: 17
url: /net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Introduction
In this tutorial, we will explore how to add a watermark to shape images within Word documents using GroupDocs.Watermark for .NET. Watermarking is a crucial aspect of document protection, especially when dealing with sensitive or confidential information. By adding watermarks to shape images, you can ensure the integrity and security of your documents.
## Prerequisites
Before we begin, ensure you have the following:
1. GroupDocs.Watermark for .NET: Download and install the GroupDocs.Watermark library from the [download page](https://releases.groupdocs.com/Watermark/net/).
2. Document: Prepare the Word document where you want to add the watermark.
3. Development Environment: Set up your preferred .NET development environment.
## Import Namespaces
Before writing the code, make sure to import the necessary namespaces:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the Document
First, define the path to your document and specify the output file name:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Step 2: Initialize Watermarker
Instantiate a `Watermarker` object by providing the document path and optional load options:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Add watermarking logic here
}
```
## Step 3: Create Text Watermark
Define the text watermark with desired properties such as text, font, alignment, rotation, sizing, etc.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Step 4: Apply Watermark to Shape Images
Iterate through the document sections and shapes to identify shape images and add the watermark:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Step 5: Save the Document
Save the document with the added watermark to the specified output file:
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
In this tutorial, we have learned how to add watermarks to shape images in Word documents using GroupDocs.Watermark for .NET. By following the step-by-step guide and leveraging the powerful features of GroupDocs.Watermark, you can enhance the security and protection of your documents effectively.
## FAQ's
### Can I customize the appearance of the watermark text?
Yes, you can adjust various properties such as font, size, color, rotation angle, and alignment to customize the watermark according to your ptutorialss.
### Does GroupDocs.Watermark support other document formats besides Word?
Yes, GroupDocs.Watermark provides support for a wide range of document formats including PDF, Excel, PowerPoint, and more.
### Is it possible to add multiple watermarks to a single document?
Absolutely, you can add multiple watermarks with different content, styles, and positions within the same document.
### Can I remove watermarks from documents using GroupDocs.Watermark?
Yes, GroupDocs.Watermark offers features to detect and remove watermarks from documents efficiently.
### Does GroupDocs.Watermark provide cross-platform compatibility?
Yes, GroupDocs.Watermark is compatible with .NET Framework, .NET Core, and .NET Standard, ensuring seamless integration across different platforms.
