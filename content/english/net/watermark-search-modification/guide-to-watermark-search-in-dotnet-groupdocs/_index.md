---
title: "How to Search Watermarks in PDF and Documents Using .NET"
linktitle: "Watermark Search in .NET"
description: "Learn how to detect and search watermarks programmatically in .NET with GroupDocs. Find image, text, and rotated watermarks in PDFs and documents with C# code examples."
keywords: "how to search watermarks in PDF .NET, detect watermarks programmatically C#, find image watermarks .NET, GroupDocs watermark search tutorial, verify watermark exists in PDF, watermark search by rotation angle"
weight: 1
url: "/net/watermark-search-modification/guide-to-watermark-search-in-dotnet-groupdocs/"
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["Document Processing"]
tags: ["watermark-detection", "groupdocs-net", "pdf-processing", "document-security"]
type: docs
---

# How to Search Watermarks in PDF and Documents Using .NET

## Introduction

Ever needed to verify whether your company logo appears in hundreds of PDFs? Or maybe you're building a document management system that needs to detect copyright watermarks automatically? If you're manually opening each file and squinting at watermarks, there's a better way.

Searching for watermarks programmatically sounds straightforward until you realize watermarks can be images, text, rotated at weird angles, or barely visible. That's where GroupDocs.Watermark for .NET comes in—it handles the heavy lifting so you don't have to write complex image comparison algorithms or text extraction logic from scratch.

**In this guide, you'll learn how to:**
- Detect specific image watermarks (like logos) across multiple documents
- Search for text-based watermarks containing keywords or phrases
- Find watermarks rotated at specific angles
- Combine multiple search criteria for precise watermark detection
- Handle common issues that trip up developers

By the end, you'll have practical code examples you can drop into your project today. Let's start with what you'll need to get rolling.

## Prerequisites

Before we jump into the code, make sure you've got these bases covered:

- **.NET Framework or .NET Core**: This library works with both, so you're good either way. .NET 6+ is recommended for the best performance.
- **GroupDocs.Watermark for .NET Library**: We'll show you how to install this in a moment—it's the engine that powers everything here.
- **Basic C# Knowledge**: You don't need to be a C# wizard, but understanding classes, methods, and using statements will help you follow along.
- **Sample Documents**: Have a few PDFs or Word docs with watermarks handy for testing. (Pro tip: create test files with known watermarks so you can verify your searches actually work.)

**A Quick Note on Licensing**: GroupDocs offers a free trial that's perfect for development and testing. For production use, you'll want to grab a full license to avoid any limitations. You can also get a temporary license if you need more time to evaluate.

## Setting Up GroupDocs.Watermark for .NET

### Installation (Choose Your Preferred Method)

Installing GroupDocs.Watermark is straightforward—pick whichever method fits your workflow:

**.NET CLI** (if you're a command-line person):
```bash
dotnet add package GroupDocs.Watermark
```

**Package Manager Console** (for Visual Studio users):
```powershell
Install-Package GroupDocs.Watermark
```

**NuGet Package Manager UI** (the point-and-click way):
Just search for "GroupDocs.Watermark" in the NuGet Package Manager and hit Install. Make sure you're grabbing the latest stable version.

### License Setup (Don't Skip This)

Here's the thing about licenses: the free trial is great for learning, but it adds watermarks to your output and has feature limitations. For production environments, you'll want to apply a license properly.

If you're just getting started, grab a [free trial](https://releases.groupdocs.com/watermark/net/) or request a [temporary license](https://purchase.groupdocs.com/temporary-license/) to test without restrictions.

### Basic Initialization

Once installed, you'll need this using statement at the top of your C# file:

```csharp
using GroupDocs.Watermark;
```

That's it for setup! Now let's get into the actual watermark searching.

## Understanding Watermark Search Types (And When to Use Each)

Before we dive into code, let's talk about the three main ways you can search for watermarks. Each one solves a different problem, and knowing which to use will save you headaches later.

### Image-Based Search
**When to use it**: You need to find a specific logo, stamp, or image watermark across documents. Perfect for brand protection or verifying authorized document versions.

**How it works**: Uses DCT (Discrete Cosine Transform) hashing to compare images—basically, it looks at the frequency patterns rather than exact pixels. This means it can still find your logo even if the watermark is slightly compressed or resized.

### Text-Based Search
**When to use it**: You're looking for watermarks containing specific words or phrases, like "CONFIDENTIAL," "DRAFT," or your company name.

**How it works**: Straightforward text matching. You provide a search string, and it finds watermarks containing that text.

### Rotation Angle Search
**When to use it**: You need to find watermarks rotated at specific angles—like diagonal "DRAFT" stamps or rotated logos. This is surprisingly common in legal and architectural documents.

**How it works**: Filters watermarks based on their rotation angle in degrees. You can specify a range (e.g., 30-60 degrees) to catch watermarks that aren't perfectly horizontal.

### Combined Search (The Power Move)
**When to use it**: Real-world scenarios are messy. Maybe you need to find your company logo rotated at 45 degrees with specific text nearby. Combined searches let you mix and match criteria.

Now let's see these in action with actual code.

## Implementation Guide

### How to Search for Image Watermarks in Documents

Let's start with the most common scenario: you've got a logo or image, and you need to find all documents containing that watermark. This is incredibly useful for tracking down unauthorized document copies or verifying document authenticity.

#### Step 1: Set Up Your Document and Image Paths

First, define where your target document and reference watermark image are located:

```csharp
string documentPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "example.pdf");
string logoImagePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "logo.png");

using (Watermarker watermarker = new Watermarker(documentPath))
{
    // We'll add the search logic here in the next step
}
```

**What's happening here**: The `Watermarker` class is your main entry point for all watermark operations. We're using it in a `using` statement because it implements `IDisposable`—this ensures proper cleanup of resources even if something goes wrong.

**Pro tip**: Replace `"YOUR_DOCUMENT_DIRECTORY"` with your actual paths. I know it's obvious, but you'd be surprised how many people forget this step and wonder why nothing works!

#### Step 2: Configure the Image Search Criteria

Now for the interesting part—setting up the DCT hash search:

```csharp
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(logoImagePath);
imageSearchCriteria.MaxDifference = 0.9; // Adjust based on similarity tolerance
```

**Understanding MaxDifference**: This value ranges from 0 to 1:
- **0.9 to 1.0**: Very strict matching (almost pixel-perfect)
- **0.7 to 0.9**: Moderate tolerance (catches slightly compressed or resized versions)
- **0.5 to 0.7**: Loose matching (use with caution—might catch unrelated images)

**When to adjust this**: If you're getting false positives (finding images that aren't actually your watermark), increase the value. If you're missing obvious matches, decrease it slightly.

#### Complete Example: Finding Logo Watermarks

Here's the full code to search for an image watermark and see what you found:

```csharp
string documentPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "example.pdf");
string logoImagePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "logo.png");

using (Watermarker watermarker = new Watermarker(documentPath))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(logoImagePath);
    imageSearchCriteria.MaxDifference = 0.9;
    
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(imageSearchCriteria);
    
    // Now you can iterate through found watermarks
    foreach (PossibleWatermark watermark in possibleWatermarks)
    {
        // Process each found watermark
        // (We'll cover what you can do with these in the Practical Applications section)
    }
}
```

### How to Find Text Watermarks in Your Documents

Text watermarks are everywhere—think "CONFIDENTIAL," "SAMPLE," "DRAFT," or company names stamped across pages. Here's how to find them programmatically.

#### Step 1: Define What Text You're Looking For

This one's simpler than image searches:

```csharp
string searchText = "Company Name";
TextSearchCriteria textSearchCriteria = new TextSearchCriteria(searchText);
```

**Important note**: The search is case-sensitive by default. If you're looking for "DRAFT" but the watermark says "Draft," you won't find it. Keep this in mind when troubleshooting (we'll cover how to handle this in the Common Issues section).

**Real-world tip**: If you're building a system that needs to catch variations (like "Company Name," "CompanyName," or "COMPANY NAME"), you'll need to run multiple searches or preprocess the text. There's no built-in fuzzy matching here.

#### Complete Example: Finding Text Watermarks

Here's how to search for text watermarks and work with the results:

```csharp
string documentPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "example.pdf");
string searchText = "Company Name";

using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria(searchText);
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(textSearchCriteria);
    
    if (possibleWatermarks.Count > 0)
    {
        Console.WriteLine($"Found {possibleWatermarks.Count} watermark(s) containing '{searchText}'");
    }
    else
    {
        Console.WriteLine($"No watermarks found with text '{searchText}'");
    }
}
```

### Searching for Watermarks by Rotation Angle

This is one of those features you don't think you need until you desperately need it. Rotated watermarks are common in legal documents, architectural drawings, and scanned files. Here's how to find them.

#### Understanding Rotation Angles

Rotation angles in GroupDocs work like this:
- **0 degrees**: Horizontal (normal orientation)
- **90 degrees**: Vertical (rotated clockwise)
- **45 degrees**: Diagonal (think classic "DRAFT" stamps)
- **Negative values**: Counter-clockwise rotation

#### Step 1: Set Your Angle Range

You typically want to search within a range rather than an exact angle, because watermarks might be rotated at 44.7 degrees instead of exactly 45:

```csharp
int minAngle = 30;
int maxAngle = 60;

RotateAngleSearchCriteria rotateAngleSearchCriteria = new RotateAngleSearchCriteria(minAngle, maxAngle);
```

**When to use this**: If you know your watermarks are diagonally placed (common for "CONFIDENTIAL" stamps), use a range like 30-60 degrees. For vertical text, try 80-100 degrees.

**Complete Example with Context**:

```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Looking for watermarks rotated between 30-60 degrees
    // (typical for diagonal "DRAFT" or "CONFIDENTIAL" stamps)
    RotateAngleSearchCriteria rotateAngleSearchCriteria = new RotateAngleSearchCriteria(30, 60);
    
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(rotateAngleSearchCriteria);
    
    Console.WriteLine($"Found {possibleWatermarks.Count} diagonally rotated watermark(s)");
}
```

### Combining Multiple Search Criteria (Advanced Searches)

Here's where things get powerful. Real-world watermark detection often requires checking multiple conditions at once. Maybe you need to find your company logo that's also rotated at a specific angle, or text watermarks that appear alongside specific images.

#### How Criterion Combination Works

You can combine criteria using logical operators:
- **`.Or()`**: Finds watermarks matching EITHER criterion
- **`.And()`**: Finds watermarks matching BOTH criteria (more restrictive)

#### Example: Find Logo OR Company Name

This search will catch documents containing either your logo or your company name:

```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(logoImagePath);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
    
    // Find documents with either the logo OR the text
    SearchCriteria combinedSearchCriteria = imageSearchCriteria.Or(textSearchCriteria);
    
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(combinedSearchCriteria);
}
```

#### Example: Find Logo AND Specific Rotation

This is more restrictive—it only finds watermarks that match ALL conditions:

```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(logoImagePath);
    RotateAngleSearchCriteria rotateAngleSearchCriteria = new RotateAngleSearchCriteria(30, 60);
    
    // Find only logo watermarks that are also rotated 30-60 degrees
    SearchCriteria combinedSearchCriteria = imageSearchCriteria.And(rotateAngleSearchCriteria);
    
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(combinedSearchCriteria);
}
```

#### Complex Example: Logo OR Text, AND Rotated

You can chain multiple operators for sophisticated searches:

```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Path.Combine("YOUR_DOCUMENT_DIRECTORY", "logo.png"));
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
    RotateAngleSearchCriteria rotateAngleSearchCriteria = new RotateAngleSearchCriteria(30, 60);

    // Find watermarks that are (logo OR text) AND rotated 30-60 degrees
    SearchCriteria combinedSearchCriteria = imageSearchCriteria.Or(textSearchCriteria).And(rotateAngleSearchCriteria);

    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(combinedSearchCriteria);
}
```

**When to use combined searches**: This is perfect when you're dealing with standardized document templates where watermarks follow specific patterns. For example, legal documents might always have a company logo at 45 degrees plus a "CONFIDENTIAL" text watermark.

## Which Search Method Should You Use?

Still not sure which approach fits your needs? Here's a quick decision guide:

**Use Image Search when**:
- You're protecting brand assets (logos, stamps, signatures)
- You need to verify document authenticity
- You're tracking unauthorized document distribution
- Visual consistency matters more than text content

**Use Text Search when**:
- You're checking for compliance keywords ("CONFIDENTIAL," "DRAFT")
- You're cataloging documents by watermark content
- You need to verify legal disclaimers are present
- The exact wording matters (contracts, legal docs)

**Use Rotation Search when**:
- You're dealing with scanned documents (often slightly rotated)
- Your watermarks use diagonal placement for security
- You need to filter by watermark orientation
- You're processing architectural or engineering documents

**Use Combined Searches when**:
- You're implementing complex document verification workflows
- You need to match specific watermark "signatures" (logo + text + angle)
- You're building automated document classification systems
- False positives from single-criteria searches are causing problems

## Practical Applications (Real-World Use Cases)

Now that you know the "how," let's talk about the "why." Here are real scenarios where these techniques solve actual business problems:

### Intellectual Property Protection
**The problem**: Your company logo appears in documents you didn't authorize.
**The solution**: Automated image watermark search across repositories. Run scheduled scans of shared drives or document management systems to detect unauthorized use of your branding.

### Legal Compliance Verification
**The problem**: Legal requires "CONFIDENTIAL" watermarks on all client documents, but manual verification is impossible at scale.
**The solution**: Batch text watermark search that flags documents missing required markings before they leave your organization.

### Content Verification Before Publishing
**The problem**: Draft watermarks accidentally make it into published materials (embarrassing and unprofessional).
**The solution**: Pre-publish pipeline that scans for "DRAFT," "SAMPLE," or "DO NOT DISTRIBUTE" watermarks and blocks publication if found.

### Document Authentication
**The problem**: You need to verify documents are official versions with proper security markings.
**The solution**: Combined search for specific logo + text + rotation combinations that match your organization's watermark "signature."

### Digital Asset Management
**The problem**: Categorizing thousands of images by watermark type for archival or licensing purposes.
**The solution**: Automated watermark detection and metadata tagging based on found watermarks.

### Data Security Audits
**The problem**: Discovering which documents contain sensitive information markings during security reviews.
**The solution**: Comprehensive watermark search across file systems to identify and catalog documents by security level.

## Common Pitfalls and How to Avoid Them

Here are mistakes I've seen developers make (and made myself) when working with watermark searches:

### Pitfall #1: Not Handling Empty Results
**The mistake**: Assuming watermarks will always be found, then getting null reference exceptions.

**The fix**: Always check the count before iterating:
```csharp
PossibleWatermarkCollection possibleWatermarks = watermarker.Search(criteria);

if (possibleWatermarks != null && possibleWatermarks.Count > 0)
{
    // Safe to process watermarks
}
else
{
    // Handle the case where no watermarks were found
}
```

### Pitfall #2: Wrong MaxDifference Values
**The mistake**: Setting `MaxDifference` too low (like 0.5) and missing obvious matches, or too high (like 0.99) and catching false positives.

**The fix**: Start with 0.9 and adjust based on results. Test with known watermarked documents first.

### Pitfall #3: Case-Sensitive Text Searches
**The mistake**: Searching for "draft" when the watermark says "DRAFT" or "Draft."

**The fix**: If you need case-insensitive matching, search for all variations or normalize text before searching.

### Pitfall #4: Forgetting to Dispose Resources
**The mistake**: Not properly disposing of the `Watermarker` object, leading to memory leaks in long-running applications.

**The fix**: Always use `using` statements as shown in the examples above.

### Pitfall #5: Ignoring Document Format Limitations
**The mistake**: Assuming all watermark types work with all document formats.

**The fix**: Test your specific document types first. Some formats (like encrypted PDFs) may have limitations.

## Troubleshooting Your Watermark Searches

**Problem**: "I know the watermark exists, but the search returns zero results."

**Possible causes and solutions**:
1. **Case sensitivity issue**: Try searching with different capitalizations
2. **MaxDifference too strict**: For image searches, lower the value to 0.7-0.8
3. **Wrong rotation range**: Watermark might be at a different angle than you think
4. **Watermark is embedded differently**: Some watermarks are images, some are text—make sure you're using the right search type
5. **Document is corrupted or password-protected**: Check if you can open the document normally first

**Problem**: "I'm getting too many false positives."

**Solutions**:
- Increase `MaxDifference` for image searches (move toward 1.0)
- Use combined criteria with `.And()` to be more restrictive
- Add rotation angle criteria to filter out unrelated matches

**Problem**: "The search is really slow on large documents."

**Solutions**:
- Process documents in batches rather than all at once
- Use more specific search criteria to reduce processing time
- Consider running searches asynchronously in production environments

**Problem**: "Memory usage keeps climbing when processing multiple documents."

**Solutions**:
- Ensure you're properly disposing of `Watermarker` objects (use `using` statements)
- Process documents one at a time rather than loading them all into memory
- Implement proper garbage collection between batch operations

## Best Practices for Production Environments

If you're moving beyond testing and into production, here are some hard-learned lessons:

### Performance Optimization

**Batch Processing**: Don't try to process 10,000 documents in one go. Break them into batches of 50-100:

```csharp
var documentBatches = allDocuments.Chunk(50); // Requires .NET 6+

foreach (var batch in documentBatches)
{
    foreach (var doc in batch)
    {
        // Process document
    }
    
    // Optional: Add delay between batches to prevent resource exhaustion
    Thread.Sleep(100);
}
```

**Memory Management**: Monitor your application's memory usage. If processing large PDFs with high-resolution watermarks, consider:
- Processing during off-peak hours
- Implementing a queue-based system
- Setting memory limits and handling out-of-memory exceptions gracefully

**Parallel Processing**: For faster throughput, process multiple documents simultaneously:

```csharp
Parallel.ForEach(documents, new ParallelOptions { MaxDegreeOfParallelism = 4 }, document =>
{
    using (Watermarker watermarker = new Watermarker(document))
    {
        // Perform search
    }
});
```

**Note on parallelism**: Don't go crazy with the thread count. `MaxDegreeOfParallelism = 4` is usually a good starting point. More threads doesn't always mean faster processing—you'll hit diminishing returns.

### Error Handling and Logging

In production, you need to know when and why things fail:

```csharp
try
{
    using (Watermarker watermarker = new Watermarker(documentPath))
    {
        var results = watermarker.Search(criteria);
        // Process results
    }
}
catch (Exception ex)
{
    // Log the error with document context
    Logger.Error($"Watermark search failed for {documentPath}: {ex.Message}");
    
    // Decide whether to continue or stop based on your requirements
}
```

### Caching Search Results

If you're repeatedly searching the same documents, cache the results:

```csharp
private Dictionary<string, PossibleWatermarkCollection> _watermarkCache = new();

public PossibleWatermarkCollection GetWatermarks(string documentPath, SearchCriteria criteria)
{
    string cacheKey = $"{documentPath}_{criteria.GetHashCode()}";
    
    if (!_watermarkCache.ContainsKey(cacheKey))
    {
        using (Watermarker watermarker = new Watermarker(documentPath))
        {
            _watermarkCache[cacheKey] = watermarker.Search(criteria);
        }
    }
    
    return _watermarkCache[cacheKey];
}
```

**Cache invalidation tip**: Clear the cache when documents are modified or after a certain time period (e.g., 24 hours).

## Real-World Workflow Example

Let's tie everything together with a complete workflow that checks documents before they're published:

```csharp
public class DocumentPublishingValidator
{
    private readonly string _approvedLogoPath;
    private readonly List<string> _bannedTexts = new List<string> { "DRAFT", "SAMPLE", "DO NOT DISTRIBUTE" };
    
    public DocumentPublishingValidator(string approvedLogoPath)
    {
        _approvedLogoPath = approvedLogoPath;
    }
    
    public ValidationResult ValidateDocument(string documentPath)
    {
        var result = new ValidationResult { IsValid = true };
        
        using (Watermarker watermarker = new Watermarker(documentPath))
        {
            // Check 1: Ensure approved logo is present
            var logoSearch = new ImageDctHashSearchCriteria(_approvedLogoPath);
            logoSearch.MaxDifference = 0.9;
            var logoWatermarks = watermarker.Search(logoSearch);
            
            if (logoWatermarks.Count == 0)
            {
                result.IsValid = false;
                result.Errors.Add("Required company logo watermark not found");
            }
            
            // Check 2: Ensure no banned text watermarks exist
            foreach (var bannedText in _bannedTexts)
            {
                var textSearch = new TextSearchCriteria(bannedText);
                var textWatermarks = watermarker.Search(textSearch);
                
                if (textWatermarks.Count > 0)
                {
                    result.IsValid = false;
                    result.Errors.Add($"Document contains banned watermark text: {bannedText}");
                }
            }
        }
        
        return result;
    }
}

public class ValidationResult
{
    public bool IsValid { get; set; }
    public List<string> Errors { get; set; } = new List<string>();
}
```

**How this helps**: Before any document gets published to customers or external partners, it goes through this validator. Documents pass only if they have the approved logo and don't contain draft markings.

## Conclusion

You've now got a solid foundation for implementing watermark search in your .NET applications. Whether you're protecting intellectual property, ensuring compliance, or building automated document workflows, GroupDocs.Watermark gives you the tools to detect watermarks programmatically without the headache of writing complex image processing or text extraction logic yourself.

**Key takeaways**:
- Image searches work great for logos and visual watermarks (adjust `MaxDifference` based on your tolerance needs)
- Text searches are straightforward but case-sensitive (plan accordingly)
- Rotation angle searches help you find diagonally-placed or oddly-oriented watermarks
- Combined criteria searches give you surgical precision when you need it
- Always wrap `Watermarker` in `using` statements to prevent resource leaks

**Next steps**: Start with the code examples that match your use case, test with your actual documents, and gradually add more sophisticated criteria as your needs grow. The API is flexible enough to grow with you.

Got stuck? Check the troubleshooting section, or dive into the resources below for deeper technical details.

## FAQ Section

**Q: Can I search for watermarks in formats other than PDFs?**
Yes! GroupDocs.Watermark supports a wide range of formats including Word documents (.doc, .docx), Excel spreadsheets (.xls, .xlsx), PowerPoint presentations (.ppt, .pptx), and various image formats (.png, .jpg, .gif, etc.). The API works the same across all formats.

**Q: How does the DCT hash image search actually work?**
The Discrete Cosine Transform (DCT) hash compares images based on their frequency patterns rather than exact pixels. Think of it like comparing the "fingerprint" of an image. This means it can find your logo even if it's been slightly compressed, resized, or had minor color adjustments—which is perfect for real-world scenarios where watermarks aren't pixel-perfect matches.

**Q: Is text search case-sensitive?**
Yes, by default text searches are case-sensitive. If you're looking for "DRAFT" but the watermark says "Draft," you won't find it. To handle this, you'll need to search for both variations or preprocess your search strings.

**Q: What's the practical limit for combining search criteria?**
While you can technically chain together many criteria, remember that each additional criterion increases processing time and can make your searches overly restrictive. In practice, 2-3 combined criteria usually hit the sweet spot between precision and performance. If you need more, consider whether you're actually describing multiple separate searches rather than one complex one.

**Q: Can I remove watermarks after finding them?**
Yes! Once you've found watermarks using the search methods described here, you can modify or remove them. That's a separate topic, but the `PossibleWatermark` objects returned by searches have methods for removal and modification. Check the GroupDocs.Watermark documentation for watermark removal examples.

**Q: How do I handle password-protected or encrypted documents?**
You'll need to provide the password when creating the `Watermarker` object. If the document is encrypted and you don't have the password, the library won't be able to access it (which is kind of the point of encryption).

**Q: Will this work with scanned documents (images of documents)?**
Yes and no. If the scan resulted in an image file (like a PNG or JPG), you can search for image-based watermarks within it. However, if the document was scanned and the watermark is part of the scanned image (not a separate watermark layer), detection becomes much harder—you're essentially looking for an image within an image, which requires much more sophisticated image recognition than basic watermark detection.

**Q: Can I search for invisible or hidden watermarks?**
GroupDocs.Watermark can find watermarks that aren't visible to the naked eye, like very faint watermarks or those using transparency. However, for steganographic watermarks (data hidden using steganography techniques), you'd need specialized steganography detection tools—that's beyond the scope of basic watermark searching.

## Resources and Further Learning

**Documentation**:
- [GroupDocs.Watermark for .NET Documentation](https://docs.groupdocs.com/watermark/net/) - Comprehensive guides covering all features
- [API Reference](https://reference.groupdocs.com/watermark/net) - Detailed technical documentation for every class and method

**Downloads and Licensing**:
- [Download GroupDocs.Watermark](https://releases.groupdocs.com/watermark/net/) - Get the latest version
- [Free Trial](https://releases.groupdocs.com/watermark/net/) - Test before you buy
- [Temporary License](https://purchase.groupdocs.com/temporary-license/) - Extended evaluation period
- [Purchase License](https://purchase.groupdocs.com/buy) - For production use

**Community Support**:
- [GroupDocs Forum](https://forum.groupdocs.com/c/watermark) - Ask questions and get help from the community and GroupDocs team
