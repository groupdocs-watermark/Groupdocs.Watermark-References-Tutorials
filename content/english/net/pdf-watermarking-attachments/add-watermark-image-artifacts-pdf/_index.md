---
title: Add Watermark to Image Artifacts in PDF
linktitle: Add Watermark to Image Artifacts in PDF
second_title: GroupDocs.Watermark .NET API
description: Protect your PDF files with personalized watermarks using GroupDocs.Watermark for .NET. Easily add text or image watermarks to image artifacts in PDF documents.
type: docs
weight: 18
url: /net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Introduction
In this tutorial, we'll guide you through the process of adding a watermark to image artifacts in a PDF document using GroupDocs.Watermark for .NET. By following these steps, you can efficiently protect your PDF files with personalized watermarks.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs.Watermark for .NET: Download and install the GroupDocs.Watermark for .NET library from [here](https://releases.groupdocs.com/Watermark/net/).
2. Document Path: Have the path to the PDF document where you want to add the watermark.
3. Output Directory: Create a directory where the watermarked document will be saved.

## Import Namespaces
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Load the Document and Initialize Watermarker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Step 2: Get PDF Content and Add Watermark
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Initialize image or text watermark
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Add watermark to the image
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Step 3: Save the Watermarked Document
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusion
With GroupDocs.Watermark for .NET, adding watermarks to image artifacts in PDF documents becomes a seamless process. By following this tutorial, you can efficiently protect your PDF files with customized watermarks, ensuring their security and authenticity.
## FAQ's
### Can I add both image and text watermarks to my PDF document?
Yes, GroupDocs.Watermark for .NET supports adding both image and text watermarks simultaneously.
### Is there any limitation on the number of watermarks I can add to a document?
No, you can add multiple watermarks to a document without any limitations.
### Can I customize the appearance and position of the watermark?
Absolutely, you have full control over the appearance, position, and properties of the watermark.
### Does GroupDocs.Watermark for .NET support other document formats besides PDF?
Yes, it supports various document formats including Word, Excel, PowerPoint, and more.
### Is there a way to remove watermarks from a document?
Yes, GroupDocs.Watermark for .NET provides methods to remove watermarks from documents if needed.
