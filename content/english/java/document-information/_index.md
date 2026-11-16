---
date: 2026-09-11
description: Learn to extract PDF page dimensions and other document metadata with
  GroupDocs.Watermark for Java. Complete guides, code examples, and practical tips.
images:
- /java/document-information/og-image.png
keywords:
- extract pdf page dimensions
- determine document dimensions
- java extract pdf metadata
lastmod: 2026-09-11
og_description: Extract PDF page dimensions using GroupDocs.Watermark for Java. Learn
  how to retrieve page size, count, and other metadata to drive intelligent watermark
  placement and document automation.
og_image_alt: Guide showing how to extract PDF page dimensions with GroupDocs.Watermark
  Java
og_title: Extract PDF page dimensions using GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn to extract PDF page dimensions and other document metadata with
    GroupDocs.Watermark for Java. Complete guides, code examples, and practical tips.
  headline: Extract PDF page dimensions using GroupDocs.Watermark Java
  type: TechArticle
- description: Learn to extract PDF page dimensions and other document metadata with
    GroupDocs.Watermark for Java. Complete guides, code examples, and practical tips.
  name: Extract PDF page dimensions using GroupDocs.Watermark Java
  steps:
  - name: add the Maven dependency
    text: '*(The version number reflects the latest stable release at the time of
      writing.)*'
  - name: instantiate the Watermark object
    text: The `Watermark` class is the entry point for all document‑analysis operations.
  - name: retrieve dimensions
    text: '`PageDimensions` provides `getWidth()` and `getHeight()` in points, which
      you can convert to inches or millimeters if required.'
  type: HowTo
- questions:
  - answer: Yes. Pass the password to the `Watermark` constructor or use `LoadOptions`
      with the `setPassword` method before calling `getPageDimensions()`.
    question: Can I extract dimensions from encrypted PDFs?
  - answer: The API returns values in points (1 pt = 1/72 in). You can convert to
      pixels using the document’s DPI (typically 72 dpi for PDF).
    question: Does the API return dimensions in pixels?
  - answer: GroupDocs.Watermark provides analogous methods such as `getSlideDimensions()`
      for PowerPoint and `getPageDimensions()` for Word when the document is rendered
      as PDF internally.
    question: Is it possible to extract dimensions from other formats like DOCX or
      PPTX?
  - answer: The library can handle PDFs with **500+ pages** in a single instance without
      loading the whole file into memory, thanks to its streaming architecture.
    question: How many pages can be processed in a single call?
  - answer: The `Watermark` class implements `AutoCloseable`; use a try‑with‑resources
      block or call `watermark.close()` to release file handles promptly.
    question: Do I need to close the Watermark object?
  type: FAQPage
tags:
- extract pdf page dimensions
- GroupDocs.Watermark
- Java document processing
- PDF metadata
- document analysis
title: Extract PDF page dimensions using GroupDocs.Watermark Java
type: docs
url: /java/document-information/
weight: 14
---

# Extract PDF page dimensions using GroupDocs.Watermark Java

In this comprehensive guide you’ll discover how to **extract PDF page dimensions** and other valuable document information with GroupDocs.Watermark for Java. Whether you need page width and height for precise watermark placement, want to audit document size before processing, or simply wish to build smarter document‑handling workflows, these tutorials give you step‑by‑step code, real‑world use cases, and best‑practice tips. Let’s explore the full set of resources that help you turn raw PDFs into actionable data.

## Quick answers
- **What can I retrieve?** File type, page count, page width / height, image dimensions, shape details, and supported format list.  
- **Why does page size matter?** Accurate dimensions let you position watermarks without clipping or distortion.  
- **Do I need a license?** A temporary license works for development; a full license is required for production.  
- **Which Java version is supported?** Java 8 + and any JVM‑compatible environment.  
- **Is the API thread‑safe?** Yes – you can safely use separate `Watermark` instances in parallel threads.

## What is extract PDF page dimensions?
PDF page dimensions refer to the width and height of each page measured in points (1 pt = 1/72 in). Knowing these dimensions lets you calculate exact coordinates for watermark overlays, ensuring consistent visual results across pages of varying sizes. These measurements are essential for aligning watermarks, headers, footers, and other graphical elements precisely on each page.

## Why determine document dimensions with GroupDocs.Watermark?
GroupDocs.Watermark supports **50+ input and output formats** and can process multi‑hundred‑page PDFs without loading the entire file into memory. Its dimension‑extraction API returns size data in O(1) time per page, enabling real‑time watermark placement even in high‑throughput batch jobs significantly.

## Prerequisites
- Java 8 or newer installed.  
- Maven or Gradle build system to manage dependencies.  
- A valid GroupDocs.Watermark for Java license (temporary license for testing).  
- Sample PDF files to experiment with.

## How to extract PDF page dimensions in Java using GroupDocs.Watermark

Load the PDF with `Watermark` and call `getPageDimensions()` – that single call returns the width and height for every page in the document. The API abstracts away PDF parsing, so you don’t need to work with low‑level iText or PDFBox objects.  
`getPageDimensions()` returns a list of `PageDimensions` objects, each containing the width and height of a page in points.

### Step 1: add the Maven dependency
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>23.12</version>
</dependency>
```
*(The version number reflects the latest stable release at the time of writing.)*

### Step 2: instantiate the Watermark object
```java
Watermark watermark = new Watermark("sample.pdf");
```
The `Watermark` class is the entry point for all document‑analysis operations.

### Step 3: retrieve dimensions
```java
List<PageDimensions> dimensions = watermark.getPageDimensions();
for (int i = 0; i < dimensions.size(); i++) {
    PageDimensions d = dimensions.get(i);
    System.out.printf("Page %d – Width: %.2f pt, Height: %.2f pt%n", i + 1, d.getWidth(), d.getHeight());
}
```
`PageDimensions` provides `getWidth()` and `getHeight()` in points, which you can convert to inches or millimeters if required.

## Available tutorials

Below is the curated list of deep‑dive tutorials that cover every aspect of document information extraction. Click each link to open the full guide.

### [Extract Document Information Using GroupDocs.Watermark for Java&#58; A Complete Guide](./extract-document-info-groupdocs-watermark-java/)
Learn how to efficiently extract document metadata like file type, page count, and size using GroupDocs.Watermark for Java. This guide covers setup, implementation, and practical applications.

### [Extract PDF Page Dimensions in Java Using GroupDocs.Watermark&#58; A Complete Guide](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Learn how to extract PDF page dimensions with GroupDocs.Watermark for Java. This guide covers setup, code examples, and practical applications.

### [Extract Shapes from Word Documents Using GroupDocs.Watermark in Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Learn how to extract and analyze shapes from Word documents using GroupDocs.Watermark for Java, enhancing document automation and manipulation.

### [How to Extract Slide Background Information Using GroupDocs.Watermark for Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Learn how to extract slide background details such as image dimensions and file size using GroupDocs.Watermark for Java. Perfect for customization, analysis, or documentation.

### [How to List Supported File Formats Using GroupDocs.Watermark for Java&#58; A Complete Guide](./groupdocs-watermark-java-list-supported-formats/)
Learn how to efficiently list supported file formats with GroupDocs.Watermark in Java, ensuring compatibility across various document types.

### [How to Retrieve Document Information Using GroupDocs.Watermark for Java&#58; A Step‑By‑Step Guide](./retrieve-document-info-groupdocs-watermark-java/)
Learn how to efficiently retrieve document information such as file type, page count, and size using GroupDocs.Watermark for Java. Follow our detailed guide with code examples.

### [How to Retrieve Section Properties in Word Documents Using GroupDocs.Watermark for Java](./groupdocs-java-word-section-properties-retrieval/)
Learn how to efficiently retrieve and manipulate section properties in Word documents using GroupDocs.Watermark for Java. Perfect for developers looking to enhance document handling.

## Additional resources
- [GroupDocs.Watermark for Java Documentation](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark for Java API Reference](https://reference.groupdocs.com/watermark/java/)
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark Forum](https://forum.groupdocs.com/c/watermark)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Common issues and solutions
- **Null dimensions** – Ensure the PDF is not password‑protected or corrupted; supply the password to the `Watermark` constructor if needed.  
- **Incorrect page count** – Use `watermark.getPageCount()` to verify the document was loaded completely before calling `getPageDimensions()`.  
- **Performance bottleneck on large files** – Enable streaming mode (`watermark.setLoadOptions(new LoadOptions(LoadOptions.LoadMode.Stream))`) to keep memory usage low.

## Frequently asked questions

**Q: Can I extract dimensions from encrypted PDFs?**  
A: Yes. Pass the password to the `Watermark` constructor or use `LoadOptions` with the `setPassword` method before calling `getPageDimensions()`.

**Q: Does the API return dimensions in pixels?**  
A: The API returns values in points (1 pt = 1/72 in). You can convert to pixels using the document’s DPI (typically 72 dpi for PDF).

**Q: Is it possible to extract dimensions from other formats like DOCX or PPTX?**  
A: GroupDocs.Watermark provides analogous methods such as `getSlideDimensions()` for PowerPoint and `getPageDimensions()` for Word when the document is rendered as PDF internally.

**Q: How many pages can be processed in a single call?**  
A: The library can handle PDFs with **500+ pages** in a single instance without loading the whole file into memory, thanks to its streaming architecture.

**Q: Do I need to close the Watermark object?**  
A: The `Watermark` class implements `AutoCloseable`; use a try‑with‑resources block or call `watermark.close()` to release file handles promptly.

---

**Last Updated:** 2026-09-11  
**Tested With:** GroupDocs.Watermark 23.12 for Java  
**Author:** GroupDocs

## Related Tutorials

- [Extract Document Information Using GroupDocs.Watermark for Java: A Complete Guide](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)
- [How to Retrieve Document Information Using GroupDocs.Watermark for Java: A Step‑By‑Step Guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [How to Extract PDF Annotations Using GroupDocs.Watermark in Java: A Comprehensive Guide](/watermark/java/pdf-document-watermarking/extract-pdf-annotations-groupdocs-watermark-java/)