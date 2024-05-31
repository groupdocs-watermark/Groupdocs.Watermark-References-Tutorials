---
title: Lägg till vattenstämpel med forminställningar i Word Docs
linktitle: Lägg till vattenstämpel med forminställningar i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar med forminställningar i Word-dokument med hjälp av GroupDocs Watermark for .NET. Skydda dina dokument effektivt.
type: docs
weight: 20
url: /sv/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Introduktion
I den här handledningen går vi igenom processen att lägga till en vattenstämpel med forminställningar till Word-dokument med hjälp av GroupDocs.Watermark för .NET.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1.  GroupDocs.Watermark för .NET installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/Watermark/net/).
2. Grundläggande kunskaper i C#-programmering.
3. Förståelse för bearbetning av Word-dokument.

## Importera namnområden
Först måste du importera de nödvändiga namnområdena för att komma åt de obligatoriska klasserna och metoderna.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
Ladda Word-dokumentet där du vill lägga till vattenstämpeln.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tilläggskoden för vattenstämpel går här
}
```
## Steg 2: Lägg till vattenstämpel
 Instantiera en`TextWatermark` objekt och ange texten du vill använda som vattenstämpel.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Steg 3: Anpassa vattenstämpelinställningar
Ställ in olika inställningar för vattenstämpeln, såsom justering, rotationsvinkel, färg och opacitet.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Steg 4: Definiera alternativ för vattenstämpel
Definiera alternativ för vattenstämpelavsnittet, såsom formnamn och alternativ text.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Steg 5: Lägg till vattenstämpel i dokumentet
Lägg till vattenstämpeln i dokumentet med de angivna alternativen.
```csharp
watermarker.Add(watermark, options);
```
## Steg 6: Spara dokumentet
Spara dokumentet med den tillagda vattenstämpeln.
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
Att lägga till vattenstämplar med forminställningar i Word-dokument med hjälp av GroupDocs Watermark för .NET är en enkel process. Genom att följa stegen som beskrivs i denna handledning kan du effektivt skydda dina dokument med anpassade vattenstämplar.
## FAQ's
### Kan jag lägga till flera vattenstämplar i samma dokument?
Ja, du kan lägga till flera vattenstämplar med olika inställningar till samma dokument.
### Stöder GroupDocs.Watermark andra dokumentformat än Word?
Ja, GroupDocs.Watermark stöder olika dokumentformat, inklusive Excel, PowerPoint, PDF och mer.
### Kan jag anpassa utseendet på vattenstämpeln ytterligare?
Absolut, du kan justera olika parametrar som teckenstorlek, stil, färg och position för att passa dina behov.
### Finns det en testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan få en gratis provperiod från[här](https://releases.groupdocs.com/).
### Var kan jag hitta support för GroupDocs.Watermark?
 Du kan hitta support och ställa frågor på GroupDocs forum[här](https://forum.groupdocs.com/c/watermark/19).