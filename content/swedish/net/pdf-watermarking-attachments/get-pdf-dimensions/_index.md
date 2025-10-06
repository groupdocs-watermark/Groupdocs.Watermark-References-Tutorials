---
title: Hämta PDF-mått
linktitle: Hämta PDF-mått
second_title: GroupDocs.Watermark .NET API
description: Skydda dina dokument enkelt med Groupdocs.Watermark för .NET. Lägg till vattenstämplar, stämplar och anteckningar utan ansträngning.
weight: 26
url: /sv/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# Hämta PDF-mått

## Introduktion
dagens digitala tidsålder är det viktigt att skydda dina dokument. Oavsett om du är en affärsman, en juridisk expert eller en kreativ konstnär, är det viktigt att skydda din immateriella egendom. Groupdocs.Watermark för .NET erbjuder en robust lösning för att lägga till vattenstämplar, stämplar och anteckningar till dina dokument, vilket säkerställer deras säkerhet och äkthet.
## Förutsättningar
Innan du dyker in i världen av Groupdocs.Watermark for .NET, se till att du har följande förutsättningar på plats:
1.  Installation av Groupdocs.Watermark for .NET: Ladda ner och installera Groupdocs.Watermark for .NET från[nedladdningslänk](https://releases.groupdocs.com/Watermark/net/).
2.  Licensnyckel (valfritt): Medan Groupdocs.Watermark för .NET erbjuder en gratis provperiod kan du välja en tillfällig licens eller köpa en fullständig licens från[här](https://purchase.groupdocs.com/buy) för utökad funktionalitet.
3. Bekantskap med C#: Grundläggande kunskaper i programmeringsspråket C# rekommenderas för att förstå och implementera exemplen som ges.
4. Dokument att skydda: Ha ett exempeldokument (t.ex. PDF, Word, Excel) redo på din lokala dator att experimentera med.

## Importera namnområden
För att börja arbeta med Groupdocs.Watermark för .NET måste du importera de nödvändiga namnrymden till ditt C#-projekt.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Steg 1: Deklarera variabler
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Steg 2: Ladda dokument
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Steg 3: Hämta PDF-innehåll
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Steg 4: Hämta mått
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Slutsats
Sammanfattningsvis erbjuder Groupdocs.Watermark för .NET en heltäckande lösning för att skydda dina dokument från obehörig användning och distribution. Genom att följa stegen som beskrivs ovan och utnyttja kraften i Groupdocs.Watermark för .NET kan du säkerställa säkerheten och integriteten hos dina värdefulla digitala tillgångar.
## FAQ's
### Kan jag använda Groupdocs.Watermark för .NET gratis?
Ja, Groupdocs.Watermark för .NET erbjuder en gratis testversion för utvärderingsändamål. För utökad funktionalitet kan du dock överväga att köpa en fullständig licens.
### Stöder Groupdocs.Watermark flera dokumentformat?
Ja, Groupdocs Watermark stöder ett brett utbud av dokumentformat inklusive PDF, Word, Excel, PowerPoint och mer.
### Kan jag anpassa vattenstämplar och stämplar med Groupdocs.Watermark?
Absolut! Groupdocs.Watermark erbjuder omfattande anpassningsalternativ för vattenstämplar, stämplar och anteckningar för att passa dina specifika krav.
### Finns teknisk support tillgänglig för Groupdocs.Watermark-användare?
 Ja, du kan få teknisk assistans och engagera dig i Groupdocs-communityt genom[supportforum](https://forum.groupdocs.com/c/watermark/19).
### Hur kan jag få en tillfällig licens för Groupdocs.Watermark?
 Du kan få en tillfällig licens för Groupdocs.Watermark från[här](https://purchase.groupdocs.com/temporary-license/).