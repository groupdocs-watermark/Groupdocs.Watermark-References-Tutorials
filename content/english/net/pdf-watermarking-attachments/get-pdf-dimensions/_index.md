---
title: "How to Get PDF Dimensions in C#"
linktitle: "Get PDF Dimensions C#"
description: "Learn how to get PDF page dimensions in C# using GroupDocs.Watermark .NET. Essential for accurate watermark positioning and document validation."
keywords: "get PDF dimensions C#, read PDF page size, PDF width height .NET, measure PDF dimensions, check PDF page size programmatically"
weight: 26
url: /net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["PDF Processing"]
tags: ["pdf-dimensions", "csharp", "document-metadata", "watermarking"]
---

# How to Get PDF Dimensions in C#

## Introduction

Ever tried to add a watermark to a PDF only to find it's cut off, misaligned, or covering important content? You're not alone. One of the most common issues when working with PDF watermarking is not knowing the exact dimensions of your document pages before applying overlays.

Getting PDF page dimensions programmatically isn't just about curiosity—it's essential for proper document processing. Whether you're positioning watermarks, validating document sizes for printing, or batch-processing files with varying dimensions, knowing how to read PDF page measurements in C# can save you hours of manual work and frustrating trial-and-error.

In this guide, you'll learn how to get PDF dimensions using GroupDocs.Watermark for .NET, understand what those measurements mean, and discover practical ways to use this information in your document workflow.

## Prerequisites

Before we dive into reading PDF dimensions, make sure you have:

1. **GroupDocs.Watermark for .NET**: Download and install from the [download page](https://releases.groupdocs.com/Watermark/net/). The library works with .NET Framework 4.6.1+ and .NET Core 2.0+.

2. **Development Environment**: Visual Studio 2019 or later (though any C# IDE will work).

3. **Basic C# Knowledge**: You should be comfortable with using namespaces, classes, and basic file operations.

4. **Test PDF File**: Have a sample PDF ready on your local machine. Multi-page PDFs are ideal for testing, as you'll see how dimensions can vary between pages.

5. **License (Optional)**: While GroupDocs.Watermark offers a [free trial](https://releases.groupdocs.com/), you can get a [temporary license](https://purchase.groupdocs.com/temporary-license/) for full functionality or [purchase a license](https://purchase.groupdocs.com/buy) for production use.

## Import Namespaces

First things first—let's import the necessary namespaces into your C# project. These give you access to PDF-specific functionality and the core Watermarker class.

```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```

Here's what each namespace does:
- `GroupDocs.Watermark.Contents.Pdf`: Provides PDF-specific content classes (like `PdfContent`)
- `GroupDocs.Watermark.Options.Pdf`: Contains loading options for PDF files
- `System` and `System.IO`: Standard .NET libraries for console output and file path handling

## Why PDF Dimensions Matter

Before we jump into the code, let's talk about why you'd want to retrieve PDF dimensions in the first place.

### Accurate Watermark Positioning

This is the big one. If you're adding watermarks, stamps, or signatures to PDFs, you need to know the page dimensions to:
- Position elements precisely (center, bottom-right, etc.)
- Scale watermarks proportionally to the page size
- Avoid cutting off elements on smaller pages
- Ensure consistency across documents with varying sizes

### Document Validation

Many workflows require specific page sizes. For example:
- Verifying documents meet print requirements (A4, Letter, Legal)
- Ensuring uploaded files match expected dimensions
- Batch processing only files of certain sizes
- Quality control in document management systems

### Batch Processing Intelligence

When processing multiple PDFs, dimension checking helps you:
- Route documents to appropriate processing pipelines
- Apply different watermark strategies based on orientation (portrait vs. landscape)
- Skip or flag non-standard documents
- Optimize processing based on document complexity

## Understanding PDF Dimension Units

Here's something that trips up a lot of developers: **PDF dimensions are measured in points by default**, not pixels or inches.

One point = 1/72 of an inch. So a standard US Letter page (8.5 × 11 inches) is 612 × 792 points.

Common page sizes in points:
- **US Letter**: 612 × 792 points (8.5 × 11 inches)
- **A4**: 595 × 842 points (210 × 297 mm)
- **Legal**: 612 × 1008 points (8.5 × 14 inches)
- **Tabloid**: 792 × 1224 points (11 × 17 inches)

You can convert to inches by dividing by 72, or to centimeters by dividing by 28.35 (since 1 inch = 2.54 cm and 72 points = 1 inch).

## Step-by-Step Implementation

Now let's walk through the actual code to get PDF dimensions. I'll break it down step by step so you understand exactly what's happening.

### Step 1: Set Up Your File Paths

```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```

**What's happening here?**
- `documentPath`: Points to your source PDF file (replace with your actual file path)
- `outputDirectory`: Where you'll save any processed files (if needed later)
- `outputFileName`: Combines the directory and filename for the output

**Pro tip**: Use `Path.Combine()` instead of string concatenation—it handles different operating systems' path separators automatically.

### Step 2: Load the PDF Document

```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```

**Breaking it down:**
- `PdfLoadOptions()`: Creates loading options specific to PDF files (you can customize password-protected PDFs here)
- `Watermarker`: The main class for document operations—not just for watermarking despite the name!
- `using` statement: Ensures proper resource cleanup when we're done

**Why use PdfLoadOptions?** Even though we're just reading dimensions, using PDF-specific load options ensures the library properly parses PDF structure and handles edge cases like encrypted or damaged files.

### Step 3: Access PDF Content

```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```

This is where the magic happens. The `GetContent<PdfContent>()` method gives you access to the PDF's internal structure, including:
- Page collection
- Metadata
- Attachments
- Form fields

**Important note**: Always use the generic `GetContent<T>()` method with the appropriate content type. For PDFs, that's `PdfContent`. This provides type-safe access to PDF-specific properties.

### Step 4: Retrieve and Display Dimensions

```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

Finally, we're accessing the first page's dimensions (index `[0]`). The `Width` and `Height` properties return values in points.

**Working with multiple pages?** You can loop through all pages:

```csharp
for (int i = 0; i < pdfContent.Pages.Count; i++)
{
    Console.WriteLine($"Page {i + 1}: {pdfContent.Pages[i].Width} × {pdfContent.Pages[i].Height} points");
}
```

## Complete Working Example

Here's the full code in context:

```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;

public class PdfDimensionReader
{
    public static void Main()
    {
        string documentPath = @"C:\Documents\sample.pdf";
        string outputDirectory = @"C:\Documents\Output";
        string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

        var loadOptions = new PdfLoadOptions();
        using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
        {
            PdfContent pdfContent = watermarker.GetContent<PdfContent>();
            
            Console.WriteLine($"Width: {pdfContent.Pages[0].Width} points");
            Console.WriteLine($"Height: {pdfContent.Pages[0].Height} points");
            
            // Convert to inches for readability
            double widthInches = pdfContent.Pages[0].Width / 72.0;
            double heightInches = pdfContent.Pages[0].Height / 72.0;
            Console.WriteLine($"Dimensions: {widthInches:F2} × {heightInches:F2} inches");
        }
    }
}
```

## Common Issues and Troubleshooting

### Problem: "Index was outside the bounds of the array"

**Cause**: You're trying to access a page that doesn't exist (like `Pages[0]` on an empty PDF).

**Solution**: Always check `pdfContent.Pages.Count` before accessing pages:
```csharp
if (pdfContent.Pages.Count > 0)
{
    Console.WriteLine(pdfContent.Pages[0].Width);
}
```

### Problem: Dimensions seem wrong or inconsistent

**Cause**: PDF pages can have different dimensions, or the PDF might have rotation applied.

**Solution**: Check the page rotation property and adjust accordingly:
```csharp
var page = pdfContent.Pages[0];
Console.WriteLine($"Rotation: {page.Rotation}");
// Swap width/height if rotated 90° or 270°
```

### Problem: Cannot load password-protected PDFs

**Cause**: The PDF is encrypted and requires a password.

**Solution**: Provide the password in `PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions { Password = "yourpassword" };
```

### Problem: File not found or access denied errors

**Cause**: Incorrect path or file permissions.

**Solution**: 
- Use absolute paths during development
- Check file permissions
- Ensure the file isn't open in another application
- Use `File.Exists()` to verify the path before loading

## Best Practices for Production Code

### 1. Always Validate Page Indices

Don't assume a PDF has pages. Always check:
```csharp
if (pdfContent.Pages.Count > pageIndex && pageIndex >= 0)
{
    // Safe to access pdfContent.Pages[pageIndex]
}
```

### 2. Handle Exceptions Gracefully

Wrap your code in try-catch blocks for production:
```csharp
try
{
    using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
    {
        // Your dimension-reading code
    }
}
catch (GroupDocs.Watermark.Exceptions.IncorrectPasswordException)
{
    Console.WriteLine("The PDF is password-protected.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error: {ex.Message}");
}
```

### 3. Cache Dimensions for Batch Processing

If you're processing the same PDF multiple times, cache the dimensions:
```csharp
var pageDimensions = new Dictionary<int, (double Width, double Height)>();
for (int i = 0; i < pdfContent.Pages.Count; i++)
{
    pageDimensions[i] = (pdfContent.Pages[i].Width, pdfContent.Pages[i].Height);
}
```

### 4. Consider Memory Usage

The `Watermarker` class loads the entire PDF into memory. For very large files:
- Process pages individually if possible
- Dispose of the Watermarker object promptly
- Use the `using` statement to ensure cleanup

## Pro Tips for Advanced Scenarios

### Detecting Page Orientation

You can determine if a page is portrait or landscape:
```csharp
bool isLandscape = pdfContent.Pages[0].Width > pdfContent.Pages[0].Height;
Console.WriteLine(isLandscape ? "Landscape" : "Portrait");
```

### Finding the Largest/Smallest Pages

Useful for batch processing:
```csharp
var largestPage = pdfContent.Pages.OrderByDescending(p => p.Width * p.Height).First();
var smallestPage = pdfContent.Pages.OrderBy(p => p.Width * p.Height).First();
```

### Checking for Standard Paper Sizes

Create a helper method to identify common sizes:
```csharp
public static string IdentifyPageSize(double width, double height)
{
    if (Math.Abs(width - 612) < 5 && Math.Abs(height - 792) < 5)
        return "US Letter";
    if (Math.Abs(width - 595) < 5 && Math.Abs(height - 842) < 5)
        return "A4";
    if (Math.Abs(width - 612) < 5 && Math.Abs(height - 1008) < 5)
        return "Legal";
    return "Custom";
}
```

## When to Use Dimension Checking in Your Workflow

Here are practical scenarios where checking PDF dimensions before watermarking makes sense:

**Responsive Watermarking**: Adjust watermark size and position based on page dimensions (smaller watermarks for smaller pages).

**Quality Control**: Reject or flag documents that don't meet size requirements before processing.

**Cost Optimization**: For API-based processing with usage limits, skip oversized documents or warn users beforehand.

**Multi-Format Support**: When accepting various document types, validate PDFs meet your application's requirements.

**Print Preparation**: Ensure documents match printer specifications before sending to print services.

## Conclusion

Getting PDF dimensions in C# with GroupDocs.Watermark .NET is straightforward once you understand the basics: load the document with appropriate options, access the PDF content, and read the page dimensions (which are in points by default).

This seemingly simple operation unlocks powerful capabilities for document processing workflows—from precise watermark positioning to intelligent batch processing and document validation.

The key takeaways:
- Always use `PdfLoadOptions` for proper PDF handling
- Remember that dimensions are in points (divide by 72 for inches)
- Check page count before accessing pages
- Handle exceptions for production code
- Consider caching dimensions for performance

Ready to start implementing watermarks based on these dimensions? Check out our related guides on watermark positioning and batch processing.

## FAQ's

### Can I get dimensions for password-protected PDFs?

Yes! Just provide the password in `PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions { Password = "yourpassword" };
```
If the password is incorrect, you'll get an `IncorrectPasswordException`.

### Do all pages in a PDF have the same dimensions?

Not necessarily. PDFs can have pages with different sizes, which is why it's important to check each page individually if you're processing all pages. Mixed-size PDFs are common in scanned documents or combined files.

### How do I convert points to inches or centimeters?

Divide by 72 for inches: `widthInches = width / 72.0`
Divide by 28.35 for centimeters: `widthCm = width / 28.35`

These conversions work because PDF points are defined as 1/72 of an inch.

### Can I use GroupDocs.Watermark for .NET for free?

GroupDocs offers a [free trial](https://releases.groupdocs.com/) for evaluation purposes. For extended functionality and production use, you'll need to purchase a [full license](https://purchase.groupdocs.com/buy) or get a [temporary license](https://purchase.groupdocs.com/temporary-license/) for development.

### What if I need help or run into issues?

The GroupDocs community is active and helpful! Visit the [support forum](https://forum.groupdocs.com/c/watermark/19) to get technical assistance, ask questions, and see solutions to common problems. The documentation is also comprehensive and regularly updated.

### Does this work with other document formats besides PDF?

Yes! GroupDocs.Watermark supports multiple formats including Word, Excel, PowerPoint, and images. However, the dimension-reading approach varies by format. For PDFs specifically, the method shown here is the most reliable. Check the documentation for format-specific approaches to other document types.
