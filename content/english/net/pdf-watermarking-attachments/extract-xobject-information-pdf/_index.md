---
title: Extract XObject Information from PDF
linktitle: Extract XObject Information from PDF
second_title: GroupDocs.Watermark .NET API
description: Unlock the power of document watermarking with GroupDocs.Watermark for .NET. Seamlessly manage watermarks in PDFs, Word documents, and images.
type: docs
weight: 25
url: /net/pdf-watermarking-attachments/extract-xobject-information-pdf/
---
## Introduction
GroupDocs.Watermark for .NET is a powerful document watermarking API designed to manipulate watermarks in various document formats such as PDF, Word, Excel, PowerPoint, and images. It provides developers with a straightforward approach to add, remove, search, and replace watermarks in documents programmatically. Whether you need to add a company logo, copyright notice, or confidential stamp to your documents, GroupDocs.Watermark simplifies the process with its intuitive API.
## Prerequisites
Before diving into GroupDocs.Watermark for .NET, ensure you have the following prerequisites in place:
1. Installation: Download and install GroupDocs.Watermark for .NET from the [download page](https://releases.groupdocs.com/Watermark/net/).
2. Development Environment: Have Visual Studio or any other .NET IDE installed on your system.
3. .NET Framework: Make sure you have the required .NET Framework installed on your development machine.

## Importing Namespaces
To start using GroupDocs.Watermark for .NET in your project, you need to import the necessary namespaces.
In your .NET project, add a reference to GroupDocs.Watermark.dll.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Step 1: Load the Document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
## Step 2: Access PDF Content
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Step 3: Iterate Through Pages
```csharp
foreach (PdfPage page in pdfContent.Pages)
```
## Step 4: Access XObjects
```csharp
foreach (PdfXObject xObject in page.XObjects)
```
## Step 5: Extract Information
```csharp
if (xObject.Image != null)
{
    Console.WriteLine(xObject.Image.Width);
    Console.WriteLine(xObject.Image.Height);
    Console.WriteLine(xObject.Image.GetBytes().Length);
}
Console.WriteLine(xObject.Text);
Console.WriteLine(xObject.X);
Console.WriteLine(xObject.Y);
Console.WriteLine(xObject.Width);
Console.WriteLine(xObject.Height);
Console.WriteLine(xObject.RotateAngle);
```

## Conclusion
GroupDocs.Watermark for .NET empowers developers to manage document watermarks seamlessly in their .NET applications. With its intuitive API and robust features, it's the go-to solution for any watermarking needs. By following the steps outlined in this guide, you can harness the full potential of GroupDocs.Watermark and enhance your document management workflows.
## FAQ's
### Is GroupDocs.Watermark compatible with all .NET frameworks?
Yes, GroupDocs.Watermark supports a wide range of .NET frameworks, including .NET Core and .NET Framework.
### Can I apply multiple watermarks to a single document using GroupDocs.Watermark?
Absolutely! GroupDocs.Watermark allows you to add multiple watermarks of different types to a single document.
### Does GroupDocs.Watermark provide support for document encryption?
Yes, GroupDocs.Watermark offers encryption capabilities to secure your documents against unauthorized access.
### Is there a trial version available for GroupDocs.Watermark?
Yes, you can access the free trial version of GroupDocs.Watermark from the [download page](https://releases.groupdocs.com/).
### Where can I find additional support and resources for GroupDocs.Watermark?
You can explore the GroupDocs.Watermark documentation, join the community forum, or reach out to the support team for assistance.
