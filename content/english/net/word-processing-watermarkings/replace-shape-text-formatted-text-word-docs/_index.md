---
title: Replace Shape Text with Formatted Text in Word Docs
linktitle: Replace Shape Text with Formatted Text in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to replace shape text with formatted text in Word documents using GroupDocs.Watermark for .NET. Your document editing capabilities effortlessly.
type: docs
weight: 34
url: /net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Introduction
In this tutorial, we'll guide you through the process of replacing shape text with formatted text in Word documents using GroupDocs.Watermark for .NET. This library provides powerful features for working with watermarks, including replacing text within shapes.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs.Watermark for .NET: Make sure you have installed and set up GroupDocs.Watermark for .NET. You can download it from [here](https://releases.groupdocs.com/Watermark/net/).
2. Document Path: You should have the path to the Word document where you want to replace the text.

## Import Namespaces
Before writing the code, import the necessary namespaces:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the Document
Load the Word document using the `Watermarker` class:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Your code continues here...
}
```
## Step 2: Get Content and Replace Text
Once the document is loaded, get the content and replace the text within shapes:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Step 3: Save the Document
After replacing the text, save the modified document:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusion
Replacing shape text with formatted text in Word documents is made easy with GroupDocs.Watermark for .NET. By following the steps outlined in this tutorial, you can efficiently manage and manipulate text within your documents.

## FAQ's
### Can I replace text in other types of documents using GroupDocs.Watermark for .NET?
Yes, GroupDocs.Watermark supports various document formats such as PDF, Excel, PowerPoint, and more.
### Is GroupDocs.Watermark compatible with .NET Core?
Yes, GroupDocs.Watermark supports both .NET Framework and .NET Core.
### Does GroupDocs.Watermark provide support for adding images as watermarks?
Absolutely, GroupDocs.Watermark allows you to add both text and image watermarks to your documents.
### Can I customize the appearance of the watermarks added using GroupDocs.Watermark?
Yes, you have full control over the appearance, position, and other properties of the watermarks.
### Is there a trial version available for GroupDocs.Watermark for .NET?
Yes, you can download a free trial from [here](https://releases.groupdocs.com/).
