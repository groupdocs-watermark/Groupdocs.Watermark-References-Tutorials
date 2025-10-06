---
title: Voeg een betegeld afbeeldingswatermerk toe
linktitle: Voeg een betegeld afbeeldingswatermerk toe
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u naast elkaar geplaatste afbeeldingswatermerken aan uw documenten kunt toevoegen met GroupDocs.Watermark voor .NET. Eenvoudig, efficiënt en aanpasbaar.
weight: 10
url: /nl/net/image-watermarkings/add-tiled-image-watermark/
type: docs
---
# Voeg een betegeld afbeeldingswatermerk toe

## Invoering
GroupDocs.Watermark voor .NET is een krachtige API waarmee ontwikkelaars programmatisch watermerken in verschillende documentformaten kunnen toevoegen, verwijderen en zoeken. In deze zelfstudie begeleiden we u bij het toevoegen van een betegeld afbeeldingswatermerk aan uw documenten met behulp van GroupDocs.Watermark voor .NET.
## Vereisten
Zorg ervoor dat u over het volgende beschikt voordat u begint:
- Basiskennis van de programmeertaal C#.
- Visual Studio is op uw systeem geïnstalleerd.
- GroupDocs.Watermark voor .NET-bibliotheek toegevoegd aan uw project. Je kunt het downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).

## Naamruimten importeren
Zorg ervoor dat u de benodigde naamruimten importeert aan het begin van uw C#-bestand:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Stap 1: Stel het documentpad en de uitvoermap in
Definieer het pad van uw invoerdocument en de map waarin u het uitvoerdocument wilt opslaan:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Path"` met het absolute of relatieve pad naar uw invoerdocument.
## Stap 2: Initialiseer het watermerkobject
Maak een Watermarker-object met behulp van het invoerdocumentpad:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Voeg hier een watermerk toe
}
```
## Stap 3: Voeg een betegeld afbeeldingswatermerk toe
Instantieer een ImageWatermark-object met het pad naar het afbeeldingsbestand dat u als watermerk wilt gebruiken:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Configureer tegelopties
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Voeg een watermerk toe aan het document
    watermarker.Add(watermark);
    // Sla het gewijzigde document op
    watermarker.Save(outputFileName);
}
```
 Vervangen`"Path to Your Image"` met het daadwerkelijke pad naar uw watermerkafbeeldingsbestand.

## Conclusie
Door deze stappen te volgen, kunt u eenvoudig een betegeld afbeeldingswatermerk aan uw documenten toevoegen met GroupDocs.Watermark voor .NET. Experimenteer met verschillende opties en configuraties om het gewenste resultaat te bereiken.
## Veelgestelde vragen
### Kan ik meerdere watermerken aan één document toevoegen?
Ja, u kunt meerdere watermerken van verschillende typen aan een document toevoegen met GroupDocs.Watermark voor .NET.
### Ondersteunt GroupDocs.Watermark alle documentformaten?
GroupDocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder PDF, Word, Excel, PowerPoint en nog veel meer.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Kan ik het uiterlijk van het watermerk aanpassen?
Ja, u kunt verschillende aspecten van het watermerk aanpassen, zoals positie, grootte, rotatie, transparantie, enz.
### Biedt GroupDocs.Watermark technische ondersteuning?
 Ja, u kunt technische ondersteuning krijgen via het GroupDocs.Watermark-forum[hier](https://forum.groupdocs.com/c/watermark/19).