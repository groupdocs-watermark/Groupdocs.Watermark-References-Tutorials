---
title: Remove Shapes with Specific Text Formatting in Word Docs
linktitle: Remove Shapes with Specific Text Formatting in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to remove shapes with specific text formatting in Word documents using GroupDocs.Watermark for .NET. Follow our guide for efficient manipulation of watermarks.
weight: 31
url: /net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
type: docs
---
# Remove Shapes with Specific Text Formatting in Word Docs

## Introduction
GroupDocs.Watermark for .NET is a powerful API that allows developers to manipulate watermarks in various document formats programmatically. In this tutorial, we will focus on removing shapes with specific text formatting in Word documents using GroupDocs.Watermark for .NET. Whether you're a seasoned developer or just starting out, this step-by-step guide will help you understand the process of removing shapes efficiently and effectively.
## Prerequisites
Before we dive into the tutorial, make sure you have the following prerequisites in place:
1. GroupDocs.Watermark for .NET: Ensure that you have the GroupDocs.Watermark for .NET library installed in your development environment. You can download it from the [website](https://releases.groupdocs.com/Watermark/net/).
2. Development Environment: Set up a suitable development environment with Visual Studio or any other .NET IDE installed.
3. Word Document: Prepare a Word document containing shapes with specific text formatting that you want to remove.

## Import Namespaces
Before we begin the implementation, let's import the necessary namespaces:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the Document
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Implementation goes here
}
```
## Step 2: Get Content and Iterate through Sections
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    // Implementation goes here
}
```
## Step 3: Iterate through Shapes and Remove Based on Text Formatting
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## Step 4: Save the Document
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusion
In this tutorial, we've learned how to remove shapes with specific text formatting in Word documents using GroupDocs.Watermark for .NET. By following the step-by-step guide and utilizing the provided code examples, developers can easily manipulate watermarks according to their requirements.
## FAQ's
### Is GroupDocs.Watermark for .NET compatible with other document formats besides Word?
Yes, GroupDocs.Watermark for .NET supports various document formats including Excel, PowerPoint, PDF, and more.
### Can I customize the criteria for removing shapes based on text formatting?
Absolutely! You can modify the code to target specific text attributes such as font size, style, color, etc.
### Does GroupDocs.Watermark for .NET provide support for adding watermarks as well?
Yes, besides removal, you can also add text or image watermarks to your documents using GroupDocs.Watermark for .NET.
### Is there a trial version available for testing before purchasing?
Yes, you can download a free trial version from the GroupDocs [website](https://releases.groupdocs.com/).
### How can I get technical support or assistance with GroupDocs.Watermark for .NET?
For technical assistance, you can visit the support forum at [GroupDocs.Watermark Forum](https://forum.groupdocs.com/c/watermark/19).
