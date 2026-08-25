---
date: '2026-08-25'
description: Leer hoe u diagrambestanden kunt bewerken en hyperlinks kunt verwijderen
  met GroupDocs.Watermark for Java. Beveilig uw diagrammen snel met stapsgewijze begeleiding.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Leer hoe u diagrambestanden kunt bewerken en hyperlinks kunt verwijderen
  met GroupDocs.Watermark for Java. Volg duidelijke stappen om uw documenten te beschermen.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Hoe diagrammen te bewerken en hyperlinks te verwijderen met Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Hoe diagrammen te bewerken en hyperlinks te verwijderen met Java
type: docs
url: /nl/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Hoe diagram bewerken en hyperlinks verwijderen met Java  

Het beheren van digitale documenten omvat vaak het bewerken van diagrammen, vooral wanneer u **edit diagram** bestanden moet ontdoen van hyperlinks voor beveiliging of visuele duidelijkheid. Deze tutorial laat u precies zien hoe u diagrambestanden kunt bewerken en ongewenste hyperlinks uit diagramvormen kunt verwijderen met behulp van de krachtige **GroupDocs.Watermark** bibliotheek voor Java. Aan het einde van deze gids heeft u een schoon, link‑vrij diagram klaar voor distributie.  

## Snelle antwoorden  
- **Wat is het hoofddoel?** Verwijder alle hyperlinks uit diagramvormen om de beveiliging en presentatie te verbeteren.  
- **Welke bibliotheek is vereist?** GroupDocs.Watermark for Java, versie 24.11 of nieuwer.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een commerciële licentie is vereist voor productie.  
- **Kan ik veel bestanden tegelijk verwerken?** Ja – dezelfde code kan in een lus worden geplaatst om batches te verwerken.  
- **Welke Java‑versie wordt ondersteund?** Java 8 of hoger (Java 11 aanbevolen).  

## Wat is “how to edit diagram”?  
**How to edit diagram** verwijst naar het proces van programmatically een diagrambestand openen, de interne elementen (zoals vormen, tekst of hyperlinks) wijzigen en het resultaat opslaan. Met GroupDocs.Watermark kunt u diagrambestanden bewerken zonder het oorspronkelijke authoring‑tool nodig te hebben.  

## Waarom GroupDocs.Watermark voor Java gebruiken?  
GroupDocs.Watermark ondersteunt **30+ diagram‑ en afbeeldingsformaten** (inclusief VSDX, SVG en WMF) en kan bestanden tot **500 MB** verwerken zonder het volledige document in het geheugen te laden, waardoor een **20 % snellere** verwerkingssnelheid wordt geleverd vergeleken met veel concurrenten.  

## Vereisten  
- **GroupDocs.Watermark** bibliotheek versie 24.11 of later.  
- Maven geïnstalleerd (of de JAR‑bestanden als u handmatige installatie verkiest).  
- Java Development Kit 8 of nieuwer en een IDE zoals IntelliJ IDEA of Eclipse.  

### Vereiste bibliotheken, versies en afhankelijkheden  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (als u de Maven‑aanpak gebruikt)  

### Vereisten voor omgeving configuratie  
Zorg ervoor dat de JDK `bin`‑directory in uw `PATH` staat en dat uw IDE naar de juiste JDK‑versie wijst.  

### Vereiste kennis  
U moet vertrouwd zijn met basis‑Java‑syntaxis, Maven‑afhankelijkheidsbeheer en bestands‑I/O‑bewerkingen.  

## Hoe GroupDocs.Watermark voor Java instellen?  
De `Watermarker`‑klasse biedt het API‑ingangspunt voor het laden en wijzigen van documenten.  
Om GroupDocs.Watermark te gebruiken, voegt u de Maven‑coördinaten toe aan het `pom.xml`‑bestand van uw project. Dit haalt de bibliotheek en de afhankelijkheden op, zodat u de Watermarker‑klasse kunt instantiëren en direct vanuit Java‑code met diagrambestanden kunt werken. Vervolgens kunt u licenties configureren en uitvoeropties instellen voordat u een document verwerkt.  

Voeg de GroupDocs.Watermark‑afhankelijkheid toe aan uw `pom.xml`.  

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

Als u liever geen Maven gebruikt, download dan de nieuwste JAR van de officiële releases‑pagina.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Stappen voor licentie‑acquisitie  
- Begin met een gratis proefversie om de API te evalueren.  
- Voor productie verkrijgt u een tijdelijke of permanente licentie via het leveranciersportaal.  

#### Basisinitialisatie en configuratie  

De `Watermarker`‑klasse is het ingangspunt voor alle document‑verwerkingsbewerkingen.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Hoe diagram bewerken en hyperlinks verwijderen met GroupDocs.Watermark?  
De `Watermarker`‑klasse biedt het API‑ingangspunt voor het laden en wijzigen van documenten.  
Laad eerst het diagrambestand in een Watermarker‑instantie. Haal vervolgens de collectie vormen op, identificeer die met hyperlink‑objecten, en doorloop ze in omgekeerde volgorde om elke link veilig te verwijderen zonder de indexering van de collectie te beïnvloeden. Dit zorgt ervoor dat alle ingesloten URL's worden verwijderd terwijl de visuele integriteit van het diagram behouden blijft.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Waarom deze stap belangrijk is**: Laden van het bestand geeft u programmatische toegang tot elke vorm en de bijbehorende eigenschappen.  

## Hoe toegang krijgen tot vorminhoud in een diagram?  
Het `DiagramShape`‑object vertegenwoordigt een individuele vorm binnen een diagram en geeft zijn eigenschappen en bijbehorende metadata weer.  
Na het laden van het diagram, roept u `getShapes()` aan op de Watermarker om een lijst van `DiagramShape`‑objecten te verkrijgen. Elke vorm kan worden geïnspecteerd op hyperlink‑collecties, waardoor precieze targeting van links voor verwijdering of wijziging mogelijk is. U kunt ook de vormtekst, kleuren en geometrie lezen indien verdere aanpassingen nodig zijn.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Waarom deze stap belangrijk is**: Het richten op de exacte vorm zorgt ervoor dat u alleen ongewenste links verwijdert zonder andere visuele elementen te beïnvloeden.  

## Hoe hyperlinks veilig itereren en verwijderen?  
De `removeHyperlink(int index)`‑methode verwijdert een hyperlink op de opgegeven positie binnen de hyperlink‑collectie van een vorm.  
Itereer over de hyperlink‑lijst vanaf de laatste index naar nul. Deze omgekeerde lus voorkomt indexverschuiving die optreedt wanneer items worden verwijderd, waardoor elke hyperlink wordt verwerkt zonder overgeslagen te worden. Na verwijdering kunt u de staat van de vorm vernieuwen of doorgaan naar de volgende vorm in het diagram.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Waarom deze stap belangrijk is**: Een omgekeerde lus garandeert dat alle hyperlinks worden verwijderd zonder enige invoer over te slaan.  

## Hoe het bewerkte diagram opslaan en bronnen vrijgeven?  
De `save(String path)`‑methode schrijft het gewijzigde document naar de opgegeven bestandslocatie en voltooit alle wijzigingen.  
Zodra alle hyperlinks zijn verwijderd, roept u de `save`‑methode aan op de Watermarker‑instantie, met een nieuwe bestandsnaam om overschrijven van het origineel te voorkomen. Roep vervolgens `close()` aan om bestands‑handles vrij te geven en geheugen vrij te maken, wat essentieel is voor langdurige batchprocessen. Dit zorgt ervoor dat het bestand correct wordt gesloten en klaar is voor verder gebruik.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Waarom deze stap belangrijk is**: Het correct sluiten van bronnen voorkomt geheugenlekken en bestandsvergrendelingsproblemen op de server.  

## Praktische toepassingen  

Het verwijderen van hyperlinks uit diagramvormen kan nuttig zijn in verschillende real‑world scenario's:  

1. **Security** – Voorkom externe links die kunnen leiden naar kwaadaardige sites.  
2. **Compliance** – Voldoen aan bedrijfsbeleid dat ingebedde URL's in gedeelde assets verbiedt.  
3. **Clarity** – Produceer schonere presentaties waarbij links afleiden.  

U kunt deze logica in grotere automatiserings‑pipelines integreren, zoals nachtelijke batch‑taken die alle diagrammen sanitizen voordat ze op een intranet worden gepubliceerd.  

## Prestatieoverwegingen  

### Prestaties optimaliseren  
- Gebruik één `Watermarker`‑instantie per bestand om overhead te verminderen.  
- Geef de voorkeur aan omgekeerde iteratie (zoals getoond) om dure lijst‑herindexering te vermijden.  

### Richtlijnen voor resourcegebruik  
- Voor diagrammen groter dan 200 MB, monitor het heap‑gebruik en overweeg het verhogen van de JVM‑`-Xmx`‑vlag.  
- Profileringstools zoals VisualVM kunnen helpen knelpunten te identificeren in grootschalige batch‑runs.  

### Best practices voor Java‑geheugenbeheer  
- Declareer objecten binnen de kleinste mogelijke scope.  
- Gebruik try‑with‑resources bij het werken met streams om automatische sluiting te garanderen.  

## Veelgestelde vragen  

**Q: Hoe ga ik om met diagrammen die duizenden vormen bevatten?**  
A: Verwerk het diagram pagina‑voor‑pagina en geef de resources van elke pagina vrij voordat u naar de volgende gaat om het geheugenverbruik laag te houden.  

**Q: Kan ik het verwijderen van hyperlinks beperken tot specifieke pagina's?**  
A: Ja – haal de gewenste pagina‑index op en pas de verwijderingslus alleen toe op vormen op die pagina.  

**Q: Is een commerciële licentie verplicht voor batch‑verwerking?**  
A: Een geldige licentie is vereist voor elke productie‑niveau implementatie; de gratis proefversie is beperkt tot 30 dagen en 5 documenten.  

**Q: Ondersteunt GroupDocs.Watermark SVG‑diagrammen?**  
A: Absoluut – SVG behoort tot de 30+ ondersteunde formaten, en hyperlinks kunnen worden verwijderd met dezelfde API‑aanroepen.  

**Q: Wat als een vorm meerdere hyperlinks heeft?**  
A: De omgekeerde iteratielus verwijdert elke hyperlink‑vermelding afzonderlijk, waardoor alle links worden gewist.  

## Bronnen  

- [Documentatie](https://docs.groupdocs.com/watermark/java/)  
- [API‑referentie](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub‑repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Gratis ondersteuningsforum](https://forum.groupdocs.com/c/watermark/10)  
- [Tijdelijke licentie‑acquisitie](https://purchase.groupdocs.com/temporary-license/)  

---  

**Laatst bijgewerkt:** 2026-08-25  
**Getest met:** GroupDocs.Watermark 24.11 for Java  
**Auteur:** GroupDocs  

## Gerelateerde tutorials

- [Diagram Watermarking‑tutorials voor GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Diagramkop- en voetteksten bewerken in Java met GroupDocs.Watermark: Een uitgebreide gids](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Efficiënt vormen uit diagrammen verwijderen met GroupDocs.Watermark voor Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)