---
title: Vervang vormtekst door opgemaakte tekst in Word-documenten
linktitle: Vervang vormtekst door opgemaakte tekst in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u vormtekst vervangt door opgemaakte tekst in Word-documenten met GroupDocs.Watermark voor .NET. Uw documentbewerkingsmogelijkheden moeiteloos.
weight: 34
url: /nl/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---

# Vervang vormtekst door opgemaakte tekst in Word-documenten

## Invoering
In deze zelfstudie begeleiden we u bij het vervangen van vormtekst door opgemaakte tekst in Word-documenten met behulp van GroupDocs.Watermark voor .NET. Deze bibliotheek biedt krachtige functies voor het werken met watermerken, inclusief het vervangen van tekst in vormen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Watermark voor .NET: Zorg ervoor dat u GroupDocs.Watermark voor .NET hebt geïnstalleerd en ingesteld. Je kunt het downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Documentpad: U zou het pad moeten hebben naar het Word-document waar u de tekst wilt vervangen.

## Naamruimten importeren
Importeer de benodigde naamruimten voordat u de code schrijft:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het document
 Laad het Word-document met behulp van de`Watermarker` klas:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Uw code gaat hier verder...
}
```
## Stap 2: inhoud ophalen en tekst vervangen
Zodra het document is geladen, haalt u de inhoud op en vervangt u de tekst in vormen:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Stap 3: Sla het document op
Nadat u de tekst hebt vervangen, slaat u het gewijzigde document op:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusie
Het vervangen van vormtekst door opgemaakte tekst in Word-documenten is eenvoudig gemaakt met GroupDocs voor .NET. Door de stappen in deze zelfstudie te volgen, kunt u tekst in uw documenten efficiënt beheren en manipuleren.

## Veelgestelde vragen
### Kan ik tekst in andere typen documenten vervangen met GroupDocs.Watermark voor .NET?
Ja, GroupDocs Watermark ondersteunt verschillende documentformaten zoals PDF, Excel, PowerPoint en meer.
### Is GroupDocs.Watermark compatibel met .NET Core?
Ja, GroupDocs.Watermark ondersteunt zowel .NET Framework als .NET Core.
### Biedt GroupDocs.Watermark ondersteuning voor het toevoegen van afbeeldingen als watermerken?
Absoluut, met GroupDocs.Watermark kunt u zowel tekst- als afbeeldingswatermerken aan uw documenten toevoegen.
### Kan ik het uiterlijk van de watermerken die worden toegevoegd met GroupDocs.Watermark aanpassen?
Ja, u heeft volledige controle over het uiterlijk, de positie en andere eigenschappen van de watermerken.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark voor .NET?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).