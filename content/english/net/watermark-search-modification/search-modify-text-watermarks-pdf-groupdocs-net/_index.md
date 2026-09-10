---
title: "Modify PDF Watermarks in .NET - Complete Search & Replace"
linktitle: "Modify PDF Watermarks .NET"
description: "Learn how to find and replace text watermarks in PDFs using C#. Complete guide with code examples for bulk editing, rebranding, and automating watermark updates."
keywords: "modify PDF watermarks .NET, remove text watermarks PDF programmatically, PDF watermark editor C#, change watermark text in PDF, bulk edit PDF watermarks"
date: "2025-01-02"
lastmod: "2025-01-02"
weight: 1
url: "/net/watermark-search-modification/search-modify-text-watermarks-pdf-groupdocs-net/"
categories: ["PDF Processing"]
tags: ["watermarks", "pdf-editing", "groupdocs", "csharp", "document-automation"]
type: docs
---

# Modify PDF Watermarks in .NET - Complete Search & Replace

## Introduction

Picture this: Your company just rebranded, and you've got 500 PDFs with the old logo watermark. Manually opening each one? That's a nightmare. Or maybe you're dealing with confidential documents that need their security levels updated across dozens of files. Sound familiar?

Here's the good news—you don't need to touch each file individually. With GroupDocs.Watermark for .NET, you can programmatically search for specific text watermarks in your PDFs and modify them in bulk. Whether you're updating copyright notices, changing security classifications, or swapping out old branding, this guide will show you exactly how to do it.

**What You'll Master:**
- Setting up your .NET project with GroupDocs.Watermark (it's easier than you think)
- Finding specific text watermarks across multiple pages
- Modifying watermark content programmatically
- Avoiding common mistakes that trip up developers
- Knowing when this approach saves time (and when it doesn't)

Ready to automate your PDF watermark workflow? Let's dive in.

## Why This Matters

Before we get into the code, let's talk about why you'd want to do this in the first place.

### Real-World Scenarios

**1. Corporate Rebranding**  
Your marketing team changed the company tagline. Now you've got thousands of PDFs with the old version watermarked across contracts, proposals, and presentations. Manually updating them? Not happening.

**2. Document Security Management**  
Confidential documents need their classification levels updated (think "DRAFT" to "APPROVED" or "Internal Use" to "Public"). You need to change these watermarks across entire document sets while maintaining audit trails.

**3. Compliance and Legal Updates**  
Copyright notices need annual updates. Legal disclaimers change. Instead of recreating documents, you can surgically update just the watermarks.

**4. Batch Processing Automation**  
You're building a document management system that needs to automatically process uploaded PDFs—adding, modifying, or removing watermarks based on business rules.

**The Bottom Line:** Manual watermark editing doesn't scale. Programmatic modification does. And with .NET, you can integrate this into your existing workflows seamlessly.

## Prerequisites

Before we start coding, make sure you've got these bases covered:

- **GroupDocs.Watermark library** (version 23.1 or later—earlier versions might work, but why risk it?)
- **A .NET development environment** (Visual Studio, Rider, or even VS Code with the right extensions)
- **Basic C# knowledge** (if you can write a for-loop and understand try-catch blocks, you're golden)
- **A sample PDF** (preferably one with text watermarks you can experiment on—don't use production files while learning!)

**Pro Tip:** Start with a test environment. Copy some sample PDFs to a dedicated folder so you can experiment without worrying about breaking anything important.

## Setting Up GroupDocs.Watermark for .NET

### Installation (Choose Your Method)

Getting GroupDocs.Watermark into your project is straightforward. Pick whichever method matches your workflow:

**.NET CLI** (if you're a terminal person)
```bash
dotnet add package GroupDocs.Watermark
```

**Package Manager Console** (for Visual Studio fans)
```powershell
Install-Package GroupDocs.Watermark
```

**NuGet Package Manager UI** (the point-and-click approach)
1. Right-click your project → Manage NuGet Packages
2. Search for "GroupDocs.Watermark"
3. Click Install on the latest stable version

**What Just Happened?** You've added the GroupDocs.Watermark library to your project. This gives you access to all the watermark manipulation classes and methods we'll use throughout this guide.

### License Acquisition

Here's the deal with licensing:

**Free Trial:** Start here. You get full functionality for evaluation purposes. Perfect for testing and learning. Grab it from [GroupDocs Downloads](https://releases.groupdocs.com/watermark/net/).

**Temporary License:** Need more time to evaluate? Get a 30-day temporary license [here](https://purchase.groupdocs.com/temporary-license/). No watermarks on output, full feature access.

**Commercial License:** For production use, you'll need to purchase a license from [GroupDocs Purchase](https://purchase.groupdocs.com/). They've got different tiers depending on your needs.

**Important:** The trial version adds a watermark to your output files. For testing search and modification logic, that's fine. For production? You'll need a real license.

### Basic Initialization and Setup

Alright, let's write some code. First, you'll need to import the necessary namespace:

```csharp
using GroupDocs.Watermark;
using GroupDocs.Watermark.Search;
using System.Collections.Generic;
```

**Why these namespaces?**
- `GroupDocs.Watermark` - Core functionality for document loading and manipulation
- `GroupDocs.Watermark.Search` - Search-specific classes like `TextSearchCriteria`
- `System.Collections.Generic` - We'll use `List<int>` for page specifications

Now, let's create a `Watermarker` instance (this is your main tool for interacting with PDFs):

```csharp
// Replace "YOUR_DOCUMENT_DIRECTORY" with your actual path
// Pro tip: Use Path.Combine() to avoid hardcoding paths
string documentPath = "YOUR_DOCUMENT_DIRECTORY/document.pdf";

// Initialize the Watermarker - this loads your PDF into memory
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // We'll add our watermark operations here
    // The 'using' statement ensures proper resource cleanup
}
```

**What's Happening Here:**
1. We're using a `using` statement (important!) to ensure the `Watermarker` object gets disposed properly
2. The `Watermarker` constructor loads your PDF and prepares it for watermark operations
3. All subsequent operations happen within this context

**Common Mistake:** Forgetting the `using` statement can lead to file locks and memory leaks. Always wrap `Watermarker` instances in `using` blocks.

## Implementation Guide

Now for the fun part—let's actually search for and modify some watermarks.

### Searching for Text Watermarks

You can't modify what you can't find. This section shows you how to pinpoint exactly which watermarks you want to change.

#### Overview

Think of watermark searching like using Ctrl+F in a document, except you're searching specifically for watermark elements (not just any text). You can target specific pages, use exact or fuzzy matching, and retrieve all matching watermarks for modification.

#### Step-by-Step Implementation

**Step 1: Define Your Search Criteria**

This is where you tell GroupDocs *what* you're looking for and *where* to look:

```csharp
string documentPath = "YOUR_DOCUMENT_DIRECTORY/document.pdf";

// Create search criteria - this is like your watermark "filter"
TextSearchCriteria searchCriteria = new TextSearchCriteria("test", false) 
{
    // Specify exact pages to search (optional - omit to search entire document)
    Pages = new List<int> { 1, 3 } // Only check pages 1 and 3
};
```

**Breaking This Down:**
- `"test"` - The text you're searching for in watermarks
- `false` - Case-insensitive search (true would be case-sensitive)
- `Pages = new List<int> { 1, 3 }` - Only search pages 1 and 3

**Why specify pages?** Performance. If you know your watermarks are only on certain pages (like a title page or cover sheet), there's no point scanning the entire document. This is especially important with large PDFs.

**When NOT to specify pages:** If you're unsure where watermarks appear, omit the `Pages` property entirely:
```csharp
TextSearchCriteria searchCriteria = new TextSearchCriteria("test", false);
// This searches the entire document
```

**Step 2: Execute the Search**

Now let's actually find those watermarks. Here's a reusable method pattern you can adapt:

```csharp
public PossibleWatermarkCollection GetWatermarks(string documentPath, TextSearchCriteria searchCriteria)
{
    // Load the document
    using (Watermarker watermarker = new Watermarker(documentPath))
    {
        // Search returns a collection of potential watermarks
        PossibleWatermarkCollection watermarks = watermarker.Search(searchCriteria);
        
        return watermarks;
    }
}

// Usage:
PossibleWatermarkCollection watermarks = GetWatermarks(documentPath, searchCriteria);

Console.WriteLine($"Found {watermarks.Count} watermarks matching your criteria");
```

**What's a "Possible" Watermark?** GroupDocs uses the term "possible" because not everything that looks like a watermark technically is one. The library identifies elements that *could* be watermarks based on their properties. This is actually helpful—you get to decide which ones to modify.

**Pro Tip:** Always check `watermarks.Count` before proceeding. If it's zero, either your search criteria don't match anything, or there are no watermarks on the specified pages.

### Modifying Found Watermarks

Found your watermarks? Great. Now let's change them.

#### Overview

Modification is straightforward: loop through the found watermarks and update their properties. You can change text, formatting, position—pretty much anything about the watermark.

#### Implementation

**Step 1: Set Up Your Output Path**

First, decide where the modified PDF should go:

```csharp
// Always save to a NEW file - never overwrite your source during testing
string outputFileName = "YOUR_OUTPUT_DIRECTORY/modified_document.pdf";

// Pro tip: Add timestamps for testing
// string outputFileName = $"YOUR_OUTPUT_DIRECTORY/modified_{DateTime.Now:yyyyMMdd_HHmmss}.pdf";
```

**Why save to a new file?** Until you're 100% confident in your code, don't overwrite originals. You'll thank me later.

**Step 2: Modify and Save**

Here's where the magic happens:

```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Get your watermarks using the search method from earlier
    PossibleWatermarkCollection watermarks = watermarker.Search(searchCriteria);
    
    Console.WriteLine($"Processing {watermarks.Count} watermarks...");
    
    // Loop through each found watermark
    foreach (PossibleWatermark watermark in watermarks) 
    {
        try 
        {
            // Update the watermark text
            watermark.Text = "passed";
            
            // You can also modify other properties:
            // watermark.ForegroundColor = Color.Red;
            // watermark.BackgroundColor = Color.Yellow;
            // watermark.RotateAngle = 45;
            
            Console.WriteLine("Successfully modified watermark");
        } 
        catch (Exception e) 
        {
            // Some watermarks might be read-only or locked
            // Handle gracefully instead of crashing
            Console.WriteLine($"Couldn't modify watermark: {e.Message}");
        }
    }
    
    // Save changes to the new file
    watermarker.Save(outputFileName);
    
    Console.WriteLine($"Modified document saved to: {outputFileName}");
}
```

**Key Points:**

1. **The try-catch block is crucial** - Not all watermarks can be modified (some might be part of the PDF structure itself). Catch exceptions to avoid crashing your entire process.

2. **You can modify multiple properties** - Text is just the start. Change colors, rotation, opacity—whatever makes sense for your use case.

3. **Changes aren't saved until you call `Save()`** - You can modify as many watermarks as you want, but nothing hits the file until that final save call.

**Real-World Example:**  
Let's say you're updating security classifications. Here's how you might handle multiple types:

```csharp
foreach (PossibleWatermark watermark in watermarks) 
{
    try 
    {
        // Check current classification and update accordingly
        if (watermark.Text.Contains("DRAFT"))
        {
            watermark.Text = "APPROVED";
            watermark.ForegroundColor = Color.Green;
        }
        else if (watermark.Text.Contains("CONFIDENTIAL"))
        {
            watermark.Text = "PUBLIC";
            watermark.ForegroundColor = Color.Blue;
        }
    } 
    catch (Exception e) 
    {
        Console.WriteLine($"Skipped watermark: {e.Message}");
    }
}
```

### Troubleshooting Tips

Here are the gotchas I've learned the hard way (so you don't have to):

**Problem: No watermarks found**
- **Check your search text** - Typos happen. If you're searching for "test" but the watermark says "Test", and you're using case-sensitive search, you'll get zero results.
- **Verify page numbers** - Remember, PDF pages are 1-indexed. Page 1 is the first page, not page 0.
- **Confirm watermarks exist** - Open the PDF manually and verify the text you're searching for actually appears as a watermark (not just regular text).

**Problem: "Access Denied" or file lock errors**
- **Close the PDF** - If you have the file open in Adobe Reader or another viewer, you can't modify it. Close all instances.
- **Check file permissions** - Make sure your application has read/write access to both the source and output directories.
- **Use `using` statements** - They ensure files get closed properly even if exceptions occur.

**Problem: Changes aren't saving**
- **Verify output path exists** - If the directory doesn't exist, the save will fail. Create it first if needed.
- **Don't overwrite during testing** - Always save to a different filename until you're confident in your code.
- **Check exception messages** - Wrap your save call in try-catch to see what's actually failing.

**Problem: Performance is slow**
- **Narrow your search** - If you're searching the entire document but only need specific pages, specify them in `Pages`.
- **Process in batches** - For hundreds of PDFs, process them in groups rather than all at once.
- **Use async methods if available** - For web applications, consider async/await patterns to avoid blocking.

## Common Pitfalls to Avoid

These are mistakes I see developers make repeatedly. Learn from their pain:

### 1. Not Handling Non-Text Watermarks

**The Problem:** You search for text watermarks, but the PDF has image-based watermarks. Your search returns nothing.

**The Fix:** If you need to handle both, you'll need separate search operations:
```csharp
// Search for text watermarks
TextSearchCriteria textCriteria = new TextSearchCriteria("logo");
var textWatermarks = watermarker.Search(textCriteria);

// For image watermarks, use ImageSearchCriteria (different approach)
// This guide focuses on text, but be aware of the limitation
```

### 2. Assuming All "Text" is Editable

**The Problem:** Some watermarks are baked into the PDF as immutable objects. You'll get an exception when trying to modify them.

**The Fix:** Always use try-catch blocks and handle exceptions gracefully. Log which watermarks couldn't be modified for manual review.

### 3. Not Testing with Production-Like PDFs

**The Problem:** Your code works great on your simple test PDF, then fails on the client's 200-page encrypted PDF with custom fonts.

**The Fix:** Test with realistic documents—large files, secured PDFs, documents with unusual formatting. You'll discover issues in testing instead of production.

### 4. Hardcoding Paths

**The Problem:** Your code works on your machine but fails everywhere else because paths are hardcoded.

**The Fix:**
```csharp
// Instead of this:
string path = "C:\\Users\\YourName\\Documents\\test.pdf";

// Do this:
string path = Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Documents", "test.pdf");
// Or use configuration files/environment variables
```

### 5. Forgetting About Licensing in Production

**The Problem:** Your trial license expires, or you forget to apply your commercial license, and suddenly your app stops working.

**The Fix:** Implement proper license handling early:
```csharp
// Apply license at application startup
try
{
    License license = new License();
    license.SetLicense("path-to-your-license-file.lic");
}
catch (Exception ex)
{
    Console.WriteLine($"License error: {ex.Message}");
    // Handle gracefully - maybe run in trial mode with user notification
}
```

## When to Use This Approach

Not every watermark problem needs GroupDocs. Here's when this solution shines (and when it doesn't):

### Perfect Use Cases

✅ **Bulk Updates Across Multiple Documents**  
You need to change the same watermark in 50+ PDFs. Manual editing? Forget it. This approach processes them all in minutes.

✅ **Automated Document Workflows**  
You're building a system where uploaded PDFs automatically get watermarks added, modified, or removed based on business rules. This integrates seamlessly.

✅ **Regular, Predictable Changes**  
Quarterly copyright updates, monthly security classification reviews—anything that happens repeatedly on a schedule is perfect for automation.

✅ **Integration with Existing .NET Systems**  
You're already working in a .NET environment and need watermark functionality. Adding this library is straightforward.

### When to Consider Alternatives

❌ **One-Off Manual Changes**  
If you're only modifying watermarks in a single PDF once, Adobe Acrobat might be faster. The code overhead isn't worth it.

❌ **Complex Graphical Watermarks**  
If your watermarks involve intricate designs, gradients, or multiple overlapping elements, you might need more specialized tools or manual intervention.

❌ **Real-Time, High-Volume Processing**  
If you need to process thousands of PDFs per minute, you'll need distributed processing infrastructure beyond just this library (though the library itself can be part of the solution).

❌ **When You Don't Control the PDF Source**  
If users are uploading PDFs with vastly different structures and watermark types, you'll need robust error handling and possibly fallback options.

**The Bottom Line:** Use this approach when automation saves time and effort. If manual intervention is quicker or the task is a one-time thing, don't over-engineer it.

## Practical Applications

Let's talk real implementations—scenarios where developers have successfully used this approach:

### 1. Marketing Department Automation

**Scenario:** A marketing agency needed to update promotional PDFs every quarter with new campaign watermarks.

**Solution:** They built a console app that:
- Scans a designated folder for all PDFs
- Searches for watermarks containing "Campaign"
- Replaces them with the current quarter's campaign text
- Saves modified files to an output folder

**Result:** What used to take a designer 2 days now happens automatically in under 10 minutes.

### 2. Legal Document Management

**Scenario:** Law firm needed to update document status watermarks ("DRAFT" → "FINAL") across hundreds of contracts.

**Solution:** Integrated GroupDocs into their document management system so attorneys could:
- Select multiple documents in the web interface
- Click "Update Status"
- System automatically searches and modifies watermarks
- Maintains audit trail of changes

**Result:** Reduced manual errors and cut document finalization time by 75%.

### 3. Corporate Rebranding Project

**Scenario:** Company rebranded with new name and logo. Had 2000+ PDFs with old watermarks across SharePoint libraries.

**Solution:** Custom PowerShell script using GroupDocs:
```csharp
// Pseudo-code pattern they used:
foreach (var pdf in SharePointLibrary.GetAllPDFs())
{
    SearchAndReplace(pdf, "OldCompanyName", "NewCompanyName");
    UpdateLogoWatermark(pdf, newLogoImage);
    SaveAndUpload(pdf);
}
```

**Result:** Entire rebranding completed over a weekend instead of months of manual work.

### 4. Government Document Classification

**Scenario:** Government agency needed to regularly update security classification watermarks on thousands of declassified documents.

**Solution:** Automated pipeline that:
- Reads classification updates from database
- Processes PDFs in batches
- Updates watermarks based on new classifications
- Generates reports for manual review of exceptions

**Result:** Improved compliance and freed staff to focus on actual document review instead of watermark updates.

## Performance Considerations

Let's talk speed and efficiency. Here's what actually impacts performance:

### What Makes Processing Slow

**1. Document Size**
- Large PDFs (100+ pages) take longer to load and process
- PDFs with many images/graphics are slower than text-only

**2. Number of Watermarks**
- More watermarks = more search/modify operations
- Each watermark modification requires processing time

**3. Search Scope**
- Searching entire documents vs. specific pages
- Case-sensitive searches are slightly faster than case-insensitive

### Optimization Strategies

**1. Be Specific with Page Numbers**
```csharp
// Slower: Search entire 200-page document
var criteria = new TextSearchCriteria("test");

// Faster: Target known watermark locations
var criteria = new TextSearchCriteria("test") 
{ 
    Pages = new List<int> { 1, 2, 200 } // Only cover pages, first/last pages
};
```

**2. Batch Processing Pattern**
```csharp
// Instead of processing 1000 PDFs simultaneously (high memory usage):
var batches = files.Chunk(10); // Process 10 at a time

foreach (var batch in batches)
{
    Parallel.ForEach(batch, file => 
    {
        ProcessWatermarks(file);
    });
}
```

**3. Dispose Resources Promptly**
```csharp
// Good: Resources freed immediately after use
using (Watermarker watermarker = new Watermarker(path))
{
    // Process watermarks
    watermarker.Save(outputPath);
} // Disposed here, memory freed

// Bad: Resources held for no reason
var watermarker = new Watermarker(path);
// ... long processing ...
// Watermarker still in memory, file locked
```

**4. Use Async for Web Applications**
```csharp
// In ASP.NET applications, don't block the request thread
public async Task<IActionResult> ProcessDocument(string filePath)
{
    return await Task.Run(() => 
    {
        // CPU-bound work on thread pool
        SearchAndModifyWatermarks(filePath);
        return Ok();
    });
}
```

### Performance Expectations

Based on typical scenarios (your mileage may vary):

| Document Type | Processing Time | Notes |
|--------------|----------------|-------|
| Small PDF (1-10 pages, few watermarks) | <1 second | Nearly instant |
| Medium PDF (50 pages, multiple watermarks) | 2-5 seconds | Acceptable for most use cases |
| Large PDF (200+ pages, many watermarks) | 10-30 seconds | Consider background processing |
| Batch (100 PDFs) | 5-15 minutes | Depends on batch size and parallelization |

**Pro Tip:** For large-scale batch processing, consider implementing progress reporting so users know the system is working:
```csharp
for (int i = 0; i < files.Count; i++)
{
    ProcessWatermarks(files[i]);
    Console.WriteLine($"Progress: {i + 1}/{files.Count} ({(i + 1) * 100 / files.Count}%)");
}
```

## Conclusion

You've now got everything you need to programmatically search and modify text watermarks in PDFs using GroupDocs.Watermark for .NET. Whether you're updating copyright notices across hundreds of documents, changing security classifications, or handling corporate rebranding, you can automate the entire process.

**Key Takeaways:**
- Use `TextSearchCriteria` to target specific watermarks (be as specific as possible for better performance)
- Always wrap modifications in try-catch blocks (not all watermarks are editable)
- Specify page numbers when you know where watermarks appear (massive speed boost on large PDFs)
- Save to a new file during testing (never overwrite originals until you're confident)
- Consider the use case before automating (one-off tasks might be faster manually)

**Next Steps:**
1. Grab a trial license from [GroupDocs](https://releases.groupdocs.com/watermark/net/)
2. Test with a sample PDF from your actual use case
3. Build out error handling for production scenarios
4. Explore the [documentation](https://docs.groupdocs.com/watermark/net/) for advanced features (like image watermarks, different file formats, or watermark positioning)

Ready to automate your watermark workflows? Start experimenting with the code examples in this guide—adjust them to your specific needs and see how much time you can save.

**Questions or issues?** Head over to the [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/) for community support.

## FAQ Section

**1. Can I modify image-based watermarks, or just text?**  
This guide focuses on text watermarks, but GroupDocs.Watermark supports image watermarks too. You'll use `ImageSearchCriteria` instead of `TextSearchCriteria`. The modification process is similar—search, modify properties (like opacity or rotation), save. Check the [API documentation](https://reference.groupdocs.com/watermark/net) for image-specific examples.

**2. What if I need to remove watermarks entirely instead of modifying them?**  
Use the `Remove()` method on the watermark collection:
```csharp
PossibleWatermarkCollection watermarks = watermarker.Search(searchCriteria);
watermarks.Clear(); // Removes all found watermarks
watermarker.Save(outputPath);
```
Just be cautious—this is permanent once you save. Test thoroughly before running on production files.

**3. How do I handle PDFs that are password-protected?**  
You'll need to provide the password when creating the `Watermarker`:
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your_password" };
using (Watermarker watermarker = new Watermarker(path, loadOptions))
{
    // Process as normal
}
```
If you don't have the password, you can't programmatically access the watermarks (which is the whole point of password protection).

**4. Can this work with other document formats besides PDF?**  
Absolutely. GroupDocs.Watermark supports Word, Excel, PowerPoint, images (PNG, JPG), and more. The code structure is nearly identical—just pass in a .docx or .xlsx file instead of a .pdf. The library handles the format differences for you.

**5. What happens if my search finds no watermarks?**  
The `Search()` method returns an empty `PossibleWatermarkCollection` (not null). Check `watermarks.Count` before proceeding:
```csharp
if (watermarks.Count == 0)
{
    Console.WriteLine("No watermarks found matching criteria");
    return; // Exit early, nothing to modify
}
```
This isn't an error—it just means your search criteria didn't match any watermarks.

**6. How do I handle watermarks on specific positions (like top-right corner only)?**  
Combine text search with position filtering:
```csharp
var watermarks = watermarker.Search(textCriteria);
var topRightWatermarks = watermarks.Where(w => 
    w.X > pageWidth * 0.7 && // Right side
    w.Y < pageHeight * 0.3    // Top section
);
```
You'll need to determine page dimensions first, but this lets you target watermarks by location, not just text content.

**7. Is there a limit to how many watermarks I can modify in one batch?**  
No hard limit from the library itself, but practical limits exist (memory, processing time). For very large batches (thousands of PDFs), process in chunks and consider background job processing so you're not blocking user interfaces.

**8. What's the licensing cost for commercial use?**  
Pricing varies based on deployment type (developer, site, OEM licenses) and support needs. Check [GroupDocs Pricing](https://purchase.groupdocs.com/) for current rates. They offer tiered options depending on whether you need one developer license or a company-wide deployment.

## Resources

**Documentation & Tools:**
- [GroupDocs Watermark .NET Documentation](https://docs.groupdocs.com/watermark/net/) - Complete reference guide
- [API Reference](https://reference.groupdocs.com/watermark/net) - Detailed class and method documentation
- [Latest Release Downloads](https://releases.groupdocs.com/watermark/net/) - Get the newest version
- [Free Trial](https://releases.groupdocs.com/watermark/net/) - Test before you buy

**Support & Community:**
- [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/) - Free community support, great for troubleshooting
- [Temporary License](https://purchase.groupdocs.com/temporary-license/) - 30-day full-featured license for evaluation
