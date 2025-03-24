---
title: Load Document from Stream
linktitle: Load Document from Stream
second_title: GroupDocs.Watermark .NET API
description: Learn how to add watermarks to documents using GroupDocs.Watermark for .NET with this guide. Perfect for developers looking to enhance document security.
weight: 11
url: /net/document-loadings/load-document-from-stream/
---
## Introduction
Are you looking to add watermarks to your documents seamlessly using .NET? Look no further! GroupDocs.Watermark for .NET is a powerful and easy-to-use library that allows you to manage watermarks in various document formats. Whether you're working with PDFs, Word documents, or images, this tool has got you covered. In this tutorial, we’ll walk you through the process of loading a document from a stream and adding a watermark step by step. So, let’s dive right in!
## Prerequisites
Before we start, make sure you have the following set up:
1. Visual Studio: Any recent version of Visual Studio will work fine.
2. .NET Framework: Ensure you have .NET Framework 4.0 or higher installed.
3. GroupDocs.Watermark for .NET: You can download it from [here](https://releases.groupdocs.com/Watermark/net/).
4. Basic Knowledge of C#: Familiarity with C# and object-oriented programming concepts will be helpful.

## Import Namespaces
To use GroupDocs.Watermark in your project, you’ll need to import the necessary namespaces. This will enable you to access the library's features without any issues.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Step 1: Setting Up Your Project
First things first, you need to set up your project in Visual Studio. Here’s how you do it:
1. Create a New Project: Open Visual Studio and create a new C# Console Application project.
2. Install GroupDocs.Watermark: Install the GroupDocs.Watermark library via NuGet Package Manager. Simply search for `GroupDocs.Watermark` and install it.
## Step 2: Define Document Paths
Next, you need to define the paths for your document and the output file where the watermarked document will be saved.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` with the actual path of the document you want to watermark and `"Your Document Directory"` with the directory where you want to save the watermarked document.
## Step 3: Load the Document from a Stream
Now, let's load the document from a stream. This involves opening the document as a stream and then using the `Watermarker` class from the GroupDocs.Watermark library to manage it.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Your code to manage watermarks will go here
}
```
This code snippet ensures that the document is opened as a stream and the `Watermarker` class is initialized with this stream. The `using` statements ensure that resources are properly disposed of after use.
## Step 4: Create and Add a Watermark
Creating a watermark is straightforward with GroupDocs.Watermark. In this example, we’ll create a simple text watermark.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
Here, we create a `TextWatermark` object with the text "Test watermark" and specify the font details. Then, we add this watermark to the document using the `Add` method of the `Watermarker` class.
## Step 5: Save the Watermarked Document
Finally, save the watermarked document to the specified output path.
```csharp
watermarker.Save(outputFileName);
```
This code saves the document with the newly added watermark to the `outputFileName` path you defined earlier.

## Conclusion
Congratulations! You’ve successfully added a watermark to your document using GroupDocs.Watermark for .NET. This library makes it incredibly easy to manage watermarks across a variety of document formats. Whether you need to add text, images, or other types of watermarks, GroupDocs.Watermark has the tools you need. Don’t forget to check out the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for more advanced features and customization options.
## FAQ's
### What types of watermarks can I add using GroupDocs.Watermark for .NET?
You can add text watermarks, image watermarks, and even complex shapes and logos. The library supports a wide range of customization options.
### Can I remove watermarks from documents using GroupDocs.Watermark?
Yes, GroupDocs.Watermark allows you to remove existing watermarks from documents as well.
### Is there a free trial available for GroupDocs.Watermark?
Yes, you can download a free trial from [here](https://releases.groupdocs.com/).
### How do I purchase a license for GroupDocs.Watermark?
You can purchase a license directly from the [GroupDocs website](https://purchase.groupdocs.com/buy).
### Where can I get support if I encounter issues?
For support, you can visit the [GroupDocs.Watermark support forum](https://forum.groupdocs.com/c/watermark/19).
