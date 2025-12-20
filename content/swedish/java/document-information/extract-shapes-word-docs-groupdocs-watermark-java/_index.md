---
date: '2025-12-20'
description: Lär dig hur du extraherar bilder från Word-dokument och extraherar former
  med GroupDocs.Watermark för Java, perfekt för dokumentautomatisering och -manipulation.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Hur man extraherar bilder från Word-dokument med GroupDocs.Watermark i Java
type: docs
url: /sv/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Så extraherar du bilder från Word-dokument med GroupDocs.Watermark i Java

I moderna dokument‑behandlingsapplikationer är **extract images from word** dokument ett vanligt krav—oavsett om du behöver återanvända grafik, köra OCR eller helt enkelt granska innehåll. Denna handledning visar dig, steg för steg, hur du laddar ett Word‑dokument i Java med GroupDocs.Watermark och sedan **extract images from word**‑filer samtidigt som du demonstrerar **how to extract shapes**. I slutet har du ett återanvändbart kodexempel som passar direkt in i din automationspipeline.

## Snabba svar
- **Vilket bibliotek hanterar bildextraktion?** GroupDocs.Watermark for Java  
- **Kan jag extrahera både bilder och vektorgrafik?** Ja – API‑et ger åtkomst till bilder och formmetadata.  
- **Vilken Java‑version krävs?** JDK 8 eller högre.  
- **Behöver jag en licens för produktion?** En kommersiell licens rekommenderas; en gratis provperiod fungerar för utvärdering.  
- **Är processen minnes‑effektiv för stora filer?** Ja, du kan frigöra resurser omedelbart och bearbeta sektioner inkrementellt.

## Vad är “Extract Images from Word”?
Att extrahera bilder från Word innebär att programmässigt lokalisera varje bild, ritning eller inbäddad grafik i en `.docx`‑fil och hämta dess binära data eller metadata. Detta möjliggör efterföljande uppgifter såsom bildanalys, innehållsmigrering eller dynamisk rapportgenerering.

## Varför använda GroupDocs.Watermark för denna uppgift?
GroupDocs.Watermark erbjuder ett hög‑nivå API som abstraherar komplexiteten i OpenXML‑formatet. Det låter dig **load word document java**‑projekt med bara några rader kod, samtidigt som det exponerar detaljerad forminformation—perfekt för utvecklare som behöver både bildextraktion och formanalys.

## Förutsättningar
- **Java Development Kit (JDK)** 8 eller nyare  
- **IDE** – IntelliJ IDEA, Eclipse eller någon Java‑kompatibel editor  
- Grundläggande kunskap om Java I/O  
- Tillgång till en GroupDocs.Watermark‑licens (provperiod fungerar för testning)

## Installera GroupDocs.Watermark för Java
Integrera biblioteket via Maven eller direkt nedladdning.

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
För full funktionalitet, skaffa en licensnyckel från GroupDocs‑portalen. En tillfällig provlicens kan begäras för att utforska alla funktioner utan begränsningar.

## Implementeringsguide
Vi delar upp implementeringen i två logiska delar:

1. **Hur man laddar ett Word‑dokument i Java**  
2. **Hur man extraherar former och bilder (dvs. extract images from word)**

### Ladda ett Word‑dokument
Först konfigurerar du laddningsalternativen och instansierar `Watermarker`.

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

> **Pro tip:** Ersätt `"YOUR_DOCUMENT_DIRECTORY/document.docx"` med en absolut eller relativ sökväg som pekar på den fil du vill bearbeta.

### Extrahera form‑ och bildinformation
Nu när dokumentet är laddat kan du iterera genom varje sektion och varje form, och hämta både vektorformdata och inbäddade bilddetaljer.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

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

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
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

> **Varför detta är viktigt:** Anropet `shape.getImage()` ger dig direkt åtkomst till den binära representationen av varje bild, vilket gör att du kan spara den till disk, skicka den över ett nätverk eller mata in den i ett bild‑behandlingsbibliotek.

## Vanliga problem och lösningar
| Problem | Lösning |
|---------|----------|
| **FileNotFoundException** – fel sökväg | Verifiera filvägen och säkerställ att applikationen har läs‑behörighet. |
| **OutOfMemoryError** på stora dokument | Bearbeta sektioner en i taget och anropa `watermarker.close()` så snart du är klar med ett batch. |
| Former returnerar `null` för `getImage()` | Alla former är inte bilder; vissa är ritobjekt. Kontrollera `shape.getShapeType()` innan du åtkommer bilden. |
| Licens inte tillämpad | Lägg till `License.setLicense("path/to/license/file.lic");` innan du skapar `Watermarker`. |

## Praktiska tillämpningar
- **Automatiserad rapportgenerering:** Hämta diagram och logotyper från mallar för återanvändning i instrumentpaneler.  
- **Innehållsgranskning:** Skanna företagsdokument för förbjudna grafik.  
- **Migrationsprojekt:** Exportera inbäddade bilder innan innehållet flyttas till ett nytt CMS.

## Prestandaöverväganden
- Frigör `Watermarker`‑instansen omedelbart (`watermarker.close()`).  
- För massiva filer (>50 MB), överväg att strömma sektioner istället för att ladda hela dokumentet i minnet.  
- Använd den senaste GroupDocs.Watermark‑versionen för prestandaförbättringar.

## Slutsats
Du har nu ett komplett, produktionsklart tillvägagångssätt för att **extract images from word**‑dokument och hämta formmetadata med GroupDocs.Watermark för Java. Denna funktionalitet öppnar upp kraftfulla automationsscenarier, från att generera dynamiska rapporter till att utföra storskaliga dokumentgranskningar.

### Nästa steg
- Experimentera med att spara extraherade bilder till disk (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Utforska ytterligare API:er såsom borttagning eller tillägg av vattenstämplar.  
- Integrera denna logik i ditt befintliga dokument‑hanteringsarbetsflöde.

## FAQ‑avsnitt
**Q: Vad är GroupDocs.Watermark för Java?**  
A: Det är ett omfattande bibliotek designat för att hantera vattenstämplar och extrahera visuella element i olika dokumentformat, vilket underlättar automatisering av dokumentmanipuleringsuppgifter.

**Q: Kan jag extrahera bilder från lösenordsskyddade Word‑filer?**  
A: Ja. Ladda dokumentet med `WordProcessingLoadOptions` som inkluderar lösenordet, och fortsätt sedan med samma extraktionslogik.

**Q: Stöder API‑et .doc (binära) filer också?**  
A: Biblioteket fokuserar främst på OpenXML‑formatet `.docx`, men det kan även öppna äldre `.doc`‑filer efter konvertering.

**Q: Hur sparar jag de extraherade bilderna till filsystemet?**  
A: Använd `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` inuti loopen där `shape.getImage()` inte är null.

**Q: Finns det någon gräns för hur många former jag kan bearbeta?**  
A: Ingen hård gräns, men minnesförbrukningen ökar med dokumentstorleken; bearbeta sektioner sekventiellt för mycket stora filer.

---

**Senast uppdaterad:** 2025-12-20  
**Testad med:** GroupDocs.Watermark 24.11 for Java  
**Författare:** GroupDocs