---
title: Add Watermark to XObjects in PDF
linktitle: Add Watermark to XObjects in PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to add watermarks to XObjects in PDF using Groupdocs.Watermark for .NET. Follow our step-by-step guide for easy implementation.
weight: 20
url: /net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---

# Add Watermark to XObjects in PDF

## Introduction
Watermarking PDFs is a crucial step for ensuring your documents are protected from unauthorized use. With Groupdocs.Watermark for .NET, adding watermarks to XObjects within your PDFs has never been easier. In this tutorial, we'll walk you through the process step-by-step, ensuring you can confidently apply watermarks to your PDF documents. Let's get started!
## Prerequisites
Before diving into the tutorial, let's ensure you have everything you need to follow along seamlessly:
- Groupdocs.Watermark for .NET: Download and install the latest version from [here](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Make sure you have .NET Framework installed on your development machine.
- Development Environment: Use Visual Studio or any other IDE that supports .NET development.
- Temporary License: Obtain a [temporary license](https://purchase.groupdocs.com/temporary-license/) if you are evaluating the product.
Once you have these prerequisites in place, you are ready to start watermarking your PDFs.
## Import Namespaces
First, you'll need to import the necessary namespaces in your project. Open your C# project and add the following using directives:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Set Up Your Document Paths
The first step involves setting up the paths for your document. Define the path where your PDF is located and where you want to save the watermarked PDF.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` and `"Your Document Directory"` with the actual paths on your machine.
## Step 2: Initialize PDF Load Options
Next, you'll need to initialize the PDF load options. This is crucial for loading the PDF content correctly.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Step 3: Load the PDF Document
Using the load options, load the PDF document with the `Watermarker` class.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Step 4: Create the Watermark
Now, you need to create the watermark that will be added to the PDF. For this tutorial, we'll create a text watermark.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Step 5: Add Watermark to XObjects
Iterate through each page and each XObject within the PDF to apply the watermark.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Add watermark to the image
            xObject.Image.Add(watermark);
        }
    }
}
```
## Step 6: Save the Watermarked PDF
Finally, save the watermarked PDF to the specified output file.
```csharp
    watermarker.Save(outputFileName);
}
```
And there you have it! Your PDF now contains watermarks on all its XObjects.
## Conclusion
Adding watermarks to your PDF documents using Groupdocs.Watermark for .NET is a straightforward process that provides an additional layer of security. By following the steps outlined in this tutorial, you can ensure that your documents are protected from unauthorized use. Remember, you can always refer to the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for more detailed information and advanced features.
## FAQ's
### Can I use an image as a watermark instead of text?
Yes, Groupdocs.Watermark for .NET supports both text and image watermarks.
### How can I test Groupdocs.Watermark without purchasing it?
You can use a [temporary license](https://purchase.groupdocs.com/temporary-license/) to evaluate the product.
### Is it possible to customize the watermark's appearance?
Absolutely! You can customize the font, size, rotation angle, and more.
### Does Groupdocs.Watermark support other document formats?
Yes, it supports various formats, including Word, Excel, and PowerPoint.
### Where can I get support if I encounter issues?
You can get support from the [Groupdocs forum](https://forum.groupdocs.com/c/watermark/19).