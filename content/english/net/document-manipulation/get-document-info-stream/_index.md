---
title: "How to Read Document Properties from Stream in C#"
linktitle: "Read Document Info from Stream"
description: "Learn how to extract document metadata (file type, page count, size) from streams in C# without saving files. Includes practical examples, best practices, and troubleshooting."
keywords: "read document properties C#, extract document metadata stream, get file info without saving, document information API .NET, C# stream document details, GroupDocs.Watermark document info"
weight: 12
url: /net/document-manipulation/get-document-info-stream/
date: "2025-01-02"
lastmod: "2025-01-02"
type: docs
categories: ["Document Processing"]
tags: ["C#", "streams", "metadata", "document-properties", "file-info"]
---

# How to Read Document Properties from Stream in C#

## Introduction

Ever needed to check a document's file type, page count, or size before processing it—without actually saving it to disk? Whether you're building a document management system, validating uploads, or routing files based on their properties, reading document metadata from streams is a game-changer for performance and security.

Here's the problem: traditional approaches require saving files temporarily, which slows down your application and creates security risks. The solution? Extract document information directly from memory streams using GroupDocs.Watermark for .NET.

In this guide, you'll learn how to read document properties from streams efficiently, understand when this approach makes sense, and implement it correctly in your C# applications. By the end, you'll have a solid understanding of document metadata extraction that you can apply immediately.

## Why Read Document Info from Streams?

Before diving into the code, let's understand why working with streams matters:

**Performance Benefits:**
- No disk I/O operations (significantly faster for large files)
- Reduced temporary file cleanup overhead
- Better resource utilization in high-volume scenarios

**Security Advantages:**
- Documents never touch the file system
- Reduced attack surface for sensitive data
- Easier compliance with data protection regulations

**Practical Flexibility:**
- Process documents from any source (uploads, APIs, databases)
- Chain operations without intermediate file saves
- Handle documents that exist only in memory

## Common Use Cases

You'll find this technique especially useful when:

1. **Validating File Uploads**: Check file type and size before accepting user uploads
2. **Document Routing**: Direct files to different processing pipelines based on properties
3. **Pre-Processing Checks**: Verify page count limits before expensive operations
4. **API Integrations**: Handle documents received from external services without local storage
5. **Batch Processing**: Quickly categorize and filter large document collections

## Prerequisites

Before you start, make sure you have:

- **Development environment**: .NET Framework 4.6.1+ or .NET Core 2.0+ (preferably .NET 6 or later)
- **C# knowledge**: Familiarity with streams, using statements, and basic error handling
- **GroupDocs.Watermark library**: Installed via NuGet or downloaded from the [releases page](https://releases.groupdocs.com/Watermark/net/)
- **Valid license**: Either a full license [purchase here](https://purchase.groupdocs.com/buy) or temporary license for testing [get temporary license](https://purchase.groupdocs.com/temporary-license/)

**Quick Installation via NuGet:**
```bash
Install-Package GroupDocs.Watermark
```

Not sure if you need a license yet? Grab the [free trial](https://releases.groupdocs.com/) to test everything first.

## Import Namespaces

Start by importing the necessary namespaces. These give you access to the classes you'll need for working with documents and streams:

```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
```

Here's what each namespace provides:
- `System.IO`: Stream handling and file operations
- `GroupDocs.Watermark.Common`: Core watermark functionality and document info classes

## Step-by-Step Guide: Extracting Document Information

Let's break down the entire process into clear, manageable steps. Each step builds on the previous one, so you'll see exactly how everything fits together.

### Step 1: Initialize the Watermarker with Your Stream

The first step is creating a `Watermarker` instance with your document stream. This is where the magic begins—the Watermarker acts as your gateway to document properties.

```csharp
using (Watermarker watermarker = new Watermarker(stream))
{
    // We'll add more code here in the next steps
}
```

**What's happening here?**
- The `using` statement ensures proper disposal of resources (important for memory management)
- The `stream` parameter is your document's memory stream—could be from a file upload, API call, or any other source
- The Watermarker loads the document structure into memory without modifying it

**Pro tip**: Make sure your stream is positioned at the beginning (position 0) before passing it to the Watermarker. If you've read from it earlier, call `stream.Seek(0, SeekOrigin.Begin)` first.

### Step 2: Retrieve the Document Information

Once your Watermarker is initialized, retrieving document info is straightforward. The `GetDocumentInfo()` method does all the heavy lifting:

```csharp
IDocumentInfo info = watermarker.GetDocumentInfo();
```

**Behind the scenes:**
- The method analyzes the stream's content to detect file type
- It parses the document structure to count pages
- Size information is calculated from the stream
- All of this happens in memory—no temporary files created

The returned `IDocumentInfo` interface contains all the metadata you need. It's lightweight and fast to retrieve, even for large documents.

### Step 3: Access and Display Document Properties

Now that you have the document information, you can access its properties. Here's how to display the most commonly needed details:

```csharp
Console.WriteLine("File type: {0}", info.FileType);
Console.WriteLine("Number of pages: {0}", info.PageCount);
Console.WriteLine("Document size: {0} bytes", info.Size);
```

**Understanding the properties:**
- **FileType**: Returns the document format (e.g., "PDF", "DOCX", "XLSX")—useful for validation and routing
- **PageCount**: Total pages in the document—important for pricing, quotas, or processing decisions
- **Size**: Document size in bytes—helps with storage calculations and upload limits

**Real-world example:**
Let's say you're building a document upload feature with these rules:
- Only PDF and Word documents allowed
- Maximum 50 pages per document
- File size limit of 10MB

Here's how you'd implement those checks:

```csharp
using (Watermarker watermarker = new Watermarker(stream))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    
    // Validation logic
    if (info.FileType != FileType.Pdf && info.FileType != FileType.Docx)
    {
        throw new InvalidOperationException("Only PDF and Word documents are supported.");
    }
    
    if (info.PageCount > 50)
    {
        throw new InvalidOperationException("Document exceeds maximum page limit of 50 pages.");
    }
    
    if (info.Size > 10 * 1024 * 1024) // 10MB in bytes
    {
        throw new InvalidOperationException("File size exceeds 10MB limit.");
    }
    
    // If we get here, the document passed all validations
    Console.WriteLine($"Valid document: {info.FileType}, {info.PageCount} pages, {info.Size / 1024}KB");
}
```

## Best Practices for Stream-Based Document Processing

To get the most out of this approach, follow these professional guidelines:

### Memory Management
**Always use `using` statements** for both streams and Watermarker instances. This ensures proper resource disposal even if exceptions occur:

```csharp
using (var fileStream = File.OpenRead("document.pdf"))
using (var watermarker = new Watermarker(fileStream))
{
    var info = watermarker.GetDocumentInfo();
    // Process info
}
// Resources automatically cleaned up here
```

### Error Handling
**Wrap your code in try-catch blocks** to handle unsupported formats gracefully:

```csharp
try
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        IDocumentInfo info = watermarker.GetDocumentInfo();
        // Process document
    }
}
catch (UnsupportedFileTypeException ex)
{
    Console.WriteLine($"Unsupported file type: {ex.Message}");
    // Handle unsupported format
}
catch (Exception ex)
{
    Console.WriteLine($"Error processing document: {ex.Message}");
    // Handle other errors
}
```

### Performance Considerations
**For large files**, consider these optimizations:
- Use `BufferedStream` to improve read performance
- Set appropriate buffer sizes based on your typical file sizes
- Consider async operations for web applications to avoid blocking threads

```csharp
using (var bufferedStream = new BufferedStream(originalStream, bufferSize: 81920))
using (var watermarker = new Watermarker(bufferedStream))
{
    var info = watermarker.GetDocumentInfo();
}
```

### When to Use Streams vs. File Paths
**Choose streams when:**
- Processing uploaded files (already in memory)
- Working with documents from APIs or databases
- Security requires avoiding file system access
- You need maximum performance for multiple operations

**Choose file paths when:**
- Files already exist on disk and won't be moved
- You're doing simple one-off operations
- Memory is constrained (very large files)

## Troubleshooting Common Issues

### "Stream does not support reading" Error
**Problem**: You're passing a write-only stream.

**Solution**: Ensure your stream supports reading. Check `stream.CanRead` before passing it:

```csharp
if (!stream.CanRead)
{
    throw new ArgumentException("Stream must support reading");
}
```

### Incorrect Page Count or Size
**Problem**: Stream position isn't at the beginning.

**Solution**: Reset stream position before processing:

```csharp
stream.Seek(0, SeekOrigin.Begin);
using (var watermarker = new Watermarker(stream))
{
    // Now it works correctly
}
```

### Out of Memory Exceptions
**Problem**: Processing very large files in memory-constrained environments.

**Solution**: Either increase available memory or switch to file-based processing for huge documents:

```csharp
// For very large files, consider using file path instead
using (var watermarker = new Watermarker("path/to/large/file.pdf"))
{
    var info = watermarker.GetDocumentInfo();
}
```

### Unsupported File Type
**Problem**: The file format isn't supported by GroupDocs.Watermark.

**Solution**: Check supported formats in the [documentation](https://tutorials.groupdocs.com/Watermark/net/) and add appropriate error handling (see example above).

## Complete Working Example

Here's everything put together in a production-ready example:

```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;

public class DocumentInfoExtractor
{
    public static void ProcessDocument(Stream documentStream)
    {
        // Validate input
        if (documentStream == null)
            throw new ArgumentNullException(nameof(documentStream));
        
        if (!documentStream.CanRead)
            throw new ArgumentException("Stream must support reading");
        
        // Ensure stream is at the beginning
        documentStream.Seek(0, SeekOrigin.Begin);
        
        try
        {
            using (Watermarker watermarker = new Watermarker(documentStream))
            {
                IDocumentInfo info = watermarker.GetDocumentInfo();
                
                // Display document information
                Console.WriteLine("=== Document Information ===");
                Console.WriteLine($"File Type: {info.FileType}");
                Console.WriteLine($"Page Count: {info.PageCount}");
                Console.WriteLine($"Size: {info.Size:N0} bytes ({info.Size / 1024.0:F2} KB)");
                
                // Example validation
                ValidateDocument(info);
                
                Console.WriteLine("Document validation passed!");
            }
        }
        catch (UnsupportedFileTypeException ex)
        {
            Console.WriteLine($"Error: Unsupported file type - {ex.Message}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error processing document: {ex.Message}");
        }
    }
    
    private static void ValidateDocument(IDocumentInfo info)
    {
        // Example business rules
        var allowedTypes = new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
        
        if (!Array.Exists(allowedTypes, t => t == info.FileType))
        {
            throw new InvalidOperationException(
                $"File type {info.FileType} is not allowed. Supported types: PDF, DOCX, XLSX");
        }
        
        if (info.PageCount > 100)
        {
            throw new InvalidOperationException(
                $"Document has {info.PageCount} pages, maximum allowed is 100");
        }
    }
}
```

## Conclusion

Reading document properties from streams in C# doesn't have to be complicated. With GroupDocs.Watermark for .NET, you can extract file type, page count, and size information efficiently—without ever touching the file system.

Here's what we covered:
- **Why streams matter**: Performance, security, and flexibility benefits
- **Step-by-step implementation**: From initialization to property access
- **Best practices**: Memory management, error handling, and performance optimization
- **Real-world applications**: Validation, routing, and pre-processing scenarios

Ready to take it further? Check out the [complete documentation](https://tutorials.groupdocs.com/Watermark/net/) to explore advanced features like watermark extraction, modification, and removal.

## FAQ's

### What file formats does GroupDocs.Watermark support?
GroupDocs.Watermark supports 40+ formats including PDF, Word (DOC, DOCX), Excel (XLS, XLSX), PowerPoint (PPT, PPTX), Visio, images (JPG, PNG, GIF), and more. You can find the complete list in the [official documentation](https://tutorials.groupdocs.com/Watermark/net/).

### Can I read document info without a license?
Yes! You can use the [free trial](https://releases.groupdocs.com/) to evaluate all features. For longer testing periods, request a [temporary license](https://purchase.groupdocs.com/temporary-license/) which gives you full access for 30 days. Production use requires a [purchased license](https://purchase.groupdocs.com/buy).

### How do I handle password-protected documents?
Password-protected documents require additional configuration when initializing the Watermarker. Pass a `LoadOptions` object with the password:

```csharp
var loadOptions = new LoadOptions("your-password");
using (var watermarker = new Watermarker(stream, loadOptions))
{
    var info = watermarker.GetDocumentInfo();
}
```

### Is this approach thread-safe?
Each `Watermarker` instance is independent, so you can safely process multiple streams concurrently. However, don't share a single Watermarker instance across threads. Create separate instances for each thread or use proper synchronization.

### What's the performance impact compared to file-based access?
Stream-based processing is typically **20-40% faster** than file-based approaches because it eliminates disk I/O. The exact improvement depends on your hardware, document size, and operation type. For web applications handling uploads, the difference is significant.

### Can I get more detailed metadata (author, creation date, etc.)?
The `GetDocumentInfo()` method provides basic structural information (type, pages, size). For detailed metadata like author, title, and timestamps, you'll need to use format-specific properties or additional GroupDocs libraries designed for metadata extraction.

### Where can I get help if I encounter issues?
The GroupDocs team provides excellent support through their [forum](https://forum.groupdocs.com/c/watermark/19). You'll find both community help and direct responses from the development team. For urgent issues with commercial licenses, contact their support team directly.

### How large can documents be when using streams?
There's no hard limit imposed by GroupDocs.Watermark, but practical limits depend on your available memory. As a rule of thumb, ensure you have at least 2-3x the document size available as RAM. For documents over 100MB, monitor memory usage and consider file-based processing if necessary.
