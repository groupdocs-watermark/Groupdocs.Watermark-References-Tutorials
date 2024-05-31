---
title: Add Artifact Watermark to PDF
linktitle: Add Artifact Watermark to PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to add artifact watermarks to PDF files effortlessly using Groupdocs.Watermark for .NET. Protect your documents with eased.
type: docs
weight: 11
url: /net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Introduction
Adding watermarks to PDF files is a crucial aspect of document management, especially when it comes to protecting intellectual property or branding documents. Groupdocs.Watermark for .NET provides a robust solution for adding watermarks to PDF files effortlessly. In this tutorial, we'll walk through the process of adding an artifact watermark to PDF files step by step.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. Groupdocs.Watermark for .NET: Download and install Groupdocs.Watermark for .NET from [here](https://releases.groupdocs.com/Watermark/net/).
2. Development Environment: Have a .NET development environment set up.
3. PDF Document: Prepare the PDF document to which you want to add the watermark.
4. Output Directory: Create a directory to save the watermarked PDF file.

## Importing Namespaces
To start with, import the necessary namespaces in your C# project:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the PDF Document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Step 2: Define Watermark Options
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Step 3: Add Text Watermark
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Step 4: Add Image Watermark
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Step 5: Save the Watermarked PDF
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
In this tutorial, we've learned how to add artifact watermarks to PDF files using Groupdocs.Watermark for .NET. By following these steps, you can seamlessly integrate watermarking functionality into your .NET applications, ensuring the security and integrity of your documents.
## FAQ's
### Can I customize the appearance of the text watermark?
Yes, you can customize various aspects such as font, size, color, and alignment of the text watermark according to your preferences.
### Does Groupdocs.Watermark support adding watermarks to other document formats?
Yes, Groupdocs.Watermark supports adding watermarks to a wide range of document formats including Word, Excel, PowerPoint, and more.
### Is there a trial version available for Groupdocs.Watermark for .NET?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get support for any issues or queries related to Groupdocs.Watermark?
You can get support from the Groupdocs community forum [here](https://forum.groupdocs.com/c/watermark/19).
### Can I use Groupdocs.Watermark for commercial purposes?
Yes, you can purchase a license for commercial use from [here](https://purchase.groupdocs.com/buy).
