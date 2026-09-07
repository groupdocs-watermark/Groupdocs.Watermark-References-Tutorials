---
date: '2026-02-13'
description: Lär dig hur du extraherar former och bild från en form med GroupDocs.Watermark
  för Java, och hämtar detaljerad diagraminformation effektivt.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Hur man extraherar former från diagram med GroupDocs.Watermark i Java
type: docs
url: /sv/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Hur man extraherar former från diagram med GroupDocs.Watermark i Java

När du behöver **hur man extraherar former** från ett Visio‑liknande diagram programmässigt, ger GroupDocs.Watermark‑biblioteket dig ett rent, Java‑först sätt att hämta varje detalj—dimensioner, positioner, inbäddade bilder och till och med texten i varje form. I den här handledningen kommer du att se exakt **hur man extraherar former**, varför det är viktigt och steg‑för‑steg‑kod som du kan kopiera in i ditt projekt.

## Snabba svar
- **Vilket bibliotek hanterar extrahering av former?** GroupDocs.Watermark for Java  
- **Vilken Java‑version krävs?** JDK 8 eller högre  
- **Kan jag få bilddata från en form?** Ja – använd `shape.getImage()`  
- **Är text inuti en form åtkomlig?** Absolut, via `shape.getText()`  
- **Behöver jag en licens för produktion?** En giltig GroupDocs.Watermark‑licens krävs  

## Introduktion

Att hantera komplexa diagram kräver ofta åtkomst till detaljerad information om deras komponenter, såsom former och bilder. Om du någonsin har behövt programmässigt hämta data som dimensioner, positioner eller text som är kopplad till diagramformer med Java, är den här handledningen för dig. Genom att utnyttja kraften i GroupDocs.Watermark‑biblioteket kan du förenkla denna process i en Java‑applikation. I den här guiden går vi igenom **hur man extraherar former** från en diagramfil och visar också hur du **extraherar bild från form** och **extraherar text från form**.

## Vad är “hur man extraherar former”?

Att extrahera former innebär att läsa diagrammets interna objekt (sidor, former, bilder, text) så att du kan analysera, transformera eller återanvända dem i andra applikationer—perfekt för automatisering, rapportering eller integration med CAD‑verktyg.

## Varför använda GroupDocs.Watermark för extrahering av former?

- **Full formatstöd** – fungerar med VSDX, VDX och många andra diagramtyper.  
- **Rik objektmodell** – ger direkt åtkomst till formgeometri, bilder och text.  
- **Inga externa beroenden** – ren Java, enkelt att bädda in i Maven‑projekt.  

## Förutsättningar

- **GroupDocs.Watermark for Java** (version 24.11 eller senare)  
- Java Development Kit (JDK) 8 eller högre  
- Maven för beroendehantering  
- En IDE såsom IntelliJ IDEA eller Eclipse  

## Installera GroupDocs.Watermark för Java

Lägg till biblioteket i din Maven `pom.xml`:

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

Du kan också ladda ner de senaste binärerna från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Steg för att skaffa licens
- **Gratis provperiod:** Ladda ner ett provpaket för att utvärdera API‑et.  
- **Tillfällig licens:** Begär en tillfällig nyckel för förlängd testning.  
- **Köp:** Skaffa en full licens för produktionsanvändning.

### Grundläggande initiering och konfiguration

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Hur man extraherar former – Implementeringsguide

### Ladda och hämta innehåll

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Iterera genom former

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Hur man extraherar bild från form

Anropet `shape.getImage()` returnerar ett objekt som innehåller den råa bitmapen, dess dimensioner och byte‑arrayen. Använd egenskaperna som visas ovan för att lagra bilden på disk eller föra in den i en annan behandlingspipeline.

### Hur man extraherar text från form

Metoden `shape.getText()` returnerar den rena texten inuti formen. Om formen inte innehåller någon text returnerar metoden `null`. Det medföljande exempel‑loopen skriver redan ut texten, och du kan vidare manipulera den—till exempel genom att bygga ett index över alla formetiketter.

## Felsökningstips
- Verifiera filvägen och läsbehörigheterna.  
- Säkerställ att du använder ett stödd diagramformat (VSDX, VDX, etc.).  
- Om en form visas utan förväntad data, kontrollera bibliotekets release‑noteringar för format‑specifika nyanser.

## Praktiska tillämpningar

1. **Diagramanalys:** Automatiskt granska diagram för efterlevnad genom att kontrollera formstorlekar eller saknade etiketter.  
2. **Datavisualisering:** Mata in extraherade dimensioner i en rapporterings‑dashboard för att visualisera layoutdensitet.  
3. **CAD‑integration:** Kombinera formdata med CAD‑API:er för att synkronisera design‑specifikationer över verktyg.  

## Prestandaöverväganden

- **Stäng resurser:** Anropa `watermarker.close()` när du är klar för att frigöra inhemska resurser.  
- **Minneshantering:** Stora diagram kan förbruka betydande heap; övervaka minnet och öka `-Xmx` vid behov.  
- **Batch‑behandling:** Bearbeta filer i satser och återanvänd en enda `Watermarker`‑instans när det är möjligt.

## Slutsats

Genom att följa den här guiden vet du nu **hur man extraherar former**, hur man **extraherar bild från form**, och hur man **extraherar text från form** med GroupDocs.Watermark för Java. Dessa tekniker öppnar dörren till automatiserad diagramanalys, rapportering och integration med andra ingenjörssystem. Som nästa steg, utforska hela API‑et genom att titta på dess [documentation](https://docs.groupdocs.com/watermark/java/) och prova att kombinera formextraktion med anpassad affärslogik.

## FAQ‑sektion

1. **Vad är GroupDocs.Watermark?**  
   - Ett omfattande Java‑bibliotek designat för vattenmärkning och extrahering av information från olika dokumentformat, inklusive diagram.  

2. **Kan jag använda detta bibliotek för att bearbeta alla typer av diagramfiler?**  
   - Ja, men säkerställ att filformatet stöds genom att kontrollera [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Hur extraherar jag formens dimensioner och positioner från ett diagram med Java och GroupDocs.Watermark?**  
   - Ladda diagrammet, få åtkomst till `DiagramContent` och iterera sedan över formerna för att hämta egenskaper som bredd, höjd, X och Y.  

4. **Kan GroupDocs.Watermark extrahera bilder som är inbäddade i diagramformer med Java?**  
   - Ja, det tillhandahåller metoder för att komma åt bilddata inom former, inklusive storlek och pixeldata, vilket är användbart för analys eller modifiering.  

5. **Vilka förutsättningar krävs för att extrahera diagramform‑information i Java?**  
   - Java JDK 8+, Maven‑uppsättning, GroupDocs.Watermark‑bibliotek (24.11+), och grundläggande Java‑kunskaper är nödvändiga för implementeringen.  

---

**Senast uppdaterad:** 2026-02-13  
**Testat med:** GroupDocs.Watermark 24.11 for Java  
**Författare:** GroupDocs