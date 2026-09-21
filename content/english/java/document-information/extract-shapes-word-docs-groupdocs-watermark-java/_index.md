---
title: "How to Extract Shapes from Word Docs Using GroupDocs.Watermark Java"
description: "Learn how to extract shapes from Word docs using GroupDocs.Watermark for Java, including how to load a Word document Java and manipulate shape data."
date: "2026-02-05"
weight: 1
url: "/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/"
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
type: docs
---

# How to Extract Shapes from Word Documents Using GroupDocs.Watermark in Java

In this tutorial you’ll discover **how to extract shapes** from Word documents with the GroupDocs.Watermark Java library. Whether you need to analyze diagrams, pull out embedded images, or automate report generation, extracting shape metadata gives you the control to build smarter document‑processing pipelines. We’ll walk through setting up the library, loading a Word document, and pulling detailed shape information—all in clear, step‑by‑step Java code.

## Quick Answers
- **What does “extract shapes” mean?** Retrieving metadata (type, size, position, text, images) for each drawing object in a Word file.  
- **Which library handles this?** GroupDocs.Watermark for Java.  
- **Do I need a license?** A trial works for development; a full license removes usage limits.  
- **Can I also get images from shapes?** Yes – the API exposes the image bytes for picture shapes.  
- **What Java version is required?** JDK 8 or newer.

## What Is “How to Extract Shapes” in the Context of Word Documents?
Extracting shapes means programmatically accessing every drawing element—pictures, WordArt, auto‑shapes, charts, and even shapes embedded in headers or footers. This information can be used for validation, migration, or content‑driven analytics.

## Why Use GroupDocs.Watermark for Java?
GroupDocs.Watermark provides a high‑level, memory‑efficient API that abstracts the complexity of the underlying Office Open XML format. It lets you:
- Load documents quickly (`WordProcessingLoadOptions`).  
- Iterate through sections and shapes without dealing with low‑level XML.  
- Retrieve image data, text, alignment, and rotation in a single call.  
- Integrate seamlessly into existing Java services or micro‑services.

## Prerequisites
- **Java Development Kit (JDK)** 8 or higher.  
- **IDE** such as IntelliJ IDEA or Eclipse.  
- Basic Java I/O knowledge.  
- Access to a **GroupDocs.Watermark for Java** license or trial.

## Setting Up GroupDocs.Watermark for Java
Integrate the library via Maven or a direct download.

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
A free trial is sufficient for testing. For production, request a permanent license to unlock all features.

## Implementation Guide
We'll split the implementation into two clear steps: **loading the Word document** and **extracting shape information**.

### Step 1: Load a Word Document (load word document java)
First, configure the load options and create a `Watermarker` instance. This prepares the document for further inspection.

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

> **Pro tip:** Keep the `Watermarker` instance scoped as tightly as possible; closing it promptly frees native resources and avoids memory leaks.

### Step 2: Extract Shape Information (extract images from shapes)
Now we’ll pull every shape’s details, including any embedded images. The code iterates through each section and each shape, printing useful metadata.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

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

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
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

**What this code does:**  
- Retrieves each shape’s **type** (e.g., picture, WordArt).  
- Prints **size**, **position**, and **rotation** values.  
- Shows **alternative text** and **name**, which are useful for accessibility checks.  
- If the shape holds an image, it prints the image’s **pixel dimensions** and **byte size**—perfect for extracting images from shapes.  

### Common Pitfalls & How to Fix Them
| Issue | Cause | Solution |
|-------|-------|----------|
| `FileNotFoundException` | Wrong file path or missing permissions | Verify the absolute/relative path and ensure the file is readable. |
| Null `shape.getImage()` | Shape is not a picture (e.g., auto‑shape) | Guard with `if (shape.getImage() != null)` as shown. |
| High memory usage on large docs | Loading the whole document at once | Process sections one at a time or increase JVM heap (`-Xmx`). |
| Missing header/footer shapes | Not checking `shape.getHeaderFooter()` | The sample already logs when a shape belongs to a header/footer. |

## Practical Applications
1. **Automated Report Generation** – Pull charts and diagrams to embed in downstream PDFs.  
2. **Compliance Auditing** – Verify that all shapes contain appropriate alternative text for accessibility.  
3. **Content Migration** – Export embedded images from legacy Word files into a digital asset management system.  

## Performance Considerations
- **Release resources**: Always call `watermarker.close()` in a `finally` block or use try‑with‑resources if you wrap the API.  
- **Chunk processing**: For documents exceeding 50 MB, consider processing each section separately to keep the memory footprint low.  
- **Thread safety**: `Watermarker` instances are not thread‑safe; create a new instance per thread.

## Conclusion
You now know **how to extract shapes** from Word documents using GroupDocs.Watermark for Java, from loading the file to reading every shape’s metadata and embedded image data. This capability opens doors to advanced document analytics, automated content pipelines, and accessibility validation.

### Next Steps
- Experiment with modifying shape properties (e.g., resizing or repositioning).  
- Combine this approach with **GroupDocs.Parser** to extract surrounding text.  
- Integrate the extraction logic into a REST service for on‑demand processing.

## FAQ Section
**Q: What is GroupDocs.Watermark for Java?**  
A: It's a comprehensive library designed to manage watermarks and document content across formats, enabling tasks like shape extraction, image retrieval, and text manipulation.

**Q: Can I extract images from shapes without a license?**  
A: The trial version allows extraction, but a full license removes usage limits and enables commercial deployment.

**Q: Does this work with `.doc` (binary) files?**  
A: Yes, the API supports both `.docx` and legacy `.doc` formats.

**Q: How do I handle password‑protected documents?**  
A: Provide the password through `WordProcessingLoadOptions.setPassword("yourPassword")` before creating the `Watermarker`.

**Q: Is there a way to export the extracted shape data to JSON?**  
A: You can map the printed values to a POJO and use any JSON library (e.g., Jackson) to serialize the collection.

---

**Last Updated:** 2026-02-05  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs