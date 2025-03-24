---
title: Get PDF Dimensions
linktitle: Get PDF Dimensions
second_title: GroupDocs.Watermark .NET API
description: Protect your documents with ease using Groupdocs.Watermark for .NET. Add watermarks, stamps, and annotations effortlessly.
weight: 26
url: /net/pdf-watermarking-attachments/get-pdf-dimensions/
---

# Get PDF Dimensions

## Introduction
In today's digital age, safeguarding your documents is paramount. Whether you're a business professional, a legal expert, or a creative artist, protecting your intellectual property is essential. Groupdocs.Watermark for .NET offers a robust solution to add watermarks, stamps, and annotations to your documents, ensuring their security and authenticity.
## Prerequisites
Before diving into the world of Groupdocs.Watermark for .NET, ensure you have the following prerequisites in place:
1. Installation of Groupdocs.Watermark for .NET: Download and install Groupdocs.Watermark for .NET from the [download link](https://releases.groupdocs.com/Watermark/net/).
2. License Key (Optional): While Groupdocs.Watermark for .NET offers a free trial, you may opt for a temporary license or purchase a full license from [here](https://purchase.groupdocs.com/buy) for extended functionality.
3. Familiarity with C#: Basic knowledge of C# programming language is recommended to understand and implement the examples provided.
4. Document to Protect: Have a sample document (e.g., PDF, Word, Excel) ready on your local machine to experiment with.

## Import Namespaces
To begin working with Groupdocs.Watermark for .NET, you need to import the necessary namespaces into your C# project.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Step 1: Declare Variables
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Step 2: Load Document
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Step 3: Get PDF Content
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Step 4: Retrieve Dimensions
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Conclusion
In conclusion, Groupdocs.Watermark for .NET offers a comprehensive solution to protect your documents from unauthorized use and distribution. By following the steps outlined above and leveraging the power of Groupdocs.Watermark for .NET, you can ensure the security and integrity of your valuable digital assets.
## FAQ's
### Can I use Groupdocs.Watermark for .NET for free?
Yes, Groupdocs.Watermark for .NET offers a free trial version for evaluation purposes. However, for extended functionality, you may consider purchasing a full license.
### Does Groupdocs.Watermark support multiple document formats?
Yes, Groupdocs.Watermark supports a wide range of document formats including PDF, Word, Excel, PowerPoint, and more.
### Can I customize watermarks and stamps with Groupdocs.Watermark?
Absolutely! Groupdocs.Watermark provides extensive customization options for watermarks, stamps, and annotations to suit your specific requirements.
### Is technical support available for Groupdocs.Watermark users?
Yes, you can get technical assistance and engage with the Groupdocs community through the [support forum](https://forum.groupdocs.com/c/watermark/19).
### How can I obtain a temporary license for Groupdocs.Watermark?
You can obtain a temporary license for Groupdocs.Watermark from [here](https://purchase.groupdocs.com/temporary-license/).
