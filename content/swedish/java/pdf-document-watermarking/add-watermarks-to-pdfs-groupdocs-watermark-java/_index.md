---
date: '2026-08-09'
description: Lär dig hur du lägger till watermark i PDF med hjälp av GroupDocs.Watermark
  för Java. Detta java pdf watermark‑exempel visar text‑ och bild‑watermarks, samt
  sparar PDF‑filer med watermark.
keywords:
- add watermark to pdf
- save pdf with watermark
- java pdf watermark example
lastmod: '2026-08-09'
og_description: Lär dig hur du lägger till watermark i PDF med GroupDocs.Watermark
  för Java. Detta steg‑för‑steg java pdf watermark‑exempel hjälper dig att snabbt
  spara PDF med watermark.
og_image_alt: Guide showing how to add text and image watermarks to PDF files in Java
og_title: Lägg till watermark i PDF med GroupDocs.Watermark för Java
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
title: Lägg till watermark i PDF med GroupDocs.Watermark för Java
type: docs
url: /sv/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Lägg till vattenstämpel i PDF med GroupDocs.Watermark för Java

## Introduktion

I dagens digitala landskap är skydd av immateriella rättigheter avgörande, och **add watermark to PDF** är ett av de mest effektiva sätten att göra det. Denna handledning guidar dig genom att använda GroupDocs.Watermark för Java för att bädda in både text- och bildvattenstämplar i PDF-filer. I slutet kommer du att kunna:

- Initiera text- och bildvattenstämplar
- Applicera vattenstämplar villkorligt baserat på bildens dimensioner
- **save PDF with watermark** samtidigt som du bevarar originalkvaliteten

Redo att säkra dina dokument? Låt oss börja!

## Snabba svar
- **Which library adds watermarks to PDFs in Java?** GroupDocs.Watermark for Java.
- **Can I add both text and image watermarks?** Yes, the API supports both types in a single run.
- **Do I need a license for development?** A free trial works for testing; a permanent license is required for production.
- **What file formats are supported?** Over 30 formats, including PDF, DOCX, PPTX, and images.
- **How large a PDF can be processed?** Up to 2,000 pages without loading the whole file into memory.

## Vad är add watermark to PDF?
**Add watermark to PDF** betyder att bädda in synliga eller osynliga märken—såsom textsträngar eller logotyper—direkt i en PDF-fil för att ange ägandeskap, konfidentialitet eller varumärkesprofil. Denna process ändrar dokumentets visuella lager samtidigt som originalinnehållet förblir intakt.

## Varför använda GroupDocs.Watermark för Java?
GroupDocs.Watermark stöder **30+ dokumentformat**, kan bearbeta PDF-filer upp till **2 000 sidor** i ett enda pass, och lägger till upp till **500 vattenstämplar per dokument** utan märkbar prestandapåverkan. Dess API är helt trådsäkert, vilket gör det idealiskt för högkapacitets servermiljöer.

## Förutsättningar

Innan du fortsätter, bekräfta att du har:

1. **Java Development Kit (JDK):** Version 8 eller nyare installerad.
2. **GroupDocs.Watermark for Java:** Version 24.11 (eller nyare) tillagd i ditt projekt.
3. **Build tool:** Maven föredras, men en direkt JAR‑nedladdning fungerar också.

### Miljöinställning

#### Maven-konfiguration

Lägg till GroupDocs‑förrådet och beroendet i din `pom.xml`‑fil:

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

#### Direkt nedladdning

Alternativt, ladda ner den senaste JAR‑filen från den officiella releases‑sidan: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licensanskaffning

För en gratis provperiod eller en tillfällig licens, besök licensportalen: [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Produktionsdistributioner bör använda en köpt licens för att ta bort alla provbegränsningar.

## Konfigurera GroupDocs.Watermark för Java

Efter att ha lagt till biblioteket, importera de nödvändiga klasserna i din Java‑källfil:

```java
import com.groupdocs.watermark.Watermarker;
```

Detta importblock gör watermark‑relaterade API:er tillgängliga i hela ditt projekt.

## Implementeringsguide

Vi delar upp implementeringen i logiska sektioner, var och en svarar på en specifik fråga.

### Hur lägger du till vattenstämpel i PDF i Java?

`Watermarker` är huvudklassen som laddar ett dokument och möjliggör att vattenstämplar appliceras.  
Ladda din PDF med `new Watermarker("input.pdf")` och applicera sedan ett vattenstämpel‑objekt innan du anropar `save("output.pdf")`. Detta tvåstegs‑förfarande hanterar både text‑ och bildvattenstämplar i ett enda pass, vilket säkerställer att filen **saved PDF with watermark** effektivt.

### Initiera textvattenstämpel

**Definition anchor:** `TextWatermark` är klassen som representerar ett textöverlägg som kan placeras på sidor, bilder eller vektorgrafik i ett dokument.

#### Steg 1: skapa TextWatermark‑instans

Skapa en `TextWatermark` med önskad text och teckensnittinställningar:

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

Detta exempel sätter vattenstämpeltexten till “Protected image” med Arial, storlek 8.

#### Steg 2: sätt justering

Centrera vattenstämpeln horisontellt och vertikalt för enhetlig positionering:

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Steg 3: rotera vattenstämpeln

Applicera en 45‑graders rotation för att göra vattenstämpeln svårare att ta bort:

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### Steg 4: konfigurera storlek

Skala vattenstämpeln relativt målbildens dimensioner:

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### Initiera bildvattenstämpel

**Definition anchor:** `ImageWatermark` kapslar in en bild (PNG, JPEG, BMP, etc.) som kommer att läggas över dokumentets innehåll som en vattenstämpel.

#### Steg 1: ladda bildfil

Ladda vattenstämpelbilden från disk:

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Ersätt platshållarens sökväg med den faktiska platsen för din logotyp eller sigill.

#### Steg 2: sätt justering

Centrera bildvattenstämpeln för balanserad visuell effekt:

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Steg 3: rotera bildvattenstämpeln

Applicera en –30‑graders rotation för att introducera visuell variation:

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### Steg 4: konfigurera storlek

Definiera bildens storlek som en procentandel av den underliggande bildens bredd:

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### Lägg till vattenstämplar på bilder i ett dokument

**Definition anchor:** `Watermarker` är kärnklassen som laddar ett dokument, ger åtkomst till dess element och skriver tillbaka vattenstämplar till filen.

#### Steg 1: öppna dokumentet

Instansiera en `Watermarker` med sökvägen till din käll‑PDF:

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

#### Steg 2: hämta bilder

Samla alla bilder från PDF‑filen som kan ta emot en vattenstämpel:

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### Steg 3: lägg till vattenstämplar villkorligt

För varje bild, kontrollera dess dimensioner; om bredden överstiger 300 px, applicera textvattenstämpeln, annars använd bildvattenstämpeln:

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

Denna villkorliga logik säkerställer att endast lämpliga bilder får den mer framträdande textöverlägget, vilket optimerar behandlingstiden.

#### Steg 4: frigör bildresurser

Efter bearbetning, stäng bildvattenstämpel‑objektet för att frigöra inhemska resurser:

```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### Steg 5: spara ändringar

Spara ändringarna genom att skriva dokumentet till en ny fil:

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

Den resulterande filen är en **save PDF with watermark** version klar för distribution.

#### Steg 6: rensa upp

Avsluta `Watermarker`‑instansen för att förhindra minnesläckor:

```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Vanliga problem och felsökning

- **License errors:** Ensure the license file path is correctly set via `License.setLicense("license_file_path")`. A missing or expired license throws a `LicenseException`.
- **Large PDFs:** For documents larger than 1,000 pages, enable streaming mode by calling `watermarker.setStreamMode(true)` to keep memory consumption low.
- **Unsupported image formats:** GroupDocs.Watermark supports PNG, JPEG, BMP, and GIF. Converting other formats to PNG before loading avoids `UnsupportedFormatException`.

## Vanliga frågor

**Q: Kan jag lägga till en vattenstämpel i ett lösenordsskyddat PDF?**  
A: Yes. Open the document with `new Watermarker("file.pdf", "password")` and then apply the watermark as usual.

**Q: Stöder API:et batch‑bearbetning av flera PDF‑filer?**  
A: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker` for each file, apply the same watermark objects, and save the results.

**Q: Vad är det maximala antalet vattenstämplar jag kan lägga till i ett enda PDF?**  
A: The library can handle **500+ watermarks per document** without performance degradation, thanks to its optimized rendering engine.

**Q: Är det möjligt att göra vattenstämpeln osynlig (endast metadata)?**  
A: Yes. Use the `setOpacity(0)` method on the watermark object to embed it invisibly for forensic tracking.

**Q: Vilka Java‑versioner stöds officiellt?**  
A: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility with both legacy and modern applications.

## Praktiska tillämpningar

Att lägga till vattenstämplar kan användas i olika verkliga scenarier:

1. **Dokumentsäkerhet:** Märk konfidentiella filer för att avskräcka obehörig delning.
2. **Varumärkesskydd:** Överlagra företagets logotyper på marknadsförings‑PDF‑filer.
3. **Upphovsrättsassertion:** Bädda in författarnamn eller copyright‑symboler i publicerade verk.
4. **Versionskontroll:** Stämpla versionsnummer eller datum på utkastdokument.

## Slutsats

Genom att följa detta **java pdf watermark example** har du nu en komplett, produktionsklar lösning för **add watermark to PDF** med GroupDocs.Watermark för Java. Du kan anpassa text, bilder, rotation och storlek, samt villkorligt applicera vattenstämplar baserat på bilddimensioner—allt medan processen förblir snabb och minnes‑effektiv.

---  

**Senast uppdaterad:** 2026-08-09  
**Testat med:** GroupDocs.Watermark 24.11 for Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [How to Add Text and Image Watermarks to Specific PDF Pages Using GroupDocs.Watermark for Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Add Print-Only Watermarks to PDFs Using GroupDocs.Watermark Java: A Comprehensive Guide](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-print-only-pdf-watermark/)
- [Access and Iterate Over PDF Artifacts Using GroupDocs.Watermark in Java for Document Watermarking](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)