---
title: How to Get Document Info from Local Disk in C# .NET
linktitle: Get Document Info Local Disk
second_title: GroupDocs.Watermark .NET API
description: Learn how to retrieve document properties, file type, page count & size from local disk using GroupDocs.Watermark for .NET. Includes code examples & troubleshooting tips.
keywords: "get document info C# local disk, retrieve document properties .NET, GroupDocs watermark document information, C# get file metadata, check document details before processing"
weight: 11
url: /net/document-manipulation/get-document-info-local-disk/
type: docs
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["Document Processing"]
tags: ["document-info", "file-metadata", "csharp", "dotnet", "groupdocs"]
---

# How to Get Document Info from Local Disk in C# .NET

## Introduction

Ever tried processing a document only to discover it's the wrong format or has way more pages than your system can handle? Yeah, we've all been there. That's where retrieving document information before processing becomes a lifesaver.

In this guide, you'll learn how to get document info from local disk using GroupDocs.Watermark for .NET. We're talking file type, page count, document size—all the metadata you need to make smart decisions before diving into document manipulation. Whether you're building a document management system, automating batch processing, or just need to validate files before watermarking, this tutorial has you covered.

By the end, you'll know exactly how to extract document properties programmatically and use that information to handle your files more intelligently. Let's get started!

## Why Check Document Info Before Processing?

Here's the thing: blindly processing documents is like cooking without checking if you have all the ingredients. You might get halfway through before realizing you're missing something crucial (or worse, working with the wrong file entirely).

**Checking document info first helps you:**

- **Validate file formats** before attempting operations that might fail
- **Estimate processing time** based on page count and file size
- **Prevent memory issues** by detecting oversized documents early
- **Make smart routing decisions** in automated workflows (send small files to fast processing, large ones to batch queues)
- **Improve user experience** by providing accurate progress indicators
- **Save resources** by filtering out unsupported or problematic files upfront

In practical terms, if you're building a watermarking service, you'd want to know if someone's trying to upload a 500-page PDF versus a single-page image. Your processing strategy should be different for each, right?

## Prerequisites

Before we jump into the code, let's make sure you've got everything set up:

1. **.NET Framework**: You'll need .NET Framework installed on your machine. GroupDocs.Watermark for .NET works with various .NET versions (check the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for your specific version compatibility).

2. **GroupDocs.Watermark for .NET Library**: Grab the latest version from the [download page](https://releases.groupdocs.com/Watermark/net/). Installation is straightforward—just add it to your project via NuGet or direct download.

3. **Development Environment**: Visual Studio is the go-to for most .NET developers, but any IDE that supports C# will work fine.

4. **Basic C# Knowledge**: You don't need to be a C# wizard, but understanding classes, methods, and using statements will help you follow along easily.

5. **Sample Documents**: Have some test documents ready (PDFs, Word docs, Excel files, etc.) to experiment with.

## Import Namespaces

First things first—you need to import the necessary namespaces to access GroupDocs.Watermark functionality. This is super straightforward:

```csharp
using System;
using GroupDocs.Watermark.Common;
```

That's it! These two namespaces give you everything you need to work with document information and watermarking features. The `GroupDocs.Watermark.Common` namespace contains the classes for document info retrieval, while `System` gives you basic console output capabilities for testing.

## Step-by-Step Guide: Getting Document Info from Local Disk

Let's break this down into digestible steps. Each one builds on the previous, so you'll understand exactly what's happening at every stage.

## Step 1: Load Your Document

The journey starts with loading your document into the `Watermarker` class. Think of this as opening the file so you can peek inside and see what you're working with.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Document is now loaded and ready for inspection
}
```

Replace `"Your Document Path"` with the actual path to your document (something like `"C:\\Documents\\sample.pdf"` on Windows or `"/home/user/docs/sample.pdf"` on Linux).

**What's happening here?** The `using` statement ensures your document is properly closed after you're done with it—no memory leaks, no locked files. The `Watermarker` class is your gateway to all document operations, not just watermarking (despite the name!).

**Pro tip**: Always use the `using` statement when working with file operations. It automatically disposes of resources, even if an exception occurs. Your future self (and your server's memory) will thank you.

## Step 2: Retrieve Document Information

Now for the main event—actually getting the document info. This is where you extract all those juicy metadata details:

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```

The `GetDocumentInfo()` method does the heavy lifting here. It returns an `IDocumentInfo` object packed with useful properties about your document.

**Understanding the output:**

- **FileType**: Tells you the format (PDF, DOCX, XLSX, etc.). Super useful for validation before processing.
- **PageCount**: Number of pages in the document. Essential for progress bars, time estimates, or deciding if you need to split processing into batches.
- **Size**: File size in bytes. You can use this to prevent processing of files that are too large for your system or to calculate storage costs.

**Real-world scenario**: Imagine you're building a document converter. Before starting conversion, you check if the file is over 50MB. If it is, you route it to a background worker instead of trying to process it synchronously. That's smart resource management!

## Understanding Document Properties in Depth

Let's dig a bit deeper into what these properties mean and how you can use them effectively.

**File Type Detection**

The `FileType` property isn't just a string—it's actually an enum that GroupDocs uses to represent different document formats. This means you can use it in switch statements or conditionals to handle different file types differently:

```csharp
// Example of how you might use FileType in practice
switch (info.FileType)
{
    case FileType.Pdf:
        // Handle PDFs one way
        break;
    case FileType.Docx:
        // Handle Word documents another way
        break;
    // ... and so on
}
```

**Page Count Considerations**

Page count is straightforward for documents like PDFs and Word files, but what about spreadsheets or presentations? For Excel files, this typically represents the number of worksheets. For PowerPoint, it's the number of slides. Keep this in mind when building your logic.

**File Size and Performance**

The size is given in bytes, so you'll often want to convert it to something more readable:

```csharp
double sizeInMB = info.Size / (1024.0 * 1024.0);
Console.WriteLine("Document size: {0:F2} MB", sizeInMB);
```

This kind of conversion makes your application's output much more user-friendly.

## Common Use Cases for Document Info Retrieval

Now that you know how to get document info, let's talk about when and why you'd actually use this in real applications:

**1. Batch Document Processing**

Before processing hundreds of documents, you can scan them all first to:
- Sort by size (process small ones first for quick wins)
- Group by type (process all PDFs together, all Word docs together)
- Identify problem files (corrupted files often report zero pages or unusual sizes)

**2. File Upload Validation**

When users upload documents to your web application:
- Check file type matches what they claim (someone might rename an image to .pdf)
- Verify file size is within acceptable limits
- Confirm page count for services with page-based pricing

**3. Document Management Systems**

For organizing and categorizing documents:
- Auto-tag files by type and size
- Create metadata records for search functionality
- Calculate storage requirements and costs

**4. Automated Workflow Routing**

Direct documents to appropriate processing pipelines:
- Small, single-page docs → fast lane processing
- Large, multi-page docs → batch queue
- Specific file types → specialized handlers

## Step 3: Adding a Text Watermark (Practical Application)

Okay, so you've got your document info. Now let's see a practical application—adding a watermark. This shows you why knowing your document properties beforehand is so valuable.

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

Here's what's happening: you're creating a `TextWatermark` object with custom styling—text, font, colors, opacity, and rotation angle. Then you add it to your document and save the result.

**Why document info matters here**: If you checked the page count beforehand, you could decide whether to apply the watermark to all pages or just the first one. If you know the file size, you can estimate how large the watermarked version will be.

**Customization tips:**
- Adjust opacity (0.0 to 1.0) to make watermarks more or less prominent
- Use rotation angles (typically 45 or -45 degrees) for diagonal watermarks
- Choose colors that contrast well with your document content

## Step 4: Adding an Image Watermark

Text watermarks are great, but sometimes you need to brand documents with your company logo. Here's how to add an image watermark:

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

Replace `"Path to Your Image"` with the actual path to your watermark image (logo, stamp, etc.). The `using` statement for the image watermark ensures the image file is properly closed after use.

**Image watermark best practices:**
- Use transparent PNG images for best results
- Keep image file sizes reasonable (under 500KB) to avoid bloating your documents
- Test different opacity levels—logos often look better at 0.3-0.5 opacity
- Consider document size when choosing image dimensions (scale your logo for small vs. large docs)

## Step 5: Removing Existing Watermarks

Sometimes you need to clean up documents by removing existing watermarks. Maybe you're re-branding, or you received watermarked documents that need to be cleaned:

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```

The `Remove()` method lets you specify which type of watermarks to remove—text, image, or both. This is particularly useful when you know what kind of watermarks your documents contain (remember that document info you retrieved earlier? You could use that to decide your removal strategy).

**Removal scenarios:**
- Remove only text watermarks to replace with new branding
- Remove all watermarks before archiving confidential documents
- Clean up drafts before final publication

## Step 6: Extracting Watermarks for Inspection

If you need to see what watermarks already exist in a document (maybe for audit purposes or to decide if you need to add more), you can extract and inspect them:

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

This retrieves all watermarks from the document, allowing you to iterate through them and examine their properties. You might use this to:
- Check if a document already has your company's watermark (avoid duplicates)
- Audit which documents contain specific watermarks
- Extract watermark text for content analysis

**Pro tip**: You can inspect individual watermark properties like text content, position, size, and rotation. This gives you complete visibility into a document's watermarking history.

## Troubleshooting File Access Issues

Let's be real—file operations don't always go smoothly. Here are common problems you might encounter when working with local disk files and how to handle them:

**Problem: "File not found" errors**

This usually happens when:
- The path is incorrect (typos, wrong slashes, missing escape characters)
- The file has been moved or deleted
- You don't have permission to access the directory

**Solution**: Always validate paths before processing. You can use `System.IO.File.Exists()` to check if a file exists before trying to load it:

```csharp
string filePath = "Your Document Path";
if (!System.IO.File.Exists(filePath))
{
    Console.WriteLine("Error: File not found at " + filePath);
    return;
}
// Proceed with document loading...
```

**Problem: "File is being used by another process"**

Windows locks files when they're open in another application. This is frustrating but common.

**Solution**: Make sure files aren't open in other programs. In your code, always use `using` statements to ensure files are properly closed. If you're running into this in production, implement retry logic with short delays.

**Problem: Unsupported file format**

Sometimes you'll try to load a file that GroupDocs.Watermark doesn't support, or the file extension doesn't match the actual content.

**Solution**: Wrap your document loading in try-catch blocks:

```csharp
try
{
    using (Watermarker watermarker = new Watermarker(filePath))
    {
        // Your processing logic
    }
}
catch (UnsupportedFileTypeException ex)
{
    Console.WriteLine("This file format is not supported: " + ex.Message);
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

**Problem: Out of memory errors with large files**

Processing very large documents (100+ MB) can exhaust available memory, especially on shared hosting or containers.

**Solution**: Check file size before loading (that's where `GetDocumentInfo()` really shines!). For huge files, consider:
- Processing them in batches
- Increasing available memory
- Using streaming approaches where possible
- Implementing a queue system for background processing

## Best Practices for Document Processing

After working with thousands of documents, here are some hard-won lessons:

**1. Always validate before processing**

Check file existence, size, and format before attempting any operations. Five seconds of validation can save minutes of failed processing time (and better user experience).

**2. Use proper error handling**

Wrap file operations in try-catch blocks. Log errors with enough detail to debug later, but show user-friendly messages to end users.

**3. Clean up resources**

Always use `using` statements with file operations. Dispose of objects properly. Memory leaks in document processing applications can kill server performance fast.

**4. Test with diverse files**

Don't just test with perfectly formatted documents. Throw corrupted files, wrong extensions, empty files, and massive files at your code. You'll be surprised what users will upload.

**5. Consider performance at scale**

What works for one document might not work for 1,000 simultaneous operations. Think about:
- Memory usage (load files on-demand, not all at once)
- Processing time (do you need async/await for better responsiveness?)
- Disk I/O (are you reading/writing efficiently?)

**6. Keep security in mind**

File paths from user input can be dangerous. Always:
- Validate and sanitize file paths
- Store uploaded files outside your web root
- Check file content, not just extensions
- Implement virus scanning for user uploads

## Wrapping Up

And there you have it! You now know how to get document info from local disk using GroupDocs.Watermark for .NET, and you understand why this information is so valuable for building robust document processing applications.

Here's what we covered:

- Loading documents and retrieving their metadata (file type, page count, size)
- Using that information to make smart processing decisions
- Practical applications like adding text and image watermarks
- Removing and extracting existing watermarks
- Troubleshooting common file access issues
- Best practices for production document processing

The key takeaway? Always check your document properties before processing. It's like measuring twice and cutting once—a little upfront work saves a lot of headaches later.

Want to explore more advanced features? The [documentation](https://tutorials.groupdocs.com/Watermark/net/) is packed with detailed information about every aspect of GroupDocs.Watermark. And if you run into any issues, the [support forum](https://forum.groupdocs.com/c/watermark/19) is full of helpful folks who've probably solved your problem before.

Happy coding, and may your documents always be properly formatted!

## Frequently Asked Questions

**Can I use GroupDocs.Watermark for .NET with any .NET version?**

GroupDocs.Watermark for .NET supports a wide range of .NET Framework versions, from classic .NET Framework to .NET Core and .NET 5+. Check the [documentation](https://tutorials.groupdocs.com/Watermark/net/) for specific version compatibility—it's usually pretty comprehensive about which features work with which versions.

**Where can I download GroupDocs.Watermark for .NET?**

Head over to the [official download page](https://releases.groupdocs.com/Watermark/net/) to grab the latest version. You can also install it via NuGet Package Manager in Visual Studio, which is often the easiest route for keeping your dependencies updated.

**How do I get a temporary license for testing?**

If you want to test the full functionality before committing to a purchase, you can request a temporary license from the [temporary license page](https://purchase.groupdocs.com/temporary-license/). It's completely free and gives you access to all features for evaluation purposes.

**Is there a free trial available?**

Absolutely! You can start a free trial by visiting the [free trial page](https://releases.groupdocs.com/). This lets you experiment with the library and see if it fits your needs before spending any money. The trial has some limitations, but it's perfect for testing basic functionality.

**Where can I get support if I run into problems?**

The best place for support is the [GroupDocs Watermark forum](https://forum.groupdocs.com/c/watermark/19). The community there is pretty active, and the GroupDocs team regularly answers questions. You'll often find that someone else has already solved the exact problem you're facing, so it's worth searching existing threads first.