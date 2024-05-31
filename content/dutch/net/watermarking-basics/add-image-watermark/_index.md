---
title: Voeg afbeeldingswatermerk toe
linktitle: Voeg afbeeldingswatermerk toe
second_title: GroupDocs.Watermark .NET API
description: Voeg moeiteloos afbeeldingswatermerken toe aan uw documenten met GroupDocs.Watermark voor .NET. Bescherm uw intellectuele eigendom met gemak.
type: docs
weight: 10
url: /nl/net/watermarking-basics/add-image-watermark/
---
## Invoering
In deze zelfstudie gaan we dieper in op het proces van het toevoegen van een afbeeldingswatermerk aan uw documenten met behulp van GroupDocs.Watermark voor .NET. Het watermerken van documenten is essentieel voor de bescherming van intellectueel eigendom en branding. Met GroupDocs.Watermark voor .NET kunt u watermerken naadloos integreren in verschillende documentformaten zoals Word, Excel, PowerPoint, PDF en nog veel meer.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Watermark voor .NET Library: Download en installeer de GroupDocs.Watermark voor .NET-bibliotheek van de[website](https://releases.groupdocs.com/Watermark/net/).
2. Document: Houd het document gereed waaraan u het watermerk wilt toevoegen.
3. Afbeelding voor watermerk: bereid het afbeeldingsbestand voor dat u als watermerk wilt gebruiken.

## Naamruimten importeren
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Stap 1: Initialiseer het documentpad en de uitvoermap
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Path"`met het absolute of relatieve pad naar uw document en`"Your Document Directory"` met de map waarin u het document met een watermerk wilt opslaan.
## Stap 2: Open Document Stream en initialiseer Watermarker
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Het watermerkproces komt hier terecht
    }
}
```
 Open de documentstroom met`FileStream` en initialiseer de`Watermarker` voorwerp.
## Stap 3: Voeg een afbeeldingswatermerk toe
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Creëer een`ImageWatermark` object met het pad naar het afbeeldingsbestand dat u als watermerk wilt gebruiken. Stel de horizontale en verticale uitlijning van het watermerk in.
## Stap 4: Bewaar het watermerkdocument
```csharp
watermarker.Save(outputFileName);
```
Sla het document met watermerk op in de opgegeven uitvoermap met de gewenste bestandsnaam.

## Conclusie
Concluderend biedt GroupDocs.Watermark voor .NET een uitgebreide oplossing voor het moeiteloos toevoegen van watermerken aan verschillende documentformaten. Door de stappen in deze zelfstudie te volgen, kunt u op efficiënte wijze afbeeldingswatermerken aan uw documenten toevoegen en uw intellectuele eigendom beschermen.
## Veelgestelde vragen
### Kan ik tekstwatermerken toevoegen met GroupDocs.Watermark voor .NET?
Ja, GroupDocs.Watermark voor .NET ondersteunt het toevoegen van zowel afbeeldings- als tekstwatermerken aan documenten.
### Is GroupDocs.Watermark voor .NET compatibel met verschillende documentformaten?
Absoluut, GroupDocs.Watermark voor .NET ondersteunt een breed scala aan documentformaten, waaronder Word, Excel, PowerPoint, PDF en meer.
### Biedt GroupDocs.Watermark voor .NET aanpassingsopties voor watermerken?
Ja, u kunt verschillende aspecten van het watermerk aanpassen, zoals positie, grootte, dekking en rotatie.
### Kan ik watermerken uit documenten verwijderen met GroupDocs.Watermark voor .NET?
Ja, GroupDocs.Watermark voor .NET biedt functionaliteit om watermerken uit documenten te detecteren en te verwijderen.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark voor .NET?
 Ja, u kunt op de website gebruikmaken van een gratis proefversie om de functies te verkennen voordat u tot aankoop overgaat[hier](https://releases.groupdocs.com/).