---
title: Användning av formtyp i Word Docs
linktitle: Användning av formtyp i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du manipulerar former i Word-dokument med GroupDocs.Watermark for .NET. Denna handledning ger vägledning för effektiv dokumentbehandling.
weight: 37
url: /sv/net/word-processing-watermarkings/shape-type-usage-word-docs/
---

# Användning av formtyp i Word Docs

## Introduktion
I den här handledningen kommer vi att utforska hur man använder formtyper i Word-dokument med GroupDocs.Watermark för .NET. Former i Word-dokument kan variera, och att förstå hur man manipulerar dem kan vara avgörande för olika dokumentbearbetningsuppgifter.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
1.  GroupDocs.Watermark for .NET Library: Ladda ner och installera GroupDocs.Watermark for .NET-biblioteket från[nedladdningslänk](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentsökväg: Ha ett Word-dokument redo för bearbetning.
3. Utvecklingsmiljö: Sätt upp en lämplig utvecklingsmiljö med stöd för .NET framework.

## Importera namnområden
För att komma igång måste du importera de nödvändiga namnrymden till ditt projekt. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att arbeta med Word-dokument.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Steg 1: Ladda dokumentet
Börja med att ladda Word-dokumentet i Watermarker-objektet. Se till att ange dokumentets sökväg och eventuella ytterligare alternativ som krävs under laddningsprocessen.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dokumentbehandlingskoden går här
}
```
## Steg 2: Få åtkomst till dokumentinnehåll
 Få åtkomst till innehållet i det laddade Word-dokumentet med hjälp av`GetContent<WordProcessingContent>()` metod. Detta ger tillgång till avsnitt, stycken och former som finns i dokumentet.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Steg 3: Iterera genom sektioner och former
Iterera genom varje avsnitt och form i dokumentet för att inspektera och manipulera dem efter behov.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Formmanipulationskod går här
    }
}
```
## Steg 4: Kontrollera formtyper
Inom slingan, kontrollera efter specifika formtyper med hjälp av`ShapeType` fast egendom. Det här exemplet visar identifiering och hantering av diagonala hörn rundade former.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Formspecifik manipulationskod går här
}
```
## Steg 5: Manipulera former
Utför åtgärder som att lägga till text, ändra formatering eller tillämpa visuella ändringar på de identifierade formerna.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Steg 6: Spara dokumentet
När alla nödvändiga ändringar har gjorts, spara dokumentet med de tillämpade ändringarna i den angivna utdatafilen.
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
Att manipulera former i Word-dokument kan vara avgörande för olika dokumentbearbetningsuppgifter. Med GroupDocs.Watermark för .NET kan du enkelt identifiera, modifiera och manipulera former för att uppfylla dina krav effektivt.
## FAQ's
### Kan GroupDocs.Watermark för .NET hantera andra dokumentformat än Word?
Ja, GroupDocs.Watermark för .NET stöder ett brett utbud av dokumentformat, inklusive PDF, Excel, PowerPoint och mer.
### Finns det en gratis testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan få tillgång till en gratis testversion från[släpper sida](https://releases.groupdocs.com/).
### Ger GroupDocs.Watermark för .NET teknisk support?
 Ja, du kan söka hjälp och engagera dig i samhället genom[supportforum](https://forum.groupdocs.com/c/watermark/19).
### Kan jag anpassa vattenmärkningsprocessen för specifika dokumentkrav?
Absolut, GroupDocs.Watermark för .NET erbjuder omfattande anpassningsalternativ för att skräddarsy vattenmärkningsprocessen efter dina behov.
### Hur kan jag få en tillfällig licens för GroupDocs.Watermark för .NET?
 Du kan skaffa en tillfällig licens från[Sida för tillfällig licensköp](https://purchase.groupdocs.com/temporary-license/) för test- och utvärderingsändamål.