---
title: Ersätt formtext med formaterad text i Word Docs
linktitle: Ersätt formtext med formaterad text i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du ersätter formtext med formaterad text i Word-dokument med hjälp av GroupDocs.Watermark för .NET. Dina dokumentredigeringsmöjligheter utan ansträngning.
weight: 34
url: /sv/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
type: docs
---
# Ersätt formtext med formaterad text i Word Docs

## Introduktion
den här självstudien guidar vi dig genom processen att ersätta formtext med formaterad text i Word-dokument med hjälp av GroupDocs.Watermark för .NET. Det här biblioteket ger kraftfulla funktioner för att arbeta med vattenstämplar, inklusive att ersätta text i former.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1.  GroupDocs.Watermark for .NET: Se till att du har installerat och konfigurerat GroupDocs.Watermark för .NET. Du kan ladda ner den från[här](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentsökväg: Du bör ha sökvägen till Word-dokumentet där du vill ersätta texten.

## Importera namnområden
Innan du skriver koden, importera de nödvändiga namnrymden:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
 Ladda Word-dokumentet med hjälp av`Watermarker` klass:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din kod fortsätter här...
}
```
## Steg 2: Hämta innehåll och ersätt text
När dokumentet har laddats hämtar du innehållet och ersätter texten i former:
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
## Steg 3: Spara dokumentet
När du har ersatt texten, spara det ändrade dokumentet:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Slutsats
Att ersätta formtext med formaterad text i Word-dokument görs enkelt med GroupDocs Watermark för .NET. Genom att följa stegen som beskrivs i denna handledning kan du effektivt hantera och manipulera text i dina dokument.

## FAQ's
### Kan jag ersätta text i andra typer av dokument med GroupDocs.Watermark för .NET?
Ja, GroupDocs Watermark stöder olika dokumentformat som PDF, Excel, PowerPoint och mer.
### Är GroupDocs.Watermark kompatibel med .NET Core?
Ja, GroupDocs.Watermark stöder både .NET Framework och .NET Core.
### Ger GroupDocs.Watermark stöd för att lägga till bilder som vattenstämplar?
Absolut, GroupDocs.Watermark låter dig lägga till både text- och bildvattenstämplar till dina dokument.
### Kan jag anpassa utseendet på de vattenstämplar som lagts till med GroupDocs.Watermark?
Ja, du har full kontroll över vattenstämplarnas utseende, position och andra egenskaper.
### Finns det en testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).