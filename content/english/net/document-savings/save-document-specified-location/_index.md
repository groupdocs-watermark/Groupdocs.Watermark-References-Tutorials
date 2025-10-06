---
title: Save Document to Specified Location
linktitle: Save Document to Specified Location
second_title: GroupDocs.Watermark .NET API
description: Learn how to easily add watermarks to your documents using GroupDocs.Watermark for .NET with this step-by-step guide. Enhance document security.
weight: 11
url: /net/document-savings/save-document-specified-location/
type: docs
---
# Save Document to Specified Location

## Introduction
In the digital age, securing documents has become more crucial than ever. Watermarking is an effective way to protect your documents from unauthorized use. GroupDocs.Watermark for .NET offers a robust solution for adding watermarks to your documents. Whether you're a developer looking to integrate watermarking into your application or someone interested in safeguarding your documents, this tutorial will guide you through the process step-by-step.
## Prerequisites
Before diving into the tutorial, make sure you have the following prerequisites in place:
- .NET Development Environment: Ensure you have Visual Studio or any other .NET development environment installed.
- GroupDocs.Watermark for .NET Library: Download and tutorials the library in your project. [Download GroupDocs.Watermark for .NET](https://releases.groupdocs.com/Watermark/net/)
- Basic Knowledge of C# Programming: Understanding basic C# programming concepts will be helpful.
- Document to Watermark: Have a sample document ready that you want to apply the watermark to.
## Import Namespaces
Before we start with the example, you need to import the necessary namespaces. Add the following using statements at the top of your code file:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Let's break down the process of adding a watermark to a document using GroupDocs.Watermark for .NET into manageable steps. Follow these steps to successfully apply a watermark and save your document to a specified location.
## Step 1: Set Up Your Project
Start by creating a new .NET project in Visual Studio. You can choose a Console App for simplicity.
1. Open Visual Studio.
2. Select `File` > `New` > `Project`.
3. Choose `Console App (.NET Core)` or `Console App (.NET Framework)`.
4. Name your project and click `Create`.

## Step 2: Prepare Your Document and Watermark Text
### Specify Document Path
Define the path of the document you want to watermark. For this example, let's use a placeholder path.
```csharp
string documentPath = "Your Document Path";
```
### Define Output Path
Set up the output path where you want the watermarked document to be saved.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Step 3: Load the Document
Use the `Watermarker` class to load your document. This class provides methods to add, remove, and edit watermarks.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Add watermarking logic here
}
```
## Step 4: Create and Add a Watermark

### Create Text Watermark
Instantiate a `TextWatermark` object with your desired text and font properties.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Add Watermark to Document
Add the created watermark to your document using the `Add` method of the `Watermarker` class.
```csharp
watermarker.Add(watermark);
```
## Step 5: Save the Document
Finally, save the document with the watermark to the specified location.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
Watermarking your documents using GroupDocs.Watermark for .NET is a straightforward process that can significantly enhance your document security. By following this step-by-step guide, you can easily add watermarks to your documents and save them to your desired location. Whether you are protecting intellectual property, ensuring document authenticity, or simply adding a professional touch, GroupDocs.Watermark for .NET provides the tools you need.
## FAQ's
### Can I use images as watermarks with GroupDocs.Watermark for .NET?
Yes, you can use both text and image watermarks with GroupDocs.Watermark for .NET. The library supports various types of watermarks to suit your needs.
### Is there a free trial available for GroupDocs.Watermark for .NET?
Yes, you can download a free trial from the [website](https://releases.groupdocs.com/).
### How can I purchase a license for GroupDocs.Watermark for .NET?
You can purchase a license from the [purchase page](https://purchase.groupdocs.com/buy).
### Does GroupDocs.Watermark for .NET support batch watermarking?
Yes, you can watermark multiple documents in a batch process by iterating through a list of documents and applying watermarks.
### Where can I get support for GroupDocs.Watermark for .NET?
Support is available on the [GroupDocs forum](https://forum.groupdocs.com/c/watermark/19).
