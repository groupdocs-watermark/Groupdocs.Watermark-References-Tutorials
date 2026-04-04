---
title: "How to Strip Links from Diagram Shapes using GroupDocs.Watermark Java"
description: "Learn how to strip links from diagram shapes with GroupDocs.Watermark Java, ensuring document security and clarity."
date: "2026-04-04"
weight: 1
url: "/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/"
keywords:
  - how to strip links
  - remove hyperlinks java
  - java diagram editing
type: docs
---
# How to Strip Links from Diagram Shapes using GroupDocs.Watermark Java

Managing digital documents often involves editing diagrams, especially when you need **how to strip links** for security or clarity. In this tutorial you’ll learn a simple, step‑by‑step way to remove unwanted hyperlinks from diagram shapes using the powerful **GroupDocs.Watermark** library for Java. By the end, you’ll have clean, link‑free diagrams that are safe to share.

## Quick Answers
- **What does “how to strip links” mean?** It refers to removing hyperlink objects embedded in diagram shapes.  
- **Which library handles this?** GroupDocs.Watermark for Java (version 24.11 or newer).  
- **Do I need a license?** A free trial works for testing; a valid license is required for production.  
- **Can I process many files at once?** Yes – wrap the code in a loop or batch job.  
- **Is this approach language‑specific?** The example is Java, but the same concept applies to other .NET/Java APIs.

## What is “how to strip links” in diagram editing?
Stripping links means locating hyperlink objects attached to shapes inside a diagram (e.g., Visio *.vsdx) and deleting them. This eliminates external URLs that could expose sensitive information or break presentation flow.

## Why use GroupDocs.Watermark for Java?
- **Precision** – Direct access to shape objects and their hyperlink collections.  
- **Performance** – Optimized for large diagrams without loading the whole document into memory.  
- **Cross‑format support** – Works with many diagram formats (Visio, Draw.io, etc.).  

## Prerequisites
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (or manual JAR inclusion).  
- Java JDK 8 or newer.  
- An IDE such as IntelliJ IDEA or Eclipse.

## Setting Up GroupDocs.Watermark for Java
### Maven Setup
Add the repository and dependency to your `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

### Direct Download
If you prefer not to use Maven, grab the latest JAR from the official site:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### License Acquisition Steps
- Start with a free trial download.  
- For production, obtain a temporary or full license from the GroupDocs portal.

#### Basic Initialization and Setup
Create a `Watermarker` instance that points to the folder containing your diagram:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## How to Strip Links from Diagram Shapes
Below is a concise, four‑step process that shows **remove hyperlinks java** in action.

### Step 1: Load the Diagram File
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Why?* Loading the file gives you programmatic access to its pages, shapes, and hyperlink collections.

### Step 2: Access Shape Content
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Why?* You need a reference to the specific shape that may contain hyperlinks.

### Step 3: Iterate and Remove Hyperlinks
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Why?* Looping in reverse prevents index‑shift problems when deleting items from the collection.

### Step 4: Save and Close
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Why?* Saving writes the cleaned diagram to disk, and closing releases file handles to avoid memory leaks.

## Practical Applications of Stripping Links
1. **Security** – Remove external URLs that could lead to phishing or data leakage.  
2. **Compliance** – Ensure diagrams meet internal policies before distribution.  
3. **Presentation Cleanliness** – Eliminate unnecessary clickable areas that distract viewers.

## Performance Considerations
- **Loop Efficiency** – Use the reverse‑iteration pattern shown above.  
- **Resource Management** – Prefer `try‑with‑resources` or explicit `close()` calls.  
- **Large Files** – Monitor CPU/memory; consider processing pages in batches.

## Common Issues and Solutions
- **No hyperlinks found** – Verify that the diagram actually contains hyperlink objects; some formats store them differently.  
- **IndexOutOfBoundsException** – Always iterate in reverse when removing items from a collection.  
- **License errors** – Ensure your license file is correctly placed or passed to the `Watermarker` constructor.

## Frequently Asked Questions

**Q: How do I handle multiple shapes on multiple pages?**  
A: Loop through `content.getPages()` and then through each page’s `getShapes()` collection, applying the same removal logic to every shape.

**Q: Can I filter links by domain instead of a full URL?**  
A: Yes – change the `contains` check to look for the domain string (e.g., `"example.com"`).

**Q: Is there a way to log which links were removed?**  
A: Inside the loop, capture `shape.getHyperlinks().get_Item(i).getAddress()` before removal and write it to a log file.

**Q: Does this work with PDF diagrams embedded in other documents?**  
A: GroupDocs.Watermark supports many formats; ensure the file type is recognized as a diagram (Visio, VDX, etc.).

**Q: What licensing is required for batch processing?**  
A: A full production license is needed for any non‑trial, high‑volume operations.

## Conclusion
You now have a complete, production‑ready method for **how to strip links** from diagram shapes using GroupDocs.Watermark for Java. Incorporate this into your document‑processing pipelines to boost security, compliance, and visual quality.

### Next Steps
- Explore other manipulation features such as adding watermarks or stamping text.  
- Combine this routine with a file‑watcher service to automatically clean diagrams as they are uploaded.

---

**Last Updated:** 2026-04-04  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

## Resources
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)