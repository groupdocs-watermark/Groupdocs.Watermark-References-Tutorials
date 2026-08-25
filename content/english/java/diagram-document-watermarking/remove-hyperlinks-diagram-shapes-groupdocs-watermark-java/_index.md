---
date: '2026-08-25'
description: Learn how to edit diagram files and remove hyperlinks using GroupDocs.Watermark
  for Java. Secure your diagrams quickly with step‑by‑step guidance.
images:
- /java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/og-image.png
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Learn how to edit diagram files and remove hyperlinks using GroupDocs.Watermark
  for Java. Follow clear steps to protect your documents.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: How to edit diagram and remove hyperlinks with Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: How to edit diagram and remove hyperlinks with Java
type: docs
url: /java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# How to edit diagram and remove hyperlinks with Java  

Managing digital documents often involves editing diagrams, especially when you need to **edit diagram** files to strip out hyperlinks for security or visual clarity. This tutorial shows you exactly how to edit diagram files and remove unwanted hyperlinks from diagram shapes using the powerful **GroupDocs.Watermark** library for Java. By the end of this guide you’ll have a clean, link‑free diagram ready for distribution.  

## Quick answers  
- **What is the main goal?** Remove all hyperlinks from diagram shapes to improve security and presentation.  
- **Which library is required?** GroupDocs.Watermark for Java, version 24.11 or newer.  
- **Do I need a license?** A free trial works for testing; a commercial license is required for production.  
- **Can I process many files at once?** Yes – the same code can be placed inside a loop to handle batches.  
- **What Java version is supported?** Java 8 or higher (Java 11 recommended).  

## What is “how to edit diagram”?  
**How to edit diagram** refers to the process of programmatically opening a diagram file, modifying its internal elements (such as shapes, text, or hyperlinks), and saving the result. Using GroupDocs.Watermark you can edit diagram files without needing the original authoring tool.  

## Why use GroupDocs.Watermark for Java?  
GroupDocs.Watermark supports **30+ diagram and image formats** (including VSDX, SVG, and WMF) and can process files up to **500 MB** without loading the entire document into memory, delivering a **20 % faster** processing speed compared with many competitors.  

## Prerequisites  
- **GroupDocs.Watermark** library version 24.11 or later.  
- Maven installed (or the JAR files if you prefer manual setup).  
- Java Development Kit 8 or newer and an IDE such as IntelliJ IDEA or Eclipse.  

### Required libraries, versions, and dependencies  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (if you use the Maven approach)  

### Environment setup requirements  
Make sure the JDK `bin` directory is on your `PATH` and that your IDE points to the correct JDK version.  

### Knowledge prerequisites  
You should be comfortable with basic Java syntax, Maven dependency management, and file I/O operations.  

## How to set up GroupDocs.Watermark for Java?  
The `Watermarker` class provides the API entry point for loading and modifying documents.  
To begin using GroupDocs.Watermark, add its Maven coordinates to your project’s `pom.xml`. This pulls the library and its dependencies, allowing you to instantiate the Watermarker class and work with diagram files directly from Java code. You can then configure licensing and set output options before processing any document.  

Add the GroupDocs.Watermark dependency to your `pom.xml`.  

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

If you prefer not to use Maven, download the latest JAR from the official releases page.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### License acquisition steps  
- Start with a free trial to evaluate the API.  
- For production, obtain a temporary or permanent license from the vendor portal.  

#### Basic initialization and setup  

The `Watermarker` class is the entry point for all document‑processing operations.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## How to edit diagram and remove hyperlinks with GroupDocs.Watermark?  
The `Watermarker` class provides the API entry point for loading and modifying documents.  
First, load the diagram file into a Watermarker instance. Then retrieve the collection of shapes, identify those containing hyperlink objects, and iterate through them in reverse order to safely delete each link without affecting the collection indexing. This ensures all embedded URLs are removed while preserving the visual integrity of the diagram.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Why this step matters**: Loading the file gives you programmatic access to every shape and its associated properties.  

## How to access shape content in a diagram?  
The `DiagramShape` object represents an individual shape within a diagram, exposing its properties and attached metadata.  
After loading the diagram, call `getShapes()` on the Watermarker to obtain a list of `DiagramShape` objects. Each shape can be inspected for hyperlink collections, allowing precise targeting of links for removal or modification. You can also read shape text, colors, and geometry if further adjustments are required.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Why this step matters**: Targeting the exact shape ensures you only remove unwanted links without affecting other visual elements.  

## How to iterate and remove hyperlinks safely?  
The `removeHyperlink(int index)` method deletes a hyperlink at the specified position within a shape’s hyperlink collection.  
Iterate over the hyperlink list from the last index down to zero. This reverse loop prevents index shifting that occurs when items are removed, ensuring every hyperlink is processed without being skipped. After removal, you may refresh the shape’s state or continue to the next shape in the diagram.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Why this step matters**: A reverse loop guarantees that all hyperlinks are removed without skipping any entries.  

## How to save the edited diagram and release resources?  
The `save(String path)` method writes the modified document to the specified file location, finalizing all changes.  
Once all hyperlinks are removed, invoke the `save` method on the Watermarker instance, providing a new filename to avoid overwriting the original. Then call `close()` to release file handles and free memory, which is essential for long‑running batch processes. This ensures the file is properly closed and ready for further use.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Why this step matters**: Properly closing resources avoids memory leaks and file‑locking issues on the server.  

## Practical applications  

Removing hyperlinks from diagram shapes can be beneficial in several real‑world scenarios:  

1. **Security** – Prevent external links that could lead to malicious sites.  
2. **Compliance** – Meet corporate policies that forbid embedded URLs in shared assets.  
3. **Clarity** – Produce cleaner presentations where links would be distracting.  

You can embed this logic into larger automation pipelines, such as nightly batch jobs that sanitize all diagrams before they are published to an intranet.  

## Performance considerations  

### Optimizing performance  
- Use a single `Watermarker` instance per file to reduce overhead.  
- Prefer reverse iteration (as shown) to avoid costly list re‑indexing.  

### Resource usage guidelines  
- For diagrams larger than 200 MB, monitor heap usage and consider increasing the JVM `-Xmx` flag.  
- Profiling tools like VisualVM can help identify bottlenecks in large‑scale batch runs.  

### Best practices for Java memory management  
- Declare objects inside the smallest possible scope.  
- Use try‑with‑resources when working with streams to ensure automatic closure.  

## Frequently asked questions  

**Q: How do I handle diagrams that contain thousands of shapes?**  
A: Process the diagram page‑by‑page and release each page’s resources before moving to the next to keep memory usage low.  

**Q: Can I limit hyperlink removal to specific pages only?**  
A: Yes – retrieve the page index you want, then apply the removal loop only to shapes on that page.  

**Q: Is a commercial license mandatory for batch processing?**  
A: A valid license is required for any production‑level deployment; the free trial is limited to 30 days and 5 documents.  

**Q: Does GroupDocs.Watermark support SVG diagrams?**  
A: Absolutely – SVG is among the 30+ supported formats, and hyperlinks can be stripped using the same API calls.  

**Q: What if a shape has multiple hyperlinks?**  
A: The reverse‑iteration loop removes each hyperlink entry individually, ensuring all links are cleared.  

## Resources  

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)  

---  

**Last Updated:** 2026-08-25  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## Related Tutorials

- [Diagram Watermarking Tutorials for GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Edit Diagram Headers & Footers in Java Using GroupDocs.Watermark: A Comprehensive Guide](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)
- [Efficiently Remove Shapes from Diagrams Using GroupDocs.Watermark for Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)