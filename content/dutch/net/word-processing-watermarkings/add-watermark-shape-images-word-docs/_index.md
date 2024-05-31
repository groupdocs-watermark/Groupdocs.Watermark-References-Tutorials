---
title: Voeg een watermerk toe aan vormafbeeldingen in Word-documenten
linktitle: Voeg een watermerk toe aan vormafbeeldingen in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken kunt toevoegen om afbeeldingen in Word-documenten vorm te geven met GroupDocs.Watermark voor .NET. Verbeter de documentbeveiliging met deze zelfstudie.
type: docs
weight: 17
url: /nl/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u een watermerk kunt toevoegen om afbeeldingen in Word-documenten vorm te geven met behulp van GroupDocs.Watermark voor .NET. Watermerken zijn een cruciaal aspect van documentbescherming, vooral als het gaat om gevoelige of vertrouwelijke informatie. Door watermerken toe te voegen aan vormafbeeldingen kunt u de integriteit en veiligheid van uw documenten garanderen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1.  GroupDocs.Watermark voor .NET: Download en installeer de GroupDocs.Watermark-bibliotheek van de[downloadpagina](https://releases.groupdocs.com/Watermark/net/).
2. Document: bereid het Word-document voor waaraan u het watermerk wilt toevoegen.
3. Ontwikkelomgeving: Stel de .NET-ontwikkelomgeving van uw voorkeur in.
## Naamruimten importeren
Zorg ervoor dat u de benodigde naamruimten importeert voordat u de code schrijft:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het document
Definieer eerst het pad naar uw document en geef de naam van het uitvoerbestand op:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Stap 2: Initialiseer watermerker
 Instantieer een`Watermarker` object door het documentpad en optionele laadopties op te geven:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Voeg hier watermerklogica toe
}
```
## Stap 3: Maak een tekstwatermerk
Definieer het tekstwatermerk met de gewenste eigenschappen zoals tekst, lettertype, uitlijning, rotatie, grootte, enz.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Stap 4: Pas watermerk toe op vormafbeeldingen
Blader door de documentsecties en vormen om vormafbeeldingen te identificeren en het watermerk toe te voegen:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Stap 5: Sla het document op
Sla het document met het toegevoegde watermerk op in het opgegeven uitvoerbestand:
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u watermerken kunt toevoegen om afbeeldingen in Word-documenten vorm te geven met behulp van GroupDocs.Watermark voor .NET. Door de stapsgewijze handleiding te volgen en gebruik te maken van de krachtige functies van GroupDocs.Watermark, kunt u de beveiliging en bescherming van uw documenten effectief verbeteren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de watermerktekst aanpassen?
Ja, u kunt verschillende eigenschappen aanpassen, zoals lettertype, grootte, kleur, rotatiehoek en uitlijning, om het watermerk aan uw voorkeuren aan te passen.
### Ondersteunt GroupDocs.Watermark andere documentformaten dan Word?
Ja, GroupDocs.Watermark biedt ondersteuning voor een breed scala aan documentformaten, waaronder PDF, Excel, PowerPoint en meer.
### Is het mogelijk om meerdere watermerken aan één document toe te voegen?
Absoluut, u kunt meerdere watermerken met verschillende inhoud, stijlen en posities binnen hetzelfde document toevoegen.
### Kan ik watermerken uit documenten verwijderen met GroupDocs.Watermark?
Ja, GroupDocs.Watermark biedt functies om watermerken efficiënt uit documenten te detecteren en te verwijderen.
### Biedt GroupDocs.Watermark platformonafhankelijke compatibiliteit?
Ja, GroupDocs.Watermark is compatibel met .NET Framework, .NET Core en .NET Standard, waardoor een naadloze integratie tussen verschillende platforms wordt gegarandeerd.