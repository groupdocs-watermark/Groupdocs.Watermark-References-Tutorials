---
title: Get Supported File Formats
linktitle: Get Supported File Formats
second_title: GroupDocs.Watermark .NET API
description: Effortlessly add watermarks to your documents using GroupDocs.Watermark for .NET. Follow our comprehensive, step-by-step guide to protect your digital assets.
weight: 13
url: /net/document-manipulation/get-supported-file-formats/
---
## Introduction
Watermarking your documents is a crucial step in safeguarding your digital assets. Whether it's for protecting intellectual property, ensuring confidentiality, or simply branding, watermarks play a vital role. If you're a .NET developer looking to integrate watermarking capabilities into your applications, GroupDocs.Watermark for .NET is a powerful and versatile tool you should consider. This tutorial will guide you through the essentials of using GroupDocs.Watermark, from installation to applying your first watermark, breaking down each step to ensure you can easily follow along.
## Prerequisites
Before we dive into the specifics, let's make sure you have everything you need to get started:
1. Visual Studio: Make sure you have Visual Studio installed on your machine. You can download it from the [Visual Studio website](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark supports various versions of the .NET Framework. Ensure that your project targets a compatible version.
3. GroupDocs.Watermark for .NET: You can download the latest version from the [release page](https://releases.groupdocs.com/Watermark/net/).
4. Basic Knowledge of C#: This tutorial assumes you have a fundamental understanding of C# and .NET development.
## Import Namespaces
First, let's import the necessary namespaces in your project. Open your C# file and add the following using directives at the top:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
With these namespaces imported, you're ready to start adding watermarks to your documents.

## Step 1: Initialize the Watermarking Engine
The first step is to initialize the watermarking engine. This involves creating an instance of the `Watermarker` class with the document you want to watermark.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
This code snippet sets up the `Watermarker` object, which you'll use to apply watermarks to your document.
## Step 2: Add a Text Watermark
Now, let's add a simple text watermark to your document. Text watermarks are great for adding labels like "Confidential" or "Draft."
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
Here, we've created a `TextWatermark` object with the text "Confidential," set its font and color, and aligned it to the center of the document.
## Step 3: Add an Image Watermark
If you prefer to use an image as a watermark, GroupDocs.Watermark makes it easy to do so.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
In this example, we create an `ImageWatermark` object, set its dimensions, and align it to the top-right corner of the document.
## Step 4: Save the Document
After adding the desired watermarks, the final step is to save the modified document.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
This will save the watermarked document to the specified path and release any resources used by the `Watermarker` instance.
## Step 5: Get Supported File Formats
To see which file formats are supported by GroupDocs.Watermark, you can use the following code snippet:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
This will print out all the file types that GroupDocs.Watermark can handle, giving you a comprehensive view of its capabilities.
## Conclusion
Watermarking your documents with GroupDocs.Watermark for .NET is straightforward and efficient. By following this tutorial, you've learned how to initialize the watermarking engine, add text and image watermarks, save your watermarked documents, and list supported file formats. With these tools, you can protect your documents with confidence.
If you have any questions or need further assistance, don't hesitate to visit the [GroupDocs.Watermark support forum](https://forum.groupdocs.com/c/watermark/19).
## FAQ's
### How do I install GroupDocs.Watermark for .NET?
You can download it from the [release page](https://releases.groupdocs.com/Watermark/net/) and add the DLL to your project.
### Can I try GroupDocs.Watermark for free?
Yes, you can request a [free trial](https://releases.groupdocs.com/) to evaluate the software before purchasing.
### What file formats are supported by GroupDocs.Watermark?
You can use the provided code snippet to list all supported file formats.
### How can I buy a license for GroupDocs.Watermark?
Licenses can be purchased directly from the [purchase page](https://purchase.groupdocs.com/buy).
### Is there any documentation available for GroupDocs.Watermark?
Yes, comprehensive documentation is available [here](https://tutorials.groupdocs.com/Watermark/net/).
