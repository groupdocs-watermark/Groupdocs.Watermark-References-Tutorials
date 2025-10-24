---
title: "Add Watermark to PDF in C# - Protect Your Documents Automatically"
linktitle: "Add Watermark to PDF in C#"
description: "Learn how to add watermarks to PDF files in C# using GroupDocs.Watermark for .NET. Protect documents, mark confidentiality, and automate batch processing with simple code examples."
keywords: "add watermark to PDF C#, document watermarking .NET tutorial, watermark PDF files programmatically .NET, add text watermark to document C#, batch watermark documents C# code, protect documents with watermarks .NET"
weight: 1
url: "/net/advanced-features/implement-document-copying-watermarking-groupdocs-watermark-dotnet/"
keywords:
- document copying and watermarking
- GroupDocs.Watermark for .NET
- text watermarks in .NET
type: docs
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["Document Processing"]
tags: ["PDF", "watermarking", "C#", "document-security", "GroupDocs"]
---
# How to Implement Document Copying and Watermarking in .NET Using GroupDocs.Watermark

## Introduction

Ever sent out a document only to worry about how it might be used or shared? You're not alone. Whether you're dealing with confidential business reports, draft contracts, or copyright-sensitive materials, watermarking is your first line of defense.

Here's the thing: manually adding watermarks to dozens (or hundreds) of documents isn't just tedious—it's error-prone and time-consuming. That's where programmatic watermarking comes in, and specifically, why you'll want to know how to add watermarks to PDFs and other documents using C#.

In this guide, I'll show you how to use GroupDocs.Watermark for .NET to automatically watermark your documents, copy files while maintaining integrity, and even batch-process entire folders. No fluff, just practical code you can implement today.

**What You'll Learn:**
- How to add text watermarks to PDFs, Word docs, and other formats using C#
- Why programmatic watermarking beats manual methods (spoiler: it's not just about speed)
- How to copy documents efficiently while preserving their structure
- Real-world use cases from legal firms, marketing agencies, and enterprises
- Troubleshooting tips for common watermarking challenges

Ready to protect your documents the smart way? Let's dive in.

## Why Watermark Your Documents?

Before we get into the code, let's talk about why watermarking matters (especially if you're trying to convince your team or manager that this is worth implementing).

**Common Scenarios Where Watermarking Saves the Day:**
- **Legal and Compliance**: Mark documents as "CONFIDENTIAL" or "DRAFT" to prevent misuse
- **Copyright Protection**: Add visible ownership marks to creative work or reports
- **Version Control**: Watermark documents with version numbers or dates to avoid confusion
- **Client Deliverables**: Brand documents with your company logo or "PREVIEW" for client review
- **Internal Security**: Mark sensitive documents before distribution to track leaks

The manual approach? Opening each file, using design software or built-in watermark features, and saving individually. For 5 documents, that's manageable. For 500? You'll lose your mind (and waste hours).

**The Programmatic Advantage:**
- Process hundreds of documents in seconds
- Ensure consistency across all watermarks
- Automate as part of your document workflow
- Customize watermarks based on document type or metadata
- Free up your time for actual work instead of repetitive tasks

## Prerequisites

Before we jump into the code, let's make sure you've got everything set up. Don't worry—this is the easy part.

**What You'll Need:**
1. **Development Environment**: Visual Studio 2019 or later (or any .NET-compatible IDE)
2. **Framework**: .NET Framework 4.6.1+ or .NET Core 2.0+ or .NET 5/6/7/8
3. **GroupDocs.Watermark Package**: We'll install this in the next section
4. **Basic C# Knowledge**: If you can work with file paths and using statements, you're good to go
5. **Sample Documents**: A few PDF or Word files to test with (I'll show you where to get them if you don't have any)

That's it! No complex setup, no server configuration, no headaches.

## Setting Up GroupDocs.Watermark for .NET

### Installation (Takes 2 Minutes)

Let's get the GroupDocs.Watermark package installed. You've got three options—pick whichever method you're most comfortable with:

**Option 1: .NET CLI (My Favorite)**
```bash
dotnet add package GroupDocs.Watermark
```

**Option 2: Package Manager Console**
```powershell
Install-Package GroupDocs.Watermark
```

**Option 3: NuGet Package Manager UI**
1. Right-click your project in Visual Studio
2. Select "Manage NuGet Packages"
3. Search for "GroupDocs.Watermark"
4. Click "Install" on the latest version

That's it—the package will download and you're ready to start coding.

### License Acquisition (Free Trial Available)

Here's the deal with licensing: GroupDocs.Watermark offers a free trial with some limitations (perfect for testing), and you can grab a temporary license if you need to evaluate all features without restrictions.

**For Testing and Development:**
- Free trial includes basic watermarking features
- Great for POC (proof of concept) work
- Visit [GroupDocs' licensing page](https://purchase.groupdocs.com/temporary-license/) to get a free temporary license

**For Production:**
- You'll need a full license (pricing is reasonable for what you get)
- Check their website for current pricing and options

Pro tip: Start with the free trial, build your solution, and then show your manager the time savings. Makes the license purchase conversation much easier!

### Basic Initialization and Setup

Once installed, you'll initialize the watermarker like this:

```csharp
using GroupDocs.Watermark;

// Initialize the Watermarker with your file path
Watermarker watermarker = new Watermarker("your_file_path");
```

Quick note: The `Watermarker` object is your main interface for everything—loading documents, adding watermarks, and saving results. Think of it as your document processing Swiss Army knife.

## Implementation Guide

Alright, let's get to the good stuff—actually writing code that does something useful.

### Document Copying Feature (The Foundation)

#### Why Copy Documents First?

You might be wondering: "Why do I need to copy documents? Can't I just watermark the originals?" Well, you *could*, but here's why you probably shouldn't:

- **Safety First**: Always work with copies to avoid accidentally corrupting original files
- **Version Management**: Keep originals pristine while creating watermarked versions
- **Audit Trails**: Maintain both watermarked and non-watermarked versions for comparison
- **Workflow Integration**: Many document systems require separate originals and processed versions

#### Step-by-Step Implementation

Let's start with the copying part. This is straightforward .NET file I/O—nothing fancy, but crucial for a safe workflow.

**1. Define File Paths**

First, set up your source and destination paths. I'm using `Path.Combine` here because it handles path separators automatically (Windows vs. Linux/Mac compatibility—you're welcome).

```csharp
using System.IO;

string sourceFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "your_source_file.ext");
string outputFilePath = Path.Combine("YOUR_OUTPUT_DIRECTORY", Path.GetFileName(sourceFilePath));
```

**Real-World Example:**
```csharp
// More realistic paths you might use
string sourceFilePath = Path.Combine(@"C:\Documents\Originals", "Q4_Report.pdf");
string outputFilePath = Path.Combine(@"C:\Documents\Watermarked", "Q4_Report.pdf");
```

**2. Copy the Document**

Now we actually copy the file. The `File.Copy` method is built into .NET and does exactly what you'd expect:

```csharp
File.Copy(sourceFilePath, outputFilePath);
```

**What This Does:**
- Creates an exact duplicate of your source file
- Maintains all file metadata (creation date, permissions, etc.)
- Throws an exception if the destination file already exists (which is actually good—prevents accidental overwrites)

**Pro Tip**: Want to overwrite existing files? Add a third parameter:
```csharp
File.Copy(sourceFilePath, outputFilePath, overwrite: true);
```

**When to Use Overwrite:**
- Automated batch processing where you're regenerating watermarked versions
- Development and testing scenarios
- When you're absolutely sure you want to replace existing files

**When NOT to Use Overwrite:**
- Production environments where accidental overwrites could cause data loss
- When you need version history
- If multiple processes might be writing to the same location

### Document Watermarking Feature (The Main Event)

#### Why Add Watermarks Programmatically?

I mentioned this earlier, but let's dig deeper into the specific advantages:

**Consistency**: Every watermark will have the exact same font, size, position, and opacity. No human error, no "whoops, I forgot to watermark page 3."

**Scalability**: Whether you're watermarking 10 documents or 10,000, the effort is the same. Your code doesn't get tired.

**Customization**: Dynamically change watermark text based on document properties, dates, user names, or any other data you have.

**Integration**: Plug this into your existing document management system, email workflows, or content generation pipeline.

#### Step-by-Step Implementation

Now for the fun part—actually adding watermarks to your documents.

**1. Initialize Watermarker**

First, you'll create a `Watermarker` object pointed at your target file. This is the file you want to watermark (typically the copy you just made):

```csharp
using System.IO;
using GroupDocs.Watermark;

string filePath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "your_output_file.ext");
```

**Important**: Notice we're using the *output* file path here, not the source. That's because we're watermarking the copy, not the original.

**2. Create and Configure Text Watermark**

This is where you define what your watermark looks like. The `TextWatermark` class gives you control over the text content and basic styling:

```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;

TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```

**Breaking This Down:**
- `"Test watermark"`: The actual text that appears on your document
- `new Font("Arial", 12)`: Font family and size (12pt Arial in this case)

**Customization Ideas for Different Use Cases:**

For confidential documents:
```csharp
TextWatermark watermark = new TextWatermark("CONFIDENTIAL - DO NOT DISTRIBUTE", new Font("Arial", 16));
```

For draft versions:
```csharp
TextWatermark watermark = new TextWatermark($"DRAFT - {DateTime.Now:yyyy-MM-dd}", new Font("Times New Roman", 14));
```

For copyright protection:
```csharp
TextWatermark watermark = new TextWatermark("© 2025 Your Company Name", new Font("Calibri", 10));
```

**Available Fonts**: You can use any font installed on your system. Common safe choices include Arial, Times New Roman, Calibri, and Courier New. For specialized branding, install custom fonts on your server.

**3. Add Watermark to Document**

Finally, you'll apply the watermark and save the document. The `using` statement here is important—it ensures proper resource cleanup even if something goes wrong:

```csharp
using (Watermarker watermarker = new Watermarker(filePath))
{
    watermarker.Add(watermark);
    watermarker.Save();
}
```

**What Happens Here:**
1. The `Watermarker` opens your document and loads it into memory
2. The `Add()` method embeds your watermark into the document
3. The `Save()` method writes the changes back to the file
4. The `using` block ensures the `Watermarker` releases the file when done (so you don't get "file in use" errors)

**Behind the Scenes**: The library analyzes your document type (PDF, Word, Excel, etc.) and adds the watermark in a format-appropriate way. For PDFs, it's added as a content layer. For Word docs, it's added as a shape or header/footer element.

### Complete Working Example

Let me put it all together in a single, copy-paste-ready example that you can actually use:

```csharp
using System;
using System.IO;
using GroupDocs.Watermark;
using GroupDocs.Watermark.Watermarks;

class Program
{
    static void Main(string[] args)
    {
        try
        {
            // Step 1: Define paths
            string sourceFile = @"C:\Documents\Originals\Important_Report.pdf";
            string outputFile = @"C:\Documents\Watermarked\Important_Report.pdf";
            
            // Step 2: Copy the document (preserves original)
            File.Copy(sourceFile, outputFile, overwrite: true);
            
            // Step 3: Add watermark
            using (Watermarker watermarker = new Watermarker(outputFile))
            {
                TextWatermark watermark = new TextWatermark(
                    "CONFIDENTIAL", 
                    new Font("Arial", 36)
                );
                
                watermarker.Add(watermark);
                watermarker.Save();
            }
            
            Console.WriteLine("Watermark added successfully!");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

This example handles the entire workflow: copy, watermark, and save. Run this code, and you'll have a watermarked PDF ready to go.

## Common Watermarking Mistakes to Avoid

Let me save you some headaches by sharing mistakes I've seen (and made myself):

**1. Forgetting to Use `using` Statements**
```csharp
// BAD - File stays locked!
Watermarker watermarker = new Watermarker(filePath);
watermarker.Add(watermark);
watermarker.Save();
// File is still locked here!

// GOOD - File properly released
using (Watermarker watermarker = new Watermarker(filePath))
{
    watermarker.Add(watermark);
    watermarker.Save();
} // File released here automatically
```

**2. Watermarking the Original Instead of a Copy**
Always work with copies unless you have a very specific reason not to. Trust me on this—the one time you accidentally watermark your only copy of an important document, you'll wish you'd listened.

**3. Not Handling Exceptions**
File I/O can fail for countless reasons (permissions, disk space, network issues). Always wrap your code in try-catch blocks:

```csharp
try
{
    // Your watermarking code
}
catch (IOException ex)
{
    Console.WriteLine($"File error: {ex.Message}");
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine($"Permission denied: {ex.Message}");
}
```

**4. Using Tiny Fonts on Large Documents**
A 12pt watermark might look fine on a letter-size document but be invisible on a poster-size PDF. Scale your font size based on document dimensions if needed.

**5. Not Testing with Different Document Types**
PDFs behave differently than Word docs, which behave differently than PowerPoint files. Test your watermarking code with all formats you'll encounter in production.

## Troubleshooting Tips

### File Path Issues

**Problem**: "File not found" or "Path not found" errors

**Solutions:**
- Use `Path.Combine()` instead of manually concatenating strings
- Use verbatim strings (`@"C:\Path"`) to avoid escape character issues
- Verify paths exist before processing: `if (!File.Exists(sourcePath)) { /* handle error */ }`
- For relative paths, use `Path.GetFullPath()` to see the actual resolved path

**Debugging Trick:**
```csharp
Console.WriteLine($"Looking for file at: {Path.GetFullPath(sourceFilePath)}");
```

### Watermark Visibility

**Problem**: Watermark is too faint, too dark, or positioned badly

**Solutions:**
- Adjust font size based on document size (test with small and large documents)
- For PDFs with dark backgrounds, use light-colored watermarks
- For light backgrounds, use dark watermarks
- Consider opacity settings if available in advanced configurations
- Test with different fonts—some are more readable than others

**Rule of Thumb**: Your watermark should be obvious enough to serve its purpose but not so obtrusive that it makes the document unreadable.

### Performance Issues

**Problem**: Processing large files or batches is slow

**Solutions:**
- Process files in parallel when handling batches (use `Parallel.ForEach`)
- Consider processing only specific pages for very large PDFs
- Monitor memory usage—close Watermarker objects promptly
- For very large batches, implement queue-based processing

### Permission Errors

**Problem**: "Access denied" when trying to read or write files

**Solutions:**
- Ensure your application has read/write permissions for source and destination folders
- For network paths, verify network credentials
- Run your IDE as administrator during development (but fix permissions for production)
- Check if files are locked by other processes (open in Adobe Reader, for example)

## Real-World Use Cases by Industry

Let me show you how different industries use this in practice:

### Legal Firms
**Scenario**: Watermarking client documents with case numbers and confidentiality notices

```csharp
string caseNumber = "2025-CV-12345";
string watermarkText = $"ATTORNEY-CLIENT PRIVILEGED\nCase: {caseNumber}";
TextWatermark watermark = new TextWatermark(watermarkText, new Font("Arial", 14));
```

**Why It Matters**: Legal documents are highly sensitive. Automated watermarking ensures every page is marked correctly, reducing liability.

### Marketing Agencies
**Scenario**: Adding "PREVIEW" watermarks to client presentations before final approval

```csharp
string watermarkText = $"PREVIEW - NOT FOR DISTRIBUTION\n{DateTime.Now:MM/dd/yyyy}";
TextWatermark watermark = new TextWatermark(watermarkText, new Font("Arial", 24));
```

**Why It Matters**: Prevents clients from using draft materials in production, protects work-in-progress.

### Financial Services
**Scenario**: Watermarking quarterly reports with version numbers and timestamps

```csharp
string version = "v2.3";
string watermarkText = $"Internal Use Only - {version}\nGenerated: {DateTime.Now:yyyy-MM-dd HH:mm}";
TextWatermark watermark = new TextWatermark(watermarkText, new Font("Courier New", 10));
```

**Why It Matters**: Compliance and audit trails. Knowing exactly which version of a report was distributed is crucial.

### Educational Institutions
**Scenario**: Watermarking exam papers and course materials with student names

```csharp
string studentName = "John Smith";
string watermarkText = $"Licensed to: {studentName}\n© 2025 University Name";
TextWatermark watermark = new TextWatermark(watermarkText, new Font("Times New Roman", 12));
```

**Why It Matters**: Prevents unauthorized distribution of course materials, protects intellectual property.

## Watermark Best Practices

**Design Guidelines:**
1. **Visibility vs. Readability**: Make watermarks visible but not distracting
2. **Consistent Placement**: Same position across all documents (or use smart positioning based on content)
3. **Professional Fonts**: Stick to clean, professional fonts for business documents
4. **Dynamic Content**: Include dates, version numbers, or user names when relevant

**Technical Best Practices:**
1. **Always Work with Copies**: Preserve originals
2. **Implement Error Handling**: Wrap I/O operations in try-catch blocks
3. **Use Resource Management**: Properly dispose of Watermarker objects with `using` statements
4. **Test Across Formats**: Don't assume PDF watermarking works the same as Word
5. **Validate Input**: Check that source files exist before processing

**Performance Optimization:**
1. **Batch Processing**: Group similar operations together
2. **Parallel Processing**: Use multi-threading for large batches (with care)
3. **Memory Management**: Don't keep too many documents open simultaneously
4. **Progress Tracking**: Implement logging for long-running batch jobs

## Practical Applications

### Batch Processing Multiple Documents

Want to watermark an entire folder? Here's a simple batch processing example:

```csharp
string[] files = Directory.GetFiles(@"C:\Documents\Originals", "*.pdf");

foreach (string file in files)
{
    string outputFile = file.Replace("Originals", "Watermarked");
    File.Copy(file, outputFile, overwrite: true);
    
    using (Watermarker watermarker = new Watermarker(outputFile))
    {
        TextWatermark watermark = new TextWatermark("CONFIDENTIAL", new Font("Arial", 24));
        watermarker.Add(watermark);
        watermarker.Save();
    }
    
    Console.WriteLine($"Processed: {Path.GetFileName(file)}");
}
```

### Integrating with Document Management Systems

If you're using a DMS like SharePoint, Alfresco, or a custom system, you can hook watermarking into your document upload or approval workflows:

**Trigger Points:**
- When a document is uploaded
- When a document status changes (e.g., "Draft" to "Final")
- When a document is requested for download
- On a scheduled basis (nightly batch processing)

### Automated Workflow Integration

Here's a conceptual example of integrating watermarking into a document approval workflow:

```csharp
public void ProcessDocumentApproval(string documentId, ApprovalStatus status)
{
    // Fetch document from your system
    string sourcePath = GetDocumentPath(documentId);
    string tempPath = CreateTempCopy(sourcePath);
    
    // Add status-based watermark
    string watermarkText = status switch
    {
        ApprovalStatus.Draft => "DRAFT - NOT APPROVED",
        ApprovalStatus.UnderReview => "UNDER REVIEW",
        ApprovalStatus.Approved => $"APPROVED - {DateTime.Now:yyyy-MM-dd}",
        _ => "INTERNAL USE ONLY"
    };
    
    using (Watermarker watermarker = new Watermarker(tempPath))
    {
        TextWatermark watermark = new TextWatermark(watermarkText, new Font("Arial", 18));
        watermarker.Add(watermark);
        watermarker.Save();
    }
    
    // Save back to your system
    UpdateDocument(documentId, tempPath);
}
```

## Performance Considerations

### Resource Usage

**Memory Footprint:**
- Each `Watermarker` instance loads the entire document into memory
- For large files (100MB+), this can be significant
- Solution: Process files sequentially rather than loading many simultaneously

**CPU Usage:**
- Watermarking is relatively CPU-intensive, especially for large PDFs
- Multiple complex watermarks compound the issue
- Solution: Use background workers or separate service processes for heavy processing

**Disk I/O:**
- Copying files and reading/writing documents creates disk activity
- For network storage, this can introduce latency
- Solution: Consider local temp storage for processing, then copy to network

### Best Practices for Large-Scale Operations

**1. Implement Queuing:**
```csharp
// Pseudo-code concept
Queue<string> filesToProcess = GetPendingDocuments();
ProcessQueue(filesToProcess, maxConcurrency: 4);
```

**2. Use Progress Tracking:**
```csharp
int total = files.Length;
int processed = 0;

foreach (string file in files)
{
    // Process file...
    processed++;
    Console.WriteLine($"Progress: {processed}/{total} ({(processed * 100.0 / total):F1}%)");
}
```

**3. Implement Retry Logic:**
```csharp
int maxRetries = 3;
for (int attempt = 0; attempt < maxRetries; attempt++)
{
    try
    {
        // Watermarking code
        break; // Success!
    }
    catch (IOException)
    {
        if (attempt == maxRetries - 1) throw;
        Thread.Sleep(1000); // Wait before retry
    }
}
```

**4. Monitor and Log:**
- Track processing times for performance analysis
- Log errors for troubleshooting
- Monitor memory usage to prevent out-of-memory errors
- Set up alerts for failures in production

## Conclusion

And there you have it—everything you need to implement professional document watermarking in your .NET applications. Let's recap the key takeaways:

**What We Covered:**
- How to copy documents safely before watermarking
- Adding text watermarks to PDFs and other formats using C#
- Real-world use cases across different industries
- Troubleshooting common issues and performance optimization
- Batch processing and workflow integration strategies

**The Bottom Line**: Programmatic watermarking isn't just a time-saver—it's a necessity for any organization handling sensitive or valuable documents at scale. The initial setup takes minutes, but the benefits (consistency, speed, automation) compound over time.

**Next Steps:**
1. Install GroupDocs.Watermark and try the basic examples
2. Test with your actual document types (PDF, Word, Excel, etc.)
3. Build a simple batch processing script for your use case
4. Integrate into your existing workflows or document management system
5. Explore advanced features like image watermarks, positioning, and opacity control

**Ready to Level Up?**
- Explore image-based watermarks (logos, stamps)
- Learn about watermark positioning and rotation
- Implement advanced customization (opacity, colors, multiple watermarks)
- Check out format-specific features (PDF layers, Word headers)

Start protecting your documents today—your future self will thank you when you're not manually watermarking documents at 2 AM before a deadline!

## FAQ Section

**1. What is GroupDocs.Watermark for .NET?**  
GroupDocs.Watermark is a powerful library that lets you add watermarks to various file formats (PDF, Word, Excel, PowerPoint, images) in .NET applications. It handles the complexity of different file formats so you don't have to.

**2. How do I install GroupDocs.Watermark?**  
Use NuGet Package Manager or run `dotnet add package GroupDocs.Watermark` in your terminal. It's that simple—no manual DLL references or complex configuration needed.

**3. Can I use GroupDocs.Watermark for free?**  
Yes and no. There's a free trial for testing and evaluation. For production use, you'll need a license. You can get a temporary license from their [licensing page](https://purchase.groupdocs.com/temporary-license/) to fully evaluate it before purchasing.

**4. What file formats does GroupDocs.Watermark support?**  
Tons! PDFs, Microsoft Office files (Word, Excel, PowerPoint), images (JPG, PNG, TIFF), Visio diagrams, and many more. Check their documentation for the complete list—it's extensive.

**5. Can I watermark multiple documents at once?**  
Absolutely! Just loop through your files and apply watermarks. For better performance with large batches, consider parallel processing with `Parallel.ForEach`.

**6. How do I make my watermarks more visible?**  
Increase font size, use bold fonts, choose high-contrast colors relative to your document background, and consider opacity settings. Test with actual documents to find the sweet spot.

**7. Will watermarks affect document file size?**  
Slightly, yes. Text watermarks add minimal overhead (a few KB). Image watermarks can add more depending on image complexity and size, but it's usually not significant.

**8. Can I remove watermarks later?**  
That depends on how they were added. Watermarks added by GroupDocs.Watermark can potentially be detected and removed by the same library (if you have the original document type). This is why working with copies is important.

**9. Does this work with .NET Core and .NET 5/6/7/8?**  
Yes! GroupDocs.Watermark supports .NET Framework, .NET Core, and modern .NET versions. Check the package documentation for specific version compatibility.

**10. What's the performance like for large files?**  
Depends on file size and complexity. Small to medium files (under 10MB) process in seconds. Larger files (50MB+) take longer but are still reasonable. For massive files or high-volume scenarios, implement queuing and background processing.

## Resources

Here's everything you need to go deeper:

**Documentation:**
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/net/) - Comprehensive guide with examples
- [API Reference](https://reference.groupdocs.com/watermark/net) - Complete API documentation
- [Download Page](https://releases.groupdocs.com/watermark/net/) - Get the latest version

**Support and Community:**
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/) - Ask questions, get help from the community
- [Temporary License](https://purchase.groupdocs.com/temporary-license/) - Evaluate all features before buying

