---
date: 2026-11-13
description: Learn how to extract metadata, list supported formats, and retrieve document
  information using GroupDocs.Watermark for Java.
images:
- /java/document-information/og-image.png
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: How to extract metadata using GroupDocs.Watermark for Java. Learn
  to list supported formats, retrieve document info, and extract slide backgrounds
  in minutes.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: How to extract metadata with GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: How to extract metadata with GroupDocs.Watermark for Java
type: docs
url: /java/document-information/
weight: 14
---

# How to extract metadata with GroupDocs.Watermark for Java

In this guide you’ll discover **how to extract metadata** from a wide range of document types using GroupDocs.Watermark for Java. Whether you need to read file type, page count, author details, or custom properties, the library gives you programmatic access to this information so you can make intelligent decisions about watermark placement, document routing, or compliance checks. The tutorial also shows how to list supported formats, pull slide‑background data, and retrieve other useful document characteristics.

## Quick answers
- **Can I extract metadata from PDFs and Word files?** Yes, the API reads metadata from over 70 common formats.  
- **Do I need a license for development?** A free temporary license works for testing; a full license is required for production.  
- **Which Java version is required?** Java 8 or higher is supported.  
- **Is the library thread‑safe?** Core extraction classes are designed for concurrent use.  
- **How many formats are recognised?** More than 70 input and output formats are recognised out of the box.

## What is metadata extraction?
Metadata extraction is the process of reading embedded information—such as author, creation date, page count, and custom properties—from a document file without altering its content. It enables automated workflows that depend on document attributes. It typically includes properties such as title, keywords, and modification timestamps, which can be leveraged for indexing and compliance reporting.

## Why use GroupDocs.Watermark for Java?
GroupDocs.Watermark for Java supports **70+ file formats**, including PDF, DOCX, PPTX, XLSX, and image types, and can process documents up to 500 MB without loading the entire file into memory. Its API returns metadata in a single, consistent object, reducing the need for format‑specific parsers and cutting development time by up to 40 %.

## Prerequisites
- Java 8 or newer installed on your development machine.  
- Maven or Gradle to manage the `groupdocs-watermark` dependency.  
- A temporary or full GroupDocs.Watermark license file.

## How to extract metadata step by step

### How do I retrieve basic document information?
The `Watermark` class represents a document and provides access to its metadata. The `getDocumentInfo()` method extracts the metadata object from the loaded document. Load the document with the `Watermark` class, then call `getDocumentInfo()` to obtain an object containing file type, size, page count, and creation date. This single call returns all core metadata in under a second for typical files under 100 MB. The returned `DocumentInfo` object also includes the document's author, last modified date, and any embedded custom properties, giving a comprehensive overview.

### How can I list all supported file formats?
The `SupportedFormats` utility provides a catalog of all file types the SDK can process. Use the `SupportedFormats` utility provided by the SDK. It returns a collection of format identifiers that you can display or validate against before uploading files, ensuring compatibility and preventing runtime errors. Each entry includes the format's name, typical file extension, and a brief description of its capabilities, helping developers validate inputs before processing.

### How do I extract slide background details from a PowerPoint file?
`SlideInfo` is an object that describes visual properties of a slide, such as background image and dimensions. `getSlides()` returns a collection of `SlideInfo` objects for each slide in the presentation. The `SlideInfo` object exposes background image dimensions, file size, and color depth. Access it through the `getSlides()` collection, then iterate over each slide to read its background properties—useful for dynamic styling or thumbnail generation. These details can be used to generate thumbnails, apply consistent styling, or replace backgrounds programmatically across multiple presentations.

## Common issues and solutions
- **Missing metadata:** Some older files may not contain standard properties. In that case, enable the `extractCustomProperties` flag to pull any user‑defined fields.  
- **Large files cause timeouts:** Increase the SDK’s `maxMemory` setting or process the document in streaming mode to avoid loading the whole file into RAM.  
- **Unsupported format error:** Verify the format against the list returned by `SupportedFormats` before attempting extraction.

## Frequently asked questions

**Q: Can I extract metadata from password‑protected documents?**  
A: Yes, provide the password when opening the document; the API will decrypt it in memory and then read the metadata.

**Q: Does the library work on Android?**  
A: The core extraction features are compatible with Android API 21+ when bundled as a standard JAR.

**Q: How do I handle custom metadata fields?**  
A: Use the `getCustomProperties()` method on the `DocumentInfo` object; it returns a map of key‑value pairs you can iterate over.

**Q: Is there a way to batch‑process many files?**  
A: Wrap the extraction logic in a loop and reuse a single `Watermark` instance; the SDK is designed for high‑throughput scenarios.

**Q: What licensing options are available?**  
A: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses; the temporary license is ideal for evaluation and CI pipelines.

## Available tutorials

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

---

**Last Updated:** 2026-11-13  
**Tested with:** GroupDocs.Watermark 23.12 for Java  
**Author:** GroupDocs

## Related Tutorials

- [How to List Supported File Formats Using GroupDocs.Watermark for Java: A Complete Guide](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [How to Retrieve Document Information Using GroupDocs.Watermark for Java: A Step-by-Step Guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Extract Document Information Using GroupDocs.Watermark for Java: A Complete Guide](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)