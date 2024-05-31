---
title: Remove Watermark from PDF
linktitle: Remove Watermark from PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to remove watermarks from PDF files using GroupDocs.Watermark for .NET. Easy steps for professional document editing.
type: docs
weight: 34
url: /net/pdf-watermarking-attachments/remove-watermark-pdf/
---
## Introduction
In today's digital age, protecting sensitive documents with watermarks is a common practice. However, there are instances where you may need to remove watermarks from PDF files for various reasons. Whether you're editing a document or simply need a clean version for presentation, GroupDocs.Watermark for .NET provides a seamless solution for removing watermarks from PDF files.
## Prerequisites
Before we dive into removing watermarks from PDF files using GroupDocs.Watermark for .NET, ensure you have the following prerequisites:
1. GroupDocs.Watermark for .NET Library: Download and install the library from [here](https://releases.groupdocs.com/Watermark/net/).
2. Development Environment: Have Visual Studio or any compatible IDE installed on your system.
3. Document with Watermark: Prepare a PDF document containing the watermark you wish to remove.

## Importing Namespaces
In your C# project, start by importing the necessary namespaces:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Step 1: Load the PDF Document
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
In this step, specify the path to your PDF document and the directory where you want to save the output file.
## Step 2: Initialize Watermarker and Search Criteria
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
Initialize the Watermarker object with the PDF document path and load options. Then, define search criteria for the watermark you want to remove. You can search for watermarks based on images or text.
## Step 3: Search and Remove Watermarks
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // Remove all found watermarks
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
Search for possible watermarks on the first page of the PDF document based on the defined search criteria. Then, iterate through the collection of possible watermarks and remove them one by one. Finally, save the modified PDF document without the watermark.

## Conclusion
Removing watermarks from PDF files is a crucial task in various scenarios, from document editing to presentation preparation. With GroupDocs.Watermark for .NET, you can effortlessly remove watermarks from PDF files using simple C# code, ensuring your documents are clean and professional.
## FAQ's
### Is GroupDocs.Watermark for .NET compatible with all versions of Visual Studio?
Yes, GroupDocs.Watermark for .NET is compatible with all versions of Visual Studio, including Visual Studio 2019 and Visual Studio 2022.
### Can I remove multiple watermarks from a single PDF document using GroupDocs.Watermark for .NET?
Yes, you can search for and remove multiple watermarks from a single PDF document by specifying appropriate search criteria.
### Does GroupDocs.Watermark for .NET support other document formats besides PDF?
Yes, GroupDocs.Watermark for .NET supports a wide range of document formats, including Word documents, Excel spreadsheets, PowerPoint presentations, and more.
### Is there a trial version available for GroupDocs.Watermark for .NET?
Yes, you can download a free trial version of GroupDocs.Watermark for .NET from [here](https://releases.groupdocs.com/).
### Where can I find additional support and assistance for GroupDocs.Watermark for .NET?
For additional support, you can visit the GroupDocs.Watermark forum [here](https://forum.groupdocs.com/c/watermark/19).
