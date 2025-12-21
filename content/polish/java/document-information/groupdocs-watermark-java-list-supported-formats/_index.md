---
date: '2025-12-21'
description: Dowiedz się, jak używać znaków wodnych z GroupDocs.Watermark dla Javy,
  wymieniając wszystkie obsługiwane formaty plików, zapewniając płynną kompatybilność
  dokumentów.
keywords:
- GroupDocs Watermark Java
- list supported file formats GroupDocs
- Java watermarking library
title: Jak używać znaku wodnego – lista obsługiwanych formatów w Javie
type: docs
url: /pl/java/document-information/groupdocs-watermark-java-list-supported-formats/
weight: 1
---

# How to Use Watermark – List Supported Formats in Java

Praca z wieloma typami dokumentów może być wyzwaniem, szczególnie gdy potrzebujesz **how to use watermark** w sposób niezawodny w swoich aplikacjach. W tym przewodniku przeprowadzimy Cię krok po kroku przez dokładne instrukcje, jak wyświetlić wszystkie formaty plików obsługiwane przez GroupDocs.Watermark for Java. Po zakończeniu będziesz wiedział, jak zintegrować bibliotekę, pobrać listę formatów i zastosować tę wiedzę w rzeczywistych scenariuszach, takich jak systemy zarządzania dokumentami czy potoki publikacji treści.

## Quick Answers
- **What does “how to use watermark” mean in Java?** It means calling the GroupDocs.Watermark API to interact with supported file types.  
- **Which library version is required?** GroupDocs.Watermark Java 24.11 or newer.  
- **Do I need a license?** A trial works for development; a permanent license is required for production.  
- **Can I run this on JDK 8+?** Yes, the library is compatible with JDK 8 and later.  
- **Is the format list static?** The list reflects the library version you use; newer releases may add formats.

## How to Use Watermark – List Supported Formats

### Introduction

Zanim przejdziesz do kodu, upewnij się, że Twoje środowisko programistyczne spełnia poniższe wymagania wstępne. Ten krok przygotowawczy oszczędza czas i zapobiega typowym błędom „class not found”, które napotykają wielu programistów, zaczynając pracę z **how to use watermark**.

## Prerequisites

- **Required Libraries**: GroupDocs.Watermark for Java 24.11 or later.  
- **Environment**: JDK 8 or higher, Maven 3.6 +.  
- **Knowledge**: Basic Java syntax and Maven dependency management.

## Setting Up GroupDocs.Watermark for Java

### Installation via Maven

Add the repository and dependency entries to your `pom.xml` file:

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

Alternatively, download the latest version of GroupDocs.Watermark for Java from [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

#### License Acquisition

To use GroupDocs.Watermark in production, obtain a license. You can start with a free trial or request a temporary license for evaluation.

### Initialization and Setup

After adding the dependency or downloading the library, initialize it in your Java project:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.common.FileType;

public class WatermarkExample {
    public static void main(String[] args) {
        // Initialize a watermarker object for demonstration purposes
        Watermarker watermarker = new Watermarker("path/to/your/file");
        
        // Your code to list supported file formats will go here

        watermarker.close();
    }
}
```

## Implementation Guide

### Listing Supported File Formats

This feature enables you to retrieve and display all the file types that GroupDocs.Watermark supports.

#### Step 1: Retrieve All Supported File Types

Use the `FileType` class method to get an array of supported file formats:

```java
// STEP 1: Retrieve all supported file types from the GroupDocs library
FileType[] fileTypes = FileType.getSupportedFileTypes();
```

#### Step 2: Iterate and Print File Type Names

Iterate through the retrieved file types to print their names:

```java
// STEP 2: Iterate over each file type and print its name
for (FileType fileType : fileTypes) {
    System.out.println(fileType);
}
```

### Troubleshooting Tips

- **Common Issues**: Verify that Maven dependencies are correctly defined. Incompatible JDK versions often cause `NoClassDefFoundError`.  
- **Performance Considerations**: For very large format lists, redirect output to a log file instead of the console to avoid UI slowdown.

## Practical Applications

Understanding which file formats GroupDocs.Watermark supports can benefit various scenarios:

1. **Document Management Systems** – Automatically apply watermarks only to supported types, preventing runtime errors.  
2. **Content Publishing Platforms** – Secure PDFs, images, and Office documents before distribution.  
3. **Legal Document Handling** – Ensure confidentiality by watermarking all supported legal file formats.

## Performance Considerations

When processing many files, keep these best practices in mind:

- **Resource Management** – Always close `Watermarker` objects to free memory.  
- **Memory Monitoring** – Use Java profiling tools to watch heap usage during bulk operations.

## Conclusion

We’ve covered **how to use watermark** to list every format supported by GroupDocs.Watermark for Java. This knowledge helps you design robust watermarking workflows that automatically adapt to the capabilities of the library.

### Next Steps

- Explore adding text or image watermarks using the same `Watermarker` instance.  
- Experiment with custom watermark positioning and opacity settings.

Ready to implement? Add the snippets above to your project and start building smarter, more secure document pipelines today!

## FAQ Section

1. **What file formats does GroupDocs.Watermark support?**  
   - The library supports PDFs, common image types (PNG, JPEG, BMP, GIF, TIFF), Microsoft Office files (DOCX, PPTX, XLSX), and several others.
2. **How do I troubleshoot issues with GroupDocs.Watermark?**  
   - Ensure Maven dependencies are correct and that you’re using a compatible JDK version.
3. **Can I use GroupDocs.Watermark for commercial purposes?**  
   - Yes, a valid license is required for production use.
4. **What should I do if my application slows down when listing file formats?**  
   - Optimize resource handling by closing `Watermarker` objects promptly and consider logging to a file.
5. **Where can I find more examples of using GroupDocs.Watermark?**  
   - Check out the [GroupDocs GitHub repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) for additional code samples.

## Additional Frequently Asked Questions

**Q: Does the format list update automatically with new library releases?**  
A: The list reflects the formats compiled into the version you’re using; upgrading the library adds any newly supported types.

**Q: Can I filter the list to only image formats?**  
A: Yes, after retrieving `FileType[]`, inspect each `FileType` and match against known image extensions.

**Q: Is it possible to programmatically check if a specific file is supported before processing?**  
A: Use `FileType.isSupported(filePath)` (or similar utility) to validate a file’s compatibility.

---

**Last Updated:** 2025-12-21  
**Tested With:** GroupDocs.Watermark Java 24.11  
**Author:** GroupDocs  

**Resources**

- **Documentation**: [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API Reference**: [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download**: [Latest Release](https://releases.groupdocs.com/watermark/java/)  
- **GitHub**: [GroupDocs.Watermark Java GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free Support**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary License**: [Purchase Temporary License](https://purchase.groupdocs.com/temporary-license/)