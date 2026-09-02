---
title: "How to Watermark Images in Word with .NET"
linktitle: "Watermark Word Images .NET"
description: "Learn how to watermark images in Word documents using .NET. Protect embedded images, prevent unauthorized use, and secure your content with this practical tutorial."
keywords: "watermark images in word dotnet, protect word document images, add watermark to word shapes programmatically, groupdocs watermark tutorial, prevent image theft word documents"
weight: 17
url: /net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["Document Security"]
tags: ["watermarking", "word-processing", "image-protection", "dotnet", "groupdocs"]
---

# How to Watermark Images in Word Documents with .NET

## Introduction

Ever published a Word document only to find your carefully crafted images floating around the internet without attribution? Or maybe you're working with confidential diagrams that need an extra layer of protection? You're not alone—and there's a straightforward solution.

In this tutorial, we'll walk through how to watermark images embedded in Word documents using GroupDocs.Watermark for .NET. Unlike simple overlay watermarks that sit on top of your document, this approach targets the actual image shapes inside your Word file, making the protection much harder to remove. Whether you're protecting intellectual property, adding copyright notices, or preventing unauthorized distribution, this method gives you programmatic control over your document's visual assets.

By the end of this guide, you'll know exactly how to implement watermarks on shape images (those pictures, diagrams, and graphics embedded in your Word docs) with just a few lines of C# code. Let's dive in.

## Why Watermark Embedded Images in Word Documents?

Before we jump into the code, let's talk about why this matters. Watermarking shape images in Word documents serves several practical purposes:

**Intellectual Property Protection**: If you're creating reports, whitepapers, or documentation with original diagrams, screenshots, or graphics, watermarks help establish ownership. Even if someone extracts the image from your document, your watermark travels with it.

**Confidentiality Indicators**: For internal documents that contain sensitive flowcharts, architectural diagrams, or proprietary visualizations, watermarks can indicate classification levels ("Confidential", "Internal Use Only", etc.) directly on the images themselves.

**Brand Consistency**: Marketing teams often need to ensure all visual assets carry brand identifiers. Programmatically watermarking images in Word documents ensures consistency across large document libraries without manual intervention.

**Deterrent Against Misuse**: While watermarks won't stop determined bad actors, they significantly reduce casual image theft. Most people won't bother removing watermarks for unofficial use, especially when the watermark is embedded in the image data itself rather than just overlaid on the page.

The key advantage of watermarking shape images (as opposed to just putting a watermark on the page) is that the protection stays with the image even if someone copies or extracts it from the document. This makes it far more effective for real-world security needs.

## Prerequisites

Before we begin, make sure you have the following ready:

1. **GroupDocs.Watermark for .NET**: Download and install the library from the [download page](https://releases.groupdocs.com/Watermark/net/). You'll need either a valid license or a temporary one for testing (available from the GroupDocs website).

2. **Word Document with Images**: Prepare a Word document that contains shape images (pictures, diagrams, or graphics inserted into the document—not just background images or floating text boxes).

3. **Development Environment**: Any .NET IDE will work—Visual Studio, Visual Studio Code, or Rider. The library supports .NET Framework, .NET Core, and .NET Standard, so you've got flexibility on your platform.

4. **Basic C# Knowledge**: You should be comfortable with basic C# syntax, file I/O, and working with objects. If you can instantiate classes and iterate through collections, you're all set.

**Quick Compatibility Note**: This tutorial uses .NET Standard 2.0 compatible code, which means it works across .NET Framework 4.6.1+, .NET Core 2.0+, and .NET 5/6/7/8. The library handles all the heavy lifting of parsing Word's complex XML structure (those .docx files are actually zipped XML files under the hood), so you don't need to worry about the underlying format.

## Import Namespaces

Before writing the core logic, you'll need to import the necessary namespaces. These provide access to the GroupDocs.Watermark classes and helper utilities:

```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

**What These Namespaces Do**:
- `GroupDocs.Watermark.Common`: Contains core types like alignment enums and sizing options
- `GroupDocs.Watermark.Contents.WordProcessing`: Provides Word-specific content classes (sections, shapes, etc.)
- `GroupDocs.Watermark.Options.WordProcessing`: Load and save options specifically for Word documents
- `GroupDocs.Watermark.Watermarks`: The main watermark types (text, image) and their properties
- `System.IO`: Standard .NET file operations for path handling

These imports give you everything you need to load Word documents, identify image shapes, create watermarks, and save the results—all without dealing with the complexity of the Open XML SDK directly.

## Step 1: Load the Document

First, you'll need to specify where your input document lives and where you want to save the watermarked version. This is standard file I/O setup:

```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```

**What's Happening Here**: 
- `documentPath` points to your source Word document (the one containing images you want to watermark)
- `outputFileName` creates a path for the watermarked output file, preserving the original filename but placing it in your desired output directory

**Pro Tip**: In production code, you'll want to validate that `documentPath` exists using `File.Exists()` before proceeding. Also consider generating unique output filenames (maybe with timestamps) to avoid accidentally overwriting files if you're processing multiple documents in batch operations.

**Real-World Context**: Many developers process documents in bulk—think compliance teams watermarking hundreds of reports or marketing teams preparing document libraries for publication. Using `Path.Combine()` ensures your code works across Windows and Linux environments without hardcoding path separators.

## Step 2: Initialize Watermarker

Now you'll create the `Watermarker` object, which is your main interface for interacting with the document:

```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Add watermarking logic here
}
```

**Understanding This Code**:
- `WordProcessingLoadOptions()` creates an options object specifically for Word documents. While we're using defaults here, this is where you'd configure things like password protection for encrypted documents or specify custom parsers if needed.
- The `using` statement ensures proper resource disposal. Word documents can be memory-intensive (especially those with lots of images), so this pattern guarantees the document is closed and memory is released even if an exception occurs.
- The `Watermarker` constructor loads the entire document into memory and parses its structure, identifying all sections, shapes, headers, footers, and other elements.

**Performance Consideration**: For very large Word documents (50+ pages with dozens of images), the initialization step can take 1-2 seconds. If you're building a web application, consider running this operation asynchronously to avoid blocking your main thread.

**Common Gotcha**: If your Word document is password-protected, you'll need to provide the password in the `loadOptions` object before initialization. Otherwise, you'll get an exception. The library doesn't attempt to crack passwords (thankfully!).

## Step 3: Create Text Watermark

This is where you define what your watermark will look like and how it behaves:

```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```

**Breaking Down Each Property**:

**Text Content**: `"Protected image"` is your watermark text. In practice, you might use:
- Copyright notices: "© 2025 YourCompany"
- Confidentiality labels: "CONFIDENTIAL - Internal Use Only"
- Custom identifiers: "Draft - Review Copy 3.2"
- User attributions: "Created by JohnDoe@company.com"

**Font Selection**: `new Font("Arial", 8)` creates an 8-point Arial font. Why Arial? It's universally available across all systems, ensuring consistent rendering. The small font size (8pt) makes the watermark visible but not overwhelming. For production, consider these alternatives:
- For professional documents: Times New Roman or Calibri
- For modern/tech documents: Segoe UI or Roboto
- For maximum legibility on small images: Arial Bold or Helvetica Bold

**Alignment Properties**: 
- `HorizontalAlignment.Center` and `VerticalAlignment.Center` place the watermark dead-center on each image. This is the most common approach since it's hard to crop out without destroying the image's core content.
- Alternative: `HorizontalAlignment.Right` + `VerticalAlignment.Bottom` creates a corner watermark (like traditional photo copyright stamps).

**Rotation Angle**: `RotateAngle = 45` creates that classic diagonal watermark look. This 45-degree angle is psychologically effective—it clearly indicates "this is a watermark" without being too intrusive. You can adjust from 0 (horizontal) to 90 (vertical) depending on your image layouts.

**Sizing Behavior**:
- `SizingType.ScaleToParentDimensions` is crucial—it tells the watermark to scale relative to the image size. A watermark on a 100x100px thumbnail will be proportionally smaller than on a 1000x1000px image.
- `ScaleFactor = 1` means 100% scaling. Reduce to `0.8` for more subtle watermarks or increase to `1.2` for more prominent ones.

**Why These Defaults Work**: This configuration creates a professional, visible but non-intrusive watermark that scales appropriately across different image sizes. The diagonal angle prevents easy cropping, and the centered position ensures it's always visible regardless of image aspect ratio.

## Step 4: Apply Watermark to Shape Images

Now comes the core logic—finding all images in your document and applying the watermark:

```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```

**Let's Break Down This Logic**:

**Getting the Content**: `watermarker.GetContent<WordProcessingContent>()` retrieves a strongly-typed representation of your Word document's structure. This object model mirrors how Word organizes content internally—sections contain shapes, paragraphs, tables, etc.

**Section Iteration**: Word documents are divided into sections (think of these as page layout containers—each section can have different margins, orientations, or column settings). By iterating through `content.Sections`, we ensure we check every part of the document, even if it spans multiple sections with different formatting.

**Shape Iteration**: Within each section, `section.Shapes` gives us all graphical objects. In Word's object model, "shapes" include:
- Pictures and photos (the most common)
- Diagrams and SmartArt graphics
- Text boxes with images
- Grouped objects
- Charts with embedded graphics

**The Conditional Check**: `if (shape.HeaderFooter == null && shape.Image != null)` is critical:
- `shape.HeaderFooter == null`: This ensures we're only watermarking shapes in the main document body, not in headers or footers. Why? Headers/footers often contain logos or branding that shouldn't be watermarked. If you DO want to watermark header/footer images, simply remove this condition.
- `shape.Image != null`: This confirms the shape actually contains image data. Not all shapes are images—some are text boxes, drawing objects, or empty placeholders.

**Adding the Watermark**: `shape.Image.Add(watermark)` applies your configured watermark directly to the image data. This modifies the actual image bytes, meaning the watermark becomes part of the image itself, not just an overlay on the Word page.

**What Happens Under the Hood**: When you call `.Add()`, the library:
1. Extracts the image data from the Word document's internal media folder
2. Decodes the image (whether it's JPG, PNG, GIF, etc.)
3. Renders your watermark text onto the image at the specified position, angle, and scale
4. Re-encodes the image (preserving the original format when possible)
5. Updates the Word document's internal references

**Performance Note**: For documents with many images (say, 50+ photos in a report), this step takes the most time. Each image requires decode → render → encode operations. On average hardware, expect about 100-200ms per image.

## Step 5: Save the Document

Finally, save your watermarked document to disk:

```csharp
watermarker.Save(outputFileName);
```

**Simple But Important**: This single line does several things:
1. Packages all your changes (watermarked images) back into the Word document's internal structure
2. Writes the modified .docx file to your specified output path
3. Ensures proper compression (Word documents are ZIP archives of XML files)
4. Maintains all original formatting, styles, and non-image content

**What Gets Preserved**: Everything except the images you watermarked remains untouched—text formatting, page layouts, table structures, styles, embedded fonts, macros (if any), document properties, and metadata all stay exactly as they were.

**Important**: The original document at `documentPath` remains unmodified. You're creating a new file at `outputFileName`. If you want to overwrite the original (be very careful!), you'd set `outputFileName = documentPath`, but this is generally not recommended for production code—always keep backups.

**File Size Considerations**: Watermarked images may be slightly larger than originals (typically 5-15% increase) because the watermark adds visual complexity, which can reduce compression efficiency. For documents with many images, the overall file size might increase by 10-30%.

## When to Use This Approach

This watermarking technique shines in specific scenarios. Here's when to use it (and when to consider alternatives):

**✅ Perfect For**:

**Document Distribution**: When you're sending Word documents outside your organization and want to protect visual assets—think reports to clients, research papers for review, or marketing materials for partners.

**Compliance and Legal**: Industries like finance, healthcare, or government often require visible document classification. Watermarking diagrams with "CONFIDENTIAL" or "DRAFT" directly on images ensures compliance even if pages are extracted or shared separately.

**Bulk Document Processing**: When you need to watermark entire document libraries programmatically—maybe you're preparing hundreds of reports for publication or updating legacy documents with new copyright notices.

**Preventing Casual Misuse**: For educational materials, training documents, or internal wikis where you want to discourage unauthorized distribution without implementing heavyweight DRM.

**❌ Consider Alternatives When**:

**Real-Time Collaboration**: If users are actively editing documents in real-time (like Microsoft 365 co-authoring), this approach isn't suitable—it's a batch operation, not an interactive one.

**Already Using DRM**: If your documents are protected by Information Rights Management (IRM) or Azure RMS, you might not need image watermarks—the DRM handles access control at a higher level.

**Images Are Secondary**: If your document's value is in the text content (like contracts or legal documents), focus on document-level watermarks rather than image watermarks.

**High-Performance Requirements**: For web applications needing sub-second response times, consider caching watermarked versions or using dedicated image processing services rather than watermarking on-demand.

## Common Issues & Solutions

Here are real problems developers encounter when implementing this code, along with fixes:

**Issue 1: "Password Protected Document" Exception**

```
Exception: Cannot load password protected document without password.
```

**Solution**: Add password to load options:
```csharp
var loadOptions = new WordProcessingLoadOptions();
loadOptions.Password = "your-document-password";
```

If processing many documents with different passwords, consider storing passwords securely (like Azure Key Vault) and fetching them dynamically rather than hardcoding.

**Issue 2: Watermark Not Appearing on Some Images**

**Symptom**: Some images get watermarked, others don't, with no obvious pattern.

**Common Causes**:
- **Header/Footer Images**: Your code explicitly excludes these (`shape.HeaderFooter == null`). If you want to include them, remove that condition.
- **Grouped Shapes**: Images inside grouped objects might need different iteration logic. Check if `shape.Type == ShapeType.Group` and recursively process group members.
- **Drawing Canvas Objects**: Some legacy Word documents use drawing canvases. These require accessing `shape.ChildShapes` collection.

**Diagnostic Tip**: Add logging inside your loop to see which shapes are being skipped:
```csharp
if (shape.Image == null)
{
    Console.WriteLine($"Skipping non-image shape: {shape.ShapeType}");
}
```


**Issue 3: Watermark Too Small or Too Large**

**Symptom**: Watermarks look perfect on some images but are illegible on thumbnails or massive on large photos.

**Solution**: The key is the `ScaleFactor` property. Here's how to calculate adaptive scaling:

```csharp
// For very small images (< 200px), use larger scale factor
double adaptiveScale = shape.Image.Width < 200 ? 1.5 : 1.0;
watermark.ScaleFactor = adaptiveScale;
```

Or set absolute sizes instead of scaling:
```csharp
watermark.SizingType = SizingType.Absolute;
watermark.Width = 100;  // pixels
watermark.Height = 20;  // pixels
```


**Issue 4: Performance Degradation with Many Images**

**Symptom**: Processing takes minutes for documents with 100+ images.

**Solutions**:
1. **Process in Parallel** (for multiple documents):
```csharp
Parallel.ForEach(documentPaths, docPath => {
    // Your watermarking code here
});
```

2. **Skip Already Watermarked Images**: Implement detection logic to avoid re-watermarking:
```csharp
// Check if image already has watermark metadata
if (!ImageAlreadyWatermarked(shape.Image))
{
    shape.Image.Add(watermark);
}
```

3. **Use Asynchronous I/O**: If you're loading/saving over network paths, make operations async to avoid blocking.


**Issue 5: Memory Exceptions on Large Documents**

**Symptom**: `OutOfMemoryException` when processing documents over 50MB.

**Solution**: Process documents in batches and force garbage collection:
```csharp
foreach (var docPath in documentBatch)
{
    using (Watermarker watermarker = new Watermarker(docPath, loadOptions))
    {
        // Watermarking logic
    }
    GC.Collect();
    GC.WaitForPendingFinalizers();
}
```

Also consider increasing your application's memory limit in production environments.

## Best Practices for Production Use

Moving from prototype to production? Follow these guidelines:

**1. Error Handling and Logging**

Don't just wrap everything in try-catch—be specific:

```csharp
try
{
    using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
    {
        // Watermarking code
    }
}
catch (PasswordProtectedException ex)
{
    Log.Error($"Document requires password: {documentPath}");
    // Possibly prompt user or retrieve from secure store
}
catch (UnsupportedDocumentTypeException ex)
{
    Log.Error($"Unsupported document format: {documentPath}");
    // Skip or convert document
}
catch (Exception ex)
{
    Log.Error($"Unexpected error processing {documentPath}: {ex.Message}");
    // General fallback
}
```

**2. Configuration Management**

Avoid hardcoding watermark settings. Use configuration files:

```json
{
  "WatermarkSettings": {
    "Text": "© 2025 MyCompany",
    "FontName": "Arial",
    "FontSize": 8,
    "RotationAngle": 45,
    "Opacity": 0.5,
    "ScaleFactor": 1.0
  }
}
```

Load these dynamically so you can adjust without redeploying code.

**3. Validation Before Processing**

Always validate inputs:

```csharp
if (!File.Exists(documentPath))
{
    throw new FileNotFoundException($"Document not found: {documentPath}");
}

if (new FileInfo(documentPath).Length > 100 * 1024 * 1024) // 100MB
{
    throw new InvalidOperationException("Document too large for processing");
}

if (!documentPath.EndsWith(".docx", StringComparison.OrdinalIgnoreCase))
{
    throw new ArgumentException("Only .docx files supported");
}
```

**4. Preserve Original Documents**

Never overwrite source files in production:

```csharp
// Bad: Overwrites original
watermarker.Save(documentPath);

// Good: Creates new version
string watermarkedPath = documentPath.Replace(".docx", "_watermarked.docx");
watermarker.Save(watermarkedPath);

// Better: Use versioning
string watermarkedPath = $"{Path.GetFileNameWithoutExtension(documentPath)}_watermarked_v{DateTime.Now:yyyyMMddHHmmss}.docx";
```

**5. License Management**

In production, use a valid license (not trial mode):

```csharp
// Set license once at application startup
var license = new License();
license.SetLicense("path/to/GroupDocs.Watermark.lic");
```

Trial mode adds watermarks to your watermarks (meta!) and has page limits. A proper license removes these restrictions.

**6. Thread Safety**

The `Watermarker` class is NOT thread-safe. If processing documents concurrently:

```csharp
// Safe: Each thread gets its own Watermarker instance
Parallel.ForEach(documents, doc => {
    using (var watermarker = new Watermarker(doc, loadOptions))
    {
        // Process independently
    }
});
```

**7. Resource Monitoring**

For long-running services, monitor memory and disk usage:

```csharp
var process = Process.GetCurrentProcess();
if (process.WorkingSet64 > 1024 * 1024 * 1024) // 1GB threshold
{
    Log.Warning("High memory usage detected, throttling operations");
    Thread.Sleep(5000); // Brief pause
}
```

## Conclusion

You've now learned how to programmatically watermark images embedded in Word documents using GroupDocs.Watermark for .NET. This technique gives you powerful control over protecting visual assets in your documents—whether you're preventing unauthorized use, adding copyright notices, or meeting compliance requirements.

The key takeaways:
- Watermarks applied to shape images stay with the image even if extracted
- The library handles the complex Word document format details for you
- Configuration options (text, font, position, rotation, scaling) give you flexibility for different use cases
- Production implementations require proper error handling, validation, and resource management

Remember, this approach works best for batch processing documents where you need consistent, automated watermark application. For interactive scenarios or real-time collaboration, you might need different strategies.

Ready to implement this in your project? Start with a test document containing a few images, run through the code step-by-step, and adjust the watermark properties until you get the look you want. Once you're happy with the results, scale up to batch processing and integrate into your document workflow.

## FAQ's

### Can I customize the appearance of the watermark text?

Absolutely. You have full control over the watermark's visual properties. Beyond what we covered in this tutorial, you can adjust:

- **Font Properties**: `watermark.Font.Bold = true`, `watermark.Font.Italic = true`, or even change font families dynamically
- **Color and Opacity**: Use `watermark.ForegroundColor = Color.FromArgb(128, 255, 0, 0)` for semi-transparent red (the first parameter, 128, controls opacity—lower values are more transparent)
- **Text Formatting**: Add multiple lines with `\n` in your text: `"Line 1\nLine 2"`
- **Borders and Background**: Set `watermark.BackgroundColor` for a background box behind your text

The most common customization is opacity—setting it around 40-60% (`Color.FromArgb(100-150, ...)`) makes watermarks visible but not overwhelming.

### Does GroupDocs.Watermark support other document formats besides Word?

Yes, GroupDocs.Watermark is a multi-format library. Beyond Word (.docx, .doc), it supports:

- **PDF**: The most requested format for document protection
- **Excel**: Watermark spreadsheets (.xlsx, .xls) on sheets or within cells
- **PowerPoint**: Add watermarks to presentation slides (.pptx, .ppt)
- **Images**: Directly watermark image files (JPG, PNG, GIF, TIFF, BMP)
- **Visio**: Protect Visio diagrams (.vsdx, .vsd)

The API structure is similar across formats, so once you understand the Word implementation, adapting to PDF or Excel is straightforward. Just swap `WordProcessingContent` for `PdfContent` or `SpreadsheetContent`.

### Is it possible to add multiple watermarks to a single document?

Yes, and there are two ways to do this:

**Multiple Watermarks per Image**: Call `.Add()` multiple times on the same image:

```csharp
shape.Image.Add(copyrightWatermark);
shape.Image.Add(confidentialWatermark);
shape.Image.Add(draftWatermark);
```

This stacks watermarks on top of each other. Useful for combining copyright notices with confidentiality labels.

**Different Watermarks per Image**: Use conditional logic:

```csharp
if (shape.Image.Width > 500)
{
    shape.Image.Add(largeImageWatermark);
}
else
{
    shape.Image.Add(smallImageWatermark);
}
```

This lets you tailor watermarks based on image properties, positions, or even content (if you're doing image analysis).

**Best Practice**: Don't overdo it. More than 2-3 watermarks per image starts looking cluttered and defeats the purpose. Focus on clarity over quantity.

### Can I remove watermarks from documents using GroupDocs.Watermark?

Yes, the library includes watermark detection and removal capabilities. This is useful for:

- Cleaning up documents before republishing
- Removing outdated confidentiality labels
- Updating copyright notices to newer versions

**Basic Removal Example**:

```csharp
using (Watermarker watermarker = new Watermarker("document.docx"))
{
    var watermarks = watermarker.Search(); // Finds all watermarks
    watermarks.Clear(); // Removes all
    watermarker.Save("clean_document.docx");
}
```

**Selective Removal**:

```csharp
var watermarks = watermarker.Search(new TextFormattingSearchCriteria("DRAFT"));
foreach (var watermark in watermarks)
{
    watermark.Remove();
}
```

**Important Note**: Removal works best on watermarks added by GroupDocs.Watermark. Manually added watermarks (like those inserted directly in Word) might not be detectable. The library uses metadata and pattern recognition to identify watermarks it can safely remove.

### Does GroupDocs.Watermark provide cross-platform compatibility?

Yes, the library is built on .NET Standard 2.0, which means it runs on:

- **Windows**: .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5/6/7/8
- **Linux**: .NET Core 2.0+, .NET 5/6/7/8 (fully supported)
- **macOS**: .NET Core 2.0+, .NET 5/6/7/8 (fully supported)

**Deployment Scenarios**:
- Desktop applications (WPF, WinForms, Avalonia)
- ASP.NET web applications (Framework or Core)
- Console applications and background services
- Docker containers (Linux or Windows containers)
- Azure Functions, AWS Lambda, or other serverless platforms

**One Caveat**: Some advanced font rendering features work best on Windows due to GDI+ dependencies. For maximum cross-platform consistency, stick to common system fonts (Arial, Times New Roman, Courier) that are available across all operating systems. If you're using custom fonts, make sure they're installed on your Linux/Mac servers or include them as embedded resources.

The library handles platform-specific file path formatting automatically, so you don't need to worry about Windows backslashes vs. Unix forward slashes—just use `Path.Combine()` and it works everywhere.