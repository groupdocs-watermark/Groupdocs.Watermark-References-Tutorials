---
title: Add Locked Watermark to Specific Pages in Word Docs
linktitle: Add Locked Watermark to Specific Pages in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to add a locked watermark to specific pages in Word documents using GroupDocs.Watermark for .NET with our easy step-by-step guide.
type: docs
weight: 12
url: /net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## Introduction
Are you looking to add a watermark to specific pages in your Word documents, but want it to be locked so that it cannot be easily removed or edited? You’re in the right place! In this tutorial, we will guide you through the process of adding a locked watermark to specific pages in Word documents using GroupDocs.Watermark for .NET. This powerful library makes it easy to apply, manage, and customize watermarks on a variety of document types. Whether you're a developer or just someone who needs to secure their documents, this guide will walk you through each step in a straightforward manner.
## Prerequisites
Before we dive into the tutorial, let's ensure you have everything you need:
1. GroupDocs.Watermark for .NET: You can [download](https://releases.groupdocs.com/Watermark/net/) the latest version.
2. Development Environment: An IDE like Visual Studio.
3. Basic Knowledge of C#: Familiarity with C# programming will be helpful.
4. Document to Watermark: A Word document (.docx or .doc) that you want to add a watermark to.
## Import Namespaces
First, you need to import the necessary namespaces in your C# project. These namespaces provide access to the classes and methods required to work with GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Now that we've got the prerequisites covered and the necessary namespaces imported, let's break down the process step by step.
## Step 1: Load the Word Document
To begin with, you need to load the Word document you want to add a watermark to. This can be done using the `Watermarker` class along with `WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Continue to the next steps
}
```
## Step 2: Create the Text Watermark
Next, create a text watermark. You can customize the text, font, color, and other properties according to your requirements.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Step 3: Configure Watermark Options
To apply the watermark to specific pages and lock it, configure the `WordProcessingWatermarkPagesOptions`. Here, you specify the page numbers where the watermark should appear and set the locking options.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Specify the pages
options.IsLocked = true; // Lock the watermark
options.LockType = WordProcessingLockType.AllowOnlyComments; // Set lock type
// To protect with a password
// options.Password = "7654321";
```
## Step 4: Add the Watermark to the Document
With your watermark and options configured, you can now add the watermark to the document.
```csharp
watermarker.Add(watermark, options);
```
## Step 5: Save the Document
Finally, save the document with the watermark applied. Choose an appropriate output path and save the file.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusion
Congratulations! You've successfully added a locked watermark to specific pages in a Word document using GroupDocs.Watermark for .NET. This tutorial covered all the essential steps from loading the document to saving the watermarked file. By following these steps, you can ensure that your documents are securely watermarked, protecting your content from unauthorized editing and use.
For more information, you can refer to the [GroupDocs.Watermark documentation](https://reference.groupdocs.com/Watermark/net/). If you have any questions or need further assistance, feel free to visit the [support forum](https://forum.groupdocs.com/c/watermark/19).
## FAQ's
### What is GroupDocs.Watermark for .NET?
GroupDocs.Watermark for .NET is a powerful library that allows developers to add watermarks to various types of documents, including Word, PDF, Excel, and more.
### Can I apply watermarks to multiple pages in a document?
Yes, you can specify multiple page numbers in the `PageNumbers` array to apply watermarks to multiple pages.
### How do I protect a watermark with a password?
You can protect a watermark with a password by setting the `Password` property in the `WordProcessingWatermarkPagesOptions`.
### Is it possible to customize the appearance of the watermark?
Absolutely! You can customize the text, font, color, size, and other properties of the watermark to suit your needs.
### Where can I get a temporary license for GroupDocs.Watermark?
You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
