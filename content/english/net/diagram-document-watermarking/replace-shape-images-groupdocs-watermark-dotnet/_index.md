---
title: "How to Automate Image Replacement in Visio Diagrams Using .NET"
linktitle: "Replace Visio Diagram Images .NET"
description: "Learn how to programmatically replace images in Visio diagrams using .NET. Step-by-step guide with code examples, troubleshooting tips, and real-world applications for automating diagram updates."
keywords: "replace images in Visio diagrams programmatically, update diagram images .NET, modify Visio shape images C#, change diagram graphics programmatically, automate diagram image updates"
date: "2025-01-02"
lastmod: "2025-01-02"
weight: 1
url: "/net/diagram-document-watermarking/replace-shape-images-groupdocs-watermark-dotnet/"
categories: ["Document Automation"]
tags: ["visio-automation", "diagram-manipulation", "image-replacement", "dotnet-libraries"]
type: docs
---

# How to Automate Image Replacement in Visio Diagrams Using .NET

## Introduction

Ever had to update a company logo across dozens of Visio diagrams? Or maybe you're managing technical documentation where product images need refreshing every quarter? Doing this manually is tedious, error-prone, and—let's be honest—a terrible use of your time.

Here's the thing: replacing images in diagram shapes programmatically sounds complicated, but with the right .NET library, it's actually pretty straightforward. Whether you're updating branding elements, correcting outdated visuals, or automating document workflows, you can handle it all through code.

In this guide, I'll show you how to use GroupDocs.Watermark for .NET to replace shape images in Visio and other diagram formats automatically. You'll learn the complete process—from setup to implementation—plus troubleshooting tips and real-world use cases you can apply immediately.

**What You'll Learn:**
- How to set up your .NET environment for diagram manipulation
- Step-by-step code implementation for replacing shape images
- Which diagram formats are supported (and which aren't)
- Common mistakes to avoid when automating image replacement
- When this approach makes sense vs. manual editing
- Performance optimization for bulk operations

Let's start by making sure you've got everything you need before writing any code.

## Prerequisites

Before you dive in, here's what you'll need on your machine:

### Required Libraries and Tools
- **GroupDocs.Watermark for .NET**: This is your main library for manipulating diagram images (yeah, the name says "watermark" but it does way more than that—more on this below)
- **.NET Framework 4.6.1+ or .NET Core 2.0+**: Make sure your project targets a compatible version
- **Visual Studio 2019+** or **Visual Studio Code**: Any modern C# IDE will work

### Environment Setup Requirements
- A code editor with NuGet package management
- Basic C# project structure (console app or ASP.NET project both work fine)
- File system access for reading source diagrams and saving modified versions

### Knowledge Prerequisites
You should be comfortable with:
- Basic C# syntax and object-oriented programming
- Working with NuGet packages
- File I/O operations in .NET
- Understanding of try-catch error handling (you'll need it for production scenarios)

Don't worry if you're not a Visio expert—you don't need to understand diagram internals. The library handles that complexity for you.

## Why Use a Watermark Library for Image Replacement?

I know what you're thinking: "Why am I using a watermark library to replace images?" Fair question.

GroupDocs.Watermark was originally built for adding watermarks to documents, but it gained powerful content manipulation capabilities along the way. Here's why it's actually perfect for image replacement:

1. **Deep Format Understanding**: It doesn't just overlay content—it understands the internal structure of diagram formats like Visio (VSD, VSDX), which means it can access and modify shape properties directly
2. **Shape-Level Access**: Unlike simple image editors, it lets you target specific shapes within diagrams and replace their embedded images
3. **Format Preservation**: It maintains all diagram properties, connections, and metadata while updating images
4. **No External Dependencies**: You don't need Visio installed on your server to manipulate Visio files

Think of it as a Swiss Army knife for document manipulation that happens to include watermarking as one feature among many. The "watermark" in the name is a bit misleading for what it can actually do.

## Supported Diagram Formats

Before you start coding, make sure your diagram files are in a supported format. Here's what works with GroupDocs.Watermark:

**Fully Supported Formats:**
- **VSD**: Legacy Visio binary format (pre-2013)
- **VSDX**: Modern Visio format (2013 and later) - this is what you'll use most often
- **VSS**: Visio stencil files
- **VSSX**: Visio stencil XML format
- **VDX**: Visio XML drawing format

**Important Limitations:**
- **PDF exports of diagrams**: Not supported—once exported to PDF, the shape structure is flattened
- **Image formats (PNG, JPG)**: Obviously not supported—these aren't diagrams with editable shapes
- **Third-party diagram tools**: Limited support—stick with actual Visio formats for best results

**Pro Tip**: If you're working with mixed formats, check the file extension before processing. VSDX files are the safest bet and offer the best compatibility with modern Visio versions.

## Setting Up GroupDocs.Watermark for .NET

Alright, let's get the library installed. You've got three options here—pick whichever fits your workflow:

### Installation Options

**Option 1: Using .NET CLI** (my preferred method for scripting)
```bash
dotnet add package GroupDocs.Watermark
```

**Option 2: Using Package Manager Console** (if you're in Visual Studio)
```powershell
Install-Package GroupDocs.Watermark
```

**Option 3: NuGet Package Manager UI** (for those who like clicking buttons)
1. Right-click your project in Solution Explorer
2. Select "Manage NuGet Packages"
3. Search for "GroupDocs.Watermark"
4. Click Install on the latest stable version

### License Acquisition

Here's the deal with licensing—you've got options depending on your needs:

**For Testing/Development:**
- Start with the free trial (comes with some limitations on document processing)
- Perfect for evaluating if this solution fits your use case

**For Production:**
1. Get a temporary license for extended testing: [Request here](https://purchase.groupdocs.com/temporary-license)
2. Purchase a full license for commercial projects
3. Apply the license in your code before processing documents

### Basic Initialization and Setup

Once installed, here's your basic setup pattern. This is what you'll use as the foundation for all diagram operations:

```csharp
using GroupDocs.Watermark;

// Initialize watermarker with an input file path
Watermarker watermarker = new Watermarker("inputFilePath");
```

**Important Note**: Always wrap your `Watermarker` instance in a `using` statement (or call `Dispose()` manually) to prevent memory leaks. Diagram files can be large, and you don't want them hanging around in memory.

Now you're ready to start replacing images. Let's get into the actual implementation.

## Implementation Guide

### Overview

This walkthrough shows you exactly how to replace images within diagram shapes. The process is more straightforward than you might expect—we'll load a diagram, find shapes with images, swap them out, and save the result.

This approach works great for batch operations where you need to update multiple diagrams with consistent changes (like logo updates across an entire documentation set).

#### Step 1: Load the Diagram File

First, set up your file paths and loading options. Pay attention to these paths—getting them wrong is the #1 cause of "file not found" errors:

```csharp
using GroupDocs.Watermark.Contents.Diagram;
using System.IO;

DiagramLoadOptions loadOptions = new DiagramLoadOptions();
string documentPath = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
```

**What's Happening Here:**
- `DiagramLoadOptions` tells the library you're working with diagram files (not PDFs or Word docs)
- `documentPath` should point to your source diagram file
- `outputDirectory` is where your modified diagram will be saved

**Gotcha Alert**: Make sure your output directory exists before running this code. The library won't create it automatically, and you'll get a cryptic error if it's missing.

#### Step 2: Initialize Watermarker

Create your `Watermarker` instance with the diagram file. This is where the library loads and parses the file structure:

```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Proceed with accessing diagram content
}
```

**Why the `using` Statement Matters:**
Diagram files can be memory-intensive, especially complex Visio drawings with lots of shapes. The `using` statement ensures resources are released properly when you're done, even if an exception occurs.

#### Step 3: Access Diagram Content

Now we're getting into the diagram structure. This line gives you access to all pages and shapes:

```csharp
DiagramContent content = watermarker.GetContent<DiagramContent>();
```

**Understanding Diagram Content:**
Think of `DiagramContent` as your gateway to everything inside the diagram. It contains collections of pages, and each page contains shapes. You can access any shape on any page from here.

#### Step 4: Iterate Through Shapes

Here's where the actual replacement happens. We'll loop through shapes on the first page and swap out any images we find:

```csharp
foreach (DiagramShape shape in content.Pages[0].Shapes)
{
    if (shape.Image != null)
    {
        // Replace existing image with a new one from specified source
        shape.Image = new DiagramWatermarkableImage(File.ReadAllBytes("YOUR_DOCUMENT_DIRECTORY/TestPng.png"));
    }
}
```

**Breaking This Down:**
- `content.Pages[0]` accesses the first page (index starts at 0)
- We check `if (shape.Image != null)` to make sure the shape actually contains an image before trying to replace it
- `File.ReadAllBytes()` loads your replacement image as a byte array
- `DiagramWatermarkableImage` is the wrapper that makes the image compatible with diagram shapes

**Common Question**: "What if I want to replace only specific images, not all of them?"

You'd add additional logic inside the loop to identify target shapes. For example, you might check shape names, dimensions, or position before replacing:

```csharp
if (shape.Image != null && shape.Name == "CompanyLogo")
{
    // Replace only shapes named "CompanyLogo"
    shape.Image = new DiagramWatermarkableImage(File.ReadAllBytes("new-logo.png"));
}
```

**Processing Multiple Pages:**
The example only processes `Pages[0]`. If your diagrams have multiple pages, you'll need to loop through all pages:

```csharp
foreach (DiagramPage page in content.Pages)
{
    foreach (DiagramShape shape in page.Shapes)
    {
        if (shape.Image != null)
        {
            shape.Image = new DiagramWatermarkableImage(File.ReadAllBytes("replacement.png"));
        }
    }
}
```

#### Step 5: Save the Modified Diagram

Finally, write your changes to a new file. Never overwrite the original until you're 100% sure your code works correctly:

```csharp
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

**Best Practice**: Use a different output directory or filename prefix (like "modified_") during development. This way, you can compare before/after results and you always have the original to fall back on if something goes wrong.

### Complete Working Example

Here's everything put together in a single, ready-to-use method:

```csharp
using GroupDocs.Watermark;
using GroupDocs.Watermark.Contents.Diagram;
using System.IO;

public class DiagramImageReplacer
{
    public void ReplaceShapeImages(string inputPath, string outputPath, string newImagePath)
    {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        using (Watermarker watermarker = new Watermarker(inputPath, loadOptions))
        {
            DiagramContent content = watermarker.GetContent<DiagramContent>();
            byte[] newImageBytes = File.ReadAllBytes(newImagePath);
            
            foreach (DiagramPage page in content.Pages)
            {
                foreach (DiagramShape shape in page.Shapes)
                {
                    if (shape.Image != null)
                    {
                        shape.Image = new DiagramWatermarkableImage(newImageBytes);
                    }
                }
            }
            
            watermarker.Save(outputPath);
        }
    }
}
```

### Troubleshooting Tips

**Problem**: "File not found" errors
- **Solution**: Use absolute paths during development, not relative paths. Print your paths to the console to verify they're correct.

**Problem**: Output file is corrupted or won't open
- **Solution**: Make sure you're not modifying the file while Visio has it open. Close all instances of the source file before processing.

**Problem**: Some shapes aren't being updated
- **Solution**: Not all shapes contain images—some might be text boxes or connectors. Add logging to see which shapes are being skipped and why.

**Problem**: Memory exceptions with large diagrams
- **Solution**: Process diagrams one at a time rather than loading multiple simultaneously. Dispose of resources properly using `using` statements.

## Common Mistakes to Avoid

Let me save you some debugging time by highlighting the mistakes I see most often:

### 1. Forgetting to Check for Null Images
**The Mistake:**
```csharp
foreach (DiagramShape shape in content.Pages[0].Shapes)
{
    // This will throw NullReferenceException on shapes without images
    shape.Image = new DiagramWatermarkableImage(newImageBytes);
}
```

**The Fix:**
Always check if `shape.Image` exists before attempting replacement. Not every shape contains an image—some are text, connectors, or containers.

### 2. Using the Wrong Image Format
**The Mistake:** Trying to use vector formats (SVG, EPS) directly without conversion.

**The Reality:** GroupDocs.Watermark works best with raster formats (PNG, JPG, BMP). If you need to use vector graphics, convert them to PNG first at an appropriate resolution.

### 3. Ignoring Image Dimensions
**The Mistake:** Replacing a 100x100px logo with a 2000x2000px image without considering aspect ratio.

**The Result:** Distorted or improperly scaled images in your diagrams.

**The Fix:** Pre-process your replacement images to match the aspect ratio of the originals, or accept that some manual adjustment might be needed afterward.

### 4. Not Handling Exceptions
**The Mistake:**
```csharp
// No try-catch means one failed diagram crashes your entire batch process
watermarker.Save(outputPath);
```

**The Fix:**
```csharp
try
{
    watermarker.Save(outputPath);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to process {inputPath}: {ex.Message}");
    // Log error and continue with next file
}
```

### 5. Modifying Original Files Directly
**Why It's Dangerous:** One bug in your code could corrupt important source files with no way to recover them.

**Better Approach:** Always save to a new location first, verify the output looks correct, then replace originals if needed.

## When to Use This Approach

This automation isn't always the right solution. Here's when it makes sense (and when it doesn't):

### Perfect Use Cases ✅

**1. Bulk Branding Updates**
You've got 50+ diagrams with the old company logo that all need updating. Manual editing would take days—automation takes minutes.

**2. Automated Documentation Pipelines**
Your CI/CD system generates technical diagrams with placeholder images that need replacing with actual product screenshots before deployment.

**3. Regular Refresh Cycles**
Monthly or quarterly updates to product images, charts, or status indicators across documentation sets.

**4. Template-Based Generation**
Creating multiple diagrams from templates where only the images change (like org charts with employee photos).

### When Manual Editing Is Better ❌

**1. One-Off Changes**
Updating a single diagram once? Just open Visio and do it manually. The setup time for automation isn't worth it.

**2. Complex Design Decisions**
If each image replacement requires judgment calls about placement, sizing, or composition, automation will create more work than it saves.

**3. Highly Customized Layouts**
Diagrams where each shape has unique properties that need manual adjustment after image replacement.

**4. Learning Purposes**
If you're trying to learn Visio itself, manually working with shapes is more educational than scripting it.

### The Decision Matrix

Ask yourself:
- **How many diagrams?** (Less than 5 = manual, 10+ = automate)
- **How often?** (Once = manual, recurring = automate)
- **How complex?** (Simple swaps = automate, design work = manual)
- **Is consistency critical?** (Yes = automate, No = either works)

## Practical Applications

Let's look at real-world scenarios where this approach shines:

### 1. Corporate Rebranding Projects
**The Scenario:** Your company just rolled out a new logo, and it needs to appear in 200+ technical diagrams, flowcharts, and process maps.

**The Solution:**
- Identify all diagram files in your document repository
- Use this code to batch-process them overnight
- QA team reviews a sample of outputs the next morning
- Deploy updated diagrams to your documentation portal

**Time Saved:** What would take weeks of manual work becomes a couple of hours of scripting plus review time.

### 2. Product Documentation Automation
**The Scenario:** You maintain technical docs where diagrams show product interfaces that change with each release.

**The Implementation:**
```csharp
// Part of your build pipeline
public void UpdateProductScreenshots(string diagramsFolder, string screenshotsFolder)
{
    var diagrams = Directory.GetFiles(diagramsFolder, "*.vsdx");
    var replacementImage = Path.Combine(screenshotsFolder, "latest-ui.png");
    
    foreach (var diagram in diagrams)
    {
        var outputPath = diagram.Replace(".vsdx", "_updated.vsdx");
        ReplaceShapeImages(diagram, outputPath, replacementImage);
    }
}
```

**The Benefit:** Every build automatically updates diagrams with the latest UI screenshots. No manual intervention needed.

### 3. Multi-Language Documentation
**The Scenario:** You maintain documentation in 10 languages, with localized screenshots in diagrams for each language.

**The Approach:**
- Keep master diagrams with English screenshots
- Run automated replacement for each language variant
- Generate language-specific versions in your build process

### 4. Dynamic Report Generation
**The Scenario:** Monthly executive reports with network diagrams that need current status indicators (green/yellow/red dots for system health).

**The Automation:**
- Template diagrams contain placeholder status indicators
- Script pulls current system health from monitoring API
- Replaces placeholders with appropriate colored indicators
- Generates ready-to-present reports automatically

### 5. Design System Maintenance
**The Scenario:** You've updated icon sets or UI components that appear in architecture diagrams across multiple projects.

**The Process:**
- Catalog all diagrams using the old icon set
- Prepare replacement images in a consistent format
- Batch-process all affected diagrams
- Version control both old and new sets for rollback capability

**Industry-Specific Example: Healthcare**
Medical device companies often maintain huge libraries of technical diagrams showing device configurations. When a component design changes, dozens of diagrams need updating. Automation ensures consistency and reduces the risk of outdated information in critical documentation.

## Performance Considerations

When you're processing large batches of diagrams or working with complex files, performance matters. Here's how to keep things running smoothly:

### Optimize Image Sizes Before Processing

**The Problem:** Loading a 5MB replacement image to swap into a shape that's 200x200 pixels on screen.

**The Solution:**
```csharp
// Pre-process images to appropriate sizes before replacement
public byte[] OptimizeImageForDiagram(string imagePath, int maxWidth, int maxHeight)
{
    // Use System.Drawing or ImageSharp to resize
    // This example is conceptual—implement based on your image library
    var optimized = ResizeImage(imagePath, maxWidth, maxHeight);
    return optimized;
}
```

**Why This Matters:** Smaller images mean less memory usage, faster processing, and smaller output files. A 200KB PNG works just as well as a 5MB one for diagram shapes.

### Memory Management for Batch Operations

**The Anti-Pattern:**
```csharp
// DON'T DO THIS—loads all files into memory at once
var watermarkers = new List<Watermarker>();
foreach (var file in GetAllDiagrams())
{
    watermarkers.Add(new Watermarker(file, loadOptions)); // Memory leak waiting to happen
}
```

**The Right Way:**
```csharp
// Process one at a time, dispose immediately
foreach (var file in GetAllDiagrams())
{
    using (var watermarker = new Watermarker(file, loadOptions))
    {
        ProcessDiagram(watermarker);
        watermarker.Save(GetOutputPath(file));
    } // Disposed here, memory released
}
```

**Rule of Thumb:** Never hold more than 2-3 large diagram objects in memory simultaneously. Process sequentially and dispose promptly.

### Parallel Processing Considerations

**When It Helps:**
If you're processing 100+ independent diagram files and have multiple CPU cores available, parallel processing can significantly speed things up:

```csharp
Parallel.ForEach(diagramFiles, new ParallelOptions { MaxDegreeOfParallelism = 4 }, file =>
{
    using (var watermarker = new Watermarker(file, loadOptions))
    {
        ProcessDiagram(watermarker);
        watermarker.Save(GetOutputPath(file));
    }
});
```

**When to Avoid It:**
- If your replacement images are huge (parallel processing will multiply memory usage)
- When processing from/to network shares (I/O becomes the bottleneck, not CPU)
- On systems with limited RAM (sequential processing is safer)

### Benchmarking Your Scenario

Performance varies based on:
- **Diagram complexity**: More shapes = longer processing time
- **File size**: 50KB files vs. 10MB files behave very differently
- **Image size**: Replacement image dimensions affect memory usage
- **Storage speed**: SSD vs. HDD vs. network share makes a huge difference

**Quick Test:**
```csharp
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
ProcessDiagram(testFile);
stopwatch.Stop();
Console.WriteLine($"Processing took {stopwatch.ElapsedMilliseconds}ms");
```

Run this on a representative sample of your diagrams to establish baseline performance. If a single diagram takes more than 5 seconds, investigate why before scaling up.

### Practical Performance Tips

1. **Cache replacement image bytes**: Don't read the same image file repeatedly if you're using it in multiple diagrams
2. **Use appropriate image formats**: PNG with transparency when needed, JPG for photos
3. **Monitor memory usage**: Use Task Manager or perfmon to watch for memory leaks during development
4. **Consider storage location**: Local SSD processing is 10-50x faster than network shares
5. **Batch strategically**: Process 50-100 files at a time rather than all 1000 at once

## Conclusion

You've now got a complete blueprint for automating image replacement in Visio diagrams using .NET. Let's recap the key points:

**What We Covered:**
- Setting up GroupDocs.Watermark for .NET in your development environment
- Understanding why a "watermark" library is actually perfect for image manipulation
- Implementing shape image replacement with production-ready code
- Avoiding common pitfalls that trip up developers
- Optimizing performance for batch operations
- Identifying scenarios where automation makes sense (and where it doesn't)

**The Bottom Line:**
If you're facing bulk diagram updates, recurring image refreshes, or need to integrate diagram modification into automated workflows, this approach will save you significant time and reduce errors compared to manual editing.

**Next Steps:**

1. **Try it yourself**: Start with a simple test—grab a sample Visio file and run through the implementation guide
2. **Explore advanced features**: The GroupDocs.Watermark library can do much more than image replacement (check out the API reference for watermarking, text manipulation, and format conversion)
3. **Build it into your workflow**: If you're managing documentation or maintaining design systems, consider how to integrate this into your CI/CD pipeline
4. **Share your results**: Found a clever use case? Hit the GroupDocs community forum and share your implementation

Ready to automate your diagram workflows? The code's right here—give it a shot and see how much time you can reclaim from manual image editing.

**Useful Resources:**
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/net/) - Complete API reference and guides
- [Community Forum](https://forum.groupdocs.com/c/watermark/) - Get help from other developers
- [Download Page](https://releases.groupdocs.com/watermark/net/) - Latest library versions
- [Request Temporary License](https://purchase.groupdocs.com/temporary-license) - For extended evaluation

## FAQ Section

**1. Can I replace images in diagrams other than Visio files?**
Yes, GroupDocs.Watermark supports multiple diagram formats including VSD, VSDX, VSS, VSSX, and VDX. However, VSDX (modern Visio format) offers the best compatibility and reliability.

**2. What happens to the original image aspect ratio when I replace it?**
The new image takes on the dimensions of the shape it's replacing. If your replacement image has a different aspect ratio, it may appear stretched or compressed. Pre-process your images to match the original aspect ratio for best results.

**3. Can I replace only specific images rather than all images in a diagram?**
Absolutely. Add conditional logic in your loop to check shape properties like `Name`, `X`, `Y` position, or `Width`/`Height` before replacing. This lets you target specific shapes while leaving others untouched.

**4. Is it possible to undo changes if something goes wrong?**
Not directly within the code, but this is why you should always save to a different output path during development. Keep your original files intact until you've verified the modified versions are correct.

**5. How do I handle diagrams with multiple pages?**
The example code shows processing only the first page (`Pages[0]`). To process all pages, wrap your shape iteration in an outer loop: `foreach (DiagramPage page in content.Pages)`. This ensures every page gets updated.

**6. What image formats work best for replacement?**
PNG (for images needing transparency) and JPG (for photos) work reliably. Avoid using excessively large images—resize them to appropriate dimensions before replacement to optimize performance and file size.

**7. Can this be used in a web application or does it require desktop installation?**
GroupDocs.Watermark is a .NET library that works in both desktop applications and web applications (ASP.NET, ASP.NET Core). No desktop installation required beyond your development environment.

**8. What should I do if my modified diagrams won't open in Visio?**
This usually indicates a problem during processing. Check that: (1) you're not modifying files while they're open elsewhere, (2) your replacement images are valid and not corrupted, (3) you're disposing of the Watermarker properly, and (4) you have write permissions to the output directory.

**9. How do I handle errors when processing batches of diagrams?**
Wrap each file's processing in a try-catch block so one failed diagram doesn't crash your entire batch. Log errors with details about which file failed and why, then continue processing the rest.

**10. Is there a limit to how many diagrams I can process?**
The library itself doesn't impose hard limits, but your system resources (RAM, CPU) and license terms matter. Free trials typically have document processing limits. For production batch processing, you'll need an appropriate commercial license.

## Resources

**Documentation and Support:**
- **Complete Documentation**: [GroupDocs.Watermark for .NET Docs](https://docs.groupdocs.com/watermark/net/)
- **API Reference**: [GroupDocs API Reference](https://reference.groupdocs.com/watermark/net)
- **Download Library**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/net/)
- **Community Support**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/)
- **Licensing**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license)
