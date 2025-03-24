---
title: Lägg till vattenstämpel på en specifik sida i Word Docs
linktitle: Lägg till vattenstämpel på en specifik sida i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar på specifika sidor i Word-dokument med hjälp av GroupDocs Watermark for .NET. Skydda ditt innehåll utan ansträngning.
weight: 14
url: /sv/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---
## Introduktion
Vattenmärkning av dokument är en avgörande aspekt av dokumentsäkerhet och varumärke. I den här självstudien kommer vi att utforska hur man lägger till en vattenstämpel på en specifik sida i Word-dokument med GroupDocs.Watermark for .NET.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
- Grundläggande kunskaper i C#-programmering.
- Installerade Visual Studio IDE.
- GroupDocs.Watermark för .NET installerat i ditt projekt.

## Importera namnområden
Innan du dyker in i koden, se till att du importerar de nödvändiga namnrymden:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din kod kommer hit
}
```
## Steg 2: Lägg till vattenstämpeln
```csharp
// Definiera vattenstämpelns text och stil
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Lägg till vattenstämpel på sista sidan
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Steg 3: Spara dokumentet
```csharp
// Spara dokumentet med vattenstämpeln
watermarker.Save(outputFileName);
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till en vattenstämpel på en specifik sida i Word-dokument med hjälp av GroupDocs.Watermark for .NET. Genom att följa dessa steg kan du effektivt skydda dina dokument och lägga till varumärkeselement efter behov.
## FAQ's
### Kan jag anpassa vattenstämpelns text och stil?
Ja, du kan anpassa text, teckensnitt, storlek, färg och placering av vattenstämpeln enligt dina krav.
### Är GroupDocs.Watermark for .NET kompatibelt med andra dokumentformat?
Ja, GroupDocs.Watermark stöder olika dokumentformat, inklusive Word, Excel, PowerPoint, PDF och mer.
### Kan jag lägga till flera vattenstämplar i ett enda dokument?
Absolut, du kan lägga till flera vattenstämplar med olika innehåll och stilar till samma dokument.
### Finns det en gratis testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan utforska funktionerna i GroupDocs.Watermark med en gratis provperiod. Besök bara den medföljande länken för att komma igång[här](https://releases.groupdocs.com/).
### Var kan jag få teknisk support för GroupDocs.Watermark?
 Du kan hitta användbara resurser och få teknisk support från[här](https://forum.groupdocs.com/c/watermark/19)forumet GroupDocs.Watermark. Besök den medföljande länken för att gå med i gemenskapen.