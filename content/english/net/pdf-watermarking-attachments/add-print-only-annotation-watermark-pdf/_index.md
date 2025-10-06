---
title: Add Print Only Annotation Watermark to PDF
linktitle: Add Print Only Annotation Watermark to PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to add print-only annotation watermarks to PDFs using GroupDocs.Watermark for .NET. Enhance document security and branding effortlessly.
weight: 13
url: /net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
type: docs
---
# Add Print Only Annotation Watermark to PDF

## Introduction
In this tutorial, we'll delve into the process of adding a print-only annotation watermark to a PDF using GroupDocs.Watermark for .NET. Watermarking documents is a crucial aspect of document security and branding, and GroupDocs.Watermark provides a seamless solution for .NET developers to achieve this.
## Prerequisites
Before we get started, ensure you have the following prerequisites:
- Basic understanding of C# programming language.
- Visual Studio installed on your machine.
- GroupDocs.Watermark for .NET library installed in your project.

## Import Namespaces
To begin, make sure you import the necessary namespaces:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the Document
Firstly, you need to load the PDF document that you want to watermark. Replace `"Your Document Path"` with the path to your PDF file and `"Your Document Directory"` with the directory where you want to save the output file.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Watermarking code will be added here
}
```
## Step 2: Add Watermark
Next, create a text watermark object with the desired text and font. Set `isPrintOnly` to `true` to ensure that the watermark is only visible when the document is printed, not in the view mode.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Step 3: Configure Watermark Options
Define options for the watermark, such as the page index where the watermark should be added and specifying it as a print-only annotation.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Step 4: Apply Watermark
Add the watermark to the document using the specified options and save the output file.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Conclusion
In this tutorial, we learned how to add a print-only annotation watermark to a PDF document using GroupDocs.Watermark for .NET. This enables developers to enhance document security and branding with ease.
## FAQ's
### Is GroupDocs.Watermark compatible with other document formats besides PDF?
Yes, GroupDocs.Watermark supports various document formats such as Word, Excel, PowerPoint, and images.
### Can I customize the appearance of the watermark?
Certainly, GroupDocs.Watermark provides extensive options to customize watermark text, font, color, size, and positioning.
### Does GroupDocs.Watermark offer batch processing capabilities?
Absolutely, developers can watermark multiple documents simultaneously using batch processing features.
### Is there a trial version available for GroupDocs.Watermark?
Yes, you can access a free trial version of GroupDocs.Watermark from the provided link.
### How can I get technical support for GroupDocs.Watermark?
You can seek technical assistance from the GroupDocs.Watermark forum available at the provided support link.
