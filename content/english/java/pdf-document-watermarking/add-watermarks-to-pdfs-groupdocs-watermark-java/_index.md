---
title: "How to Watermark PDF Using GroupDocs.Watermark for Java"
description: "Learn how to watermark PDF files with text and image watermarks using GroupDocs.Watermark for Java – a complete guide for PDF document security."
date: "2026-01-23"
weight: 1
url: "/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/"
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
type: docs
---
# How to Watermark PDF Using GroupDocs.Watermark for Java

In today's digital world, **how to watermark PDF** files is a common question for anyone who needs to protect intellectual property or brand assets. Adding watermarks—whether text or images—helps you enforce **PDF document security** and makes unauthorized distribution much harder. In this tutorial, you’ll learn step‑by‑step how to use **GroupDocs.Watermark for Java** to add both text and image watermarks to PDF documents.

## Quick Answers
- **What library adds watermarks to PDF in Java?** GroupDocs.Watermark for Java.  
- **Can I add both text and image watermarks?** Yes, the API supports both types.  
- **Do I need a license?** A free trial works for evaluation; a paid license removes limitations.  
- **Which Java version is required?** JDK 8 or higher.  
- **Is Maven supported?** Absolutely – just add the repository and dependency.

## What is PDF Watermarking and Why Use It?
Watermarking a PDF embeds a visible or invisible marker that identifies ownership, confidentiality, or branding. It’s a lightweight yet powerful way to deter copying, prove authorship, and comply with corporate policies.

## Prerequisites

Before you start, make sure you have:

1. **Java Development Kit (JDK) 8+** installed on your machine.  
2. **GroupDocs.Watermark for Java** (the latest version).  
3. **Maven** (or the ability to add a JAR manually).

### Environment Setup

#### Maven Configuration
Add the GroupDocs repository and the watermark dependency to your `pom.xml`:

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

#### Direct Download
If you prefer not to use Maven, you can download the JAR directly from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition
To start with a free trial or obtain a temporary license, visit [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). For production use, purchase a subscription to unlock all features.

## Setting Up GroupDocs.Watermark for Java

Import the core class that drives all watermark operations:

```java
import com.groupdocs.watermark.Watermarker;
```

This import gives you access to the `Watermarker` class, which is the entry point for adding watermarks to any supported document type.

## Step‑by‑Step Implementation

Below we break the process into logical sections: creating text watermarks, creating image watermarks, and finally applying them to images inside a PDF.

### 1. Initialize a Text Watermark

**Why a text watermark?** It’s lightweight, searchable, and perfect for adding copyright notices or confidentiality statements.

#### 1.1 Create the TextWatermark Instance
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Set Alignment
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Rotate the Watermark
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Configure Sizing
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Initialize an Image Watermark

**When to use an image watermark?** Ideal for branding with logos or for adding complex visual patterns.

#### 2.1 Load the Image File
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Set Alignment
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Rotate the Image Watermark
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Configure Sizing
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Add Watermarks to Images Inside a PDF

Now we’ll put everything together: open a PDF, locate every image, and apply either the text or image watermark based on size.

#### 3.1 Open the PDF Document
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Retrieve All Images
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Apply Watermarks Conditionally
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 Release Image Resources
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Save the Modified PDF
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Clean Up
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Practical Applications of PDF Watermarking

| Use Case | How Watermarking Helps |
|----------|------------------------|
| **Document Security** | Marks confidential files, deterring leaks. |
| **Brand Protection** | Embeds logos on marketing PDFs, reinforcing brand identity. |
| **Copyright Assertion** | Adds author name or © symbol to assert ownership. |
| **Version Control** | Shows version numbers or dates directly on the page. |

## Common Pitfalls & Tips

- **Path separators:** Use double backslashes (`\\`) on Windows or forward slashes (`/`) on Linux/macOS to avoid `FileNotFoundException`.
- **Large PDFs:** Process images in batches or increase JVM heap size (`-Xmx2g`) to prevent OutOfMemory errors.
- **License limits:** The trial version may limit the number of pages processed; upgrade for unlimited usage.
- **Rotation confusion:** Remember that `setRotateAngle` expects degrees; negative values rotate counter‑clockwise.

## Frequently Asked Questions

**Q: Can I watermark password‑protected PDFs?**  
A: Yes. Open the document with the password using the `Watermarker` constructor that accepts a password string.

**Q: Does the library support other formats like DOCX or PPTX?**  
A: Absolutely. GroupDocs.Watermark works with Word, PowerPoint, Excel, and image files as well.

**Q: How do I change the opacity of a watermark?**  
A: Use `setOpacity(float opacity)` on the watermark object (value between 0.0 and 1.0).

**Q: Is it possible to add a watermark to only the first page?**  
A: Retrieve the page collection via `watermarker.getPages()` and apply the watermark to the desired page index.

**Q: What if I need to watermark a PDF stored in a cloud bucket?**  
A: Load the PDF into a `InputStream` and pass it to the `Watermarker` constructor; after processing, write the output stream back to the cloud.

## Conclusion

You now have a complete, production‑ready method for **how to watermark PDF** files using GroupDocs.Watermark for Java. By combining text and image watermarks, you can achieve robust **PDF document security** that meets both branding and compliance requirements. Explore the library’s other features—such as watermark removal or batch processing—to further extend your document workflow.

---

**Last Updated:** 2026-01-23  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---