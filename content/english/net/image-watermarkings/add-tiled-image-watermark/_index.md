---
title: Add Tiled Image Watermark
linktitle: Add Tiled Image Watermark
second_title: GroupDocs.Watermark .NET API
description: Learn how to add tiled image watermarks to your documents using GroupDocs.Watermark for .NET. Easy, efficient, and customizable.
weight: 10
url: /net/image-watermarkings/add-tiled-image-watermark/
---
## Introduction
GroupDocs.Watermark for .NET is a powerful API that allows developers to add, remove, and search watermarks in various document formats programmatically. In this tutorial, we will guide you through the process of adding a tiled image watermark to your documents using GroupDocs.Watermark for .NET.
## Prerequisites
Before you begin, ensure you have the following:
- Basic knowledge of C# programming language.
- Visual Studio installed on your system.
- GroupDocs.Watermark for .NET library added to your project. You can download it from [here](https://releases.groupdocs.com/Watermark/net/).

## Import Namespaces
Make sure to import the necessary namespaces at the beginning of your C# file:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Step 1: Set Document Path and Output Directory
Define the path of your input document and the directory where you want to save the output document:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` with the absolute or relative path to your input document.
## Step 2: Initialize Watermarker Object
Create a Watermarker object using the input document path:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Add watermark here
}
```
## Step 3: Add Tiled Image Watermark
Instantiate an ImageWatermark object with the path to the image file you want to use as a watermark:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Configure tile options
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Add watermark to the document
    watermarker.Add(watermark);
    // Save the modified document
    watermarker.Save(outputFileName);
}
```
Replace `"Path to Your Image"` with the actual path to your watermark image file.

## Conclusion
By following these steps, you can easily add a tiled image watermark to your documents using GroupDocs.Watermark for .NET. Experiment with different options and configurations to achieve the desired result.
## FAQ's
### Can I add multiple watermarks to a single document?
Yes, you can add multiple watermarks of different types to a document using GroupDocs.Watermark for .NET.
### Does GroupDocs.Watermark support all document formats?
GroupDocs.Watermark supports a wide range of document formats, including PDF, Word, Excel, PowerPoint, and many more.
### Is there a trial version available for GroupDocs.Watermark?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### Can I customize the appearance of the watermark?
Yes, you can customize various aspects of the watermark, such as position, size, rotation, transparency, etc.
### Does GroupDocs.Watermark offer technical support?
Yes, you can get technical support from the GroupDocs.Watermark forum [here](https://forum.groupdocs.com/c/watermark/19).
