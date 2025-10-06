---
title: Voeg een watermerk toe met vorminstellingen in Word-documenten
linktitle: Voeg een watermerk toe met vorminstellingen in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken met vorminstellingen aan Word-documenten kunt toevoegen met GroupDocs voor .NET. Bescherm uw documenten effectief.
weight: 20
url: /nl/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
type: docs
---
# Voeg een watermerk toe met vorminstellingen in Word-documenten

## Invoering
In deze zelfstudie doorlopen we het proces van het toevoegen van een watermerk met vorminstellingen aan Word-documenten met behulp van GroupDocs.Watermark voor .NET.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1.  GroupDocs.Watermark voor .NET geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Basiskennis van programmeren in C#.
3. Een goed begrip van de verwerking van Word-documenten.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten importeren om toegang te krijgen tot de vereiste klassen en methoden.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het document
Laad het Word-document waar u het watermerk wilt toevoegen.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // De code voor het toevoegen van een watermerk komt hier terecht
}
```
## Stap 2: voeg een watermerk toe
 Instantieer een`TextWatermark` object en geef de tekst op die u als watermerk wilt gebruiken.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Stap 3: Pas de watermerkinstellingen aan
Stel verschillende instellingen in voor het watermerk, zoals uitlijning, rotatiehoek, kleur en dekking.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Stap 4: Definieer de opties voor de watermerksectie
Definieer opties voor de watermerksectie, zoals de vormnaam en alternatieve tekst.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Stap 5: voeg watermerk toe aan document
Voeg het watermerk toe aan het document met de opgegeven opties.
```csharp
watermarker.Add(watermark, options);
```
## Stap 6: Bewaar het document
Sla het document op met het toegevoegde watermerk.
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
Het toevoegen van watermerken met vorminstellingen aan Word-documenten met behulp van GroupDocs voor .NET is een eenvoudig proces. Door de stappen in deze zelfstudie te volgen, kunt u uw documenten effectief beschermen met aangepaste watermerken.
## Veelgestelde vragen
### Kan ik meerdere watermerken aan hetzelfde document toevoegen?
Ja, u kunt meerdere watermerken met verschillende instellingen aan hetzelfde document toevoegen.
### Ondersteunt GroupDocs.Watermark andere documentformaten dan Word?
Ja, GroupDocs.Watermark ondersteunt verschillende documentformaten, waaronder Excel, PowerPoint, PDF en meer.
### Kan ik het uiterlijk van het watermerk verder aanpassen?
Absoluut, u kunt verschillende parameters, zoals lettergrootte, stijl, kleur en positie, aanpassen aan uw behoeften.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark voor .NET?
 Ja, u kunt een gratis proefperiode krijgen van[hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning vinden voor GroupDocs.Watermark?
 U kunt ondersteuning vinden en vragen stellen op het GroupDocs-forum[hier](https://forum.groupdocs.com/c/watermark/19).