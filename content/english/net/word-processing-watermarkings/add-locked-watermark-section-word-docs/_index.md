---
title: Add Locked Watermark to Section in Word Docs
linktitle: Add Locked Watermark to Section in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to add a locked watermark to a specific section in Word documents using Groupdocs.Watermark for .NET with this comprehensive step-by-step guide.
weight: 13
url: /net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---
## Introduction
Are you looking for an efficient way to add a locked watermark to a section in your Word documents? Look no further! With Groupdocs.Watermark for .NET, you can seamlessly insert watermarks into Word documents while ensuring they remain locked and tamper-proof. This powerful tool offers a variety of features to cater to your watermarking needs, whether for branding, confidentiality, or security purposes. In this step-by-step tutorial, we'll walk you through how to add a locked watermark to a specific section of a Word document using Groupdocs.Watermark for .NET. Let’s dive in!
## Prerequisites
Before we get started, ensure you have the following prerequisites in place:
1. Groupdocs.Watermark for .NET: Ensure you have the Groupdocs.Watermark library installed. You can download it [here](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Make sure you have the .NET framework set up in your development environment.
3. IDE: Use an Integrated Development Environment (IDE) like Visual Studio.
4. Document: A Word document (.docx) to apply the watermark.
## Import Namespaces
To begin, you'll need to import the necessary namespaces in your project. Here's how to do it:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load Your Document
First, you need to load the document to which you want to add the watermark. This step involves specifying the path of your document and loading it using the `Watermarker` class.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Your watermarking code will go here.
}
```
## Step 2: Create the Watermark
Next, create the watermark you want to add to your document. In this example, we'll create a text watermark with specific font settings and color.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Step 3: Configure Watermark Options
Now, configure the watermark options to specify the section index and lock settings. This ensures the watermark is added to the correct section and is locked.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // Add to the first section
options.IsLocked = true; // Lock the watermark
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Lock type
```
## Step 4: Add the Watermark to the Document
With your watermark and options configured, it's time to add the watermark to the document using the `Add` method of the `Watermarker` class.
```csharp
watermarker.Add(watermark, options);
```
## Step 5: Save the Modified Document
Finally, save the document with the added watermark to your desired output location.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
Adding a locked watermark to a specific section in a Word document using Groupdocs.Watermark for .NET is a straightforward process. By following these steps, you can enhance the security and integrity of your documents, ensuring that important information is protected. Whether you're safeguarding sensitive data or adding a professional touch to your documents, Groupdocs.Watermark for .NET provides the tools you need to achieve your goals effectively.
## FAQ's
### What is Groupdocs.Watermark for .NET?
Groupdocs.Watermark for .NET is a powerful library that allows developers to add watermarks to various document types, including Word, PDF, and images, with advanced customization and security features.
### Can I lock a watermark with a password?
Yes, you can protect the watermark with a password by setting the `options.Password` property in the `WordProcessingWatermarkSectionOptions` class.
### Is it possible to apply different watermarks to different sections of a document?
Absolutely! By setting different `SectionIndex` values in the `WordProcessingWatermarkSectionOptions`, you can apply unique watermarks to different sections of the document.
### What types of watermarks can I add using Groupdocs.Watermark?
Groupdocs.Watermark supports various types of watermarks, including text, image, and shape watermarks, offering extensive customization options for each type.
### Where can I find more information about Groupdocs.Watermark for .NET?
For more information, you can visit the [documentation](https://tutorials.groupdocs.com/Watermark/net/) and [support forum](https://forum.groupdocs.com/c/watermark/19).
