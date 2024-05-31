---
title: Lägg till bildvattenstämpel
linktitle: Lägg till bildvattenstämpel
second_title: GroupDocs.Watermark .NET API
description: Lägg enkelt till bildvattenstämplar till dina dokument med GroupDocs.Watermark för .NET. Skydda din immateriella egendom med lätthet.
type: docs
weight: 10
url: /sv/net/watermarking-basics/add-image-watermark/
---
## Introduktion
I den här handledningen kommer vi att fördjupa oss i processen att lägga till en bildvattenstämpel till dina dokument med hjälp av GroupDocs.Watermark for .NET. Vattenmärkningsdokument är avgörande för att skydda immateriella rättigheter och varumärkesbyggande. Med GroupDocs.Watermark för .NET kan du sömlöst integrera vattenstämplar i olika dokumentformat som Word, Excel, PowerPoint, PDF och många fler.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
1.  GroupDocs.Watermark for .NET Library: Ladda ner och installera GroupDocs.Watermark for .NET-biblioteket från[hemsida](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Ha dokumentet redo som du vill lägga till vattenstämpeln till.
3. Bild för vattenstämpel: Förbered bildfilen som du vill använda som vattenstämpel.

## Importera namnområden
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Steg 1: Initiera dokumentsökväg och utdatakatalog
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"`med den absoluta eller relativa sökvägen till ditt dokument och`"Your Document Directory"` med katalogen där du vill spara det vattenmärkta dokumentet.
## Steg 2: Öppna Document Stream och initiera Watermarker
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Vattenmärkningsprocessen kommer att gå här
    }
}
```
 Öppna dokumentströmmen med`FileStream` och initiera`Watermarker` objekt.
## Steg 3: Lägg till bildvattenstämpel
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Skapa en`ImageWatermark` objekt med sökvägen till bildfilen du vill använda som vattenstämpel. Ställ in den horisontella och vertikala justeringen av vattenstämpeln.
## Steg 4: Spara vattenmärkt dokument
```csharp
watermarker.Save(outputFileName);
```
Spara det vattenmärkta dokumentet i den angivna utdatakatalogen med önskat filnamn.

## Slutsats
Sammanfattningsvis ger GroupDocs.Watermark för .NET en heltäckande lösning för att lägga till vattenstämplar i olika dokumentformat utan ansträngning. Genom att följa stegen som beskrivs i denna handledning kan du effektivt lägga till bildvattenstämplar i dina dokument och skydda din immateriella egendom.
## FAQ's
### Kan jag lägga till textvattenstämplar med GroupDocs.Watermark för .NET?
Ja, GroupDocs.Watermark för .NET stöder att lägga till både bild- och textvattenstämplar i dokument.
### Är GroupDocs.Watermark for .NET kompatibelt med olika dokumentformat?
Absolut, GroupDocs.Watermark för .NET stöder ett brett utbud av dokumentformat inklusive Word, Excel, PowerPoint, PDF och mer.
### Ger GroupDocs.Watermark for .NET anpassningsalternativ för vattenstämplar?
Ja, du kan anpassa olika aspekter av vattenstämpeln som position, storlek, opacitet och rotation.
### Kan jag ta bort vattenstämplar från dokument med GroupDocs.Watermark for .NET?
Ja, GroupDocs.Watermark för .NET erbjuder funktionalitet för att upptäcka och ta bort vattenstämplar från dokument.
### Finns det en testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan använda en gratis testversion från webbplatsen för att utforska funktionerna innan du köper[här](https://releases.groupdocs.com/).