---
title: PDF-document rasteren
linktitle: PDF-document rasteren
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u PDF-documenten kunt rasteren met GroupDocs.Watermark voor .NET. Verbeter moeiteloos de documentbeveiliging en visuele aantrekkingskracht.
weight: 27
url: /nl/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# PDF-document rasteren

## Invoering
Op het gebied van documentbeheer en -manipulatie staat GroupDocs.Watermark voor .NET hoog als een krachtig hulpmiddel, dat robuuste mogelijkheden biedt voor het toevoegen, verwijderen en doorzoeken van watermerken in verschillende documentformaten. Of het nu gaat om het beveiligen van uw documenten met auteursrechtvermeldingen, het toevoegen van bedrijfslogo's voor branding, of het eenvoudig annoteren van documenten met stempels, GroupDocs.Watermark vereenvoudigt het proces met zijn intuïtieve API en uitgebreide functieset.
## Vereisten
Voordat u in de wereld van watermerken duikt met GroupDocs.Watermark voor .NET, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
### 1. Installeer .NET Framework
Zorg ervoor dat .NET Framework op uw ontwikkelmachine is geïnstalleerd. U kunt het downloaden van de Microsoft-website of de pakketbeheerder van uw voorkeur gebruiken.
#### Stap 1: Download .NET Framework
Bezoek de downloadpagina van Microsoft .NET Framework.
#### Stap 2: Installeer .NET Framework
Volg de installatie-instructies op de downloadpagina om .NET Framework op uw systeem te installeren.
### 2. Verkrijg een GroupDocs.Watermark-licentie
Om de volledige mogelijkheden van GroupDocs.Watermark te kunnen benutten, heeft u een geldige licentie nodig. U kunt een licentie aanschaffen of een tijdelijke licentie verkrijgen voor evaluatiedoeleinden.
#### Stap 1: Verkrijg een licentie
Bezoek de GroupDocs.Watermark-aankooppagina.
#### Stap 2: Koop of verkrijg een tijdelijke licentie
Kies de juiste licentieoptie op basis van uw behoeften: koop een licentie voor voortgezet gebruik of schaf een tijdelijke licentie aan voor evaluatiedoeleinden.

## Naamruimten importeren
Voordat u uw documenten van een watermerk voorziet, moet u ervoor zorgen dat u de benodigde naamruimten importeert om naadloos toegang te krijgen tot de functionaliteit van GroupDocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Nu u alles hebt ingesteld, gaan we dieper in op het rasteren van een PDF-document met GroupDocs.Watermark voor .NET. Rasterisatie converteert elke pagina van het PDF-document naar een rasterafbeeldingsindeling, zoals PNG.
## Stap 1: Initialiseer variabelen
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Zorg ervoor dat u "Uw documentpad" en "Uw documentmap" vervangt door respectievelijk het daadwerkelijke pad naar uw PDF-document en de gewenste uitvoermap.
## Stap 2: Document laden en watermerk toevoegen
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Initialiseer een afbeeldings- of tekstwatermerk
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Voeg eerst een watermerk van elk type toe
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Alle pagina's rasteren
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // De inhoud van alle pagina's wordt vervangen door rasterafbeeldingen
    watermarker.Save(outputFileName);
}
```
In deze stap laden we het PDF-document en initialiseren we een tekstwatermerk met gespecificeerde eigenschappen zoals tekst, lettertype, uitlijning, rotatiehoek, formaattype, schaalfactor en dekking. Vervolgens voegen we het watermerk toe aan het document. Vervolgens halen we de inhoud van het PDF-document op en rasteren we alle pagina's naar PNG-formaat met een resolutie van 100 DPI. Ten slotte slaan we het gewijzigde document op met gerasterde inhoud.

## Conclusie
GroupDocs.Watermark voor .NET biedt een uitgebreide oplossing voor het eenvoudig toevoegen van watermerken aan verschillende documentformaten. Door de stappen in deze zelfstudie te volgen, kunt u PDF-documenten effectief rasteren en de beveiliging en visuele aantrekkingskracht ervan verbeteren.
## Veelgestelde vragen
### Is GroupDocs.Watermark compatibel met andere documentformaten dan PDF?
Ja, GroupDocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder Microsoft Word, Excel, PowerPoint, Visio, Outlook en nog veel meer.
### Kan ik het uiterlijk aanpassen van watermerken die zijn toegevoegd met GroupDocs.Watermark?
Absoluut! GroupDocs.Watermark biedt uitgebreide opties voor het aanpassen van watermerkeigenschappen zoals tekst, lettertype, kleur, grootte, dekking, rotatie en positie.
### Biedt GroupDocs.Watermark ondersteuning voor batchverwerking?
Ja, u kunt eenvoudig meerdere documenten in batchmodus verwerken met GroupDocs, waardoor u tijd en moeite bespaart bij het watermerken van grote sets bestanden.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark?
Ja, u kunt een gratis proefversie van GroupDocs.Watermark downloaden van de website om de functies ervan te evalueren voordat u een aankoop doet.
### Hoe kan ik hulp krijgen als ik problemen ondervind of vragen heb over GroupDocs.Watermark?
U kunt het GroupDocs.Watermark-forum bezoeken om ondersteuning te zoeken bij de community of contact opnemen met het GroupDocs-ondersteuningsteam voor hulp.