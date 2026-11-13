---
date: 2026-11-13
description: Leer hoe u metadata kunt extraheren, ondersteunde formaten kunt weergeven
  en documentinformatie kunt ophalen met GroupDocs.Watermark voor Java.
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: Hoe metadata te extraheren met GroupDocs.Watermark voor Java. Leer
  hoe u ondersteunde formaten kunt weergeven, documentinformatie kunt ophalen en dia-achtergronden
  in enkele minuten kunt extraheren.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: Hoe metadata te extraheren met GroupDocs.Watermark voor Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: Hoe metadata te extraheren met GroupDocs.Watermark voor Java
type: docs
url: /nl/java/document-information/
weight: 14
---

# Hoe metadata extraheren met GroupDocs.Watermark voor Java

In deze gids ontdek je **hoe je metadata kunt extraheren** uit een breed scala aan documenttypen met GroupDocs.Watermark voor Java. Of je nu het bestandstype, het aantal pagina's, auteursgegevens of aangepaste eigenschappen wilt lezen, de bibliotheek biedt programmeerbare toegang tot deze informatie zodat je intelligente beslissingen kunt nemen over watermerkplaatsing, documentroutering of nalevingscontroles. De tutorial laat ook zien hoe je ondersteunde formaten kunt opsommen, slide‑achtergrondgegevens kunt ophalen en andere nuttige documentkenmerken kunt ophalen.

## Snelle antwoorden
- **Kan ik metadata extraheren uit PDF- en Word‑bestanden?** Ja, de API leest metadata uit meer dan 70 gangbare formaten.  
- **Heb ik een licentie nodig voor ontwikkeling?** Een gratis tijdelijke licentie werkt voor testen; een volledige licentie is vereist voor productie.  
- **Welke Java‑versie is vereist?** Java 8 of hoger wordt ondersteund.  
- **Is de bibliotheek thread‑safe?** Kern‑extractieklassen zijn ontworpen voor gelijktijdig gebruik.  
- **Hoeveel formaten worden herkend?** Meer dan 70 invoer‑ en uitvoerformaten worden direct herkend.

## Wat is metadata‑extractie?
Metadata‑extractie is het proces van het lezen van ingebedde informatie—zoals auteur, aanmaakdatum, paginacount en aangepaste eigenschappen—uit een documentbestand zonder de inhoud te wijzigen. Het maakt geautomatiseerde workflows mogelijk die afhankelijk zijn van documentattributen. Het omvat doorgaans eigenschappen zoals titel, trefwoorden en wijzigings‑tijdstempels, die kunnen worden benut voor indexering en nalevingsrapportage.

## Waarom GroupDocs.Watermark voor Java gebruiken?
GroupDocs.Watermark voor Java ondersteunt **meer dan 70 bestandsformaten**, waaronder PDF, DOCX, PPTX, XLSX en afbeeldingsformaten, en kan documenten tot 500 MB verwerken zonder het volledige bestand in het geheugen te laden. De API retourneert metadata in één consistent object, waardoor de noodzaak voor formaat‑specifieke parsers afneemt en de ontwikkelingstijd met tot wel 40 % wordt verkort.

## Vereisten
- Java 8 of nieuwer geïnstalleerd op je ontwikkelmachine.  
- Maven of Gradle om de `groupdocs-watermark`‑dependency te beheren.  
- Een tijdelijk of volledig GroupDocs.Watermark‑licentiebestand.

## Hoe metadata stap voor stap extraheren

### Hoe haal ik basisdocumentinformatie op?
De `Watermark`‑klasse vertegenwoordigt een document en biedt toegang tot de metadata. De `getDocumentInfo()`‑methode haalt het metadata‑object op uit het geladen document. Laad het document met de `Watermark`‑klasse en roep vervolgens `getDocumentInfo()` aan om een object te verkrijgen dat het bestandstype, de grootte, het paginacount en de aanmaakdatum bevat. Deze enkele oproep retourneert alle kern‑metadata in minder dan een seconde voor typische bestanden onder 100 MB. Het geretourneerde `DocumentInfo`‑object bevat ook de auteur van het document, de datum van laatste wijziging en eventuele ingebedde aangepaste eigenschappen, wat een uitgebreid overzicht geeft.

### Hoe kan ik alle ondersteunde bestandsformaten opsommen?
Het `SupportedFormats`‑hulpmiddel biedt een catalogus van alle bestandstypen die de SDK kan verwerken. Gebruik het `SupportedFormats`‑hulpmiddel dat door de SDK wordt geleverd. Het retourneert een collectie van formaat‑identifiers die je kunt weergeven of valideren voordat je bestanden uploadt, waardoor compatibiliteit wordt gegarandeerd en runtime‑fouten worden voorkomen. Elke vermelding bevat de naam van het formaat, de typische bestandsextensie en een korte beschrijving van de mogelijkheden, waardoor ontwikkelaars invoer kunnen valideren vóór verwerking.

### Hoe haal ik slide‑achtergronddetails uit een PowerPoint‑bestand op?
`SlideInfo` is een object dat de visuele eigenschappen van een slide beschrijft, zoals achtergrondafbeelding en afmetingen. `getSlides()` retourneert een collectie van `SlideInfo`‑objecten voor elke slide in de presentatie. Het `SlideInfo`‑object geeft de afmetingen van de achtergrondafbeelding, de bestandsgrootte en de kleurdiepte weer. Toegang krijg je via de `getSlides()`‑collectie, waarna je over elke slide itereren om de achtergrond‑eigenschappen uit te lezen—handig voor dynamische styling of het genereren van thumbnails. Deze details kunnen worden gebruikt om thumbnails te genereren, consistente styling toe te passen of achtergronden programmatisch te vervangen in meerdere presentaties.

## Veelvoorkomende problemen en oplossingen
- **Ontbrekende metadata:** Sommige oudere bestanden bevatten mogelijk geen standaardeigenschappen. Schakel in dat geval de `extractCustomProperties`‑vlag in om alle door de gebruiker gedefinieerde velden op te halen.  
- **Grote bestanden veroorzaken time‑outs:** Verhoog de `maxMemory`‑instelling van de SDK of verwerk het document in streaming‑modus om te voorkomen dat het hele bestand in RAM wordt geladen.  
- **Fout: niet‑ondersteund formaat:** Controleer het formaat tegen de lijst die door `SupportedFormats` wordt geretourneerd voordat je probeert te extraheren.

## Veelgestelde vragen

**V: Kan ik metadata extraheren uit met een wachtwoord beveiligde documenten?**  
A: Ja, geef het wachtwoord op bij het openen van het document; de API zal het in het geheugen ontsleutelen en vervolgens de metadata lezen.

**V: Werkt de bibliotheek op Android?**  
A: De kern‑extractiefuncties zijn compatibel met Android API 21+ wanneer ze worden gebundeld als een standaard JAR.

**V: Hoe ga ik om met aangepaste metadata‑velden?**  
A: Gebruik de `getCustomProperties()`‑methode op het `DocumentInfo`‑object; deze retourneert een map van sleutel‑waardeparen die je kunt itereren.

**V: Is er een manier om veel bestanden in batch te verwerken?**  
A: Plaats de extractielogica in een lus en hergebruik één `Watermark`‑instantie; de SDK is ontworpen voor scenario's met hoge doorvoer.

**V: Welke licentie‑opties zijn beschikbaar?**  
A: GroupDocs.Watermark biedt eeuwigdurende, abonnement‑ en tijdelijke licenties; de tijdelijke licentie is ideaal voor evaluatie en CI‑pipelines.

## Beschikbare tutorials

### [Documentinformatie extraheren met GroupDocs.Watermark voor Java&#58; Een volledige gids](./extract-document-info-groupdocs-watermark-java/)
Learn how to efficiently extract document metadata like file type, page count, and size using GroupDocs.Watermark for Java. This guide covers setup, implementation, and practical applications.

### [PDF-paginadimensies extraheren in Java met GroupDocs.Watermark&#58; Een volledige gids](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Learn how to extract PDF page dimensions with GroupDocs.Watermark for Java. This guide covers setup, code examples, and practical applications.

### [Vormen extraheren uit Word‑documenten met GroupDocs.Watermark in Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Learn how to extract and analyze shapes from Word documents using GroupDocs.Watermark for Java, enhancing document automation and manipulation.

### [Hoe slide‑achtergrondinformatie extraheren met GroupDocs.Watermark voor Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Learn how to extract slide background details such as image dimensions and file size using GroupDocs.Watermark for Java. Perfect for customization, analysis, or documentation.

### [Hoe ondersteunde bestandsformaten opsommen met GroupDocs.Watermark voor Java&#58; Een volledige gids](./groupdocs-watermark-java-list-supported-formats/)
Learn how to efficiently list supported file formats with GroupDocs.Watermark in Java, ensuring compatibility across various document types.

### [Hoe documentinformatie ophalen met GroupDocs.Watermark voor Java&#58; Een stap‑voor‑stap gids](./retrieve-document-info-groupdocs-watermark-java/)
Learn how to efficiently retrieve document information such as file type, page count, and size using GroupDocs.Watermark for Java. Follow our detailed guide with code examples.

### [Hoe sectie‑eigenschappen ophalen in Word‑documenten met GroupDocs.Watermark voor Java](./groupdocs-java-word-section-properties-retrieval/)
Learn how to efficiently retrieve and manipulate section properties in Word documents using GroupDocs.Watermark for Java. Perfect for developers looking to enhance document handling.

## Aanvullende bronnen

- [GroupDocs.Watermark voor Java Documentatie](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark voor Java API‑referentie](https://reference.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark voor Java downloaden](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark‑forum](https://forum.groupdocs.com/c/watermark)
- [Gratis ondersteuning](https://forum.groupdocs.com/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-11-13  
**Tested with:** GroupDocs.Watermark 23.12 for Java  
**Author:** GroupDocs

## Gerelateerde tutorials

- [Hoe ondersteunde bestandsformaten opsommen met GroupDocs.Watermark voor Java: Een volledige gids](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [Hoe documentinformatie ophalen met GroupDocs.Watermark voor Java: Een stap‑voor‑stap gids](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Documentinformatie extraheren met GroupDocs.Watermark voor Java: Een volledige gids](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)