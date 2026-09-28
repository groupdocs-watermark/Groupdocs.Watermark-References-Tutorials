---
date: 2026-09-16
description: Learn how to add watermark to pdf, load documents from various sources,
  and save watermarked files using GroupDocs.Watermark for Java.
images:
- /java/document-loading-saving/og-image.png
keywords:
- add watermark to pdf
- load password protected document
- load document from disk
- load document from stream
- java load password protected
lastmod: 2026-09-16
og_description: Add watermark to pdf quickly using GroupDocs.Watermark for Java. Learn
  loading documents, handling passwords, and saving watermarked files.
og_image_alt: Guide showing how to add watermark to pdf using GroupDocs.Watermark
  Java SDK
og_title: Add watermark to pdf with GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to add watermark to pdf, load documents from various sources,
    and save watermarked files using GroupDocs.Watermark for Java.
  headline: How to add watermark to pdf with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark`
      or `ImageWatermark` objects; each will be layered in the order added.
    question: Can I add multiple watermarks to the same PDF?
  - answer: Absolutely. All original PDF objects, including annotations, form fields,
      and metadata, remain untouched unless you explicitly modify them.
    question: Does the library preserve existing annotations?
  - answer: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method
      to limit the watermark to specific pages.
    question: Is it possible to watermark only selected pages?
  - answer: The SDK can handle files up to **2 GB** without loading the entire document
      into memory, thanks to its streaming architecture.
    question: What is the maximum file size supported?
  - answer: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier
      returned when you initially added the watermark.
    question: How do I remove a watermark after it has been added?
  type: FAQPage
tags:
- watermark pdf
- GroupDocs.Watermark
- Java document processing
- add watermark to pdf
- load document
title: How to add watermark to pdf with GroupDocs.Watermark for Java
type: docs
url: /java/document-loading-saving/
weight: 2
---

# Add watermark to pdf with GroupDocs.Watermark for Java

In this guide you’ll learn how to **add watermark to pdf** files using the GroupDocs.Watermark Java SDK. We’ll walk through loading documents from disk, streams, or password‑protected sources, applying text or image watermarks, and finally saving the updated PDF. Whether you’re building a batch processor or a single‑file service, these steps give you a reliable, production‑ready solution.

## Quick answers
- **Can I add a watermark to a password‑protected PDF?** Yes – pass the password when loading the document, then apply the watermark normally.  
- **Which formats can be watermarked?** Over 30 formats, including PDF, DOCX, PPTX, and images.  
- **Do I need a license for development?** A temporary license works for testing; a full license is required for production.  
- **What Java version is required?** Java 8 or higher is supported.  
- **Is streaming supported?** Absolutely – you can load from `InputStream` and save to `OutputStream` without touching the file system.

## What is add watermark to pdf?
*Add watermark to pdf* refers to the process of overlaying semi‑transparent text or images onto each page of a PDF document to convey ownership, confidentiality, or branding. GroupDocs.Watermark for Java provides a single‑call API that handles positioning, opacity, and page‑range selection automatically.

## Why use GroupDocs.Watermark for Java?
GroupDocs.Watermark supports **35+ file formats** and can process **500‑page PDFs in under 2 seconds** on a typical server‑class CPU. The library works entirely in memory, so you never need Microsoft Office or Adobe Acrobat installed. Its API is thread‑safe, making it ideal for high‑throughput web services.

## Prerequisites
- Java 8 or newer installed.  
- Maven or Gradle project configured with the `groupdocs-watermark` dependency.  
- A valid GroupDocs.Watermark license (temporary license for evaluation).  
- PDF files you want to protect, optionally with passwords.

## How to add watermark to pdf – step by step

Load the source document, apply a watermark, then save the result. The following sections answer each sub‑task directly.

### How to load a document from disk?

`Watermarker` is the primary class used to load and manipulate documents for watermarking. Provide the full file path to the `Watermarker` constructor; the SDK automatically detects the file format, validates the content, and loads the document into memory ready for any watermark operation. This approach works for PDFs, Word files, images, and many other supported types.  
```java
Watermarker watermarker = new Watermarker("C:/files/input.pdf");
```

After this line the PDF is fully loaded in memory, ready for any watermark operation.

### How to load a document from stream?

`Watermarker` can also accept an `InputStream` to load documents directly from memory. When you receive a file via HTTP or a message queue, wrap the byte array in a `ByteArrayInputStream` and pass it to the `Watermarker` constructor that accepts an `InputStream`. The SDK reads the stream without writing to disk, preserving performance and security, and supports large files by processing data in chunks. This method is ideal for web services and micro‑service architectures.  
```java
InputStream pdfStream = new ByteArrayInputStream(pdfBytes);
Watermarker watermarker = new Watermarker(pdfStream);
```

The SDK reads the stream without writing to disk, preserving performance and security.

### How to load a password‑protected document?

`Watermarker` supports loading password‑protected PDFs by providing the password as a second argument. Supply the password as a second argument to the constructor. The SDK decrypts the PDF on the fly, after which you can treat it like any other document. If the password is correct, all pages become accessible for watermarking; otherwise the library throws a clear exception that you can catch and log for troubleshooting.  
```java
Watermarker watermarker = new Watermarker("C:/files/secure.pdf", "mySecretPwd");
```

If the password is incorrect, the SDK throws an informative exception that you can catch and log.

### How to apply a text watermark?

`TextWatermark` represents a textual watermark that can be applied to pages with customizable style. Create a `TextWatermark` object with your desired text, font, size, and color. Then call `add` on the `Watermarker` instance, optionally specifying page ranges. The watermark is rendered with the specified opacity and rotation, and it can be positioned using predefined locations or custom coordinates, ensuring consistent appearance across all pages.  
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 36));
watermark.setColor(Color.RED);
watermark.setTransparency(0.5);
watermarker.add(watermark);
```

This call places the watermark on every page by default; you can restrict it with `new PageRange(1, 5)` if needed.

### How to apply an image watermark?

`ImageWatermark` represents an image‑based watermark such as a logo or seal. Instantiate an `ImageWatermark` with the path or stream of your logo, then add it similarly to the text watermark. The SDK automatically scales the image to fit the page while preserving its aspect ratio, and you can adjust opacity, rotation, and placement to achieve the desired visual effect without distorting the original content.  
```java
ImageWatermark imgWatermark = new ImageWatermark("C:/images/logo.png");
imgWatermark.setTransparency(0.3);
watermarker.add(imgWatermark);
```

The SDK scales the image to fit the page while preserving aspect ratio.

### How to save the watermarked document?

`save` writes the modified document to the specified location in the chosen format. Call `save` with the output path and desired format. The same format as the source is used when you omit the format parameter. The method writes the modified PDF to disk, preserving all original content except for the newly added watermark layers, and supports saving to streams for further processing.  
```java
watermarker.save("C:/files/output.pdf");
```

The method writes the modified PDF to disk, preserving all original content except for the newly added watermark layers.

## Available tutorials

### [How to Load Password-Protected Documents in Java Using GroupDocs.Watermark](./groupdocs-watermark-java-password-protected-documents/)
Learn how to load and manage watermarks in password-protected documents using GroupDocs.Watermark for Java. This guide provides step‑by‑step instructions, practical examples, and troubleshooting tips.

### [How to Load and Watermark Password-Protected Word Documents Using GroupDocs.Watermark in Java](./groupdocs-watermark-java-password-protected-word-docs/)
Learn how to use GroupDocs.Watermark with Java to load, manage, and watermark password-protected Word documents efficiently.

## Additional resources

- [GroupDocs.Watermark for Java Documentation](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark for Java API Reference](https://reference.groupdocs.com/watermark/java/)
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark Forum](https://forum.groupdocs.com/c/watermark)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Common issues and solutions
- **Invalid password error** – double‑check the password string; it must be UTF‑8 encoded.  
- **Out‑of‑memory on large PDFs** – enable streaming mode by using `Watermarker` constructors that accept `InputStream` and `OutputStream`.  
- **Watermark not visible** – ensure the watermark’s opacity is set above 0.1 and that the color contrasts with the page background.

## Frequently asked questions

**Q: Can I add multiple watermarks to the same PDF?**  
A: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark` or `ImageWatermark` objects; each will be layered in the order added.

**Q: Does the library preserve existing annotations?**  
A: Absolutely. All original PDF objects, including annotations, form fields, and metadata, remain untouched unless you explicitly modify them.

**Q: Is it possible to watermark only selected pages?**  
A: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method to limit the watermark to specific pages.

**Q: What is the maximum file size supported?**  
A: The SDK can handle files up to **2 GB** without loading the entire document into memory, thanks to its streaming architecture.

**Q: How do I remove a watermark after it has been added?**  
A: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier returned when you initially added the watermark.

---

**Last Updated:** 2026-09-16  
**Tested with:** GroupDocs.Watermark 23.9 for Java  
**Author:** GroupDocs

## Related Tutorials

- [How to Add a Text Watermark to PDF Using GroupDocs.Watermark for Java (2023 Guide)](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)
- [How to Add Text and Image Watermarks to Specific PDF Pages Using GroupDocs.Watermark for Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [How to Load Password-Protected Documents in Java Using GroupDocs.Watermark](/watermark/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/)