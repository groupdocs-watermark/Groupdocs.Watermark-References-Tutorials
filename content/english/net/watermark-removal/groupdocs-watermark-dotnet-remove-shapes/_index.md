---
title: "Remove Shapes from Diagrams Programmatically in .NET"
linktitle: "Remove Shapes from Diagrams"
description: "Learn how to programmatically remove unwanted shapes, watermarks, and elements from Visio diagrams using .NET. Complete guide with code examples and troubleshooting."
keywords: "remove shapes from diagrams, diagram shape removal, delete Visio shapes, programmatically edit diagrams, remove watermarks from diagrams, GroupDocs Watermark, .NET diagram manipulation"
date: "2025-01-02"
lastmod: "2025-01-02"
weight: 1
url: "/net/watermark-removal/groupdocs-watermark-dotnet-remove-shapes/"
categories: ["Diagram Manipulation", ".NET Development"]
tags: ["shape-removal", "diagram-editing", "visio", "watermark-removal", "automation"]
type: docs
---

# How to Remove Shapes from Diagrams Programmatically in .NET

## Introduction

Ever opened a diagram file only to find it cluttered with outdated logos, unnecessary watermarks, or shapes that no longer serve a purpose? You're not alone. Whether you're maintaining project documentation, updating architectural plans, or preparing diagrams for client presentations, removing unwanted shapes manually can be tedious—especially when you're dealing with dozens (or hundreds) of files.

The good news? You can automate the entire process using .NET. With GroupDocs.Watermark for .NET, you can programmatically identify and remove specific shapes from diagram files in just a few lines of code. This means no more clicking through Visio menus or spending hours cleaning up documentation.

In this guide, you'll discover how to remove shapes from diagrams using two different approaches: by index (when you know the position) or by reference (when you need precision). We'll cover everything from basic setup to advanced batch processing, complete with real-world examples and troubleshooting tips.

**What You'll Learn:**
- Why programmatic shape removal beats manual editing (especially at scale)
- Setting up GroupDocs.Watermark for .NET in your project
- Two methods for removing shapes: index-based and reference-based
- Handling common errors and edge cases
- Batch processing multiple diagram files efficiently
- Performance optimization for large documents

Ready to automate your diagram cleanup workflow? Let's get started.

## Why Remove Shapes Programmatically?

Before we dive into the code, let's talk about why you'd want to automate this process in the first place.

**Common Scenarios Where This Saves You Time:**

1. **Watermark and Logo Removal**: Your company rebranded last year, but all your technical diagrams still have the old logo embedded as shapes. Instead of opening each file individually, you can batch-process them programmatically.

2. **Documentation Updates**: That "Draft" watermark made sense three months ago, but now your diagrams are production-ready. Remove all draft indicators across your entire documentation set automatically.

3. **Client Deliverables**: You've created diagrams with internal notes and reference shapes that aren't meant for client eyes. Strip them out programmatically before delivery.

4. **Legacy System Migration**: You're moving from one diagramming tool to another, and certain shapes (like custom connectors or tool-specific elements) don't translate well. Remove them systematically during migration.

5. **Template Standardization**: Creating diagram templates that need to be identical except for specific shapes. Automate the cleanup to ensure consistency.

The manual alternative? Opening each file, selecting shapes one by one, hitting delete, saving, and repeating. For a handful of files, that's manageable. For 50+ diagrams? That's a full day of mind-numbing work. Automation is the clear winner here.

## Supported Diagram Formats

GroupDocs.Watermark for .NET works with a variety of diagram formats, so you're not locked into a single tool ecosystem:

- **Visio Diagrams**: .VSD, .VSDX, .VSS, .VSSX, .VDX
- **Drawing Files**: .VDW
- **Stencil Files**: .VSS, .VSSX

This flexibility means you can process diagrams from Microsoft Visio, LibreOffice Draw, and other compatible tools using the same code. No need to write separate logic for different file types—the library handles format detection automatically.

## Prerequisites

Before we start removing shapes, make sure you have these basics covered:

### Required Libraries and Dependencies
- **GroupDocs.Watermark for .NET**: This is our main tool for diagram manipulation. It's a commercial library, but it comes with a free trial so you can test everything before committing.

### Environment Setup Requirements
- A development environment with .NET installed (Visual Studio, Visual Studio Code, or Rider all work great)
- Basic familiarity with C# programming—you don't need to be an expert, but understanding classes and methods will help
- A diagram file to work with (if you don't have one handy, you can create a simple test diagram in Visio or download sample files)

### Knowledge Prerequisites
You should be comfortable with:
- Creating and running .NET console applications
- Working with file paths and directories
- Basic C# syntax (using statements, classes, methods)

Don't worry if you're not an expert—we'll explain everything step-by-step.

## Setting Up GroupDocs.Watermark for .NET

Getting the library installed is straightforward. Here are three ways to do it (pick whichever fits your workflow):

**Option 1: Using .NET CLI (My Personal Favorite)**
```bash
dotnet add package GroupDocs.Watermark
```
This is the quickest method if you're working from the terminal or command line.

**Option 2: Using Package Manager Console in Visual Studio**
```powershell
Install-Package GroupDocs.Watermark
```
Great if you prefer Visual Studio's Package Manager.

**Option 3: Via NuGet Package Manager UI**
If you're more of a visual person:
1. Right-click your project in Solution Explorer
2. Select "Manage NuGet Packages"
3. Search for "GroupDocs.Watermark"
4. Click "Install" on the latest stable version

### License Acquisition Steps
Here's the thing about licensing: GroupDocs.Watermark is a commercial product, but you have options:

- **Free Trial**: Download and use it immediately with some limitations (usually output watermarks on processed files)
- **Temporary License**: Request a 30-day full-featured license for evaluation (no watermarks)
- **Commercial License**: Purchase for production use

For learning and testing, the free trial or temporary license is perfect. You can request a temporary license through their website—it's usually approved within a few hours.

### Basic Initialization and Setup
Once you've installed the package, here's the basic pattern you'll use in every example:

```csharp
using GroupDocs.Watermark.Contents.Diagram;
using System.IO;

string documentPath = \@"YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Your shape removal code goes here
}
```

**What's happening here:**
- `DiagramLoadOptions`: Tells the library how to load your diagram (you can specify encoding, password protection, etc.)
- `Watermarker`: The main class that opens your file and lets you manipulate its contents
- `using` statement: Ensures proper cleanup of resources when you're done (important for avoiding memory leaks)

The `Watermarker` class is your gateway to everything—think of it as opening a document in Visio, except you're doing it programmatically.

## Implementation Guide

Now for the fun part—actually removing shapes. We'll cover two different approaches, each suited to different scenarios.

### Method 1: Remove Shape by Index

This is your go-to method when you know exactly which shape you want to remove based on its position in the collection.

#### When to Use This Approach
Use index-based removal when:
- You're working with consistently structured diagrams (e.g., templates where the logo is always shape #3)
- You want to remove the first or last shape without caring about its properties
- You're iterating through shapes and need to remove specific positions

**Real-world example:** Imagine you've got 100 floor plans, and they all have a "Draft" stamp as the first shape on page one. Index-based removal lets you hit all of them with the same code.

#### Step-by-Step Implementation

**Step 1: Load Your Diagram**
First, we need to open the file and access its contents:

```csharp
string documentPath = \@"YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Access the content of the diagram document.
    DiagramContent content = watermarker.GetContent<DiagramContent>();
    
    // Remove the first shape from the first page using its index.
    content.Pages[0].Shapes.RemoveAt(0);
    
    // Save the changes to a new file in the output directory.
    string outputDirectory = \@"YOUR_OUTPUT_DIRECTORY\\";
    string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
    watermarker.Save(outputFileName);
}
```

**Breaking Down the Key Parts:**

- `watermarker.GetContent<DiagramContent>()`: Retrieves the diagram's internal structure so you can work with pages and shapes
- `content.Pages[0]`: Accesses the first page (remember, indexing starts at 0 in C#)
- `Shapes.RemoveAt(0)`: Removes the shape at index 0 (the first shape in the collection)
- `watermarker.Save(outputFileName)`: Writes the modified diagram to a new file

**Pro Tip:** Always save to a new file initially while you're testing. There's nothing worse than accidentally corrupting your only copy of an important diagram. Once you're confident everything works, you can overwrite the original if needed.

#### Parameters Explained
Let's clarify what each parameter does:

- **`DiagramLoadOptions`**: Configuration for how the diagram should be loaded. You can set properties like password protection here if your diagrams are encrypted.
- **`content.Pages[0]`**: Page indexing is zero-based. Pages[0] is page 1, Pages[1] is page 2, etc.
- **`Shapes.RemoveAt(0)`**: Shape indexing is also zero-based. The first shape is at index 0.

#### Common Pitfalls and Solutions

**Problem 1: IndexOutOfRangeException**
This happens when you try to remove a shape that doesn't exist.

```csharp
// BAD: Assuming there are at least 5 shapes
content.Pages[0].Shapes.RemoveAt(4); // Crashes if fewer than 5 shapes exist

// GOOD: Check the count first
if (content.Pages[0].Shapes.Count > 4)
{
    content.Pages[0].Shapes.RemoveAt(4);
}
```

**Problem 2: Wrong Page Index**
Multi-page diagrams can be tricky. Always verify which page contains the shape you want to remove.

```csharp
// List all pages and their shape counts for debugging
for (int i = 0; i < content.Pages.Count; i++)
{
    Console.WriteLine($"Page {i + 1} has {content.Pages[i].Shapes.Count} shapes");
}
```

**Problem 3: File Path Issues**
Windows paths can be finicky with backslashes. Use verbatim strings (@"...") or Path.Combine() to avoid headaches:

```csharp
// GOOD options:
string path1 = \@"C:\Projects\Diagrams\sample.vsdx";
string path2 = Path.Combine("C:", "Projects", "Diagrams", "sample.vsdx");

// BAD (won't work):
string path3 = "C:\Projects\Diagrams\sample.vsdx"; // Escape character issues
```

### Method 2: Remove Shape by Reference

This approach is more precise—you're targeting a specific shape object rather than just a position in the list.

#### When to Use This Approach
Use reference-based removal when:
- You need to identify shapes by their properties (name, text, size, etc.)
- You're searching for specific shapes to remove (e.g., all shapes containing "Confidential")
- The position of shapes varies between files

**Real-world example:** You've got architectural diagrams where revision notes are scattered randomly throughout the page. You can't use index-based removal because their positions aren't consistent. Instead, you search for shapes containing "Revision:" in their text and remove them by reference.

#### Step-by-Step Implementation

Here's how to remove a shape using its reference:

```csharp
string documentPath = \@"YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Access the content of the diagram document.
    DiagramContent content = watermarker.GetContent<DiagramContent>();
    
    // Remove the first shape from the first page by referencing it directly.
    content.Pages[0].Shapes.Remove(content.Pages[0].Shapes[0]);
    
    // Save the changes to a new file in the output directory.
    string outputDirectory = \@"YOUR_OUTPUT_DIRECTORY\\";
    string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
    watermarker.Save(outputFileName);
}
```

This example looks similar to the index-based approach, but the key difference is the `Remove()` method instead of `RemoveAt()`. Let me show you a more practical example that highlights why references are powerful:

```csharp
// Find and remove all shapes containing specific text
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    DiagramContent content = watermarker.GetContent<DiagramContent>();
    
    foreach (var page in content.Pages)
    {
        var shapesToRemove = new List<DiagramShape>();
        
        // Find shapes that match your criteria
        foreach (var shape in page.Shapes)
        {
            if (shape.Text != null && shape.Text.Contains("DRAFT"))
            {
                shapesToRemove.Add(shape);
            }
        }
        
        // Remove them by reference
        foreach (var shape in shapesToRemove)
        {
            page.Shapes.Remove(shape);
        }
    }
    
    watermarker.Save(outputFileName);
}
```

**Why the extra list?** You can't modify a collection while iterating through it—that causes a runtime error. By collecting references first and then removing them in a separate loop, you avoid this issue.

#### Parameters Explained

- **`content.Pages[0].Shapes.Remove(...)`**: Takes a reference to the specific shape object you want to remove
- **`shape.Text`**: Access to the shape's text content (useful for filtering)
- **`shapesToRemove` list**: Temporary storage to avoid modifying the collection during iteration

#### Advanced Filtering Examples

Here are some other ways to identify shapes for removal:

**By Shape Name:**
```csharp
if (shape.Name == "Watermark" || shape.Name == "Logo")
{
    shapesToRemove.Add(shape);
}
```

**By Size (Remove Small Shapes):**
```csharp
if (shape.Width < 50 && shape.Height < 50)
{
    shapesToRemove.Add(shape); // Remove tiny shapes
}
```

**By Position (Remove Shapes in a Specific Area):**
```csharp
if (shape.X < 100 && shape.Y < 100)
{
    shapesToRemove.Add(shape); // Remove shapes in top-left corner
}
```

#### Troubleshooting Tips

**Problem: NullReferenceException on shape.Text**
Not all shapes have text. Always check for null:

```csharp
if (shape.Text != null && shape.Text.Contains("DRAFT"))
{
    // Safe to process
}
```

**Problem: Nothing Gets Removed**
Double-check your filtering logic. Add debug output to see what's being found:

```csharp
Console.WriteLine($"Found {shapesToRemove.Count} shapes to remove");
foreach (var shape in shapesToRemove)
{
    Console.WriteLine($"Removing shape: {shape.Name ?? "Unnamed"}, Text: {shape.Text ?? "No text"}");
}
```

## Batch Processing Multiple Files

Real-world diagram management rarely involves just one file. Let's tackle the scenario where you need to process an entire directory of diagrams.

```csharp
using System;
using System.IO;
using GroupDocs.Watermark;
using GroupDocs.Watermark.Contents.Diagram;

public class BatchDiagramProcessor
{
    public static void RemoveFirstShapeFromAllDiagrams(string inputDirectory, string outputDirectory)
    {
        // Create output directory if it doesn't exist
        Directory.CreateDirectory(outputDirectory);
        
        // Get all diagram files (add more extensions if needed)
        string[] extensions = { "*.vsdx", "*.vsd", "*.vdx" };
        var diagramFiles = new List<string>();
        
        foreach (var extension in extensions)
        {
            diagramFiles.AddRange(Directory.GetFiles(inputDirectory, extension));
        }
        
        Console.WriteLine($"Found {diagramFiles.Count} diagram files to process");
        
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        int processedCount = 0;
        int errorCount = 0;
        
        foreach (var filePath in diagramFiles)
        {
            try
            {
                using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
                {
                    DiagramContent content = watermarker.GetContent<DiagramContent>();
                    
                    // Check if there are shapes to remove
                    if (content.Pages.Count > 0 && content.Pages[0].Shapes.Count > 0)
                    {
                        content.Pages[0].Shapes.RemoveAt(0);
                        
                        string outputPath = Path.Combine(outputDirectory, Path.GetFileName(filePath));
                        watermarker.Save(outputPath);
                        
                        processedCount++;
                        Console.WriteLine($"✓ Processed: {Path.GetFileName(filePath)}");
                    }
                    else
                    {
                        Console.WriteLine($"⚠ Skipped (no shapes): {Path.GetFileName(filePath)}");
                    }
                }
            }
            catch (Exception ex)
            {
                errorCount++;
                Console.WriteLine($"✗ Error processing {Path.GetFileName(filePath)}: {ex.Message}");
            }
        }
        
        Console.WriteLine($"\nBatch processing complete:");
        Console.WriteLine($"  Successfully processed: {processedCount}");
        Console.WriteLine($"  Errors encountered: {errorCount}");
    }
}
```

**Key Features of This Batch Processor:**
1. Handles multiple file extensions automatically
2. Creates the output directory if it doesn't exist
3. Includes error handling so one bad file doesn't crash the entire batch
4. Provides progress feedback so you know what's happening
5. Skips files without shapes (instead of crashing)

**Usage:**
```csharp
BatchDiagramProcessor.RemoveFirstShapeFromAllDiagrams(
    \@"C:\Diagrams\Input",
    \@"C:\Diagrams\Cleaned"
);
```

## Performance Considerations

When you're processing large diagrams or batches of files, performance matters. Here are some tips to keep things running smoothly:

### Memory Management
The `using` statement is your friend—it ensures that file handles and memory are released properly:

```csharp
// GOOD: Automatic cleanup
using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
{
    // Do work
} // Resources released here automatically

// BAD: Manual cleanup required (easy to forget)
Watermarker watermarker = new Watermarker(filePath, loadOptions);
// Do work
watermarker.Dispose(); // Must remember to call this!
```

### Optimizing for Large Diagram Files
If you're working with huge diagrams (50+ MB), consider:

1. **Process one file at a time** rather than loading multiple files into memory
2. **Use shape filters efficiently** to minimize iteration over collections
3. **Save incrementally** if making multiple changes to avoid keeping everything in memory

### Parallel Processing (Advanced)
For truly massive batches, you can process multiple files simultaneously:

```csharp
Parallel.ForEach(diagramFiles, new ParallelOptions { MaxDegreeOfParallelism = 4 }, filePath =>
{
    // Your processing code here
});
```

**Warning:** Don't go overboard with parallelism. More threads doesn't always mean faster processing—4-8 parallel operations is usually the sweet spot.

### Benchmarking Your Code
If performance is critical, measure it:

```csharp
var stopwatch = System.Diagnostics.Stopwatch.StartNew();

// Your processing code

stopwatch.Stop();
Console.WriteLine($"Processed in {stopwatch.ElapsedMilliseconds}ms");
```

## Practical Applications

Let's look at some real-world scenarios where these techniques shine:

### 1. Project Documentation Cleanup
**Scenario:** Your team has 200 technical diagrams that still have the old company watermark.

**Solution:** Use batch processing with reference-based removal to find and remove all shapes containing the old logo text.

**Impact:** What would have taken days of manual work is done in minutes.

### 2. Architectural Plan Updates
**Scenario:** Floor plans need to be updated to remove temporary partitions that are being demolished.

**Solution:** If partitions are consistently placed as specific shape indices, use index-based removal. If they vary, use reference-based with position filtering.

**Impact:** Consistent, error-free updates across all plans.

### 3. Client Deliverable Preparation
**Scenario:** Internal diagrams have notes and annotations that aren't meant for client eyes.

**Solution:** Filter shapes by text content (e.g., "Internal Only") and remove them by reference before generating PDFs.

**Impact:** Professional, clean deliverables every time.

### 4. Legacy System Migration
**Scenario:** Migrating from an old diagramming tool, and certain proprietary shapes don't convert properly.

**Solution:** Identify problematic shapes by properties (size, name patterns) and remove them automatically during migration.

**Impact:** Smooth migration with minimal manual intervention.

## Common Issues and Solutions

### Issue 1: "File is being used by another process"
**Cause:** The file is open in Visio or another program.

**Solution:** Close all applications using the file, or use a more robust file handling approach:
```csharp
int maxRetries = 3;
for (int i = 0; i < maxRetries; i++)
{
    try
    {
        using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
        {
            // Process file
            break; // Success, exit retry loop
        }
    }
    catch (IOException)
    {
        if (i == maxRetries - 1) throw;
        System.Threading.Thread.Sleep(1000); // Wait 1 second before retry
    }
}
```

### Issue 2: Output file is corrupt
**Cause:** Error occurred during save, or output directory doesn't exist.

**Solution:** Always check directory existence and handle save errors:
```csharp
try
{
    Directory.CreateDirectory(Path.GetDirectoryName(outputPath));
    watermarker.Save(outputPath);
}
catch (Exception ex)
{
    Console.WriteLine($"Save failed: {ex.Message}");
    // Consider implementing a fallback location
}
```

### Issue 3: License errors
**Cause:** License file not found, expired, or incorrectly configured.

**Solution:** Set up licensing at the start of your application:
```csharp
GroupDocs.Watermark.License license = new GroupDocs.Watermark.License();
try
{
    license.SetLicense("path-to-your-license-file.lic");
}
catch (Exception ex)
{
    Console.WriteLine($"License error: {ex.Message}");
    Console.WriteLine("Running in trial mode with limitations.");
}
```

### Issue 4: Shapes not being removed as expected
**Cause:** Usually an indexing or filtering issue.

**Solution:** Add diagnostic output to see what's actually happening:
```csharp
Console.WriteLine($"Total pages: {content.Pages.Count}");
for (int i = 0; i < content.Pages.Count; i++)
{
    Console.WriteLine($"Page {i}: {content.Pages[i].Shapes.Count} shapes");
    for (int j = 0; j < content.Pages[i].Shapes.Count; j++)
    {
        var shape = content.Pages[i].Shapes[j];
        Console.WriteLine($"  Shape {j}: Name='{shape.Name}', Text='{shape.Text}'");
    }
}
```

## Conclusion

You've now got the complete toolkit for removing shapes from diagrams programmatically. Let's recap what you've learned:

- **Index-based removal** is perfect for consistently structured diagrams where you know exactly which position to target
- **Reference-based removal** gives you precision when you need to identify shapes by their properties
- **Batch processing** scales your solution from one-off fixes to enterprise-level automation
- **Error handling** keeps your code robust when dealing with real-world files

The beauty of this approach is that you've eliminated manual grunt work. Instead of spending hours clicking through Visio, you can now process entire directories of diagrams in minutes. That's time you can spend on actual problem-solving rather than repetitive tasks.

**Next Steps to Master Diagram Automation:**
1. Start with a small batch of test files to validate your setup
2. Experiment with different filtering criteria to match your specific needs
3. Build reusable functions for your most common shape removal patterns
4. Integrate this capability into your existing documentation pipelines

Ready to take your automation further? Explore other GroupDocs.Watermark features like adding watermarks, text replacement, and image manipulation—all using the same foundational patterns you've learned here.

## FAQ Section

**1. How do I install GroupDocs.Watermark for .NET?**
Use any of these methods: `dotnet add package GroupDocs.Watermark` via CLI, `Install-Package GroupDocs.Watermark` in Package Manager Console, or search for "GroupDocs.Watermark" in Visual Studio's NuGet Package Manager UI. The library is compatible with .NET Framework 4.6.1+ and .NET Core 2.0+.

**2. Can I remove multiple shapes at once instead of one at a time?**
Absolutely. The safest approach is to collect shape references in a list first, then iterate through that list to remove them. Don't modify a collection while iterating through it directly—that causes runtime errors. See the batch processing section for a complete example.

**3. What should I do if a shape index is out of range?**
Always validate before removing: `if (page.Shapes.Count > indexToRemove) { page.Shapes.RemoveAt(indexToRemove); }`. For debugging, print the shape count first to see what's available. This is especially important when processing varied diagram files.

**4. How does removing shapes by reference differ from using an index?**
Index-based removal targets a specific position in the collection (e.g., "remove the 3rd shape"). Reference-based removal targets the actual shape object, which is more flexible—you can search for shapes by name, text content, size, or other properties before removing them.

**5. Are there performance concerns when editing large diagrams?**
Yes, for diagrams over 50 MB. Keep memory usage in check by processing files one at a time, using `using` statements for proper disposal, and avoiding loading multiple large files simultaneously. For batch processing, consider limiting parallel operations to 4-8 files at a time.

**6. What diagram formats are supported besides Visio?**
GroupDocs.Watermark handles .VSD, .VSDX, .VSS, .VSSX, .VDX, and .VDW files. The library automatically detects the format, so you don't need different code for different file types. Check the official documentation for the most current list of supported formats.

**7. Can I undo a shape removal if I make a mistake?**
Not directly in code, but you can implement your own versioning system by always saving to a new filename (e.g., `filename_cleaned.vsdx`) instead of overwriting. Keep backups until you've verified the output is correct. Once `watermarker.Save()` completes, the change is permanent in that file.

**8. How do I handle password-protected diagrams?**
Use `DiagramLoadOptions` with the password: `var options = new DiagramLoadOptions { Password = "yourPassword" };`. Pass this to the Watermarker constructor. If the password is wrong, you'll get an authentication exception.

**9. Is there a way to preview which shapes will be removed before actually removing them?**
Yes! Add logging before removal: iterate through shapes, identify which ones match your criteria, and print their details (name, text, position). Only after reviewing the output should you proceed with actual removal. This is invaluable for debugging complex filtering logic.

**10. Can I use this library in a web application or does it only work in console apps?**
GroupDocs.Watermark works in any .NET application type: console apps, web apps (ASP.NET Core, MVC), desktop apps (WPF, WinForms), and even Azure Functions. Just be mindful of file upload limits and processing time in web scenarios—consider background jobs for large files.

## Resources

**Documentation and Support:**
- **Complete Documentation**: [GroupDocs.Watermark for .NET Docs](https://docs.groupdocs.com/watermark/net/) - Comprehensive guides and tutorials
- **API Reference**: [GroupDocs.Watermark API Reference](https://reference.groupdocs.com/watermark/net) - Detailed class and method documentation
- **Download Library**: [GroupDocs.Watermark Downloads](https://releases.groupdocs.com/watermark/net/) - Latest versions and release notes
- **Community Forum**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/watermark/) - Free community support and troubleshooting
- **Temporary License**: [Request Evaluation License](https://purchase.groupdocs.com/temporary-license/) - Get full features for testing (usually approved within hours)
