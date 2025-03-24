---
title: Add Image Watermark
linktitle: Add Image Watermark
second_title: GroupDocs.Watermark .NET API
description: Effortlessly add image watermarks to your documents using GroupDocs.Watermark for .NET. Protect your intellectual property with ease.
weight: 10
url: /net/watermarking-basics/add-image-watermark/
---

# Add Image Watermark

## Introduction
In this tutorial, we'll delve into the process of adding an image watermark to your documents using GroupDocs.Watermark for .NET. Watermarking documents is essential for protecting intellectual property and branding. With GroupDocs.Watermark for .NET, you can seamlessly integrate watermarks into various document formats such as Word, Excel, PowerPoint, PDF, and many more.
## Prerequisites
Before we begin, ensure you have the following prerequisites in place:
1. GroupDocs.Watermark for .NET Library: Download and install the GroupDocs.Watermark for .NET library from the [website](https://releases.groupdocs.com/Watermark/net/).
2. Document: Have the document ready to which you want to add the watermark.
3. Image for Watermark: Prepare the image file that you want to use as the watermark.

## Import Namespaces
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Step 1: Initialize Document Path and Output Directory
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` with the absolute or relative path to your document and `"Your Document Directory"` with the directory where you want to save the watermarked document.
## Step 2: Open Document Stream and Initialize Watermarker
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Watermarking process will go here
    }
}
```
Open the document stream using `FileStream` and initialize the `Watermarker` object.
## Step 3: Add Image Watermark
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
Create an `ImageWatermark` object with the path to the image file you want to use as the watermark. Set the horizontal and vertical alignment of the watermark.
## Step 4: Save Watermarked Document
```csharp
watermarker.Save(outputFileName);
```
Save the watermarked document to the specified output directory with the desired filename.

## Conclusion
In conclusion, GroupDocs.Watermark for .NET provides a comprehensive solution for adding watermarks to various document formats effortlessly. By following the steps outlined in this tutorial, you can efficiently add image watermarks to your documents and protect your intellectual property.
## FAQ's
### Can I add text watermarks using GroupDocs.Watermark for .NET?
Yes, GroupDocs.Watermark for .NET supports adding both image and text watermarks to documents.
### Is GroupDocs.Watermark for .NET compatible with different document formats?
Absolutely, GroupDocs.Watermark for .NET supports a wide range of document formats including Word, Excel, PowerPoint, PDF, and more.
### Does GroupDocs.Watermark for .NET provide customization options for watermarks?
Yes, you can customize various aspects of the watermark such as position, size, opacity, and rotation.
### Can I remove watermarks from documents using GroupDocs.Watermark for .NET?
Yes, GroupDocs.Watermark for .NET offers functionality to detect and remove watermarks from documents.
### Is there a trial version available for GroupDocs.Watermark for .NET?
Yes, you can avail of a free trial version from the website to explore the features before purchasing [here](https://releases.groupdocs.com/).
