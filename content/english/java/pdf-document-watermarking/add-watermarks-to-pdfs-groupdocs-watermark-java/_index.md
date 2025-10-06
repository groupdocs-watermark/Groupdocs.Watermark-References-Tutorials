---
title: "How to Add Watermarks to PDFs Using GroupDocs.Watermark for Java"
description: "Learn how to add text and image watermarks to PDFs using GroupDocs.Watermark for Java. Secure your documents with this step-by-step guide."
date: "2025-05-15"
weight: 1
url: "/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/"
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
type: docs
---
# How to Add Watermarks to PDFs Using GroupDocs.Watermark for Java

## Introduction

In today’s digital landscape, protecting intellectual property is crucial. Adding watermarks can significantly enhance document security by marking confidential content and preventing unauthorized use. This tutorial will guide you through the process of using **GroupDocs.Watermark for Java** to add both text and image watermarks to PDF files. By the end, you'll be able to:

- Initialize text and image watermarks
- Add watermarks conditionally based on image dimensions
- Save modified documents with embedded watermarks

Ready to enhance your document security? Let’s get started!

## Prerequisites

Before proceeding, ensure you have the following setup:

1. **Java Development Kit (JDK):** Install JDK 8 or higher.
2. **GroupDocs.Watermark for Java:** Use version 24.11 of the library.
3. **Maven or Direct Download:** Choose a method to include GroupDocs.Watermark in your project.

### Environment Setup

To install and configure GroupDocs.Watermark, follow these steps:

#### Maven Configuration

Add the following repository and dependency to your `pom.xml`:

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

Alternatively, download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition

To start with a free trial or obtain a temporary license, visit [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Consider purchasing a subscription for full feature access without restrictions.

## Setting Up GroupDocs.Watermark for Java

With the library installed, initialize and set up your project. Import necessary classes:

```java
import com.groupdocs.watermark.Watermarker;
```

This setup is crucial for enabling watermark functionality in your application.

## Implementation Guide

We'll break down the implementation into sections to ensure clarity.

### Initialize Text Watermark

**Overview:** This section guides you through creating a text watermark with customizable font and alignment settings.

#### Step 1: Create TextWatermark Instance

Create an instance of `TextWatermark` using your desired text and font:

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

This sets up your text as "Protected image" in Arial, size 8.

#### Step 2: Set Alignment

Center the watermark for better positioning:

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

These settings ensure that your text is centrally positioned within each image.

#### Step 3: Rotate Watermark

Apply a rotation angle for visual appeal:

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

Rotation enhances prominence and reduces removal risk.

#### Step 4: Configure Sizing

Adjust sizing relative to image dimensions:

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

This ensures consistent text appearance across various image sizes.

### Initialize Image Watermark

**Overview:** Learn how to set up an image-based watermark for enhanced document protection.

#### Step 1: Load Image File

Load your desired watermark image:

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Replace the path with your actual image location.

#### Step 2: Set Alignment

Center the image within target images:

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

This ensures aesthetic balance by central placement.

#### Step 3: Rotate Image Watermark

Apply a counter-clockwise rotation for variation:

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

Rotation adds complexity, making it harder to obscure or remove.

#### Step 4: Configure Sizing

Ensure consistent sizing across various images:

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

Proper scaling ensures uniform appearance regardless of document size.

### Add Watermarks to Images in a Document

**Overview:** This section demonstrates adding both text and image watermarks to images within a PDF document based on specific conditions.

#### Step 1: Open the Document

Begin by opening your target PDF:

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

Replace with the path to your document.

#### Step 2: Retrieve Images

Access all watermarkable images in the document:

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

This step is crucial for iterating over each image to apply watermarks.

#### Step 3: Add Watermarks Conditionally

Add either text or image watermark based on dimensions:

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

This logic ensures only larger images receive a watermark, optimizing performance and relevance.

#### Step 4: Release Image Resources

Close the image watermark to free up resources:

```java
// Close the image watermark instance after use
imageWatermark.close();
```

Resource management is essential for maintaining application efficiency.

#### Step 5: Save Changes

Persist your modifications by saving the document:

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

This saves your work and ensures all changes are applied permanently to the output file.

#### Step 6: Clean Up

Release resources by closing the Watermarker instance:

```java
// Close the main watermarker to release document resources
watermarker.close();
```

Proper cleanup prevents memory leaks, ensuring smooth application operation.

## Practical Applications

Adding watermarks can serve various purposes in real-world scenarios. Here are some use cases for applying watermarks using GroupDocs.Watermark:
1. **Document Security:** Mark confidential documents to prevent unauthorized distribution.
2. **Brand Protection:** Embed company logos on promotional materials to enhance brand visibility.
3. **Copyright Assertion:** Assert copyright claims by adding author information or copyright symbols.
4. **Version Control:** Differentiate between document versions using version numbers as watermarks.

## Conclusion

By following this guide, you can effectively add text and image watermarks to PDF documents using GroupDocs.Watermark for Java. This ensures enhanced security and protection of your digital content.
