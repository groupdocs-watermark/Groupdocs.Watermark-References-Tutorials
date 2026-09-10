---
title: "How to Remove Hyperlinks from Diagram Shapes using GroupDocs.Watermark Java"
description: "Learn how to remove hyperlinks from diagram shapes using GroupDocs.Watermark Java, a key step for java document security and batch remove hyperlinks."
date: "2025-12-19"
weight: 1
url: "/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/"
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
type: docs
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

### Direct Download
Alternatively, download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

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
*Why?* Persisting the changes and releasing resources avoids memory leaks and locked files.

## Batch Remove Hyperlinks (Advanced Use Case)
If you need to clean many diagrams at once, wrap the above logic inside a loop that iterates over a list of file paths. The same API calls apply; just change the input and output directories for each iteration. This approach aligns with **batch remove hyperlinks** requirements for large document repositories.

## Practical Applications
Removing hyperlinks from diagram shapes can be beneficial in several real‑world scenarios:

1. **Security Purposes** – Prevent external links that could expose your network to phishing or malware.  
2. **Compliance** – Meet corporate policies that forbid outbound URLs in shared documents.  
3. **Clarity** – Produce cleaner presentations where hyperlinks are unnecessary or distracting.  

## Performance Considerations
### Optimizing Performance
- Use the reverse‑iteration pattern shown above to keep loops efficient.  
- Close the `Watermarker` object as soon as you’re done to free memory.

### Resource Usage Guidelines
- Monitor CPU and RAM when processing large diagrams.  
- For bulk jobs, consider streaming the files rather than loading them all at once.

### Best Practices for Java Memory Management
- Avoid creating objects inside tight loops.  
- Use try‑with‑resources where applicable for automatic cleanup.

## Frequently Asked Questions
1. **How do I handle multiple shapes?**  
   Iterate over all pages and their shapes, applying the same hyperlink‑removal logic to each shape.  

2. **Can this process be automated for large batches of diagrams?**  
   Yes – embed the code in a batch‑processing routine or integrate it with your document‑management system.  

3. **What if I need to remove hyperlinks only from specific pages?**  
   Access the desired page by its index (`content.getPages().get_Item(pageIndex)`) and target shapes on that page only.  

4. **Is there any licensing required for production use of GroupDocs.Watermark?**  
   A valid commercial license is required beyond the trial period.  

5. **Can this method work with other diagram formats?**  
   GroupDocs.Watermark supports many diagram types; verify compatibility in the official documentation.  

**Additional Q&A**

**Q:** *Is it possible to log which hyperlinks were removed?*  
**A:** Yes – before calling `removeAt(i)`, capture `shape.getHyperlinks().get_Item(i).getAddress()` and write it to a log file.

**Q:** *Will removing hyperlinks affect the visual appearance of the shape?*  
**A:** No. The shape’s geometry stays unchanged; only the link metadata is stripped.

**Q:** *Do I need to re‑apply any styling after removal?*  
**A:** Not usually. Hyperlink removal does not alter fill, line, or text styles.

## Conclusion
You now have a complete, production‑ready method for **how to remove hyperlinks** from diagram shapes using GroupDocs.Watermark for Java. By following the steps above, you can secure your diagrams, comply with policies, and keep your documents looking polished.

**Resources**  
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