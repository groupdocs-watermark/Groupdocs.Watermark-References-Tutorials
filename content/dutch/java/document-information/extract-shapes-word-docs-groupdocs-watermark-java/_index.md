---
date: '2026-02-05'
description: Leer hoe je vormen uit Word‑documenten kunt extraheren met GroupDocs.Watermark
  voor Java, inclusief hoe je een Word‑document in Java kunt laden en vormgegevens
  kunt manipuleren.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Hoe vormen uit Word‑documenten te extraheren met GroupDocs.Watermark Java
type: docs
url: /nl/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Hoe shapes uit Word-documenten te extraheren met GroupDocs.Watermark in Java

In deze tutorial ontdek je **hoe je shapes kunt extraheren** uit Word-documenten met de GroupDocs.Watermark Java‑bibliotheek. Of je nu diagrammen moet analyseren, ingesloten afbeeldingen wilt ophalen, of rapportgeneratie wilt automatiseren, het extraheren van shape‑metadata geeft je de controle om slimmere document‑verwerkings‑pijplijnen te bouwen. We lopen door het instellen van de bibliotheek, het laden van een Word‑document, en het ophalen van gedetailleerde shape‑informatie — allemaal in duidelijke, stap‑voor‑stap Java‑code.

## Snelle antwoorden
- **Wat betekent “extract shapes”?** Het ophalen van metadata (type, grootte, positie, tekst, afbeeldingen) voor elk tekenobject in een Word‑bestand.  
- **Welke bibliotheek behandelt dit?** GroupDocs.Watermark voor Java.  
- **Heb ik een licentie nodig?** Een proefversie werkt voor ontwikkeling; een volledige licentie verwijdert gebruikslimieten.  
- **Kan ik ook afbeeldingen uit shapes krijgen?** Ja – de API maakt de afbeeldingsbytes beschikbaar voor picture‑shapes.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.

## Wat betekent “shapes extraheren” in de context van Word-documenten?
Shapes extraheren betekent programmatisch toegang krijgen tot elk teken‑element — afbeeldingen, WordArt, auto‑shapes, grafieken, en zelfs shapes die in kopteksten of voetteksten zijn ingebed. Deze informatie kan worden gebruikt voor validatie, migratie, of content‑gedreven analytics.

## Waarom GroupDocs.Watermark voor Java gebruiken?
GroupDocs.Watermark biedt een high‑level, geheugen‑efficiënte API die de complexiteit van het onderliggende Office Open XML‑formaat abstraheert. Het stelt je in staat om:
- Documenten snel te laden (`WordProcessingLoadOptions`).  
- Door secties en shapes te itereren zonder low‑level XML te hoeven behandelen.  
- Afbeeldingsgegevens, tekst, uitlijning en rotatie in één oproep op te halen.  
- Naadloos te integreren in bestaande Java‑services of micro‑services.

## Vereisten
- **Java Development Kit (JDK)** 8 of hoger.  
- **IDE** zoals IntelliJ IDEA of Eclipse.  
- Basiskennis van Java I/O.  
- Toegang tot een **GroupDocs.Watermark voor Java** licentie of proefversie.

## GroupDocs.Watermark voor Java instellen
Integreer de bibliotheek via Maven of een directe download.

### Maven gebruiken
Voeg de repository en afhankelijkheid toe aan je `pom.xml`:

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

### Directe download
Of download de nieuwste JAR van [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licentie‑acquisitie
Een gratis proefversie is voldoende voor testen. Voor productie, vraag een permanente licentie aan om alle functies te ontgrendelen.

## Implementatie‑gids
We splitsen de implementatie in twee duidelijke stappen: **het laden van het Word‑document** en **het extraheren van shape‑informatie**.

### Stap 1: Een Word‑document laden (load word document java)
Eerst configureer je de load‑opties en maak je een `Watermarker`‑instantie aan. Dit bereidt het document voor verdere inspectie voor.

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

> **Pro tip:** Houd de `Watermarker`‑instantie zo beperkt mogelijk; deze direct sluiten bevrijdt native resources en voorkomt geheugenlekken.

### Stap 2: Shape‑informatie extraheren (extract images from shapes)
Nu halen we de details van elke shape op, inclusief eventuele ingesloten afbeeldingen. De code iterereert door elke sectie en elke shape, en print nuttige metadata.

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

**Wat deze code doet:**  
- Haalt het **type** van elke shape op (bijv. picture, WordArt).  
- Print de **grootte**, **positie**, en **rotatie** waarden.  
- Toont **alternatieve tekst** en **naam**, wat nuttig is voor toegankelijkheidscontroles.  
- Als de shape een afbeelding bevat, print het de **pixelafmetingen** en **byte‑grootte** van de afbeelding — perfect voor het extraheren van afbeeldingen uit shapes.  

### Veelvoorkomende valkuilen & hoe ze op te lossen
| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| `FileNotFoundException` | Verkeerd bestandspad of ontbrekende permissies | Controleer het absolute/relatieve pad en zorg dat het bestand leesbaar is. |
| Null `shape.getImage()` | Shape is geen afbeelding (bijv. auto‑shape) | Bescherm met `if (shape.getImage() != null)` zoals getoond. |
| High memory usage on large docs | Het volledige document in één keer laden | Verwerk secties één voor één of vergroot de JVM‑heap (`-Xmx`). |
| Missing header/footer shapes | `shape.getHeaderFooter()` niet controleren | Het voorbeeld logt al wanneer een shape tot een header/footer behoort. |

## Praktische toepassingen
1. **Geautomatiseerde rapportgeneratie** – Haal grafieken en diagrammen op om in downstream‑PDF’s in te sluiten.  
2. **Compliance‑audit** – Verifieer dat alle shapes passende alternatieve tekst bevatten voor toegankelijkheid.  
3. **Content‑migratie** – Exporteer ingesloten afbeeldingen uit legacy‑Word‑bestanden naar een digital asset management‑systeem.  

## Prestatie‑overwegingen
- **Resources vrijgeven**: Roep altijd `watermarker.close()` aan in een `finally`‑blok of gebruik try‑with‑resources als je de API omsluit.  
- **Chunk‑verwerking**: Voor documenten groter dan 50 MB, overweeg elke sectie afzonderlijk te verwerken om de geheugenvoetafdruk laag te houden.  
- **Thread‑veiligheid**: `Watermarker`‑instanties zijn niet thread‑safe; maak per thread een nieuwe instantie aan.

## Conclusie
Je weet nu **hoe je shapes kunt extraheren** uit Word‑documenten met GroupDocs.Watermark voor Java, van het laden van het bestand tot het lezen van de metadata en ingesloten afbeeldingsgegevens van elke shape. Deze mogelijkheid opent de deur naar geavanceerde document‑analytics, geautomatiseerde content‑pijplijnen en toegankelijkheidsvalidatie.

### Volgende stappen
- Experimenteer met het wijzigen van shape‑eigenschappen (bijv. grootte aanpassen of verplaatsen).  
- Combineer deze aanpak met **GroupDocs.Parser** om omringende tekst te extraheren.  
- Integreer de extractielogica in een REST‑service voor on‑demand verwerking.

## Veelgestelde vragen
**Q: Wat is GroupDocs.Watermark voor Java?**  
A: Het is een uitgebreide bibliotheek ontworpen om watermerken en documentinhoud over verschillende formaten te beheren, waardoor taken zoals shape‑extractie, afbeeldings‑ophaling en tekstmanipulatie mogelijk zijn.

**Q: Kan ik afbeeldingen uit shapes extraheren zonder licentie?**  
A: De proefversie staat extractie toe, maar een volledige licentie verwijdert gebruikslimieten en maakt commerciële inzet mogelijk.

**Q: Werkt dit met `.doc` (binaire) bestanden?**  
A: Ja, de API ondersteunt zowel `.docx` als legacy `.doc` formaten.

**Q: Hoe ga ik om met wachtwoord‑beveiligde documenten?**  
A: Geef het wachtwoord door via `WordProcessingLoadOptions.setPassword("yourPassword")` voordat je de `Watermarker` aanmaakt.

**Q: Is er een manier om de geëxtraheerde shape‑gegevens naar JSON te exporteren?**  
A: Je kunt de afgedrukte waarden naar een POJO mappen en een JSON‑bibliotheek (bijv. Jackson) gebruiken om de collectie te serialiseren.

---

**Laatst bijgewerkt:** 2026-02-05  
**Getest met:** GroupDocs.Watermark 24.11 for Java  
**Auteur:** GroupDocs