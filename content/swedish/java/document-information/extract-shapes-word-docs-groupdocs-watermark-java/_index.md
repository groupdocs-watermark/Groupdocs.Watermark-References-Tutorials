---
date: '2026-02-05'
description: Lär dig hur du extraherar former från Word‑dokument med GroupDocs.Watermark
  för Java, inklusive hur du laddar ett Word‑dokument i Java och manipulerar formdata.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Hur man extraherar former från Word‑dokument med GroupDocs.Watermark Java
type: docs
url: /sv/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Hur man extraherar former från Word-dokument med GroupDocs.Watermark i Java

I den här handledningen får du reda på **hur man extraherar former** från Word-dokument med GroupDocs.Watermark‑biblioteket för Java. Oavsett om du behöver analysera diagram, hämta inbäddade bilder eller automatisera rapportgenerering, ger extrahering av formmetadata dig kontrollen att bygga smartare dokument‑bearbetningspipeline. Vi går igenom hur du installerar biblioteket, laddar ett Word‑dokument och hämtar detaljerad forminformation – allt i tydlig, steg‑för‑steg‑Java‑kod.

## Snabba svar
- **Vad betyder “extrahera former”?** Att hämta metadata (typ, storlek, position, text, bilder) för varje ritobjekt i en Word‑fil.  
- **Vilket bibliotek hanterar detta?** GroupDocs.Watermark för Java.  
- **Behöver jag en licens?** En provversion fungerar för utveckling; en full licens tar bort användningsgränser.  
- **Kan jag också få bilder från former?** Ja – API‑et exponerar bild‑bytarna för bildformer.  
- **Vilken Java‑version krävs?** JDK 8 eller nyare.

## Vad betyder “Hur man extraherar former” i samband med Word-dokument?
Att extrahera former innebär att programmässigt komma åt varje rit‑element – bilder, WordArt, auto‑former, diagram och även former som är inbäddade i sidhuvuden eller sidfötter. Denna information kan användas för validering, migrering eller innehålls‑driven analys.

## Varför använda GroupDocs.Watermark för Java?
GroupDocs.Watermark erbjuder ett hög‑nivå, minnes‑effektivt API som döljer komplexiteten i det underliggande Office Open XML‑formatet. Det låter dig:
- Ladda dokument snabbt (`WordProcessingLoadOptions`).  
- Iterera genom sektioner och former utan att behöva hantera låg‑nivå XML.  
- Hämta bilddata, text, justering och rotation i ett enda anrop.  
- Integrera sömlöst i befintliga Java‑tjänster eller mikrotjänster.

## Förutsättningar
- **Java Development Kit (JDK)** 8 eller högre.  
- **IDE** såsom IntelliJ IDEA eller Eclipse.  
- Grundläggande kunskap om Java‑I/O.  
- Tillgång till en **GroupDocs.Watermark för Java**‑licens eller provversion.

## Installera GroupDocs.Watermark för Java
Integrera biblioteket via Maven eller en direkt nedladdning.

### Använda Maven
Lägg till repository och beroende i din `pom.xml`:

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
Alternativt kan du ladda ner den senaste JAR‑filen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licensanskaffning
En gratis provversion räcker för testning. För produktion, begär en permanent licens för att låsa upp alla funktioner.

## Implementeringsguide
Vi delar upp implementeringen i två tydliga steg: **ladda Word‑dokumentet** och **extrahera forminformation**.

### Steg 1: Ladda ett Word‑dokument (load word document java)
Först konfigurerar du laddningsalternativen och skapar en `Watermarker`‑instans. Detta förbereder dokumentet för vidare inspektion.

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

> **Proffstips:** Håll `Watermarker`‑instansen så kortlivad som möjligt; att stänga den omedelbart frigör inhemska resurser och undviker minnesläckor.

### Steg 2: Extrahera forminformation (extract images from shapes)
Nu hämtar vi varje forms detaljer, inklusive eventuella inbäddade bilder. Koden itererar genom varje sektion och varje form och skriver ut användbar metadata.

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

**Vad koden gör:**  
- Hämtar varje forms **typ** (t.ex. picture, WordArt).  
- Skriver ut **storlek**, **position** och **rotations**‑värden.  
- Visar **alternativ text** och **namn**, vilket är användbart för tillgänglighetskontroller.  
- Om formen innehåller en bild, skriver den ut bildens **pixeldimensioner** och **byte‑storlek** – perfekt för att extrahera bilder från former.  

### Vanliga fallgropar & hur man löser dem
| Problem | Orsak | Lösning |
|---------|-------|----------|
| `FileNotFoundException` | Fel filväg eller saknade behörigheter | Verifiera den absoluta/relativa vägen och säkerställ att filen är läsbar. |
| Null `shape.getImage()` | Formen är inte en bild (t.ex. auto‑shape) | Sätt ett skydd med `if (shape.getImage() != null)` som i exemplet. |
| Hög minnesanvändning för stora dokument | Laddar hela dokumentet på en gång | Processa sektioner en i taget eller öka JVM‑heapen (`-Xmx`). |
| Saknade former i sidhuvud/sidfötter | Kontrollerar inte `shape.getHeaderFooter()` | Exemplet loggar redan när en form tillhör ett sidhuvud eller en sidfot. |

## Praktiska tillämpningar
1. **Automatiserad rapportgenerering** – Hämta diagram och scheman för att bädda in i efterföljande PDF‑filer.  
2. **Efterlevnadskontroll** – Verifiera att alla former har lämplig alternativ text för tillgänglighet.  
3. **Innehållsmigrering** – Exportera inbäddade bilder från äldre Word‑filer till ett digitalt tillgångshanteringssystem.  

## Prestandaöverväganden
- **Frigör resurser**: Anropa alltid `watermarker.close()` i ett `finally`‑block eller använd try‑with‑resources om du omsluter API‑et.  
- **Chunk‑bearbetning**: För dokument som överstiger 50 MB, överväg att bearbeta varje sektion separat för att hålla minnesavtrycket lågt.  
- **Trådsäkerhet**: `Watermarker`‑instanser är inte trådsäkra; skapa en ny instans per tråd.

## Slutsats
Du vet nu **hur man extraherar former** från Word‑dokument med GroupDocs.Watermark för Java, från att ladda filen till att läsa varje forms metadata och inbäddade bilddata. Denna funktion öppnar dörrar till avancerad dokumentanalys, automatiserade innehållspipelines och tillgänglighetsvalidering.

### Nästa steg
- Experimentera med att ändra formegenskaper (t.ex. storleksändring eller ompositionering).  
- Kombinera detta tillvägagångssätt med **GroupDocs.Parser** för att extrahera omgivande text.  
- Integrera extraheringslogiken i en REST‑tjänst för on‑demand‑bearbetning.

## FAQ‑avsnitt
**Q: Vad är GroupDocs.Watermark för Java?**  
A: Det är ett omfattande bibliotek designat för att hantera vattenstämplar och dokumentinnehåll över olika format, vilket möjliggör uppgifter som formextraktion, bildhämtning och textmanipulation.

**Q: Kan jag extrahera bilder från former utan licens?**  
A: Provversionen tillåter extraktion, men en full licens tar bort användningsgränser och möjliggör kommersiell distribution.

**Q: Fungerar detta med `.doc` (binära) filer?**  
A: Ja, API‑et stödjer både `.docx` och äldre `.doc`‑format.

**Q: Hur hanterar jag lösenordsskyddade dokument?**  
A: Ange lösenordet via `WordProcessingLoadOptions.setPassword("yourPassword")` innan du skapar `Watermarker`.

**Q: Finns det ett sätt att exportera den extraherade formdatan till JSON?**  
A: Du kan mappa de utskrivna värdena till en POJO och använda ett JSON‑bibliotek (t.ex. Jackson) för att serialisera samlingen.

---

**Senast uppdaterad:** 2026-02-05  
**Testat med:** GroupDocs.Watermark 24.11 för Java  
**Författare:** GroupDocs