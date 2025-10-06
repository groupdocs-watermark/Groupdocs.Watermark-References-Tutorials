---
title: Add Locked Watermark to All Pages in Word Docs
linktitle: Add Locked Watermark to All Pages in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Secure your documents by adding locked watermarks using Groupdocs.Watermark for .NET. Follow our step-by-step guide for easy implementation.
weight: 11
url: /net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Add Locked Watermark to All Pages in Word Docs

## Introduction
Adding watermarks to your documents is a vital step in securing and branding your content. Whether you're preventing unauthorized use or simply adding a professional touch, watermarks can serve multiple purposes. In this tutorial, we'll walk you through the process of adding a locked watermark to all pages of a Word document using Groupdocs.Watermark for .NET.
## Prerequisites
Before we dive into the step-by-step guide, let's ensure you have everything you need:
1. Groupdocs.Watermark for .NET: Download the latest version from [here](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Ensure you have .NET Framework installed on your machine.
3. Development Environment: A development environment like Visual Studio.
4. License: You can opt for a [free trial](https://releases.groupdocs.com/) or purchase a [temporary license](https://purchase.groupdocs.com/temporary-license/).
## Import Namespaces
First things first, you need to import the necessary namespaces in your project. These are essential for accessing the classes and methods provided by Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Set Up Your Project

Open your development environment and create a new .NET project. This can be a console application or any other type that suits your needs.

You need to add the Groupdocs.Watermark package to your project. This can be done via NuGet Package Manager. Run the following command in the NuGet Package Manager Console:
```sh
Install-Package GroupDocs.Watermark
```
## Step 2: Load the Word Document
### Define the Document Path
Specify the path to your Word document. This will be the document where you want to add the watermark.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Set Load Options
Create an instance of `WordProcessingLoadOptions` to load your Word document with specific options.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Step 3: Create the Watermark
### Initialize Watermarker
Using the `Watermarker` class, load the document with the specified load options.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Further steps will be inside this using block
}
```
### Define Watermark Properties
Create a `TextWatermark` instance with your desired text, font, and color.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Step 4: Apply Watermark to All Pages
### Set Watermark Options
Define `WordProcessingWatermarkPagesOptions` and set the `IsLocked` property to true to lock the watermark. This ensures the watermark cannot be removed easily.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Optional: Add Password Protection
If you want to add an extra layer of security, you can set a password for the watermark.
```csharp
// To protect with password
// options.Password = "7654321";
```
### Add the Watermark
Use the `Add` method of the `Watermarker` class to add the watermark to the document with the specified options.
```csharp
watermarker.Add(watermark, options);
```
## Step 5: Save the Document
Finally, save the modified document to the specified output file.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
By following these steps, you can easily add a locked watermark to all pages of your Word documents using Groupdocs.Watermark for .NET. This not only helps in protecting your documents from unauthorized use but also adds a professional touch to your content. Groupdocs.Watermark offers a comprehensive solution for watermarking needs, ensuring your documents remain secure and branded.
## FAQ's
### Can I use an image as a watermark instead of text?
Yes, Groupdocs.Watermark supports both text and image watermarks. You can replace `TextWatermark` with `ImageWatermark` and specify your image.
### Is it possible to customize the position of the watermark?
Absolutely! You can set the position of the watermark using properties like `HorizontalAlignment` and `VerticalAlignment`.
### Can I apply different watermarks to different pages of the document?
Yes, you can customize watermarks for specific pages using the `PageIndex` property in the `WordProcessingWatermarkPagesOptions`.
### Does Groupdocs.Watermark support other document formats besides Word?
Yes, Groupdocs.Watermark supports various formats including PDF, Excel, PowerPoint, and more.
### What are the system requirements for using Groupdocs.Watermark?
You need a system with .NET Framework installed and a development environment like Visual Studio.
