---
title: Lägg till Skriv ut endast anteckningsvattenstämpel till PDF
linktitle: Lägg till Skriv ut endast anteckningsvattenstämpel till PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar med endast utskriftskommentarer till PDF-filer med GroupDocs.Watermark for .NET. Förbättra dokumentsäkerhet och varumärke utan ansträngning.
weight: 13
url: /sv/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Lägg till Skriv ut endast anteckningsvattenstämpel till PDF

## Introduktion
I den här självstudien kommer vi att fördjupa oss i processen att lägga till en vattenstämpel med endast utskriftskommentarer till en PDF med GroupDocs.Watermark för .NET. Vattenmärkning av dokument är en avgörande aspekt av dokumentsäkerhet och varumärkesbyggande, och GroupDocs.Watermark tillhandahåller en sömlös lösning för .NET-utvecklare för att uppnå detta.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
- Grundläggande förståelse för programmeringsspråket C#.
- Visual Studio installerat på din dator.
- GroupDocs.Watermark för .NET-biblioteket installerat i ditt projekt.

## Importera namnområden
För att börja, se till att du importerar de nödvändiga namnrymden:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
 Först måste du ladda PDF-dokumentet som du vill vattenstämpla. Byta ut`"Your Document Path"` med sökvägen till din PDF-fil och`"Your Document Directory"` med katalogen där du vill spara utdatafilen.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Vattenmärkningskod kommer att läggas till här
}
```
## Steg 2: Lägg till vattenstämpel
Skapa sedan ett textvattenstämpelobjekt med önskad text och typsnitt. Uppsättning`isPrintOnly` till`true` för att säkerställa att vattenstämpeln endast är synlig när dokumentet skrivs ut, inte i visningsläget.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Steg 3: Konfigurera vattenstämpelalternativ
Definiera alternativ för vattenstämpeln, t.ex. sidindexet där vattenstämpeln ska läggas till och ange den som en anteckning för enbart utskrift.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Steg 4: Applicera vattenstämpel
Lägg till vattenstämpeln i dokumentet med de angivna alternativen och spara utdatafilen.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Slutsats
I den här handledningen lärde vi oss hur man lägger till en vattenstämpel för enbart utskriftskommentarer till ett PDF-dokument med GroupDocs.Watermark för .NET. Detta gör det möjligt för utvecklare att förbättra dokumentsäkerheten och varumärket med lätthet.
## FAQ's
### Är GroupDocs.Watermark kompatibel med andra dokumentformat förutom PDF?
Ja, GroupDocs Watermark stöder olika dokumentformat som Word, Excel, PowerPoint och bilder.
### Kan jag anpassa utseendet på vattenstämpeln?
Visst, GroupDocs.Watermark erbjuder omfattande alternativ för att anpassa vattenstämpeltext, teckensnitt, färg, storlek och placering.
### Erbjuder GroupDocs.Watermark batchbehandlingsmöjligheter?
Absolut, utvecklare kan vattenmärka flera dokument samtidigt med hjälp av batchbearbetningsfunktioner.
### Finns det en testversion tillgänglig för GroupDocs.Watermark?
Ja, du kan komma åt en gratis testversion av GroupDocs.Watermark från den medföljande länken.
### Hur kan jag få teknisk support för GroupDocs.Watermark?
Du kan söka teknisk hjälp från GroupDocs.Watermark-forumet som finns på den medföljande supportlänken.