---
title: Voeg een watermerk toe aan specifieke pagina's in Word-documenten
linktitle: Voeg een watermerk toe aan specifieke pagina's in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u moeiteloos watermerken kunt toevoegen aan specifieke pagina's in Word-documenten met behulp van Groupdocs voor .NET. Verbeter de documentbeveiliging en branding.
weight: 18
url: /nl/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---

# Voeg een watermerk toe aan specifieke pagina's in Word-documenten

## Invoering
In deze zelfstudie doorlopen we het proces van het toevoegen van watermerken aan specifieke pagina's in Word-documenten met behulp van Groupdocs.Watermark voor .NET. Watermerken zijn een cruciaal aspect van documentbeheer en zorgen voor beveiliging en branding van uw documenten. Met Groupdocs.Watermark voor .NET kunt u eenvoudig en nauwkeurig en efficiënt tekst- of afbeeldingswatermerken aan uw Word-documenten toevoegen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  Groupdocs.Watermark voor .NET: Download en installeer Groupdocs.Watermark voor .NET van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Document: Zorg ervoor dat u het Word-document dat u van een watermerk wilt voorzien, gereed hebt.
3. Ontwikkelomgeving: Stel uw ontwikkelomgeving in met Visual Studio of een andere .NET-ontwikkeltool.

## Naamruimten importeren
Laten we, voordat we in de code duiken, de benodigde naamruimten importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## Stap 1: Laad het document
Eerst moeten we het Word-document in het watermerkobject laden.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Voeg de watermerkcode toe. Hier komt u terecht
}
```
## Stap 2: voeg een watermerk toe
Laten we nu een tekstwatermerk toevoegen aan specifieke pagina's van het document.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Geef de pagina's op waaraan u het watermerk wilt toevoegen
};
watermarker.Add(textWatermark);
```
## Stap 3: Sla het document op
Sla ten slotte het document met een watermerk op de gewenste locatie op.
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u watermerken kunt toevoegen aan specifieke pagina's in Word-documenten met behulp van Groupdocs.Watermark voor .NET. Met slechts een paar regels code kunt u de beveiliging en branding van uw documenten moeiteloos verbeteren.
## Veelgestelde vragen
### Kan ik meerdere watermerken aan één document toevoegen?
Ja, u kunt meerdere watermerken toevoegen door het proces voor het toevoegen van watermerken voor elk watermerk te herhalen.
### Ondersteunt Groupdocs.Watermark andere documentformaten dan Word?
Ja, Groupdocs ondersteunt een breed scala aan documentformaten, waaronder PDF, Excel, PowerPoint en meer.
### Is er een proefversie beschikbaar?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Kan ik het uiterlijk van het watermerk aanpassen?
Absoluut, u kunt verschillende aspecten van het watermerk aanpassen, zoals lettertype, grootte, kleur en dekking.
### Is er technische ondersteuning beschikbaar?
 Ja, je kunt technische ondersteuning en bronnen vinden op het Groupdocs-forum[hier](https://forum.groupdocs.com/c/watermark/19).