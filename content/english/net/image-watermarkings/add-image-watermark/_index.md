---
title: Add Image Watermark
linktitle: Add Image Watermark
second_title: GroupDocs.Watermark .NET API
description: Learn how to add image watermarks to your documents using GroupDocs.Watermark for .NET with our detailed, step-by-step tutorial.
weight: 11
url: /net/image-watermarkings/add-image-watermark/
---

# Add Image Watermark

## Introduction
Welcome to this comprehensive guide on adding image watermarks using GroupDocs.Watermark for .NET! Watermarking is a powerful way to protect your documents and images from unauthorized use, ensuring that your intellectual property remains secure. In this tutorial, we'll walk you through the entire process, from setting up your environment to applying a watermark to your documents. Whether you're a seasoned developer or just getting started, you'll find this guide helpful and easy to follow.
## Prerequisites
Before we dive into the tutorial, let's make sure you have everything you need:
- Development Environment: Visual Studio or any .NET-compatible IDE
- .NET Framework: .NET Framework 4.0 or higher
- GroupDocs.Watermark for .NET: You can download it from the [GroupDocs website](https://releases.groupdocs.com/Watermark/net/)
- Image File: An image file to use as a watermark (e.g., `watermark.jpg`)
- Document File: A document to which you want to add the watermark (e.g., `presentation.pptx`)
## Import Namespaces
To get started, you'll need to import the necessary namespaces into your project. This is essential for accessing the GroupDocs.Watermark functionalities.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
In this section, we'll break down the process of adding an image watermark into clear, manageable steps. Follow each step carefully to successfully watermark your document.
## Step 1: Set Up Your Environment
First, ensure that your development environment is properly set up. Install the GroupDocs.Watermark library by downloading it from the [GroupDocs website](https://releases.groupdocs.com/Watermark/net/).
1. Open your project in Visual Studio.
2. Right-click on your project in the Solution Explorer.
3. Select "Manage NuGet Packages..."
4. Search for `GroupDocs.Watermark` and install it.
## Step 2: Define File Paths
Next, you'll need to define the paths for your input document and the output directory. This helps the program locate the files it needs to work with.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` and `"Your Document Directory"` with the actual paths to your document and desired output directory.
## Step 3: Initialize Watermarker
Now, initialize the `Watermarker` class with the path to your document. This class is responsible for managing the watermarking process.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Proceed to the next steps within this using block
}
```
## Step 4: Create ImageWatermark
Within the `Watermarker` block, create an instance of the `ImageWatermark` class using the path to your watermark image. This class represents the image you want to use as a watermark.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Continue to the next step within this using block
}
```
## Step 5: Add Watermark to Document
With the `ImageWatermark` instance ready, add it to your document using the `Add` method of the `Watermarker` class.
```csharp
watermarker.Add(watermark);
```
## Step 6: Save the Document
Finally, save the watermarked document to the specified output directory. This step ensures that your changes are written to a new file.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
Congratulations! You've successfully added an image watermark to your document using GroupDocs.Watermark for .NET. By following this step-by-step guide, you can easily protect your documents with custom watermarks. Remember, watermarking is a crucial step in safeguarding your digital assets from unauthorized use.

## FAQ's
### What file formats are supported by GroupDocs.Watermark?
GroupDocs.Watermark supports a wide range of file formats, including PDF, DOCX, PPTX, XLSX, and image files such as JPEG and PNG.
### Can I use GroupDocs.Watermark with .NET Core?
Yes, GroupDocs.Watermark is compatible with both .NET Framework and .NET Core.
### How can I get a temporary license for GroupDocs.Watermark?
You can obtain a temporary license from the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/).
### Is it possible to add multiple watermarks to a single document?
Absolutely! You can add multiple watermarks by calling the `Add` method multiple times with different watermark instances.
### Where can I find more examples and documentation?
For more examples and detailed documentation, visit the [GroupDocs.Watermark documentation](https://tutorials.groupdocs.com/Watermark/net/).
