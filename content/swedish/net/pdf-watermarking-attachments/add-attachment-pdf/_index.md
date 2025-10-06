---
title: Lägg till bilaga till PDF
linktitle: Lägg till bilaga till PDF
second_title: GroupDocs.Watermark .NET API
description: Förbättra dina .NET-dokumenthanteringsmöjligheter med GroupDocs.Watermark för sömlös vattenmärkning och hantering av bilagor.
weight: 12
url: /sv/net/pdf-watermarking-attachments/add-attachment-pdf/
type: docs
---
# Lägg till bilaga till PDF

## Introduktion
Inom .NET-utvecklingens område framstår GroupDocs.Watermark som ett kraftfullt verktyg för att hantera vattenstämplar, anteckningar och mer inom olika dokumentformat. Oavsett om du arbetar med PDF-filer, Word-dokument eller bilder ger GroupDocs.Watermark för .NET en sömlös integration som gör det möjligt för utvecklare att manipulera dokument med lätthet.
## Förutsättningar
Innan du dyker in i krångligheterna med att använda GroupDocs.Watermark för .NET, se till att du har följande förutsättningar på plats:
1.  Installation: Se till att du har installerat GroupDocs.Watermark för .NET. Du kan ladda ner den från[släpp sida](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentförberedelse: Ha ett dokument redo där du vill utföra vattenmärkning eller andra operationer.
3. Grundläggande kunskaper om C#: Bekanta dig med programmeringsspråket i C# eftersom vi kommer att använda det för att interagera med GroupDocs.Watermark API.

## Importera namnområden
Innan du börjar med implementeringen är det viktigt att importera de nödvändiga namnområdena för att komma åt funktionaliteten i GroupDocs.Watermark. Nedan finns de obligatoriska namnrymden:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Steg 1: Ladda dokument
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 I det här steget anger vi sökvägen till dokumentet vi vill arbeta med och skapar en`PdfLoadOptions` objekt för att ladda PDF-dokument. Sedan initierar vi a`Watermarker` objekt med dokumentets sökväg och laddningsalternativ.
## Steg 2: Hämta PDF-innehåll
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 Här får vi innehållet i PDF-dokumentet med hjälp av`GetContent<PdfContent>()` metod.
## Steg 3: Lägg till bilaga
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
Detta steg innebär att du lägger till en bilaga till PDF-dokumentet. Du måste ange den bifogade filens byte, namn och beskrivning.
## Steg 4: Spara ändringar
```csharp
watermarker.Save(outputFileName);
```
Slutligen sparar vi de ändringar som gjorts i dokumentet med den tillagda bilagan.

## Slutsats
GroupDocs.Watermark för .NET erbjuder en robust lösning för att hantera dokumentvattenstämplar och bilagor sömlöst. Genom att följa stegen som beskrivs ovan kan du enkelt integrera funktioner för vattenmärkning och bilagor i dina .NET-applikationer.
## FAQ's
### Är GroupDocs.Watermark kompatibel med alla .NET-ramverk?
Ja, GroupDocs.Watermark stöder .NET Framework 2.0 och högre.
### Kan jag ta bort vattenstämplar som lagts till med GroupDocs.Watermark?
Ja, GroupDocs.Watermark tillhandahåller metoder för att ta bort vattenstämplar från dokument.
### Stöder GroupDocs.Watermark dokumentkryptering?
Ja, GroupDocs.Watermark låter dig arbeta med krypterade dokument.
### Kan jag anpassa utseendet på vattenstämplar?
Absolut, GroupDocs.Watermark erbjuder olika anpassningsalternativ för vattenstämplar.
### Finns det en testversion tillgänglig för teständamål?
 Ja, du kan komma åt testversionen från[släpper sida](https://releases.groupdocs.com/).