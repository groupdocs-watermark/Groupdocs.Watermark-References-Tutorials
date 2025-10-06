---
title: Get Document Info from Local Disk
linktitle: Get Document Info from Local Disk
second_title: GroupDocs.Watermark .NET API
description: Learn how to add, remove, and extract watermarks in documents using GroupDocs.Watermark for .NET with this comprehensive step-by-step guide.
weight: 11
url: /net/document-manipulation/get-document-info-local-disk/
type: docs
---
# Get Document Info from Local Disk

## Introduction
Welcome to the ultimate guide on using GroupDocs.Watermark for .NET! Whether you're a seasoned developer or just getting started, this article will walk you through the essentials of watermarking your documents with this powerful tool. By the end, you'll be a pro at embedding watermarks in your documents, ensuring they are protected and branded to your specifications.
## Prerequisites
Before diving into the step-by-step guide, there are a few prerequisites you'll need to meet:
1. .NET Framework: Make sure you have .NET Framework installed on your system. GroupDocs.Watermark for .NET is compatible with various versions of the .NET Framework, so check the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for compatibility details.
2. GroupDocs.Watermark for .NET Library: Download and install the latest version from the [download page](https://releases.groupdocs.com/Watermark/net/).
3. Development Environment: You should have a development environment set up. Visual Studio is a popular choice for .NET development.
4. Basic C# Knowledge: Understanding the basics of C# programming will help you follow along with the examples.
## Import Namespaces
Before you can use GroupDocs.Watermark for .NET, you need to import the necessary namespaces into your project. This is a straightforward process and essential for accessing the library's features.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Let's break down the process of watermarking a document into clear, manageable steps. Each step is designed to help you understand and implement the functionality with ease.
## Step 1: Load Your Document
The first step is to load the document you want to watermark. This is done using the `Watermarker` class, which allows you to access and manipulate your document.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Document is now loaded and ready for watermarking
}
```
In this step, replace `"Your Document Path"` with the actual path to your document. This initializes the `Watermarker` object, giving you access to various watermarking functionalities.
## Step 2: Get Document Information
Before adding a watermark, you might want to gather some information about the document. This can be useful for customizing your watermark based on document properties.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
In this step, the `GetDocumentInfo` method retrieves details such as file type, page count, and document size. This information is printed to the console, but you can use it in your application as needed.
## Step 3: Add a Text Watermark
Now that you have your document loaded and its information at hand, it's time to add a watermark. We'll start with a simple text watermark.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
Here, you create a `TextWatermark` object with your desired text, font, and styling. Adjust properties like color, opacity, and rotation angle to fit your needs. Finally, the watermark is added to the document and saved to a specified path.
## Step 4: Add an Image Watermark
Text watermarks are great, but what if you want to add a logo or another image? This step covers how to add an image watermark.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
Replace `"Path to Your Image"` with the path to your watermark image. Set properties such as opacity and rotation angle to customize the appearance of your image watermark. The process of adding and saving the watermark is similar to that of a text watermark.
## Step 5: Remove Existing Watermarks
Sometimes, you might need to remove existing watermarks from a document. This can be done using the `Remove` method provided by the `Watermarker` class.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
Here, the `Remove` method is used to remove text watermarks from the document. You can specify different types of watermarks to remove, such as image or text, depending on your needs. Save the document to a new path to see the changes.
## Step 6: Extract Watermarks
If you need to extract and inspect watermarks from a document, GroupDocs.Watermark for .NET makes this possible with ease.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Additional properties and logic for each watermark
    }
}
```
This step involves using the `GetWatermarks` method to retrieve all watermarks in a document. You can then iterate through the list of watermarks and inspect their properties or perform additional actions as needed.
## Conclusion
Congratulations! You've now learned how to use GroupDocs.Watermark for .NET to add, remove, and extract watermarks from your documents. With these skills, you can protect and brand your documents effectively. Remember, the [documentation](https://tutorials.groupdocs.com/Watermark/net/) is always there if you need more detailed information or advanced functionality.
## FAQ's
### Can I use GroupDocs.Watermark for .NET with any .NET version?
Yes, GroupDocs.Watermark for .NET is compatible with various .NET Framework versions. Check the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for specifics.
### Where can I download GroupDocs.Watermark for .NET?
You can download the latest version from the [download page](https://releases.groupdocs.com/Watermark/net/).
### How do I get a temporary license?
You can obtain a temporary license from the [temporary license page](https://purchase.groupdocs.com/temporary-license/).
### Is there a free trial available?
Yes, you can start a free trial by visiting the [free trial page](https://releases.groupdocs.com/).
### Where can I get support if I encounter issues?
Support is available on the [GroupDocs Watermark forum](https://forum.groupdocs.com/c/watermark/19).
