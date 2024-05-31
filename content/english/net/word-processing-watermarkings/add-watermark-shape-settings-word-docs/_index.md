---
title: Add Watermark with Shape Settings in Word Docs
linktitle: Add Watermark with Shape Settings in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to add watermarks with shape settings to Word documents using GroupDocs.Watermark for .NET. Protect your documents effectively.
type: docs
weight: 20
url: /net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Introduction
In this tutorial, we'll walk through the process of adding a watermark with shape settings to Word documents using GroupDocs.Watermark for .NET.
## Prerequisites
Before we begin, ensure you have the following:
1. GroupDocs.Watermark for .NET installed. You can download it from [here](https://releases.groupdocs.com/Watermark/net/).
2. Basic knowledge of C# programming.
3. An understanding of Word document processing.

## Import Namespaces
First, you need to import the necessary namespaces to access the required classes and methods.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the Document
Load the Word document where you want to add the watermark.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Watermark addition code goes here
}
```
## Step 2: Add Watermark
Instantiate a `TextWatermark` object and specify the text you want to use as the watermark.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Step 3: Customize Watermark Settings
Set various settings for the watermark, such as alignment, rotation angle, color, and opacity.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Step 4: Define Watermark Section Options
Define options for the watermark section, such as the shape name and alternative text.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Step 5: Add Watermark to Document
Add the watermark to the document with the specified options.
```csharp
watermarker.Add(watermark, options);
```
## Step 6: Save the Document
Save the document with the added watermark.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
Adding watermarks with shape settings to Word documents using GroupDocs.Watermark for .NET is a straightforward process. By following the steps outlined in this tutorial, you can effectively protect your documents with customized watermarks.
## FAQ's
### Can I add multiple watermarks to the same document?
Yes, you can add multiple watermarks with different settings to the same document.
### Does GroupDocs.Watermark support other document formats besides Word?
Yes, GroupDocs.Watermark supports various document formats, including Excel, PowerPoint, PDF, and more.
### Can I customize the appearance of the watermark further?
Absolutely, you can adjust various parameters such as font size, style, color, and position to suit your needs.
### Is there a trial version available for GroupDocs.Watermark for .NET?
Yes, you can get a free trial from [here](https://releases.groupdocs.com/).
### Where can I find support for GroupDocs.Watermark?
You can find support and ask questions on the GroupDocs forum [here](https://forum.groupdocs.com/c/watermark/19).
