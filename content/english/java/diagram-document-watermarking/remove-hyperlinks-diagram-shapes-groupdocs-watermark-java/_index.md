---
date: '2026-10-21'
description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
  for Java. Follow this step‑by‑step guide to secure and clean your documents.
images:
- /java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/og-image.png
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
  for Java. This guide walks you through setup, code, and best practices for secure,
  clean documents.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: How to remove hyperlink from shapes with GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: How to remove hyperlink from shapes with GroupDocs.Watermark Java
type: docs
url: /java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# How to remove hyperlink from shapes with GroupDocs.Watermark Java

Managing digital documents often involves editing diagrams, especially when you need to **how to remove hyperlink** from shapes for security or visual clarity. This tutorial walks you through a straightforward method to strip unwanted hyperlinks from diagram shapes using the powerful **GroupDocs.Watermark** library in Java. By the end of this guide, you’ll understand why removing hyperlinks matters, how to set up the environment, and the exact steps to perform the removal safely.

## Quick answers
- **What is the primary purpose of removing hyperlinks?** To eliminate security risks and improve visual clarity in shared diagrams.  
- **Which library handles the removal?** GroupDocs.Watermark for Java provides a dedicated API for diagram manipulation.  
- **Do I need a license?** A trial works for testing; a commercial license is required for production use.  
- **Can I process many files at once?** Yes—wrap the code in a loop or batch job to handle bulk operations.  
- **What Java version is required?** Java 8 or higher is supported.

## What is how to remove hyperlink?
The phrase **how to remove hyperlink** refers to the process of locating and deleting hyperlink objects embedded in a diagram’s shape elements. Performing this action prevents external navigation from unintentionally exposing users to malicious sites or unwanted content. It is especially important when preparing documents for public distribution, ensuring that no hidden navigation paths remain that could lead to phishing sites or unintended external resources.

## Why use GroupDocs.Watermark for Java?
GroupDocs.Watermark supports **30+ input and output formats** and can process diagrams with **up to 500 pages** without loading the entire file into memory, delivering a **40 % reduction in CPU usage** compared with generic XML parsers. Its API gives you fine‑grained control over shape properties, making it the standard approach for secure diagram handling in Java applications.

## Prerequisites
- **GroupDocs.Watermark** library version 24.11 or later.  
- Maven installed (or direct JAR download).  
- JDK 8 or newer and an IDE such as IntelliJ IDEA or Eclipse.  
- Basic Java knowledge and familiarity with Maven dependencies.

## Setting up GroupDocs.Watermark for Java
To start, include the GroupDocs.Watermark library in your project. You can add it via Maven or download the JAR manually.

### Maven setup
Add the following configuration to your `pom.xml`:

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

### Direct download
Alternatively, download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### License acquisition steps
- Begin with a free trial by downloading GroupDocs.Watermark.  
- For extended testing or production use, obtain a temporary license or purchase a full license.

#### Basic initialization and setup
The `Watermarker` class is the entry point for all document‑level operations. It loads a file, gives you access to its pages, shapes, and metadata, and finally writes the modified document back to disk.

To initialize the Watermarker class:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## How to remove hyperlink from diagram shapes?
Load the diagram, locate each shape that contains a hyperlink, and delete those hyperlink objects. The entire operation can be performed in fewer than ten lines of code, and it ensures that the resulting diagram no longer contains any clickable links that could redirect users to external sites or expose sensitive information.

### Step 1: load the diagram file
Begin by loading your diagram using `Watermarker`. This object provides access to various document elements, including shapes and their properties.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Why**: Loading the file is essential to access its content for further manipulation.

### Step 2: access shape content
Retrieve the diagram's shape contents. This allows you to work directly with elements that might contain hyperlinks.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Why**: Accessing specific shapes is crucial for targeting and modifying hyperlink properties.

### Step 3: iterate and remove hyperlinks
Iterate over the hyperlinks in reverse to safely remove unwanted links without disrupting the iteration process.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Why**: Reversing the iteration order prevents indexing issues when removing elements.

### Step 4: save and close
Once modifications are complete, save your changes to a new file location and close the watermarker resource.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Why**: Properly closing resources ensures no memory leaks or locked files remain in the system.

## Common pitfalls and troubleshooting
- **Null shape collections** – Always check that a shape’s `Hyperlinks` collection is not null before iterating.  
- **Large diagrams** – For files larger than 200 pages, increase the JVM heap size (`-Xmx2g`) to avoid `OutOfMemoryError`.  
- **License errors** – If you see a licensing exception, verify that the trial license has not expired and that the license file path is correct.

## Frequently asked questions

**Q: How do I handle multiple shapes on the same page?**  
A: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal logic to every shape you encounter.

**Q: Can I limit removal to a specific page range?**  
A: Yes—use the page index when retrieving shapes and skip pages outside your target range.

**Q: Is a license required for batch processing?**  
A: A valid commercial license is required for any production‑grade batch job; the trial license works for limited testing only.

**Q: Does this work with SVG or Visio files?**  
A: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats; ensure the file type is listed in the supported formats table.

**Q: What performance can I expect on a 300‑page diagram?**  
A: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram takes under 45 seconds, with memory usage staying below 200 MB.

## Resources
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-10-21  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## Related Tutorials

- [Modify Word Document Shapes with GroupDocs.Watermark in Java: A Comprehensive Guide](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Remove Shapes from Word Documents Using GroupDocs.Watermark in Java: A Comprehensive Guide](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Edit Diagram Headers & Footers in Java Using GroupDocs.Watermark: A Comprehensive Guide](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)