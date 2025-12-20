---
title: "How to Extract Images from Word Documents Using GroupDocs.Watermark in Java"
description: "Learn how to extract images from word documents and extract shapes using GroupDocs.Watermark for Java, perfect for document automation and manipulation."
date: "2025-12-20"
weight: 1
url: "/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/"
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
type: docs
---
# How to Extract Images from Word Documents Using GroupDocs.Watermark in Java

In modern document‑processing applications, **extract images from word** documents is a frequent requirement—whether you need to reuse graphics, run OCR, or simply audit content. This tutorial shows you, step by step, how to load a Word document in Java with GroupDocs.Watermark and then **extract images from word** files while also demonstrating **how to extract shapes**. By the end, you’ll have a reusable code snippet that fits right into your automation pipeline.

## Quick Answers
- **What library handles image extraction?** GroupDocs.Watermark for Java  
- **Can I extract both pictures and vector shapes?** Yes – the API provides access to images and shape metadata.  
- **What Java version is required?** JDK 8 or higher.  
- **Do I need a license for production?** A commercial license is recommended; a free trial works for evaluation.  
- **Is the process memory‑efficient for large files?** Yes, you can release resources promptly and process sections incrementally.

## What Is “Extract Images from Word”?
Extracting images from Word means programmatically locating every picture, drawing, or embedded graphic inside a `.docx` file and retrieving its binary data or metadata. This enables downstream tasks such as image analysis, content migration, or dynamic report generation.

## Why Use GroupDocs.Watermark for This Task?
GroupDocs.Watermark offers a high‑level API that abstracts the complexities of the OpenXML format. It lets you **load word document java** projects with just a few lines of code, while also exposing detailed shape information—perfect for developers who need both image extraction and shape analysis.

## Prerequisites
- **Java Development Kit (JDK)** 8 or newer  
- **IDE** – IntelliJ IDEA, Eclipse, or any Java‑compatible editor  
- Basic Java I/O knowledge  
- Access to a GroupDocs.Watermark license (trial works for testing)

## Setting Up GroupDocs.Watermark for Java
Integrate the library via Maven or direct download.

### Using Maven
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
Alternatively, download the latest JAR from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition
For full functionality, obtain a license key from the GroupDocs portal. A temporary trial license can be requested to explore all features without restrictions.

## Implementation Guide
We'll split the implementation into two logical parts:

1. **How to load a Word document in Java**  
2. **How to extract shapes and images (i.e., extract images from word)**

### Loading a Word Document
First, configure the load options and instantiate the `Watermarker`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Pro tip:** Replace `"YOUR_DOCUMENT_DIRECTORY/document.docx"` with an absolute or relative path that points to the file you want to process.

### Extracting Shape and Image Information
Now that the document is loaded, you can iterate through each section and each shape, pulling out both vector shape data and embedded image details.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Why this matters:** The `shape.getImage()` call gives you direct access to the binary representation of each picture, enabling you to save it to disk, send it over a network, or feed it into an image‑processing library.

## Common Issues and Solutions
| Problem | Solution |
|---------|----------|
| **FileNotFoundException** – wrong path | Verify the file path and ensure the application has read permissions. |
| **OutOfMemoryError** on large docs | Process sections one at a time and call `watermarker.close()` as soon as you finish a batch. |
| Shapes return `null` for `getImage()` | Not all shapes are images; some are drawing objects. Check `shape.getShapeType()` before accessing the image. |
| License not applied | Add `License.setLicense("path/to/license/file.lic");` before creating `Watermarker`. |

## Practical Applications
- **Automated Report Generation:** Pull charts and logos from templates to reuse in dashboards.  
- **Content Auditing:** Scan corporate documents for prohibited graphics.  
- **Migration Projects:** Export embedded images before moving content to a new CMS.

## Performance Considerations
- Release the `Watermarker` instance promptly (`watermarker.close()`).  
- For massive files (>50 MB), consider streaming sections rather than loading the whole document into memory.  
- Use the latest GroupDocs.Watermark version for performance improvements.

## Conclusion
You now have a complete, production‑ready approach to **extract images from word** documents and retrieve shape metadata using GroupDocs.Watermark for Java. This capability unlocks powerful automation scenarios, from generating dynamic reports to performing large‑scale document audits.

### Next Steps
- Experiment with saving extracted images to disk (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Explore additional APIs such as watermark removal or addition.  
- Integrate this logic into your existing document‑management workflow.

## FAQ Section
**Q: What is GroupDocs.Watermark for Java?**  
A: It's a comprehensive library designed to manage watermarks and extract visual elements across various document formats, enhancing automation of document manipulation tasks.

**Q: Can I extract images from password‑protected Word files?**  
A: Yes. Load the document with `WordProcessingLoadOptions` that includes the password, then proceed with the same extraction logic.

**Q: Does the API support .doc (binary) files as well?**  
A: The library primarily targets the OpenXML `.docx` format, but it can also open legacy `.doc` files after conversion.

**Q: How do I save the extracted images to the filesystem?**  
A: Use `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` inside the loop where `shape.getImage()` is not null.

**Q: Is there a limit to the number of shapes I can process?**  
A: No hard limit, but memory consumption grows with document size; process sections sequentially for very large files.

---

**Last Updated:** 2025-12-20  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs