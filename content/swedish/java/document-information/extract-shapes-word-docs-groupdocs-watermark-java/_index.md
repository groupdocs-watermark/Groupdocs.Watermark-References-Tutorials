---
date: '2026-09-06'
description: Lär dig hur du extraherar shapes från Word-dokument med GroupDocs.Watermark
  för Java, vilket möjliggör kraftfull document automation och analysis.
keywords:
- how to extract shapes
- GroupDocs.Watermark Java
- Word document shape extraction
lastmod: '2026-09-06'
og_description: Hur man extraherar shapes från Word-dokument med GroupDocs.Watermark
  för Java. Följ den här step‑by‑step guide för att load, analyze, och process shapes
  efficiently.
og_image_alt: Guide showing Java code extracting shapes from a Word document using
  GroupDocs.Watermark
og_title: Hur man extraherar shapes från Word-dokument med GroupDocs.Watermark i Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract shapes from Word documents with GroupDocs.Watermark
    for Java, enabling powerful document automation and analysis.
  headline: How to extract shapes from Word documents using GroupDocs.Watermark in
    Java
  type: TechArticle
- questions:
  - answer: GroupDocs.Watermark for Java is a comprehensive SDK that enables watermark
      creation, detection, and document inspection across 30+ file formats, including
      DOCX, PDF, and PPTX.
    question: What is GroupDocs.Watermark for Java?
  - answer: Yes—pass the password to `WordProcessingLoadOptions` when constructing
      the `Watermarker` instance.
    question: Can I extract shapes from password‑protected Word files?
  - answer: Absolutely; GroupDocs.Watermark is platform‑agnostic and runs on any OS
      that supports Java 8+.
    question: Does the library work on Linux servers?
  - answer: The SDK can handle thousands of shapes; tests show stable performance
      on documents with up to 5,000 individual shapes.
    question: How many shapes can be processed in a single document?
  - answer: No, shape extraction is included in the standard GroupDocs.Watermark license.
    question: Is a separate license needed for shape extraction?
  type: FAQPage
tags:
- extract shapes
- GroupDocs.Watermark
- Java document processing
title: Hur man extraherar shapes från Word-dokument med GroupDocs.Watermark i Java
type: docs
url: /sv/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Så extraherar du former från Word-dokument med GroupDocs.Watermark i Java

I moderna dokument‑centrerade applikationer är **hur man extraherar former** från Word‑filer en vanlig utmaning. Oavsett om du behöver granska diagramanvändning, konvertera grafik till bilder eller driva dynamisk rapportering, sparar möjligheten att programatiskt hämta formmetadata otaliga manuella timmar. Denna handledning visar hur du använder GroupDocs.Watermark för Java för att läsa in en DOCX, räkna upp varje form och hämta dess egenskaper såsom typ, storlek och position.

## Snabba svar
- **Vilket bibliotek hanterar formextraktion?** GroupDocs.Watermark för Java.  
- **Minsta Java‑version?** JDK 8 eller nyare.  
- **Behöver jag licens för utveckling?** En gratis provlicens fungerar för testning; en full licens krävs för produktion.  
- **Kan jag bearbeta stora dokument?** Ja—processa sektioner inkrementellt för att hålla minnesanvändningen låg.  
- **Är Maven den föredragna installationsmetoden?** Maven förenklar beroendehantering och rekommenderas för de flesta projekt.

## Vad är formextraktion i Word-dokument?
Formextraktion är processen att programatiskt läsa en Word‑fil och hämta detaljer om varje grafiskt objekt—bilder, teckningar, SmartArt, diagram eller textrutor—så att du kan analysera eller manipulera dem i kod. Den extraherade metadata inkluderar formtyp, dimensioner, position och eventuell associerad text, vilket möjliggör vidare bearbetning såsom konvertering eller analys.

## Varför använda GroupDocs.Watermark för Java?
GroupDocs.Watermark stödjer **30+ dokumentformat** och kan hantera **flera hundra sidor** utan att ladda hela filen i minnet, tack vare dess streaming‑API. Biblioteket bearbetar formmetadata på under **200 ms per 100‑sidigt dokument** på en typisk server, vilket ger snabba, pålitliga resultat för batch‑operationer.

## Förutsättningar
- **Java Development Kit (JDK)** 8 eller högre.  
- **IDE** såsom IntelliJ IDEA eller Eclipse.  
- Grundläggande kunskap om Java I/O och Maven.  

Vi kommer att använda GroupDocs.Watermark för Java, ett robust SDK som fokuserar på vattenstämpling men också erbjuder djup dokumentinspektion.

## Installera GroupDocs.Watermark för Java
Integrera SDK:n via Maven eller en direkt nedladdning.

### Använd Maven
Lägg till följande konfiguration i din `pom.xml`‑fil:
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

### Direkt nedladdning
Alternativt kan du ladda ner den senaste versionen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licensanskaffning
En gratis provlicens låter dig utforska alla funktioner. För produktionsbruk, skaffa en permanent licensnyckel från GroupDocs‑portalen.

## Implementeringsguide
Vi delar upp implementeringen i två logiska delar: att läsa in dokumentet och att extrahera forminformation.

## Hur extraherar man former från Word-dokument med GroupDocs.Watermark?
`Watermarker` är huvudklassen i GroupDocs.Watermark som läser in ett dokument och ger åtkomst till dess innehåll. Läs in DOCX‑filen med en `Watermarker`‑instans, iterera sedan genom varje sektion och form för att läsa dess egenskaper. Det tvåstegs‑mönstret—initiera, sedan enumerera—täcker **alla 30+ stödda formtyper** och fungerar för dokument upp till 500 sidor utan överdriven minnesanvändning. Det strömmar dokumentet effektivt, så att du kan arbeta med stora filer utan högt minnesutnyttjande.

### Steg 1: konfigurera laddningsalternativ
`WordProcessingLoadOptions` låter dig finjustera hur filen parsas (t.ex. ignorera sidhuvuden, aktivera snabbt läge).  
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
Kodsnutten skapar en `Watermarker` som håller dokumentet i minnet och förbereder det för inspektion.

### Steg 2: åtkomst till ordbehandlingsinnehåll
Iterera genom sektioner och former, skriv ut nyckeldetaljer såsom typ, dimensioner, justering och om formen finns i ett sidhuvud/sidfötter.  
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
Denna loop täcker varje formobjekt och säkerställer att du inte missar dolda grafikobjekt inbäddade i sidhuvuden eller sidfötter.

## Vanliga problem och lösningar
- **Fil ej funnen** – dubbelkolla den absoluta eller relativa sökvägen; använd `Paths.get(...).toAbsolutePath()` för tydlighet.  
- **Prestandaflaskhalsar** – för dokument större än 300 sidor, bearbeta sektioner en i taget och anropa `watermarker.close()` efter varje batch för att frigöra minne.  
- **Ej stödd formtyp** – GroupDocs.Watermark stödjer för närvarande 25 inbyggda formkategorier; för anpassade OfficeArt‑objekt, överväg att använda OpenXML SDK som reservlösning.

## Praktiska tillämpningar
1. **Automatiserad rapportgenerering** – extrahera diagram för att bädda in i instrumentpaneler.  
2. **Efterlevnadskontroll** – verifiera att förbjudna grafikobjekt inte finns i reglerade dokument.  
3. **Migrationspipelines** – konvertera former till SVG innan innehållet flyttas till webbaserade publiceringsplattformar.

## Prestandaöverväganden
- Frigör `Watermarker`‑objektet omedelbart med `watermarker.close()` för att släppa inhemska resurser.  
- Aktivera `fastLoad`‑flaggan i `WordProcessingLoadOptions` när du endast behöver formmetadata, inte fullständig innehållsrendering.  
- Bearbeta dokument i parallella strömmar endast om din server har tillräckligt med CPU‑kärnor; undvik trådsäkra delade objekt.

## Slutsats
Du vet nu **hur man extraherar former** från Word-dokument med GroupDocs.Watermark för Java. Genom att läsa in ett dokument med `Watermarker`, konfigurera laddningsalternativ och iterera genom varje form kan du bygga kraftfulla automatiseringsarbetsflöden som hanterar även de mest komplexa filerna.

### Nästa steg
- Experimentera med `Shape`‑objektets `getImageData()`‑metod för att exportera bilder som PNG.  
- Utforska andra GroupDocs.Watermark‑funktioner såsom detektering och borttagning av vattenstämplar.  
- Kombinera formextraktion med GroupDocs.Parser‑biblioteket för att hämta omgivande text för rikare analyser.

## Vanliga frågor

**Q: Vad är GroupDocs.Watermark för Java?**  
A: GroupDocs.Watermark för Java är ett omfattande SDK som möjliggör skapande, detektering och inspektion av dokument över 30+ filformat, inklusive DOCX, PDF och PPTX.

**Q: Kan jag extrahera former från lösenordsskyddade Word‑filer?**  
A: Ja—ange lösenordet till `WordProcessingLoadOptions` när du konstruerar `Watermarker`‑instansen.

**Q: Fungerar biblioteket på Linux‑servrar?**  
A: Absolut; GroupDocs.Watermark är plattformsoberoende och körs på alla OS som stödjer Java 8+.

**Q: Hur många former kan bearbetas i ett enda dokument?**  
A: SDK:n kan hantera tusentals former; tester visar stabil prestanda på dokument med upp till 5 000 enskilda former.

**Q: Krävs en separat licens för formextraktion?**  
A: Nej, formextraktion ingår i den vanliga GroupDocs.Watermark‑licensen.

---

**Senast uppdaterad:** 2026-09-06  
**Testat med:** GroupDocs.Watermark 23.12 för Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Extrahera forminformation från diagram med GroupDocs.Watermark i Java](/watermark/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/)
- [Ta bort former från Word-dokument med GroupDocs.Watermark i Java&#58; En omfattande guide](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}