---
title: Load Document from Local Disk
linktitle: Load Document from Local Disk
second_title: GroupDocs.Watermark .NET API
description: Protect and manage your documents with Groupdocs.Watermark for .NET. Follow our detailed guide to add watermarks seamlessly.
type: docs
weight: 10
url: /net/document-loadings/load-document-from-local-disk/
---
## Introduction
Watermarking documents is essential in today's digital age to ensure content protection, ownership assertion, and confidentiality. Groupdocs.Watermark for .NET is a powerful library that allows developers to add, search, and manage watermarks in various document formats. In this tutorial, we’ll walk through the process of using Groupdocs.Watermark for .NET to add watermarks to your documents with detailed step-by-step instructions.
## Prerequisites
Before diving into the implementation, ensure you have the following:
1. Visual Studio Installed: You’ll need Visual Studio or another compatible .NET IDE.
2. Groupdocs.Watermark for .NET: Download the library from the [download link](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Ensure you have .NET Framework 4.6.1 or higher installed.
4. A Sample Document: Prepare a sample document to test the watermarking process.
## Import Namespaces
To get started, you'll need to import the necessary namespaces in your project. These are essential for accessing the classes and methods required for watermarking.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load Document from Local Disk
First, you need to load the document from your local disk. This document will be the one to which you will add a watermark.
Define the path of the document you want to watermark.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Step 2: Initialize Load Options
Next, initialize the load options. For instance, if you're working with a Word document, you'll use `WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Step 3: Create and Configure Watermarker
Now, you’ll create an instance of the `Watermarker` class. This instance will be used to manage and apply watermarks to your document.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // This block will contain further steps to add and save the watermark
}
```
## Step 4: Create a Watermark
Create a text watermark. This watermark can contain any text you choose. Here, we will use "Test watermark".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Step 5: Add Watermark to the Document
Add the created watermark to the document using the `Add` method of the `Watermarker` class.
```csharp
watermarker.Add(watermark);
```
## Step 6: Save the Watermarked Document
Finally, save the watermarked document to the specified path.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
Adding watermarks to your documents using Groupdocs.Watermark for .NET is straightforward and efficient. This guide has walked you through the entire process from setting up your environment to saving a watermarked document. With this powerful tool, you can ensure your documents are protected and your intellectual property is secure. 
For further details, check the [documentation](https://reference.groupdocs.com/Watermark/net/), and if you encounter any issues, the [support forum](https://forum.groupdocs.com/c/watermark/19) is an excellent place for assistance. 
## FAQ's
### Can I use custom fonts for watermarks?
Yes, Groupdocs.Watermark supports custom fonts. You can specify any font installed on your system.
### What types of documents are supported?
Groupdocs.Watermark supports a wide range of document formats including Word, Excel, PDF, PowerPoint, and more.
### How can I remove a watermark from a document?
You can use the `Remove` method provided by the `Watermarker` class to remove watermarks.
### Is it possible to add image watermarks?
Yes, you can add image watermarks using the `ImageWatermark` class.
### Can I try Groupdocs.Watermark for free?
Absolutely, you can download a [free trial](https://releases.groupdocs.com/) to evaluate the library before purchasing.
