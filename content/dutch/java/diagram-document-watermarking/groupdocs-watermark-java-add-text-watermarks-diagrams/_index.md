---
date: '2025-12-19'
description: Leer hoe u een tekstwatermerk aan diagrammen kunt toevoegen met GroupDocs.Watermark
  voor Java. Bescherm uw visuele inhoud effectief en waarborg de integriteit van documenten.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: Tekstwatermerk toevoegen aan diagrammen met GroupDocs.Watermark voor Java –
  Een uitgebreide gids
type: docs
url: /nl/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Tekstwatermerk toevoegen aan diagrammen met GroupDocs.Watermark voor Java: Een uitgebreide gids

## Introductie
Het beschermen van diagramdocumenten tegen ongeautoriseerd gebruik is cruciaal, en **het toevoegen van een tekstwatermerk** biedt een eenvoudige maar effectieve oplossing. In deze tutorial ontdek je hoe je diagrambestanden laadt, een aanpasbaar tekstwatermerk maakt en dit toepast op achtergrondpagina's of specifieke vormen met **GroupDocs.Watermark voor Java**. Aan het einde van de gids kun je je visuele assets beveiligen terwijl je de oorspronkelijke uitstraling behoudt.

### Snelle antwoorden
- **Wat betekent “add text watermark”?**  
  Het betekent het insluiten van een semi‑transparante tekstoverlay in een document om eigendom of vertrouwelijkheid aan te geven.  
- **Welke bibliotheek ondersteunt diagramwatermerken?**  
  GroupDocs.Watermark for Java biedt native ondersteuning voor diagramformaten (bijv. Visio, VSDX).  
- **Heb ik een licentie nodig?**  
  Een tijdelijke of volledige licentie is vereist voor productiegebruik; een gratis proefversie is beschikbaar voor evaluatie.  
- **Kan ik het watermerk op achtergrondpagina's plaatsen?**  
  Ja – gebruik de `DiagramWatermarkPlacementType.SeparateBackgrounds` optie voor een **background page watermark**.  
- **Is de code compatibel met Java 8+?**  
  Absoluut – de bibliotheek werkt met JDK 8 en nieuwer.

## Wat is een tekstwatermerk voor diagrammen?
Een tekstwatermerk is een stuk leesbare tekst (vaak semi‑transparant) dat wordt weergegeven bovenop of achter diagramonderdelen. Het kan worden gebruikt voor branding, auteursrechtbescherming of om vertrouwelijke concepten te markeren.

## Waarom GroupDocs.Watermark voor Java gebruiken?
- **Brede bestandsondersteuning** – werkt met Visio, VSDX en vele andere diagramtypen.  
- **Fijne plaatsingscontrole** – kies voorgrond, achtergrond of specifieke vormwatermerken.  
- **Eenvoudige API** – maak en pas watermerken toe met slechts een paar regels Java‑code.  

## Vereisten
- **GroupDocs.Watermark for Java** (v24.11 of later)  
- **Java Development Kit (JDK)** 8 of hoger  
- Maven (of handmatige JAR‑inclusie)  

## GroupDocs.Watermark voor Java instellen
### Maven‑configuratie
Voeg de volgende configuratie toe aan je `pom.xml`‑bestand:

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
Download de nieuwste versie vanaf [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licentie‑acquisitie
- **Free Trial** – evalueer alle functies zonder licentiesleutel.  
- **Temporary License** – gebruik tijdens ontwikkeling om volledige functionaliteit te ontgrendelen.  
- **Purchase** – verkrijg een productie‑licentie voor commerciële projecten.  

### Basisinitialisatie en -instelling
Zorg ervoor dat de volgende imports aanwezig zijn in je Java‑klasse:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Stapsgewijze implementatie

### Stap 1: Het diagramdocument laden
Wijs de bibliotheek eerst naar je diagram‑bestand en initialiseert laadopties.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Explanation*: `DiagramLoadOptions` laat je bepalen hoe het diagram wordt geparseerd vóór het watermerken.

### Stap 2: Een tekstwatermerk maken
Maak nu de watermerktekst en definieer de visuele stijl.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Explanation*: Dit maakt een `TextWatermark` met de zin **“Test watermark 1”** in het lettertype Calibri met grootte 19.

### Stap 3: Plaatsing configureren – achtergrondpagina‑watermerk
Kies waar het watermerk moet verschijnen. Voor een **background page watermark** gebruik je de volgende optie:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Explanation*: `DiagramShapeWatermarkOptions` bepaalt de exacte locatie. Door het plaatsingstype op `SeparateBackgrounds` te zetten, wordt het watermerk toegevoegd aan elke achtergrondpagina van het diagram.

### Stap 4: Het watermerk toepassen en opslaan
Voeg tenslotte het watermerk toe aan het document, sla het resultaat op en maak bronnen vrij.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Explanation*: De `add`‑methode past het geconfigureerde `textWatermark` toe met de plaatsingsopties, waarna het gewijzigde diagram wordt opgeslagen naar `outputPath`.

## Praktische toepassingen
- **Intellectuele‑eigendom bescherming** – Voorkom dat concurrenten propriëtaire diagrammen hergebruiken.  
- **Merkversterking** – Integreer bedrijfsnaam of logo als tekstwatermerk op alle geëxporteerde diagrammen.  
- **Juridische documentatie** – Markeer vertrouwelijke concepten van technische schema's.  
- **Academische inzendingen** – Voeg student‑ID’s of cursuscodes toe aan diagrammen voor plagiaat‑tracking.

## Prestatie‑overwegingen
- **Geheugenbeheer** – Sluit de `Watermarker`‑instantie (`watermarker.close()`) om native bronnen vrij te geven, vooral bij het verwerken van grote bestanden.  
- **Batchverwerking** – Loop door een verzameling diagram‑paden en hergebruik een enkele `Watermarker`‑instantie waar mogelijk om overhead te verminderen.

## Veelvoorkomende problemen en oplossingen
| Probleem | Oplossing |
|----------|-----------|
| **OutOfMemoryError bij grote diagrammen** | Verhoog de JVM‑heap‑grootte (`-Xmx2g`) en verwerk bestanden één voor één. |
| **Watermerk niet zichtbaar** | Zorg dat de watermerk‑kleur voldoende contrast heeft; stel de opacity in via `textWatermark.setOpacity(0.5)`. |
| **Niet‑ondersteund diagramformaat** | Controleer of het formaat wordt vermeld in de documentatie van ondersteunde formaten van GroupDocs.Watermark. |

## Veelgestelde vragen

**Q: Wat is de beste lettergrootte voor watermerken?**  
A: De optimale grootte hangt af van de afmetingen van het diagram; 12‑20 pt werkt goed voor de meeste gevallen.

**Q: Kan ik watermerk‑kleuren aanpassen?**  
A: Ja, gebruik `textWatermark.setColor(Color.GRAY)` (of een andere `java.awt.Color`).

**Q: Hoe ga ik om met grote batches documenten?**  
A: Maak gebruik van de batch‑API van de bibliotheek of schrijf een lus die `Watermarker`‑objecten hergebruikt om overhead te minimaliseren.

**Q: Zijn er beperkingen bij GroupDocs.Watermark?**  
A: De bibliotheek ondersteunt de meeste gangbare diagramformaten, maar sommige propriëtaire extensies worden mogelijk niet volledig gerenderd. Raadpleeg de [documentation](https://docs.groupdocs.com/watermark/java/) voor details.

**Q: Hoe krijg ik ondersteuning als ik problemen tegenkom?**  
A: Bezoek het [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) voor community‑ondersteuning of neem rechtstreeks contact op met de GroupDocs‑ondersteuning.

## Aanvullende bronnen
- **Documentation**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API Reference**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub Repository**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free Support Forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary License**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---