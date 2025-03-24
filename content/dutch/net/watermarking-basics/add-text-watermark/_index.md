---
title: Tekstwatermerk toevoegen
linktitle: Tekstwatermerk toevoegen
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u tekstwatermerken aan uw documenten kunt toevoegen met Groupdocs Watermark voor .NET met deze stapsgewijze handleiding.
weight: 11
url: /nl/net/watermarking-basics/add-text-watermark/
---
## Invoering
GroupDocs.Watermark voor .NET is een krachtige bibliotheek waarmee ontwikkelaars watermerken kunnen toevoegen, zoeken en verwijderen uit verschillende documentformaten in .NET-toepassingen. In deze zelfstudie concentreren we ons op het toevoegen van een tekstwatermerk aan een document met GroupDocs.Watermark.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1. Basiskennis van de programmeertaal C#.
2. Visual Studio is op uw systeem geïnstalleerd.
3.  GroupDocs.Watermark voor .NET-bibliotheek geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Stap 1: Definieer het documentpad en de uitvoermap
Definieer het pad naar uw invoerdocument en de uitvoermap waar het document met een watermerk zal worden opgeslagen.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Path"` met het absolute of relatieve pad naar uw invoerdocument, bijvoorbeeld:`@"C:\Docs\document.pdf"`. Geef ook de map op waarin u het document met een watermerk wilt opslaan.
## Stap 2: tekstwatermerk toevoegen
 Instantieer de`Watermarker` klasse met het invoerdocumentpad. Maak vervolgens een`TextWatermark` object met de gewenste tekst- en lettertype-instellingen.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u een tekstwatermerk aan een document kunt toevoegen met GroupDocs.Watermark voor .NET. Met de intuïtieve API kunnen ontwikkelaars eenvoudig watermerken in verschillende documentformaten manipuleren.
## Veelgestelde vragen
### Is GroupDocs.Watermark voor .NET compatibel met alle documentformaten?
GroupDocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder PDF, Microsoft Word, Excel, PowerPoint en nog veel meer.
### Kan ik het uiterlijk van het tekstwatermerk aanpassen?
Ja, u kunt verschillende eigenschappen aanpassen, zoals lettertype, kleur, uitlijning en dekking van het tekstwatermerk.
### Biedt GroupDocs.Watermark ondersteuning voor het verwijderen van watermerken uit documenten?
Ja, GroupDocs.Watermark biedt functionaliteit om watermerken uit documenten te zoeken en te verwijderen.
### Kan ik GroupDocs.Watermark voor .NET uitproberen voordat ik het aanschaf?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Watermark?
 U kunt technische ondersteuning krijgen door naar de[GroupDocs.Watermark-forum](https://forum.groupdocs.com/c/watermark/19).