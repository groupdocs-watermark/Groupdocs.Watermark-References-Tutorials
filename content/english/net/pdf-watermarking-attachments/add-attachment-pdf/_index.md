---
title: Add Attachment to PDF
linktitle: Add Attachment to PDF
second_title: GroupDocs.Watermark .NET API
description: Enhance your .NET document management capabilities with GroupDocs.Watermark for seamless watermarking and attachment handling.
weight: 12
url: /net/pdf-watermarking-attachments/add-attachment-pdf/
type: docs
---
# Add Attachment to PDF

## Introduction
In the realm of .NET development, GroupDocs.Watermark stands out as a powerful tool for managing watermarks, annotations, and more within various document formats. Whether you're working with PDFs, Word documents, or images, GroupDocs.Watermark for .NET provides a seamless integration that empowers developers to manipulate documents with ease.
## Prerequisites
Before diving into the intricacies of using GroupDocs.Watermark for .NET, ensure that you have the following prerequisites in place:
1. Installation: Make sure you have installed GroupDocs.Watermark for .NET. You can download it from the [release page](https://releases.groupdocs.com/Watermark/net/).
2. Document Preparation: Have a document ready on which you want to perform watermarking or other operations.
3. Basic Knowledge of C#: Familiarize yourself with C# programming language basics as we'll be using it to interact with GroupDocs.Watermark API.

## Import Namespaces
Before starting with the implementation, it's crucial to import the necessary namespaces to access the functionality of GroupDocs.Watermark. Below are the required namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Step 1: Load Document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
In this step, we specify the path to the document we want to work with and create a `PdfLoadOptions` object for loading PDF documents. Then, we initialize a `Watermarker` object with the document path and load options.
## Step 2: Get PDF Content
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
Here, we obtain the content of the PDF document using the `GetContent<PdfContent>()` method.
## Step 3: Add Attachment
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
This step involves adding an attachment to the PDF document. You need to provide the attachment file bytes, name, and description.
## Step 4: Save Changes
```csharp
watermarker.Save(outputFileName);
```
Finally, we save the changes made to the document with the added attachment.

## Conclusion
GroupDocs.Watermark for .NET offers a robust solution for managing document watermarks and attachments seamlessly. By following the steps outlined above, you can easily integrate watermarking and attachment functionalities into your .NET applications.
## FAQ's
### Is GroupDocs.Watermark compatible with all .NET frameworks?
Yes, GroupDocs.Watermark supports .NET Framework 2.0 and higher.
### Can I remove watermarks added using GroupDocs.Watermark?
Yes, GroupDocs.Watermark provides methods to remove watermarks from documents.
### Does GroupDocs.Watermark support document encryption?
Yes, GroupDocs.Watermark allows you to work with encrypted documents.
### Can I customize the appearance of watermarks?
Absolutely, GroupDocs.Watermark offers various customization options for watermarks.
### Is there a trial version available for testing purposes?
Yes, you can access the trial version from the [releases page](https://releases.groupdocs.com/).
