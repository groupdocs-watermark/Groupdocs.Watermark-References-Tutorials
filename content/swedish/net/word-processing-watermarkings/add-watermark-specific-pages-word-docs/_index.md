---
title: Lägg till vattenstämpel på specifika sidor i Word Docs
linktitle: Lägg till vattenstämpel på specifika sidor i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar på specifika sidor i Word-dokument utan ansträngning med hjälp av Groupdocs för .NET. Förbättra dokumentsäkerhet och varumärke.
weight: 18
url: /sv/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
type: docs
---
# Lägg till vattenstämpel på specifika sidor i Word Docs

## Introduktion
I den här självstudien går vi igenom processen att lägga till vattenstämplar på specifika sidor i Word-dokument med hjälp av Groupdocs.Watermark for .NET. Vattenmärkning är en avgörande aspekt av dokumenthantering, vilket ger säkerhet och varumärke för dina dokument. Med Groupdocs.Watermark för .NET kan du enkelt lägga till text- eller bildvattenstämplar till dina Word-dokument med precision och effektivitet.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1.  Groupdocs.Watermark for .NET: Ladda ner och installera Groupdocs.Watermark for .NET från[här](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Ha Word-dokumentet som du vill vattenstämpla redo.
3. Utvecklingsmiljö: Konfigurera din utvecklingsmiljö med Visual Studio eller något annat .NET-utvecklingsverktyg.

## Importera namnområden
Innan vi dyker in i koden, låt oss importera de nödvändiga namnrymden:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## Steg 1: Ladda dokumentet
Först måste vi ladda Word-dokumentet i vattenmärkeobjektet.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Lägg till vattenmärkningskod kommer hit
}
```
## Steg 2: Lägg till vattenstämpel
Låt oss nu lägga till en textvattenstämpel på specifika sidor i dokumentet.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Ange sidorna för att lägga till vattenstämpeln
};
watermarker.Add(textWatermark);
```
## Steg 3: Spara dokumentet
Spara slutligen det vattenmärkta dokumentet på önskad plats.
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till vattenstämplar på specifika sidor i Word-dokument med hjälp av Groupdocs.Watermark for .NET. Med bara några rader kod kan du förbättra säkerheten och varumärket för dina dokument utan ansträngning.
## FAQ's
### Kan jag lägga till flera vattenstämplar i ett enda dokument?
Ja, du kan lägga till flera vattenstämplar genom att upprepa processen för tillägg av vattenstämpel för varje vattenstämpel.
### Stöder Groupdocs.Watermark andra dokumentformat än Word?
Ja, Groupdocs Watermark stöder ett brett utbud av dokumentformat inklusive PDF, Excel, PowerPoint och mer.
### Finns det en testversion tillgänglig?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Kan jag anpassa utseendet på vattenstämpeln?
Absolut, du kan anpassa olika aspekter av vattenstämpeln som teckensnitt, storlek, färg och opacitet.
### Finns teknisk support tillgänglig?
 Ja, du kan hitta teknisk support och resurser på Groupdocs forum[här](https://forum.groupdocs.com/c/watermark/19).