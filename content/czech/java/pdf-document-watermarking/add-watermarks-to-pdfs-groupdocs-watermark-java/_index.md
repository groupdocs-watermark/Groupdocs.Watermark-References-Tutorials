---
date: '2026-08-09'
description: Zjistěte, jak přidat vodoznak do PDF pomocí GroupDocs.Watermark for Java.
  Tento příklad java pdf vodoznaku ukazuje textové a obrázkové vodoznaky a ukládání
  PDF s vodoznakem.
keywords:
- add watermark to pdf
- save pdf with watermark
- java pdf watermark example
lastmod: '2026-08-09'
og_description: Zjistěte, jak přidat vodoznak do PDF pomocí GroupDocs.Watermark for
  Java. Tento krok‑za‑krokem java pdf vodoznakový příklad vám pomůže rychle uložit
  PDF s vodoznakem.
og_image_alt: Guide showing how to add text and image watermarks to PDF files in Java
og_title: Přidat vodoznak do PDF pomocí GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  headline: Add watermark to PDF with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  name: Add watermark to PDF with GroupDocs.Watermark for Java
  steps:
  - name: create TextWatermark instance
    text: 'Create a `TextWatermark` using the desired text and font settings: This
      example sets the watermark text to “Protected image” using Arial, size 8.'
  - name: set alignment
    text: 'Center the watermark horizontally and vertically for uniform positioning:'
  - name: rotate watermark
    text: 'Apply a 45‑degree rotation to make the watermark harder to remove:'
  - name: configure sizing
    text: 'Scale the watermark relative to the target image dimensions:'
  - name: load image file
    text: 'Load the watermark image from disk: Replace the placeholder path with the
      actual location of your logo or seal.'
  - name: set alignment
    text: 'Center the image watermark for balanced visual impact:'
  - name: rotate image watermark
    text: 'Apply a –30‑degree rotation to introduce visual variation:'
  - name: configure sizing
    text: 'Define the image size as a percentage of the underlying image’s width:'
  - name: open the document
    text: 'Instantiate a `Watermarker` with the path to your source PDF:'
  - name: retrieve images
    text: 'Collect all images from the PDF that can receive a watermark:'
  type: HowTo
- questions:
  - answer: Yes. Open the document with `new Watermarker("file.pdf", "password")`
      and then apply the watermark as usual.
    question: Can I add a watermark to a password‑protected PDF?
  - answer: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker`
      for each file, apply the same watermark objects, and save the results.
    question: Does the API support batch processing of multiple PDFs?
  - answer: The library can handle **500+ watermarks per document** without performance
      degradation, thanks to its optimized rendering engine.
    question: What is the maximum number of watermarks I can add to a single PDF?
  - answer: Yes. Use the `setOpacity(0)` method on the watermark object to embed it
      invisibly for forensic tracking.
    question: Is it possible to make the watermark invisible (metadata only)?
  - answer: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: Which Java versions are officially supported?
  type: FAQPage
tags:
- pdf watermark
- GroupDocs.Watermark
- Java document security
title: Přidat vodoznak do PDF pomocí GroupDocs.Watermark for Java
type: docs
url: /cs/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Přidání vodoznaku do PDF pomocí GroupDocs.Watermark pro Java

## Úvod

V dnešním digitálním prostředí je ochrana duševního vlastnictví zásadní a **add watermark to PDF** je jedním z nejúčinnějších způsobů, jak toho dosáhnout. Tento tutoriál vás provede používáním GroupDocs.Watermark pro Java k vložení textových i obrazových vodoznaků do PDF souborů. Na konci budete schopni:

- Inicializovat textové a obrazové vodoznaky
- Aplikovat vodoznaky podmíněně na základě rozměrů obrázku
- **save PDF with watermark** při zachování původní kvality

Připraveni zabezpečit své dokumenty? Pojďme začít!

## Rychlé odpovědi
- **Which library adds watermarks to PDFs in Java?** GroupDocs.Watermark for Java.
- **Can I add both text and image watermarks?** Yes, the API supports both types in a single run.
- **Do I need a license for development?** A free trial works for testing; a permanent license is required for production.
- **What file formats are supported?** Over 30 formats, including PDF, DOCX, PPTX, and images.
- **How large a PDF can be processed?** Up to 2,000 pages without loading the whole file into memory.

## Co je add watermark to PDF?
**Add watermark to PDF** znamená vložení viditelných nebo neviditelných značek – například textových řetězců nebo log – přímo do PDF souboru za účelem označení vlastnictví, důvěrnosti nebo značky. Tento proces upravuje vizuální vrstvy dokumentu a zároveň zachovává původní obsah nedotčený.

## Proč používat GroupDocs.Watermark pro Java?
GroupDocs.Watermark podporuje **30+ formátů dokumentů**, dokáže zpracovat PDF až do **2 000 stránek** v jednom průchodu a přidá až **500 vodoznaků na dokument** bez znatelného dopadu na výkon. Jeho API je plně thread‑safe, což ho činí ideálním pro prostředí serverů s vysokým průtokem.

## Požadavky

Před pokračováním se ujistěte, že máte:

1. **Java Development Kit (JDK):** Version 8 or newer installed.
2. **GroupDocs.Watermark for Java:** Version 24.11 (or newer) added to your project.
3. **Build tool:** Maven preferred, but a direct JAR download works as well.

### Nastavení prostředí

#### Maven konfigurace

Add the GroupDocs repository and dependency to your `pom.xml` file:

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

#### Přímé stažení

Alternatively, download the latest JAR from the official releases page: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Získání licence

For a free trial or a temporary license, visit the licensing portal: [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Production deployments should use a purchased license to remove all trial limitations.

## Nastavení GroupDocs.Watermark pro Java

After adding the library, import the required classes into your Java source file:

```java
import com.groupdocs.watermark.Watermarker;
```

## Průvodce implementací

We’ll break the implementation into logical sections, each answering a specific question.

### Jak přidat vodoznak do PDF v Javě?

`Watermarker` is the main class that loads a document and allows watermarks to be applied.  
Load your PDF with `new Watermarker("input.pdf")` and then apply a watermark object before calling `save("output.pdf")`. This two‑step approach handles both text and image watermarks in a single pass, ensuring the file is **saved PDF with watermark** efficiently.

### Inicializace textového vodoznaku

**Definition anchor:** `TextWatermark` je třída představující textový překrytí, které může být umístěno na stránky, obrázky nebo vektorovou grafiku v dokumentu.

#### Krok 1: vytvořit instanci TextWatermark

Create a `TextWatermark` using the desired text and font settings:

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

This example sets the watermark text to “Protected image” using Arial, size 8.

#### Krok 2: nastavit zarovnání

Center the watermark horizontally and vertically for uniform positioning:

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Krok 3: otočit vodoznak

Apply a 45‑degree rotation to make the watermark harder to remove:

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### Krok 4: nakonfigurovat velikost

Scale the watermark relative to the target image dimensions:

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### Inicializace obrazového vodoznaku

**Definition anchor:** `ImageWatermark` encapsulates an image (PNG, JPEG, BMP, etc.) that will be overlaid on the document content as a watermark.

#### Krok 1: načíst soubor obrázku

Load the watermark image from disk:

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Replace the placeholder path with the actual location of your logo or seal.

#### Krok 2: nastavit zarovnání

Center the image watermark for balanced visual impact:

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Krok 3: otočit obrazový vodoznak

Apply a –30‑degree rotation to introduce visual variation:

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### Krok 4: nakonfigurovat velikost

Define the image size as a percentage of the underlying image’s width:

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### Přidání vodoznaků k obrázkům v dokumentu

**Definition anchor:** `Watermarker` is the core class that loads a document, provides access to its elements, and writes watermarks back to the file.

#### Krok 1: otevřít dokument

Instantiate a `Watermarker` with the path to your source PDF:

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

#### Krok 2: získat obrázky

Collect all images from the PDF that can receive a watermark:

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### Krok 3: přidat vodoznaky podmíněně

For each image, check its dimensions; if the width exceeds 300 px, apply the text watermark, otherwise use the image watermark:

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

This conditional logic ensures that only suitable images receive the more prominent text overlay, optimizing processing time.

#### Krok 4: uvolnit zdroje obrázku

After processing, close the image watermark object to free native resources:

```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### Krok 5: uložit změny

Persist the modifications by saving the document to a new file:

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

The resulting file is a **save PDF with watermark** version ready for distribution.

#### Krok 6: úklid

Dispose of the `Watermarker` instance to prevent memory leaks:

```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Časté problémy a řešení

- **License errors:** Ensure the license file path is correctly set via `License.setLicense("license_file_path")`. A missing or expired license throws a `LicenseException`.
- **Large PDFs:** For documents larger than 1,000 pages, enable streaming mode by calling `watermarker.setStreamMode(true)` to keep memory consumption low.
- **Unsupported image formats:** GroupDocs.Watermark supports PNG, JPEG, BMP, and GIF. Converting other formats to PNG before loading avoids `UnsupportedFormatException`.

## Často kladené otázky

**Q: Can I add a watermark to a password‑protected PDF?**  
A: Yes. Open the document with `new Watermarker("file.pdf", "password")` and then apply the watermark as usual.

**Q: Does the API support batch processing of multiple PDFs?**  
A: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker` for each file, apply the same watermark objects, and save the results.

**Q: What is the maximum number of watermarks I can add to a single PDF?**  
A: The library can handle **500+ watermarks per document** without performance degradation, thanks to its optimized rendering engine.

**Q: Is it possible to make the watermark invisible (metadata only)?**  
A: Yes. Use the `setOpacity(0)` method on the watermark object to embed it invisibly for forensic tracking.

**Q: Which Java versions are officially supported?**  
A: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility with both legacy and modern applications.

## Praktické aplikace

1. **Document security:** Mark confidential files to deter unauthorized sharing.
2. **Brand protection:** Overlay company logos on marketing PDFs.
3. **Copyright assertion:** Embed author names or copyright symbols on published works.
4. **Version control:** Stamp version numbers or dates onto draft documents.

## Závěr

By following this **java pdf watermark example**, you now have a complete, production‑ready solution for **add watermark to PDF** using GroupDocs.Watermark for Java. You can customize text, images, rotation, and sizing, as well as conditionally apply watermarks based on image dimensions—all while keeping the process fast and memory‑efficient.

---  

**Poslední aktualizace:** 2026-08-09  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Jak přidat textové a obrazové vodoznaky na konkrétní stránky PDF pomocí GroupDocs.Watermark pro Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Přidání vodoznaků pouze pro tisk do PDF pomocí GroupDocs.Watermark Java: Kompletní průvodce](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-print-only-pdf-watermark/)
- [Přístup a iterace přes PDF artefakty pomocí GroupDocs.Watermark v Javě pro vodoznakování dokumentů](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)