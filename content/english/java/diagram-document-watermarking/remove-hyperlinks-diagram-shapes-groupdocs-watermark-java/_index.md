---
title: "How to Remove Hyperlinks from Diagram Shapes using GroupDocs.Watermark Java"
description: "Learn how to remove hyperlinks from diagram shapes using GroupDocs.Watermark Java, a key step for java document security and batch remove hyperlinks."
date: "2025-12-19"
weight: 1
url: "/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/"
keywords:
- how to delete hyperlink
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-10-16'
og_description: Learn how to delete hyperlink from diagram shapes using GroupDocs.Watermark
  for Java. Follow step‑by‑step instructions to secure your documents quickly.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes with GroupDocs.Watermark
  Java
og_title: How to delete hyperlink from shapes with GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to delete hyperlink from diagram shapes using GroupDocs.Watermark
    for Java, ensuring secure and clean documents.
  headline: How to delete hyperlink from shapes with GroupDocs.Watermark
  type: TechArticle
- description: Learn how to delete hyperlink from diagram shapes using GroupDocs.Watermark
    for Java, ensuring secure and clean documents.
  name: How to delete hyperlink from shapes with GroupDocs.Watermark
  steps:
  - name: add the Maven dependency
    text: 'Add the following configuration to your `pom.xml`: You can also view the
      latest releases on the [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)
      page.'
  - name: initialize the Watermarker
    text: The `Watermarker` class is the entry point for all document‑processing actions.
      It opens the file and gives you access to pages, shapes, and their properties.
      For detailed usage, refer to the official [Documentation](https://docs.groupdocs.com/watermark/java/).
  - name: load the diagram file
    text: 'Create a `Watermarker` instance with the path to your diagram (e.g., `.vsdx`,
      `.drawio`). This object represents the entire document in memory. - **Why**:
      Loading the file gives you programmatic access to every shape that may contain
      a hyperlink.'
  - name: retrieve shape content
    text: 'The `Shape` class represents an individual diagram element. By calling
      `getShapes()` you obtain a collection you can iterate. - **Why**: Accessing
      shapes lets you target exactly those objects that hold hyperlink data.'
  - name: iterate and delete hyperlinks
    text: 'Iterate the shape’s hyperlink list backwards so that removal does not affect
      the loop index. Call `removeHyperlink(index)` for each unwanted link. - **Why**:
      Reverse iteration prevents `IndexOutOfBoundsException` when elements are removed.'
  - name: save the modified diagram
    text: 'After cleaning up the hyperlinks, save the document to a new location.
      This writes the changes without altering the original file. - **Why**: Saving
      to a new file preserves the original version for audit purposes and avoids file‑locking
      issues.'
  type: HowTo
- questions:
  - answer: Yes. Access the desired page via `watermarker.getPage(pageIndex)` and
      apply the removal logic only to its shapes.
    question: Can I remove hyperlinks from only specific pages?
  - answer: GroupDocs.Watermark supports vector formats like SVG, but raster images
      (PNG, JPEG) do not contain hyperlink objects.
    question: Does this work with SVG or PNG diagrams?
  - answer: Inspect each `Hyperlink` object's URL or ID and skip removal when it matches
      your whitelist criteria.
    question: How do I keep certain hyperlinks while deleting others?
  - answer: A commercial license is required for any production‑grade usage, including
      automated batch jobs.
    question: Is a commercial license mandatory for batch processing?
  - answer: Over 30 formats, including VSDX, DRAWIO, SVG, PDF, DOCX, PPTX, and more.
      See the full [API Reference](https://reference.groupdocs.com/watermark/java)
      for details.
    question: What file formats can I process with this API?
  type: FAQPage
tags:
- delete hyperlink
- GroupDocs.Watermark
- Java diagram processing
title: How to delete hyperlink from shapes with GroupDocs.Watermark
type: docs
url: /java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# How to Remove Hyperlinks from Diagram Shapes using GroupDocs.Watermark Java

Managing digital documents often involves editing diagrams, especially when **removing hyperlinks** for security or clarity. In this tutorial, you'll learn **how to remove hyperlinks** from diagram shapes with GroupDocs.Watermark for Java, ensuring your files stay clean, safe, and professional.

## Quick Answers
- **What is the primary purpose?** To strip unwanted hyperlinks from diagram shapes for better document security.  
- **Which library is used?** GroupDocs.Watermark for Java (version 24.11 or later).  
- **Do I need a license?** A trial works for testing; a valid license is required for production.  
- **Can I process many files at once?** Yes – the same logic can be placed inside a batch loop.  
- **Is Java 8 sufficient?** Java 8+ is supported; newer JDKs are recommended.

## What is “how to remove hyperlinks” in the context of diagrams?
Removing hyperlinks means deleting the URL references attached to shapes inside a diagram file (e.g., Visio *.vsdx). This operation prevents accidental navigation to external sites and helps meet compliance or internal security policies.

## Why use GroupDocs.Watermark Java for this task?
- **Robust format support** – works with a wide range of diagram types.  
- **Fine‑grained API** – lets you target individual shapes and their hyperlink collections.  
- **Performance‑optimized** – suitable for both single files and bulk processing.  

## Prerequisites
- **GroupDocs.Watermark** library version 24.11 or later.  
- Maven or direct JAR download (see the setup steps below).  
- Java Development Kit (JDK 8 or newer) and an IDE such as IntelliJ IDEA or Eclipse.  

## Setting Up GroupDocs.Watermark for Java
To start, include the library in your project via Maven or by downloading the JAR.

### Maven Setup
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

You can also view the latest releases on the [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) page.

#### License Acquisition Steps
- Start with a free trial to evaluate the API.  
- For production, obtain a temporary or full‑size license from the GroupDocs portal.

#### Basic Initialization and Setup
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## How to Remove Hyperlinks from Diagram Shapes
Below is a step‑by‑step guide that walks you through loading a diagram, locating shapes, and stripping out unwanted hyperlinks.

### Step 1: Load the Diagram File
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Why?* Loading the file gives you programmatic access to its internal structure.

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
*Why?* Looping backwards prevents index errors when you delete items from the collection.

### Step 4: Save and Close
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---
- [Remove Hyperlinks from PDFs Using GroupDocs.Watermark for Java](/watermark/java/watermark-removal/remove-hyperlinks-pdf-groupdocs-watermark-java/)
- [Mastering GroupDocs.Watermark Java to Remove or Replace Hyperlinks in Excel Spreadsheets](/watermark/java/spreadsheet-document-watermarking/remove-replace-hyperlinks-excel-groupdocs-watermark-java/)
- [Efficiently Remove Shapes from Diagrams Using GroupDocs.Watermark for Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)

