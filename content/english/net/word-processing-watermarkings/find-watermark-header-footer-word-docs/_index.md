---
title: Find Watermark in Header/Footer in Word Docs
linktitle: Find Watermark in Header/Footer in Word Docs
second_title: GroupDocs.Watermark .NET API
description: Learn how to efficiently find and remove watermarks from Word documents using GroupDocs.Watermark for .NET, ensuring document integrity and professionalism.
weight: 22
url: /net/word-processing-watermarkings/find-watermark-header-footer-word-docs/
---
## Introduction
In the world of document management and protection, watermarking plays a pivotal role. Whether it's for branding purposes, copyright protection, or document tracking, adding watermarks to your documents is essential. However, finding and removing watermarks efficiently, especially in large document sets, can be a daunting task. This is where GroupDocs.Watermark for .NET comes into play. In this tutorial, we'll delve into how to find watermarks in headers and footers of Word documents using GroupDocs.Watermark for .NET, breaking down each step to ensure a comprehensive understanding.
## Prerequisites
Before diving into the tutorial, make sure you have the following prerequisites in place:
1. GroupDocs.Watermark for .NET: Ensure you have the GroupDocs.Watermark for .NET library installed and configured in your development environment. You can download the library from [here](https://releases.groupdocs.com/Watermark/net/).
2. Access to Word Documents: Have access to the Word documents containing watermarks that you want to manipulate.
3. Basic Knowledge of C#: Familiarize yourself with C# programming language basics, as this tutorial will involve C# code snippets.
## Import Namespaces
Before getting started with the code, import the necessary namespaces:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Step 1: Define Document Path and Output File Name
First, define the path of the document containing the watermark and the output file name where the modified document will be saved.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Step 2: Initialize Watermarker
Initialize the `Watermarker` object with the document path and load options.
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Code for watermark manipulation will go here
}
```
## Step 3: Define Search Criteria
Define the search criteria to find the watermark. This can be based on image or text.
```csharp
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
## Step 4: Search for Watermarks
Search for watermarks in the primary header of the document using the defined search criteria.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
PossibleWatermarkCollection possibleWatermarks = content.Sections[0]
                                                        .HeadersFooters[OfficeHeaderFooterType.HeaderPrimary]
                                                        .Search(textSearchCriteria.Or(imageSearchCriteria));
```
## Step 5: Remove Watermarks
Remove all found watermarks from the document.
```csharp
for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
{
    possibleWatermarks.RemoveAt(i);
}
```
## Step 6: Save Document
Save the modified document with removed watermarks.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
GroupDocs.Watermark for .NET provides a robust solution for finding and removing watermarks from Word documents. By following the steps outlined in this tutorial, you can efficiently locate and eliminate watermarks from headers and footers, ensuring the integrity and professionalism of your documents.
## FAQ's
### Is GroupDocs.Watermark compatible with other document formats?
Yes, GroupDocs.Watermark supports a wide range of document formats, including Word, Excel, PowerPoint, PDF, and more.
### Can I customize the search criteria for watermarks?
Absolutely, GroupDocs.Watermark offers flexible search criteria, allowing you to search for watermarks based on various parameters such as text, image, shape, or object properties.
### Does GroupDocs.Watermark preserve the original formatting of documents?
Yes, GroupDocs.Watermark ensures that the original formatting of documents remains intact while removing watermarks, preserving the document's aesthetics and layout.
### Is GroupDocs.Watermark suitable for batch processing of documents?
Certainly, GroupDocs.Watermark provides APIs for batch processing, enabling you to handle multiple documents simultaneously with ease.
### Where can I seek assistance or support for GroupDocs.Watermark?
For any queries or assistance regarding GroupDocs.Watermark, you can visit the [GroupDocs.Watermark forum](https://forum.groupdocs.com/c/watermark/19) or reach out to the support team.
