---
title: "Remove Watermarks from PDF Programmatically with C#"
linktitle: "Remove PDF Watermarks with .NET"
description: "Learn how to programmatically remove watermarks, annotations, and unwanted text from PDF documents using GroupDocs.Watermark for .NET. Includes code examples, performance tips, and troubleshooting."
keywords: "remove watermark from PDF programmatically, PDF watermark removal .NET, delete text from PDF C#, remove unwanted text from PDF documents, GroupDocs watermark removal"
weight: 1
url: "/net/pdf-document-watermarking/remove-pdf-text-artifacts-groupdocs-watermark-net/"
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["PDF Processing"]
tags: ["watermark-removal", "pdf-manipulation", "dotnet", "csharp", "document-processing"]
type: docs
---

# Remove Watermarks from PDF Programmatically with C#

## Introduction

Ever received a batch of PDFs cluttered with outdated watermarks, "DRAFT" stamps that should've been removed before distribution, or legacy text artifacts from previous document versions? You're not alone. Whether you're building a document management system, cleaning up compliance materials, or preparing PDFs for client delivery, those persistent text elements can be a real headache.

The good news? You don't need expensive desktop software or manual editing for every single file. With GroupDocs.Watermark for .NET, you can programmatically remove watermarks, annotations, and text artifacts from PDF documents—whether it's one file or thousands.

In this guide, you'll learn how to identify and remove unwanted text elements based on their formatting (like font size or style), automate the cleanup process, and integrate this capability into your production systems. We'll cover everything from basic setup to advanced batch processing techniques.

### What You'll Learn

- How to set up GroupDocs.Watermark for .NET in your project
- Identify and remove text artifacts based on formatting criteria (font size, style, etc.)
- Handle edge cases and common errors you'll encounter in production
- Optimize performance when processing large PDFs or multiple documents
- Implement batch processing for enterprise-scale operations
- Real-world integration patterns and architectural considerations

Ready to clean up those PDFs? Let's start with what you'll need.

## Prerequisites

Before diving into the code, make sure you've got these bases covered:

### Required Libraries and Dependencies

- **GroupDocs.Watermark for .NET**: The core library that handles all PDF manipulation
- **.NET Framework 4.6.1+** or **.NET Core 2.0+** (or .NET 5/6/7/8 for modern apps)
- A PDF with text artifacts you want to remove (for testing)

### Environment Setup Requirements

You'll need a development environment with .NET installed. This tutorial uses C#, so Visual Studio, VS Code, or JetBrains Rider will work perfectly. If you're working with containerized applications, the library works great in Docker environments too.

### Knowledge Prerequisites

You should be comfortable with:
- Basic C# programming and object-oriented concepts
- File I/O operations in .NET
- Understanding of PDF structure (helpful but not required—we'll explain as we go)

**Note**: If you're new to GroupDocs products, don't worry. This guide assumes you're starting from scratch with this specific library.

## Setting Up GroupDocs.Watermark for .NET

Let's get the library installed and configured. This takes about 2 minutes.

### Installation Options

Choose your preferred method:

**.NET CLI** (fastest for new projects)
```bash
dotnet add package GroupDocs.Watermark
```

**Package Manager Console** (if you're in Visual Studio)
```powershell
Install-Package GroupDocs.Watermark
```

**NuGet Package Manager UI**
1. Right-click your project → Manage NuGet Packages
2. Search for "GroupDocs.Watermark"
3. Click Install on the latest stable version

### License Acquisition

GroupDocs.Watermark requires a license for production use, but you can evaluate it fully with a temporary license:

1. **Temporary License** (30 days, full features): Visit [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
2. **Free Trial**: Limited processing without a license—good for initial testing
3. **Full License**: [Purchase here](https://purchase.groupdocs.com/) for production deployments

**Pro Tip**: Apply for the temporary license before you start developing. It removes all trial limitations and gives you a realistic picture of performance.

### Basic Initialization and Setup

Once installed, add this using directive to your C# file:

```csharp
using GroupDocs.Watermark;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Contents.Pdf;
```

That's it for setup! The library is now ready to use. Next, let's look at the actual implementation.

## Real-World Scenarios: When You Need This

Before we jump into code, let's talk about why you'd want to programmatically remove text artifacts. Here are five common scenarios where developers need this capability:

### 1. Legacy Document Cleanup
You've acquired documents from a previous system or vendor that included watermarks like "CONFIDENTIAL - DO NOT DISTRIBUTE" or version stamps. Now you need to clean hundreds or thousands of files for your new system.

### 2. Multi-Stage Approval Workflows
During document review, you add "DRAFT" or "PENDING REVIEW" watermarks. Once approved, those need to be automatically removed before final distribution. Manual removal doesn't scale.

### 3. White-Label Solutions
You're building a SaaS platform where customers upload documents. Some PDFs come with the customer's internal watermarks that shouldn't appear in your system's outputs.

### 4. Compliance and Privacy Requirements
Documents contain text annotations or stamps with sensitive information (like internal reference numbers or reviewer names) that must be removed before external distribution due to privacy regulations.

### 5. Document Repurposing
You're converting internal training materials or presentations into client-facing documents. The internal branding, timestamps, or classification markings need to be stripped out.

## Implementation Guide

Now for the main event—let's build a solution that removes text artifacts from PDFs based on formatting criteria. We'll start simple and then show you how to handle more complex scenarios.

### Feature Overview: Smart Text Artifact Removal

Our goal is to identify and remove unwanted text elements that meet specific formatting conditions. For example, removing all text fragments with a font size greater than 42 points (often used for prominent watermarks).

**Why formatting-based removal?** Because it's more reliable than text matching. Watermarks might say "DRAFT", "Draft", or "DRAFT - DO NOT DISTRIBUTE"—but they often share consistent formatting characteristics like oversized fonts or specific colors.

#### Complete Implementation: Step-by-Step

##### Step 1: Set Up Your File Paths

First, define where your input PDF is located and where you want to save the cleaned version:

```csharp
// Point to your PDF with unwanted text artifacts
string documentPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "input.pdf");

// Where the cleaned PDF will be saved
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
```

**Real-world tip**: In production, these paths typically come from configuration files, database records, or cloud storage paths (like Azure Blob Storage or AWS S3 URLs).

##### Step 2: Load the PDF Document

Now load the PDF using `PdfLoadOptions`. This tells GroupDocs that we're working specifically with PDF content:

```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // We'll process the document here
    // The 'using' statement ensures proper cleanup of resources
}
```

**What's happening here?** The `Watermarker` object is your main interface for document manipulation. The `using` statement ensures that file handles and memory are released properly—critical when you're processing multiple documents.

##### Step 3: Access PDF Content and Iterate Through Artifacts

Here's where we get into the specifics. Every PDF page can contain "artifacts"—special objects like watermarks, headers, footers, or annotations:

```csharp
// Get the PDF-specific content structure
PdfContent pdfContent = watermarker.GetContent<PdfContent>();

// Iterate through each page in the document
foreach (PdfPage page in pdfContent.Pages)
{
    // Important: iterate backwards through artifacts
    // This prevents index shifting issues when removing items
    for (int i = page.Artifacts.Count - 1; i >= 0; i--)
    {
        // Check each text fragment in the artifact
        foreach (FormattedTextFragment fragment in page.Artifacts[i].FormattedTextFragments)
        {
            // Remove artifacts with font size greater than 42 points
            if (fragment.Font.Size > 42)
            {
                page.Artifacts.RemoveAt(i);
                break; // Exit inner loop—artifact already removed
            }
        }
    }
}
```

**Why iterate backwards?** When you remove an item from a list, all subsequent items shift down one index. If you iterate forward, you'll skip items. Iterating backwards (from `Count - 1` to `0`) avoids this problem entirely.

**About the condition** (`fragment.Font.Size > 42`): This is just an example. You can filter by:
- Font family: `fragment.Font.FamilyName == "Arial"`
- Font color: `fragment.ForegroundColor.ToArgb() == Color.Red.ToArgb()`
- Text content: `fragment.Text.Contains("DRAFT")`
- Or any combination of these!

##### Step 4: Save the Modified PDF

Once you've removed all unwanted artifacts, save the cleaned document:

```csharp
// Save to the output directory with the same filename
watermarker.Save(Path.Combine(outputDirectory, Path.GetFileName(documentPath)));
```

The `Save` method writes the modified PDF to disk. If you need to stream it to cloud storage or return it via an API, there's an overload that accepts a `Stream` instead of a file path.

### Complete Working Example

Here's the full code in one place for easy reference:

```csharp
using GroupDocs.Watermark;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Contents.Pdf;
using System.IO;

public class PdfArtifactRemover
{
    public void RemoveLargeFontArtifacts(string inputPath, string outputPath)
    {
        var loadOptions = new PdfLoadOptions();
        
        using (Watermarker watermarker = new Watermarker(inputPath, loadOptions))
        {
            PdfContent pdfContent = watermarker.GetContent<PdfContent>();
            
            foreach (PdfPage page in pdfContent.Pages)
            {
                for (int i = page.Artifacts.Count - 1; i >= 0; i--)
                {
                    foreach (FormattedTextFragment fragment in page.Artifacts[i].FormattedTextFragments)
                    {
                        if (fragment.Font.Size > 42)
                        {
                            page.Artifacts.RemoveAt(i);
                            break;
                        }
                    }
                }
            }
            
            watermarker.Save(outputPath);
        }
    }
}
```

## Common Pitfalls & Solutions

Let's address the issues you're likely to encounter (so you don't have to debug them yourself):

### 1. "Index Out of Range" Errors

**Problem**: You're iterating forward through the artifacts collection and removing items.

**Solution**: Always iterate backwards when removing items from collections:
```csharp
// Wrong - causes index errors
for (int i = 0; i < page.Artifacts.Count; i++)

// Correct - prevents index shifting
for (int i = page.Artifacts.Count - 1; i >= 0; i--)
```

### 2. No Artifacts Detected

**Problem**: Your code runs without errors, but nothing gets removed.

**Possible causes**:
- The text might not be stored as an "artifact" but as regular page content
- Your formatting criteria are too restrictive
- The PDF might be image-based (scanned document) with no text layer

**Debugging approach**:
```csharp
// Add logging to see what's actually in the document
Console.WriteLine($"Total artifacts on page: {page.Artifacts.Count}");
foreach (var artifact in page.Artifacts)
{
    Console.WriteLine($"Artifact has {artifact.FormattedTextFragments.Count} text fragments");
    foreach (var fragment in artifact.FormattedTextFragments)
    {
        Console.WriteLine($"  Text: '{fragment.Text}' | Font: {fragment.Font.FamilyName} | Size: {fragment.Font.Size}");
    }
}
```

### 3. License-Related Exceptions

**Error**: "The trial period has expired" or "This feature requires a license"

**Solution**: Apply your temporary or full license before creating the `Watermarker` object:
```csharp
// Apply license once at application startup
GroupDocs.Watermark.License license = new GroupDocs.Watermark.License();
license.SetLicense("path/to/GroupDocs.Watermark.lic");
```

### 4. File Locked or Permission Errors

**Problem**: Can't save the modified PDF or access the input file.

**Common causes**:
- Another process has the file open (like Adobe Reader)
- Insufficient write permissions on the output directory
- Trying to overwrite the input file while it's still loaded

**Solution**: Ensure files aren't open elsewhere, and use different input/output paths during development.

### 5. Performance Issues with Large PDFs

**Problem**: Processing a 200-page PDF takes several minutes.

**Solutions**:
- Use pagination—process specific page ranges instead of all pages
- Implement async processing for better resource utilization
- Consider parallel processing for multiple documents (see Performance section below)

## Advanced Techniques: Batch Processing

In real-world scenarios, you're rarely processing just one PDF. Here's how to handle multiple documents efficiently:

### Batch Processor Example

```csharp
public class BatchPdfProcessor
{
    public void ProcessDirectory(string inputDir, string outputDir, int maxFontSize)
    {
        var pdfFiles = Directory.GetFiles(inputDir, "*.pdf");
        
        Console.WriteLine($"Found {pdfFiles.Length} PDFs to process");
        
        var loadOptions = new PdfLoadOptions();
        int processed = 0;
        int errors = 0;
        
        foreach (var pdfFile in pdfFiles)
        {
            try
            {
                using (Watermarker watermarker = new Watermarker(pdfFile, loadOptions))
                {
                    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
                    int removedCount = 0;
                    
                    foreach (PdfPage page in pdfContent.Pages)
                    {
                        for (int i = page.Artifacts.Count - 1; i >= 0; i--)
                        {
                            foreach (FormattedTextFragment fragment in page.Artifacts[i].FormattedTextFragments)
                            {
                                if (fragment.Font.Size > maxFontSize)
                                {
                                    page.Artifacts.RemoveAt(i);
                                    removedCount++;
                                    break;
                                }
                            }
                        }
                    }
                    
                    var outputPath = Path.Combine(outputDir, Path.GetFileName(pdfFile));
                    watermarker.Save(outputPath);
                    
                    Console.WriteLine($"✓ {Path.GetFileName(pdfFile)} - Removed {removedCount} artifacts");
                    processed++;
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine($"✗ {Path.GetFileName(pdfFile)} - Error: {ex.Message}");
                errors++;
            }
        }
        
        Console.WriteLine($"\nCompleted: {processed} processed, {errors} errors");
    }
}
```

**Usage**:
```csharp
var processor = new BatchPdfProcessor();
processor.ProcessDirectory(
    @"C:\Documents\PDFs\ToClean", 
    @"C:\Documents\PDFs\Cleaned",
    maxFontSize: 42
);
```

### Parallel Processing for Better Performance

If you're processing many files, parallelization can significantly reduce total time:

```csharp
public void ProcessDirectoryParallel(string inputDir, string outputDir, int maxFontSize)
{
    var pdfFiles = Directory.GetFiles(inputDir, "*.pdf");
    
    Parallel.ForEach(pdfFiles, new ParallelOptions { MaxDegreeOfParallelism = 4 }, pdfFile =>
    {
        try
        {
            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(pdfFile, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();
                
                foreach (PdfPage page in pdfContent.Pages)
                {
                    for (int i = page.Artifacts.Count - 1; i >= 0; i--)
                    {
                        foreach (FormattedTextFragment fragment in page.Artifacts[i].FormattedTextFragments)
                        {
                            if (fragment.Font.Size > maxFontSize)
                            {
                                page.Artifacts.RemoveAt(i);
                                break;
                            }
                        }
                    }
                }
                
                var outputPath = Path.Combine(outputDir, Path.GetFileName(pdfFile));
                watermarker.Save(outputPath);
            }
        }
        catch (Exception ex)
        {
            // Log error (use thread-safe logging mechanism)
        }
    });
}
```

**Note**: Set `MaxDegreeOfParallelism` based on your server's CPU cores. Starting with 4 is safe for most environments.

## Performance Optimization & Best Practices

### Expected Performance Benchmarks

Based on typical hardware (8GB RAM, 4-core CPU):
- **Small PDFs** (1-10 pages): ~500ms per document
- **Medium PDFs** (50-100 pages): ~2-5 seconds per document
- **Large PDFs** (500+ pages): ~30-60 seconds per document

These times include loading, processing, and saving. Actual performance depends on:
- Number and complexity of artifacts
- PDF file structure (optimized vs. non-optimized)
- Disk I/O speed (SSD vs. HDD makes a big difference)

### Memory Management Tips

**1. Always Use `using` Statements**
The `Watermarker` object holds resources that need explicit cleanup:
```csharp
// Good - automatic disposal
using (Watermarker watermarker = new Watermarker(path, options))
{
    // Process document
}

// Bad - potential memory leaks
Watermarker watermarker = new Watermarker(path, options);
// Process document
// watermarker.Dispose() might not be called if an exception occurs
```

**2. Process in Batches for Large Volumes**
Don't load thousands of file paths into memory at once:
```csharp
// Process 100 files at a time
var allFiles = Directory.GetFiles(inputDir, "*.pdf");
foreach (var batch in allFiles.Chunk(100))
{
    foreach (var file in batch)
    {
        // Process file
    }
    // GC has chance to clean up between batches
    GC.Collect();
}
```

**3. Stream to Cloud Storage When Possible**
If you're working with cloud-based PDFs, avoid downloading to disk:
```csharp
// Download to memory stream
using (var inputStream = await DownloadFromBlobStorage(blobName))
using (Watermarker watermarker = new Watermarker(inputStream, loadOptions))
{
    // Process
    using (var outputStream = new MemoryStream())
    {
        watermarker.Save(outputStream);
        await UploadToBlobStorage(outputBlobName, outputStream);
    }
}
```

### Architecture Recommendations for Production

**For Web Applications:**
- Implement asynchronous processing using background jobs (Hangfire, Azure Functions, AWS Lambda)
- Don't process PDFs synchronously in API requests—timeout issues are inevitable
- Use a queue-based architecture (RabbitMQ, Azure Service Bus) for high volume

**For Enterprise Systems:**
- Run processing in dedicated worker services, not in your web application tier
- Implement retry logic with exponential backoff for transient failures
- Monitor processing times and set up alerts for performance degradation

**For SaaS Platforms:**
- Consider tenant-specific processing limits to prevent resource exhaustion
- Implement file size limits (e.g., max 50MB per PDF)
- Provide processing status updates via webhooks or polling endpoints

## Practical Integration Patterns

### Scenario 1: ASP.NET Core API Endpoint

```csharp
[ApiController]
[Route("api/[controller]")]
public class PdfCleanupController : ControllerBase
{
    private readonly IBackgroundJobClient _backgroundJobs;
    
    [HttpPost("remove-watermarks")]
    public IActionResult RemoveWatermarks([FromForm] IFormFile pdfFile)
    {
        if (pdfFile == null || pdfFile.Length == 0)
            return BadRequest("No file uploaded");
            
        // Save uploaded file temporarily
        var tempPath = Path.GetTempFileName();
        using (var stream = new FileStream(tempPath, FileMode.Create))
        {
            pdfFile.CopyTo(stream);
        }
        
        // Queue background job (don't process synchronously)
        var jobId = _backgroundJobs.Enqueue<PdfProcessor>(
            x => x.RemoveWatermarksAsync(tempPath, pdfFile.FileName)
        );
        
        return Ok(new { JobId = jobId, Message = "Processing started" });
    }
}
```

### Scenario 2: Azure Function for Blob Storage Trigger

```csharp
public class PdfCleanupFunction
{
    [FunctionName("CleanPdfOnUpload")]
    public async Task Run(
        [BlobTrigger("uploads/{name}", Connection = "AzureWebJobsStorage")] Stream inputBlob,
        string name,
        [Blob("cleaned/{name}", FileAccess.Write)] Stream outputBlob,
        ILogger log)
    {
        log.LogInformation($"Processing PDF: {name}");
        
        try
        {
            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(inputBlob, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();
                
                foreach (PdfPage page in pdfContent.Pages)
                {
                    for (int i = page.Artifacts.Count - 1; i >= 0; i--)
                    {
                        foreach (FormattedTextFragment fragment in page.Artifacts[i].FormattedTextFragments)
                        {
                            if (fragment.Font.Size > 42)
                            {
                                page.Artifacts.RemoveAt(i);
                                break;
                            }
                        }
                    }
                }
                
                watermarker.Save(outputBlob);
            }
            
            log.LogInformation($"Successfully processed: {name}");
        }
        catch (Exception ex)
        {
            log.LogError(ex, $"Error processing {name}");
            throw;
        }
    }
}
```

## Troubleshooting Guide: Specific Error Messages

### "Cannot open file. The file is corrupted or damaged."
**Cause**: The PDF file structure is invalid or has been corrupted.

**Solutions**:
1. Verify the file opens correctly in Adobe Reader
2. Try using a PDF repair tool before processing
3. Check if the file is actually a PDF (some files have incorrect extensions)

### "Insufficient permissions to read the file"
**Cause**: The PDF is password-protected or has restricted permissions.

**Solution**: You'll need to provide the password when loading:
```csharp
var loadOptions = new PdfLoadOptions { Password = "your-password" };
using (Watermarker watermarker = new Watermarker(path, loadOptions))
{
    // Process document
}
```

### "OutOfMemoryException" During Processing
**Cause**: The PDF is too large or has too many artifacts to process in available memory.

**Solutions**:
1. Increase heap size for your application
2. Process the PDF page-by-page instead of all at once
3. Use disk-based temporary storage for intermediate results

## Conclusion

You now have everything you need to programmatically remove watermarks and text artifacts from PDF documents using GroupDocs.Watermark for .NET. Whether you're cleaning up a few files or building an enterprise-scale document processing pipeline, the patterns and techniques in this guide will get you there.

**Key takeaways:**
- Format-based removal is more reliable than text matching
- Always iterate backwards when removing items from collections
- Use async/background processing for production systems
- Implement proper error handling and logging for batch operations
- Memory management is critical when processing large volumes

### Next Steps

Ready to expand your PDF processing capabilities? Explore these related features:
- **Adding custom watermarks** to protect your documents
- **Extracting metadata** (author, creation date, custom properties)
- **Searching for specific watermarks** before removal
- **Working with other formats** (Word, Excel, PowerPoint, images)

Check out the [GroupDocs.Watermark documentation](https://docs.groupdocs.com/watermark/net/) for comprehensive guides on all these features.

## FAQ: Your Questions Answered

### How do I remove watermarks from password-protected PDFs?
You'll need to provide the password when loading the document using `PdfLoadOptions`. Set the `Password` property before creating the `Watermarker` object. Without the correct password, you won't be able to access the PDF content.

### Can I remove watermarks from scanned PDF documents?
Not directly. Scanned PDFs are essentially images—they don't have text layers or artifacts. You'd need OCR (Optical Character Recognition) first, or use image processing techniques to remove the watermark from the underlying images.

### What other document formats does GroupDocs.Watermark support?
In addition to PDF, it supports Word (DOC, DOCX), Excel (XLS, XLSX), PowerPoint (PPT, PPTX), Visio, images (PNG, JPEG, BMP, TIFF), and many more. The API is consistent across formats.

### How fast can I process PDFs in bulk?
With parallel processing on decent hardware (8-core CPU, SSD storage), you can process approximately 100-200 small-to-medium PDFs per minute. Large PDFs (100+ pages) will be slower. Expect to process 500-1000 documents per hour in typical batch scenarios.

### Is there a file size limit for PDFs?
GroupDocs.Watermark itself doesn't impose hard limits, but you're constrained by available memory and processing time. PDFs over 100MB should be processed asynchronously. Most production systems set a limit around 50-100MB for individual file uploads.

### Can I remove only specific watermarks instead of all artifacts?
Absolutely! That's why we use formatting criteria. You can check `fragment.Text.Contains("DRAFT")` to remove only "DRAFT" watermarks, or check specific font families, colors, or sizes to target exactly what you want removed.

### What happens if I remove an artifact that's actually important content?
Your formatting criteria should be specific enough to avoid this. Always test on sample documents first. Consider checking multiple properties (font size AND color AND position) to ensure you're only removing actual watermarks, not legitimate content.

### Do I need a license for development and testing?
You can use GroupDocs.Watermark without a license for evaluation purposes, but it will add a watermark to output documents and have some feature limitations. Get a free [temporary license](https://purchase.groupdocs.com/temporary-license/) for full-featured testing—it's valid for 30 days.

### How do I handle errors when processing thousands of PDFs?
Implement try-catch blocks around each document, log errors with enough context (filename, error message, stack trace), and continue processing remaining files. Consider using a retry mechanism for transient failures (network issues, temporary file locks).

### Can I integrate this with cloud storage (AWS S3, Azure Blob, Google Cloud)?
Yes! GroupDocs.Watermark works with streams, so you can download from cloud storage to a `MemoryStream`, process it, and upload the result—all without touching the local file system. This is more efficient for cloud-native applications.

## Resources & Documentation

### Documentation
- [GroupDocs.Watermark .NET Docs](https://docs.groupdocs.com/watermark/net/)
- [API Reference](https://reference.groupdocs.com/watermark/net)

### Download & Licensing
- [Latest Release](https://releases.groupdocs.com/)
