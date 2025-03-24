---
title: Add Watermark to Images in PDF
linktitle: Add Watermark to Images in PDF
second_title: GroupDocs.Watermark .NET API
description: Learn to add watermarks to images in PDF documents using GroupDocs.Watermark for .NET with our detailed, step-by-step tutorial. Secure your PDFs easily.
weight: 19
url: /net/pdf-watermarking-attachments/add-watermark-images-pdf/
---

# Add Watermark to Images in PDF

## Introduction
Adding watermarks to images within a PDF document can be essential for protecting your intellectual property or ensuring the authenticity of your documents. Using GroupDocs.Watermark for .NET, this task can be done efficiently and with ease. This tutorial will guide you through each step of the process, from setting up your environment to adding watermarks to saving the final document. Let's dive in!
## Prerequisites
Before we begin, make sure you have the following:
1. Visual Studio: Install Visual Studio, the Integrated Development Environment (IDE) for .NET applications.
2. GroupDocs.Watermark for .NET: Download and install the GroupDocs.Watermark for .NET library from the [release page](https://releases.groupdocs.com/Watermark/net/).
3. A PDF Document: Have a PDF document with images ready to test the watermarking functionality.
4. Temporary License: Obtain a [temporary license](https://purchase.groupdocs.com/temporary-license/) if you are evaluating the product.
## Import Namespaces
First, ensure you have the necessary namespaces imported in your project. This will include the core namespaces required to work with PDF documents and watermarks.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Step 1: Set Up the Document Path and Output Directory
To start, define the paths for the input document and the output directory where the watermarked document will be saved. This step is crucial to ensure that your program knows where to find the source document and where to store the processed file.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Step 2: Load the PDF Document
Next, you'll need to load the PDF document using `PdfLoadOptions`. This class allows you to specify options for loading the PDF, such as password protection if necessary.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Your code for watermarking will go here
}
```
## Step 3: Create the Watermark
Now, initialize the watermark. In this example, we are creating a text watermark that reads "Protected image". Customize the font, alignment, rotation, and scaling according to your needs.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Step 4: Access PDF Content
Retrieve the content of the PDF document. Specifically, we need to access the images within the PDF. Here, we're focusing on the first page, but you can extend this to other pages as needed.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Get all images from the first page
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Step 5: Apply the Watermark to Images
Loop through each image found on the first page and apply the watermark. This ensures that all images on the specified page will have the watermark applied.
```csharp
// Add watermark to all found images
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Step 6: Save the Watermarked Document
Finally, save the watermarked PDF to the specified output directory. This step finalizes the process by writing the changes to a new file.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
And there you have it! Adding a watermark to images within a PDF using GroupDocs.Watermark for .NET is a straightforward process that can greatly enhance the security and authenticity of your documents. By following these steps, you can ensure that your intellectual property is protected and your documents are secure.
## FAQ's
### What is GroupDocs.Watermark for .NET?
GroupDocs.Watermark for .NET is a comprehensive library that allows developers to add, search, and remove watermarks in various document formats, including PDFs.
### Can I add both text and image watermarks using GroupDocs.Watermark?
Yes, GroupDocs.Watermark supports both text and image watermarks, providing flexibility for different types of watermarking needs.
### Is it possible to watermark multiple pages in a PDF?
Absolutely! You can loop through each page in the PDF and apply watermarks to images on every page.
### Do I need a license to use GroupDocs.Watermark for .NET?
Yes, a license is required. You can obtain a [temporary license](https://purchase.groupdocs.com/temporary-license/) for evaluation purposes.
### Where can I find more documentation on GroupDocs.Watermark for .NET?
You can find comprehensive documentation on the [GroupDocs.Watermark documentation page](https://tutorials.groupdocs.com/Watermark/net/).
