---
title: Add Watermarks to PDF
linktitle: Add Watermarks to PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to add text and image watermarks to your PDFs using GroupDocs.Watermark for .NET with our comprehensive step-by-step guide.
type: docs
weight: 14
url: /net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## Introduction
Are you looking to add watermarks to your PDFs to protect your documents or brand them with your logo? Look no further! In this tutorial, we'll dive into the process of using GroupDocs.Watermark for .NET to add both text and image watermarks to your PDF files. Whether you're a seasoned developer or just starting, this guide will walk you through each step, ensuring you can apply watermarks with ease and precision.
## Prerequisites
Before we get started, let's ensure you have everything you need to follow along with this tutorial:
- GroupDocs.Watermark for .NET: Make sure you have the latest version installed. You can [download it here](https://releases.groupdocs.com/Watermark/net/).
- .NET Development Environment: Visual Studio or any other IDE that supports .NET.
- Basic Knowledge of C#: Understanding the basics of C# programming will help you follow the steps with ease.
- PDF Document: Have a sample PDF document ready for watermarking.
- Image for Watermark: If you're adding an image watermark, have your image file ready.
## Import Namespaces
First, you need to import the necessary namespaces in your C# project. This will allow you to access the GroupDocs.Watermark functionality.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Now, let’s break down the process into manageable steps.
## Step 1: Load Your PDF Document
The first step is to load your PDF document into the watermarker. Here’s how you can do it:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Further steps will be added here
}
```
## Step 2: Add a Text Watermark to the First Page
Next, we'll add a text watermark to the first page of your PDF. Follow these instructions:
```csharp
// Add text watermark to the first page
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Adding a text watermark can help protect your document from unauthorized use or simply brand it. Imagine stamping your document with an invisible seal of authenticity.
## Step 3: Add an Image Watermark to the Second Page
Now, let's add an image watermark to the second page. This is particularly useful for logos or any graphical watermarks.
```csharp
// Add image watermark to the second page
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Image watermarks can make your documents look professional and ensure that your brand is always visible. It’s like adding your signature to every page.
## Step 4: Save the Watermarked PDF
After adding the watermarks, the final step is to save the watermarked PDF to your desired location.
```csharp
watermarker.Save(outputFileName);
```
Saving the document finalizes all the changes you made. This is the moment your efforts are solidified into a tangible result, ready for use or distribution.
## Conclusion
Congratulations! You've successfully added both text and image watermarks to your PDF using GroupDocs.Watermark for .NET. This process is not only straightforward but also highly customizable to fit your specific needs. Whether you're protecting your documents or branding them, watermarks are a powerful tool at your disposal.
## FAQ's
### Can I add multiple watermarks to the same page?
Yes, you can add multiple watermarks to the same page by calling the `Add` method multiple times with different watermark objects.
### How can I customize the appearance of the text watermark?
You can customize the text watermark by adjusting properties such as font, size, color, and opacity using the `TextWatermark` object.
### Is it possible to watermark only specific pages of a PDF?
Yes, you can specify which pages to watermark by setting the `PageIndex` property in the `PdfArtifactWatermarkOptions`.
### Can I remove watermarks from a PDF?
Yes, GroupDocs.Watermark provides functionality to search for and remove watermarks from PDF documents.
### How do I get a temporary license for GroupDocs.Watermark?
You can get a temporary license by visiting the [temporary license page](https://purchase.groupdocs.com/temporary-license/).
