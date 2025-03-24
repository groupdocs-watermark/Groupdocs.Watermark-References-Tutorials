---
title: Voeg afbeeldingswatermerk toe vanuit stream
linktitle: Voeg afbeeldingswatermerk toe vanuit stream
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u afbeeldingswatermerken aan documenten kunt toevoegen met GroupDocs.Watermark voor .NET. Volg onze stapsgewijze handleiding voor naadloze watermerkintegratie.
weight: 12
url: /nl/net/image-watermarkings/add-image-watermark-from-stream/
---

# Voeg afbeeldingswatermerk toe vanuit stream

## Invoering
Op het gebied van documentbeheer en beveiliging is het opnemen van watermerken in bestanden van het allergrootste belang. Of het nu gaat om branding, auteursrechtbescherming of het behoud van documentintegriteit, watermerken spelen een cruciale rol. Gelukkig biedt GroupDocs.Watermark voor .NET een robuuste oplossing voor het toevoegen, verwijderen en zoeken van watermerken in verschillende documentformaten.
## Vereisten
Voordat u zich verdiept in de implementatie van watermerken met GroupDocs.Watermark voor .NET, moet u ervoor zorgen dat aan de volgende vereisten is voldaan:
1.  GroupDocs.Watermark voor .NET installeren: Download en installeer de GroupDocs.Watermark voor .NET-bibliotheek vanaf de[download link](https://releases.groupdocs.com/Watermark/net/).
2. Toegang tot document: Krijg toegang tot het document waaraan u watermerken wilt toevoegen of verwijderen.
3. Basiskennis van C#: Bekendheid met de programmeertaal C# is noodzakelijk om de meegeleverde codefragmenten te begrijpen en te implementeren.

## Naamruimten importeren
Voordat u doorgaat met het toevoegen van afbeeldingswatermerken uit een stream, importeert u de benodigde naamruimten:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Stap 1: Definieer het documentpad en de uitvoermap
Definieer eerst het pad van het document waaraan u het watermerk wilt toevoegen en geef de uitvoermap voor het verwerkte document op.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Stap 2: Open Watermark Stream
 Open het watermerkafbeeldingsbestand als een stream met behulp van de`File.OpenRead` methode.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // De logica voor watermerkverwerking komt hier terecht
}
```
## Stap 3: voeg watermerk toe aan document
 Initialiseer een`Watermarker` object met het documentpad en maak vervolgens een`ImageWatermark` object met de watermerkstroom verkregen in stap 2. Voeg het watermerk toe aan het document met behulp van de`Add` werkwijze van de`Watermarker` voorwerp.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Voeg een watermerk toe aan het document
        watermarker.Add(watermark);
        // Bewaar het document met watermerk
        watermarker.Save(outputFileName);
    }
}
```

## Conclusie
GroupDocs.Watermark voor .NET biedt een naadloze oplossing voor het toevoegen van watermerken aan documenten, waardoor merkidentiteit, auteursrechtbescherming en documentintegriteit worden gegarandeerd. Door de beschreven stappen te volgen en de meegeleverde codefragmenten te gebruiken, kunnen gebruikers moeiteloos watermerken in hun documenten opnemen.
## Veelgestelde vragen
### Is GroupDocs.Watermark compatibel met verschillende documentformaten?
Ja, GroupDocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder Word-documenten, Excel-spreadsheets, PowerPoint-presentaties, PDF's en meer.
### Kan ik het uiterlijk en de positie van watermerken aanpassen?
Absoluut, GroupDocs.Watermark biedt uitgebreide opties voor het aanpassen van het uiterlijk, de positie, de transparantie, de rotatie en meer van het watermerk om aan specifieke vereisten te voldoen.
### Biedt GroupDocs.Watermark API's voor het verwijderen van bestaande watermerken?
Ja, met GroupDocs.Watermark kunnen gebruikers niet alleen watermerken toevoegen, maar ook gemakkelijk bestaande watermerken uit documenten verwijderen.
### Is er technische ondersteuning beschikbaar voor GroupDocs.Watermark-gebruikers?
 Ja, gebruikers kunnen gebruik maken van technische ondersteuning en assistentie via het speciale[GroupDocs.Watermark-forum](https://forum.groupdocs.com/c/watermark/19).
### Kan ik GroupDocs.Watermark evalueren voordat ik het aanschaf?
Gebruikers kunnen zeker kiezen voor een gratis proefversie van GroupDocs.Watermark om de kenmerken en functionaliteiten ervan te verkennen voordat ze een aankoopbeslissing nemen.