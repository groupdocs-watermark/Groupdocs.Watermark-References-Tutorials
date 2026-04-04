---
date: '2026-04-04'
description: Leer hoe je links uit diagramvormen verwijdert met GroupDocs.Watermark
  Java, waardoor documentbeveiliging en duidelijkheid worden gewaarborgd.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Hoe links uit diagramvormen te verwijderen met GroupDocs.Watermark Java
type: docs
url: /nl/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Hoe links verwijderen uit diagramvormen met GroupDocs.Watermark Java

Het beheren van digitale documenten omvat vaak het bewerken van diagrammen, vooral wanneer je **how to strip links** nodig hebt voor veiligheid of duidelijkheid. In deze tutorial leer je een eenvoudige, stap‑voor‑stap manier om ongewenste hyperlinks uit diagramvormen te verwijderen met behulp van de krachtige **GroupDocs.Watermark** bibliotheek voor Java. Aan het einde heb je schone, link‑vrije diagrammen die veilig te delen zijn.

## Snelle antwoorden
- **What does “how to strip links” mean?** Het verwijst naar het verwijderen van hyperlink‑objecten die in diagramvormen zijn ingebed.  
- **Which library handles this?** GroupDocs.Watermark for Java (versie 24.11 of nieuwer).  
- **Do I need a license?** Een gratis proefversie werkt voor testen; een geldige licentie is vereist voor productie.  
- **Can I process many files at once?** Ja – plaats de code in een lus of batch‑taak.  
- **Is this approach language‑specific?** Het voorbeeld is Java, maar hetzelfde concept geldt voor andere .NET/Java‑API's.

## Wat is “how to strip links” bij diagrambewerking?
Links strippen betekent het vinden van hyperlink‑objecten die aan vormen binnen een diagram zijn gekoppeld (bijv. Visio *.vsdx) en deze verwijderen. Dit elimineert externe URL's die gevoelige informatie kunnen blootstellen of de presentatie‑stroom kunnen onderbreken.

## Waarom GroupDocs.Watermark voor Java gebruiken?
- **Precision** – Directe toegang tot vormobjecten en hun hyperlink‑collecties.  
- **Performance** – Geoptimaliseerd voor grote diagrammen zonder het volledige document in het geheugen te laden.  
- **Cross‑format support** – Werkt met veel diagramformaten (Visio, Draw.io, enz.).

## Vereisten
- **GroupDocs.Watermark** bibliotheek ≥ 24.11.  
- Maven (of handmatige JAR‑inclusie).  
- Java JDK 8 of nieuwer.  
- Een IDE zoals IntelliJ IDEA of Eclipse.

## GroupDocs.Watermark voor Java instellen
### Maven‑configuratie
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
Als je liever geen Maven gebruikt, download dan de nieuwste JAR van de officiële site:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Stappen voor licentie‑acquisitie
- Begin met een gratis proefdownload.  
- Voor productie, verkrijg een tijdelijke of volledige licentie via het GroupDocs‑portaal.

#### Basisinitialisatie en -configuratie
Maak een `Watermarker`‑instantie die naar de map wijst die je diagram bevat:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Hoe links verwijderen uit diagramvormen
Hieronder staat een beknopt, vier‑stappenproces dat **remove hyperlinks java** in actie toont.

### Stap 1: Laad het diagrambestand
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Waarom?* Het laden van het bestand geeft je programmatische toegang tot de pagina's, vormen en hyperlink‑collecties.

### Stap 2: Toegang tot vorminhoud
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Waarom?* Je hebt een referentie nodig naar de specifieke vorm die hyperlinks kan bevatten.

### Stap 3: Itereren en hyperlinks verwijderen
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Waarom?* Itereren in omgekeerde volgorde voorkomt index‑verschuivingsproblemen bij het verwijderen van items uit de collectie.

### Stap 4: Opslaan en sluiten
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Waarom?* Opslaan schrijft het opgeschoonde diagram naar schijf, en sluiten geeft bestands‑handles vrij om geheugenlekken te voorkomen.

## Praktische toepassingen van het verwijderen van links
1. **Security** – Verwijder externe URL's die kunnen leiden tot phishing of datalekken.  
2. **Compliance** – Zorg ervoor dat diagrammen voldoen aan interne beleidsregels vóór distributie.  
3. **Presentation Cleanliness** – Elimineer onnodige klikbare gebieden die kijkers afleiden.

## Prestatie‑overwegingen
- **Loop Efficiency** – Gebruik het hierboven getoonde omgekeerde iteratiepatroon.  
- **Resource Management** – Geef de voorkeur aan `try‑with‑resources` of expliciete `close()`‑aanroepen.  
- **Large Files** – Houd CPU/geheugen in de gaten; overweeg het verwerken van pagina's in batches.

## Veelvoorkomende problemen en oplossingen
- **No hyperlinks found** – Controleer of het diagram daadwerkelijk hyperlink‑objecten bevat; sommige formaten slaan ze anders op.  
- **IndexOutOfBoundsException** – Itereer altijd in omgekeerde volgorde bij het verwijderen van items uit een collectie.  
- **License errors** – Zorg ervoor dat je licentiebestand correct geplaatst is of wordt doorgegeven aan de `Watermarker`‑constructor.

## Veelgestelde vragen

**Q: How do I handle multiple shapes on multiple pages?**  
A: Loop door `content.getPages()` en vervolgens door de `getShapes()`‑collectie van elke pagina, waarbij je dezelfde verwijderlogica op elke vorm toepast.

**Q: Can I filter links by domain instead of a full URL?**  
A: Ja – wijzig de `contains`‑controle om te zoeken naar de domein‑string (bijv. `"example.com"`).

**Q: Is there a way to log which links were removed?**  
A: Binnen de lus, capture `shape.getHyperlinks().get_Item(i).getAddress()` vóór verwijdering en schrijf dit naar een logbestand.

**Q: Does this work with PDF diagrams embedded in other documents?**  
A: GroupDocs.Watermark ondersteunt veel formaten; zorg ervoor dat het bestandstype wordt herkend als een diagram (Visio, VDX, enz.).

**Q: What licensing is required for batch processing?**  
A: Een volledige productie‑licentie is vereist voor alle niet‑proef‑, hoge‑volume operaties.

## Conclusie
Je hebt nu een volledige, productie‑klare methode voor **how to strip links** uit diagramvormen met GroupDocs.Watermark voor Java. Integreer dit in je document‑verwerkingspijplijnen om veiligheid, naleving en visuele kwaliteit te verbeteren.

### Volgende stappen
- Verken andere manipulatiefuncties zoals het toevoegen van watermerken of het stempelen van tekst.  
- Combineer deze routine met een bestands‑watcher‑service om diagrammen automatisch te reinigen bij het uploaden.

---

**Laatst bijgewerkt:** 2026-04-04  
**Getest met:** GroupDocs.Watermark 24.11 for Java  
**Auteur:** GroupDocs  

## Bronnen
- [Documentatie](https://docs.groupdocs.com/watermark/java/)
- [API‑referentie](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub‑repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Gratis ondersteuningsforum](https://forum.groupdocs.com/c/watermark/10)
- [Tijdelijke licentie‑acquisitie](https://purchase.groupdocs.com/temporary-license/)