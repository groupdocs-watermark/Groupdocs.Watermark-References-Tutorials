---
title: Add Watermark to All Attachments in PDF
linktitle: Add Watermark to All Attachments in PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to add watermarks to PDF attachments using GroupDocs.Watermark for .NET. Secure your documents with custom watermarks easily.
type: docs
weight: 16
url: /net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Introduction
Adding watermarks to PDF attachments can be a crucial step in document management, especially when ensuring security or branding. GroupDocs.Watermark for .NET offers a comprehensive solution for seamlessly embedding watermarks into PDF files. In this tutorial, we'll guide you through the process of adding a watermark to all attachments within a PDF document using GroupDocs.Watermark for .NET.
## Prerequisites
Before we begin, ensure you have the following:
1. GroupDocs.Watermark for .NET: If you haven't already, download and install GroupDocs.Watermark for .NET from the [website](https://releases.groupdocs.com/Watermark/net/).
2. Development Environment: Set up a suitable development environment with Visual Studio or any other .NET-compatible IDE.
3. PDF Document: Prepare the PDF document to which you want to add watermarks, along with the attachments you wish to watermark.

## Importing Namespaces
Before diving into the code, make sure to import the necessary namespaces to access GroupDocs.Watermark for .NET functionalities:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Define Document Path and Output Directory
First, define the path to your input PDF document and the directory where the watermarked document will be saved:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Step 2: Initialize Load Options and Watermark
Next, initialize the load options for the PDF document and create a text watermark:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Step 3: Load Document and Attachments
Load the PDF document and iterate through its attachments:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Step 4: Check Attachment Support
Check if the attached file is supported by GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Step 5: Add Watermark to Attachments
Load the attached document and add the watermark:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Step 6: Save Changes
Finally, save the changes to the watermarked PDF document:
```csharp
    watermarker.Save(outputFileName);
}
```

## Conclusion
In this tutorial, we've explored how to add watermarks to all attachments within a PDF document using GroupDocs.Watermark for .NET. By following the step-by-step guide, you can seamlessly integrate watermarks into your PDF files, ensuring document security and branding.
## FAQ's
### Can I customize the appearance of the watermark?
Yes, you can customize various aspects such as text, font, size, color, and position of the watermark according to your requirements.
### Does GroupDocs.Watermark support other document formats besides PDF?
Yes, GroupDocs.Watermark supports a wide range of document formats including Microsoft Word, Excel, PowerPoint, Visio, Outlook, and Images.
### Is there a trial version available for GroupDocs.Watermark?
Yes, you can explore the features of GroupDocs.Watermark by downloading the free trial version from the website.
### Can I add multiple watermarks to a single document?
Absolutely, GroupDocs.Watermark allows you to add multiple watermarks including text, image, and annotation simultaneously to enhance document security and branding.
### Is technical support available for GroupDocs.Watermark users?
Yes, GroupDocs provides comprehensive technical support through forums and dedicated support channels to assist users with any queries or issues they may encounter.
