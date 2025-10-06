---
title: Replace Text for Specific Shape in Word Docs
linktitle: Replace Text for Specific Shape in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to replace text for specific shapes in Word documents using GroupDocs.Watermark for .NET. Follow our step-by-step tutorial.
weight: 35
url: /net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
type: docs
---
# Replace Text for Specific Shape in Word Docs

## Introduction
In this tutorial, we will explore how to use GroupDocs.Watermark for .NET to replace text for a specific shape in Word documents. GroupDocs.Watermark for .NET is a powerful library that provides a wide range of features for working with watermarks in various document formats, including Word documents.
## Prerequisites
Before we begin, ensure that you have the following prerequisites in place:
1. GroupDocs.Watermark for .NET: Make sure you have downloaded and installed GroupDocs.Watermark for .NET. You can download it from [here](https://releases.groupdocs.com/Watermark/net/).
2. Document: Prepare the Word document in which you want to replace the text for a specific shape.
3. Development Environment: Set up your development environment with the necessary tools and dependencies.

## Import Namespaces
First, let's import the required namespaces for working with GroupDocs.Watermark for .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Step 1: Load the Document
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Your code goes here
}
```
In this step, we specify the path to the Word document and create an instance of `WordProcessingLoadOptions` to load the document.
## Step 2: Get Document Content
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
Here, we retrieve the content of the Word document using the `GetContent<T>()` method of the `Watermarker` class, specifying the type as `WordProcessingContent`.
## Step 3: Replace Text for Specific Shape
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
In this step, we iterate through each shape in the document. If the shape contains the specified text ("Some text" in this example), we replace it with the desired text ("Another text").
## Step 4: Save the Document
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
Finally, we save the modified document to the specified directory.

## Conclusion
GroupDocs.Watermark for .NET offers a convenient and efficient way to manipulate watermarks in Word documents. By following the steps outlined in this tutorial, you can easily replace text for specific shapes, providing flexibility and customization options for your document processing needs.
## FAQ's
### Can I replace text for shapes in other document formats besides Word?
GroupDocs.Watermark for .NET supports various document formats, including PDF, Excel, PowerPoint, and more. You can replace text for shapes in different formats using similar methods.
### Is there a trial version available for GroupDocs.Watermark for .NET?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Watermark for .NET?
You can get technical support by visiting the GroupDocs forum [here](https://forum.groupdocs.com/c/watermark/19).
### Do I need a temporary license to use GroupDocs.Watermark for .NET?
If you require additional features or extended usage, you can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I purchase a full license for GroupDocs.Watermark for .NET?
You can purchase a full license from the GroupDocs website [here](https://purchase.groupdocs.com/buy).
