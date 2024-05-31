---
title: Add Watermark to Annotation Images in PDF
linktitle: Add Watermark to Annotation Images in PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to protect your PDF documents by adding watermarks to annotation images using Groupdocs.Watermark for .NET.
type: docs
weight: 17
url: /net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---
## Introduction
In this tutorial, we'll explore how to add watermarks to annotation images in PDF documents using Groupdocs.Watermark for .NET. Watermarking is crucial for protecting your documents from unauthorized use or distribution. By following this step-by-step guide, you'll learn how to apply text watermarks to annotation images in PDFs effectively.
## Prerequisites
Before proceeding, ensure you have the following:
1. Basic understanding of C# programming language.
2. Installed Groupdocs.Watermark for .NET library.
3. Access to a development environment such as Visual Studio.
4. A PDF document with annotation images to watermark.

## Importing Namespaces
First, you need to import the necessary namespaces to your C# code:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## Step 2: Get PDF Content and Initialize Watermark
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Initialize image or text watermark
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Step 3: Iterate Through PDF Pages and Annotation Images
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Add watermark to the image
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Step 4: Save the Document with Watermark
```csharp
    watermarker.Save(outputFileName);
}
```
After executing these steps, your PDF document will have the specified watermark added to annotation images.

## Conclusion
Adding watermarks to annotation images in PDFs is essential for protecting your documents' integrity and ensuring they are not misused. With Groupdocs.Watermark for .NET, this process becomes simple and efficient, allowing you to safeguard your PDF files effectively.
## FAQ's
### Can I add multiple watermarks to the same PDF document?
Yes, you can add multiple watermarks to the same PDF document using Groupdocs.Watermark for .NET.
### Does Groupdocs.Watermark support other document formats besides PDF?
Yes, Groupdocs.Watermark supports various document formats, including Word, Excel, PowerPoint, and more.
### Is it possible to customize the appearance of the watermark?
Absolutely, you can customize the text, font, color, size, and position of the watermark according to your preferences.
### Can I remove watermarks from PDF documents using Groupdocs.Watermark?
Yes, Groupdocs.Watermark provides functionality to remove watermarks from PDF documents effortlessly.
### Is there any free trial available for Groupdocs.Watermark for .NET?
Yes, you can avail of a free trial of Groupdocs.Watermark for .NET from the website.
