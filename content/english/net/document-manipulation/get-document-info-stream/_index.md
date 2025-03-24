---
title: Get Document Info from Stream
linktitle: Get Document Info from Stream
second_title: GroupDocs.Watermark .NET API
description: Learn how to get document info from a stream using GroupDocs.Watermark for .NET with this step-by-step guide. Your document management capabilities effortlessly.
weight: 12
url: /net/document-manipulation/get-document-info-stream/
---

# Get Document Info from Stream

## Introduction
In today's digital age, protecting and managing document integrity is crucial. Whether you are a business professional, a developer, or someone handling sensitive information, the need to add, extract, or manipulate watermarks in your documents is essential. GroupDocs.Watermark for .NET provides a powerful toolkit to help you achieve just that. This article will guide you through using GroupDocs.Watermark for .NET to get document information from a stream, offering a step-by-step tutorial to ease you into the process. By the end, you'll be proficient in using this feature to enhance your document management capabilities.
## Prerequisites
Before diving into the tutorial, ensure you have the following prerequisites in place:
- A development environment set up with .NET.
- Basic knowledge of C# programming.
- GroupDocs.Watermark for .NET library installed.
- A valid license for GroupDocs.Watermark (or a temporary license for trial purposes).
If you haven't installed the library yet, you can download it from [here](https://releases.groupdocs.com/Watermark/net/). For licensing options, you can purchase a license [here](https://purchase.groupdocs.com/buy) or apply for a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
## Import Namespaces
To get started, you need to import the necessary namespaces. This will enable you to access the classes and methods required for watermark management.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
```
Let's break down the process of retrieving document information from a stream using GroupDocs.Watermark for .NET into simple steps. Each step will be detailed to ensure you understand and can apply the concepts effectively.
## Step 1: Initialize the Watermarker
First, you need to initialize the `Watermarker` class with your document stream. This step is crucial as it sets up the environment for you to work with the document.
```csharp
using (Watermarker watermarker = new Watermarker(stream))
{
    // Next steps will go here
}
```
## Step 2: Retrieve Document Information
Once the `Watermarker` is initialized, the next step is to retrieve the document information. The `GetDocumentInfo` method is used here to fetch details such as file type, page count, and document size.
```csharp
IDocumentInfo info = watermarker.GetDocumentInfo();
```
## Step 3: Display Document Information
After retrieving the document information, you can display it. This step involves accessing the properties of the `IDocumentInfo` object and printing them to the console.
```csharp
Console.WriteLine("File type: {0}", info.FileType);
Console.WriteLine("Number of pages: {0}", info.PageCount);
Console.WriteLine("Document size: {0} bytes", info.Size);
```

## Conclusion
Retrieving document information from a stream using GroupDocs.Watermark for .NET is a straightforward process when broken down into manageable steps. By following this guide, you can efficiently integrate this functionality into your applications, ensuring better document management and integrity. Don't hesitate to explore the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for more advanced features and options.
## FAQ's
### What file formats does GroupDocs.Watermark support?
GroupDocs.Watermark supports a wide range of file formats including PDF, Word, Excel, PowerPoint, and more. You can find the full list in the [documentation](https://tutorials.groupdocs.com/Watermark/net/).
### Can I try GroupDocs.Watermark before purchasing?
Yes, you can download a free trial from [here](https://releases.groupdocs.com/) and apply for a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### How do I install GroupDocs.Watermark for .NET?
You can install it via NuGet Package Manager in Visual Studio or download it from the [download link](https://releases.groupdocs.com/Watermark/net/).
### What is the purpose of watermarks in documents?
Watermarks are used to protect document integrity, indicate the document's status (e.g., confidential, draft), or add branding and ownership information.
### Where can I get support for GroupDocs.Watermark?
You can get support from the GroupDocs community and technical team on the [support forum](https://forum.groupdocs.com/c/watermark/19).
