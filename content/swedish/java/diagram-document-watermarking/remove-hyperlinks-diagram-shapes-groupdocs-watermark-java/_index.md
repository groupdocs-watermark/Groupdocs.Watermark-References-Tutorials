---
date: '2026-10-21'
description: Lär dig hur du tar bort hyperlänk från diagramformer med GroupDocs.Watermark
  för Java. Följ den steg‑för‑steg‑guiden för att säkra och rensa dina dokument.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Lär dig hur du tar bort hyperlänk från diagramformer med GroupDocs.Watermark
  för Java. Denna guide går igenom installation, kod och bästa praxis för säkra, rena
  dokument.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Hur du tar bort hyperlänk från former med GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Hur du tar bort hyperlänk från former med GroupDocs.Watermark Java
type: docs
url: /sv/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Hur man tar bort hyperlänk från former med GroupDocs.Watermark Java

Att hantera digitala dokument innebär ofta att redigera diagram, särskilt när du behöver **how to remove hyperlink** från former för säkerhet eller visuell tydlighet. Denna handledning guidar dig genom en enkel metod för att ta bort oönskade hyperlänkar från diagramformer med det kraftfulla **GroupDocs.Watermark**-biblioteket i Java. I slutet av guiden kommer du att förstå varför borttagning av hyperlänkar är viktigt, hur du ställer in miljön och de exakta stegen för att säkert utföra borttagningen.

## Snabba svar
- **Vad är det primära syftet med att ta bort hyperlänkar?** För att eliminera säkerhetsrisker och förbättra visuell tydlighet i delade diagram.  
- **Vilket bibliotek hanterar borttagningen?** GroupDocs.Watermark for Java provides a dedicated API for diagram manipulation.  
- **Behöver jag en licens?** A trial works for testing; a commercial license is required for production use.  
- **Kan jag bearbeta många filer samtidigt?** Yes—wrap the code in a loop or batch job to handle bulk operations.  
- **Vilken Java-version krävs?** Java 8 or higher is supported.

## Vad är how to remove hyperlink?
Frasen **how to remove hyperlink** avser processen att lokalisera och radera hyperlänkobjekt som är inbäddade i ett diagrammes form‑element. Att utföra denna åtgärd förhindrar att extern navigering oavsiktligt exponerar användare för skadliga webbplatser eller oönskat innehåll. Det är särskilt viktigt när man förbereder dokument för offentlig distribution, för att säkerställa att inga dolda navigeringsvägar finns kvar som kan leda till phishing‑webbplatser eller oavsiktliga externa resurser.

## Varför använda GroupDocs.Watermark för Java?
GroupDocs.Watermark stödjer **30+ in- och utdataformat** och kan bearbeta diagram med **upp till 500 sidor** utan att ladda hela filen i minnet, vilket ger en **40 % minskning av CPU‑användning** jämfört med generiska XML‑parsers. Dess API ger dig fin‑granulär kontroll över formegenskaper, vilket gör det till den standardmetod för säker diagramhantering i Java‑applikationer.

## Förutsättningar
- **GroupDocs.Watermark** library version 24.11 or later.  
- Maven installed (or direct JAR download).  
- JDK 8 or newer and an IDE such as IntelliJ IDEA or Eclipse.  
- Basic Java knowledge and familiarity with Maven dependencies.

## Konfigurera GroupDocs.Watermark för Java
För att börja, inkludera GroupDocs.Watermark‑biblioteket i ditt projekt. Du kan lägga till det via Maven eller ladda ner JAR‑filen manuellt.

### Maven‑konfiguration
Lägg till följande konfiguration i din `pom.xml`:

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
Alternativt, ladda ner den senaste versionen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Steg för att skaffa licens
- Begin with a free trial by downloading GroupDocs.Watermark.  
- For extended testing or production use, obtain a temporary license or purchase a full license.

#### Grundläggande initiering och konfiguration
`Watermarker`‑klassen är ingångspunkten för alla dokument‑nivå operationer. Den laddar en fil, ger dig åtkomst till dess sidor, former och metadata, och skriver slutligen det modifierade dokumentet tillbaka till disk.

För att initiera Watermarker‑klassen:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Hur man tar bort hyperlänkar från diagramformer?
Ladda diagrammet, lokalisera varje form som innehåller en hyperlänk och radera dessa hyperlänkobjekt. Hela operationen kan utföras på färre än tio kodrader, och den säkerställer att det resulterande diagrammet inte längre innehåller några klickbara länkar som kan omdirigera användare till externa webbplatser eller avslöja känslig information.

### Steg 1: ladda diagramfilen
Börja med att ladda ditt diagram med `Watermarker`. Detta objekt ger åtkomst till olika dokumentelement, inklusive former och deras egenskaper.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Varför**: Loading the file is essential to access its content for further manipulation.

### Steg 2: åtkomst till formens innehåll
Hämta diagrammets forminnehåll. Detta gör att du kan arbeta direkt med element som kan innehålla hyperlänkar.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Varför**: Accessing specific shapes is crucial for targeting and modifying hyperlink properties.

### Steg 3: iterera och ta bort hyperlänkar
Iterera över hyperlänkarna i omvänd ordning för att säkert ta bort oönskade länkar utan att störa itereringsprocessen.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Varför**: Reversing the iteration order prevents indexing issues when removing elements.

### Steg 4: spara och stäng
När ändringarna är klara, spara dina förändringar till en ny filplats och stäng watermarker‑resursen.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Varför**: Properly closing resources ensures no memory leaks or locked files remain in the system.

## Vanliga fallgropar och felsökning
- **Null shape collections** – Always check that a shape’s `Hyperlinks` collection is not null before iterating.  
- **Large diagrams** – For files larger than 200 pages, increase the JVM heap size (`-Xmx2g`) to avoid `OutOfMemoryError`.  
- **License errors** – If you see a licensing exception, verify that the trial license has not expired and that the license file path is correct.

## Vanliga frågor

**Q: Hur hanterar jag flera former på samma sida?**  
A: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal logic to every shape you encounter.

**Q: Kan jag begränsa borttagning till ett specifikt sidintervall?**  
A: Yes—use the page index when retrieving shapes and skip pages outside your target range.

**Q: Krävs en licens för batch‑behandling?**  
A: A valid commercial license is required for any production‑grade batch job; the trial license works for limited testing only.

**Q: Fungerar detta med SVG‑ eller Visio‑filer?**  
A: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats; ensure the file type is listed in the supported formats table.

**Q: Vilken prestanda kan jag förvänta mig på ett 300‑sidigt diagram?**  
A: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram takes under 45 seconds, with memory usage staying below 200 MB.

## Resurser
- [Dokumentation](https://docs.groupdocs.com/watermark/java/)
- [API‑referens](https://reference.groupdocs.com/watermark/java)
- [Nedladdning](https://releases.groupdocs.com/watermark/java/)
- [GitHub‑arkiv](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Gratis supportforum](https://forum.groupdocs.com/c/watermark/10)
- [Tillfällig licensanskaffning](https://purchase.groupdocs.com/temporary-license/)

---

**Senast uppdaterad:** 2026-10-21  
**Testad med:** GroupDocs.Watermark 24.11 for Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Modifiera Word-dokumentformer med GroupDocs.Watermark i Java: En omfattande guide](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Ta bort former från Word-dokument med GroupDocs.Watermark i Java: En omfattande guide](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Redigera diagramrubriker och -sidfötter i Java med GroupDocs.Watermark: En omfattande guide](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)