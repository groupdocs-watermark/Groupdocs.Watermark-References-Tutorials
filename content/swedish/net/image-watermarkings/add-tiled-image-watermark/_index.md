---
title: Lägg till vattenstämpel med sida vid sida
linktitle: Lägg till vattenstämpel med sida vid sida
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar med sida vid sida i dina dokument med GroupDocs.Watermark för .NET. Enkelt, effektivt och anpassningsbart.
weight: 10
url: /sv/net/image-watermarkings/add-tiled-image-watermark/
type: docs
---
# Lägg till vattenstämpel med sida vid sida

## Introduktion
GroupDocs.Watermark for .NET är ett kraftfullt API som låter utvecklare lägga till, ta bort och söka efter vattenstämplar i olika dokumentformat programmatiskt. I den här handledningen guidar vi dig genom processen att lägga till en vattenstämpel med sida vid sida i dina dokument med hjälp av GroupDocs.Watermark för .NET.
## Förutsättningar
Innan du börjar, se till att du har följande:
- Grundläggande kunskaper i programmeringsspråket C#.
- Visual Studio installerat på ditt system.
- GroupDocs.Watermark för .NET-bibliotek har lagts till i ditt projekt. Du kan ladda ner den från[här](https://releases.groupdocs.com/Watermark/net/).

## Importera namnområden
Se till att importera de nödvändiga namnrymden i början av din C#-fil:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Steg 1: Ställ in dokumentsökväg och utdatakatalog
Definiera sökvägen till ditt indatadokument och katalogen där du vill spara utdatadokumentet:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` med den absoluta eller relativa sökvägen till ditt inmatningsdokument.
## Steg 2: Initiera Watermarker Object
Skapa ett Watermarker-objekt med hjälp av indatadokumentets sökväg:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Lägg till vattenstämpel här
}
```
## Steg 3: Lägg till vattenstämpel med sida vid sida
Instantiera ett ImageWatermark-objekt med sökvägen till bildfilen du vill använda som vattenstämpel:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Konfigurera alternativ för brickor
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Lägg till vattenstämpel i dokumentet
    watermarker.Add(watermark);
    // Spara det ändrade dokumentet
    watermarker.Save(outputFileName);
}
```
 Byta ut`"Path to Your Image"` med den faktiska sökvägen till din vattenstämpelbildfil.

## Slutsats
Genom att följa dessa steg kan du enkelt lägga till en vattenstämpel med sida vid sida i dina dokument med hjälp av GroupDocs.Watermark för .NET. Experimentera med olika alternativ och konfigurationer för att uppnå önskat resultat.
## FAQ's
### Kan jag lägga till flera vattenstämplar i ett enda dokument?
Ja, du kan lägga till flera vattenstämplar av olika typer till ett dokument med GroupDocs.Watermark för .NET.
### Stöder GroupDocs.Watermark alla dokumentformat?
GroupDocs.Watermark stöder ett brett utbud av dokumentformat, inklusive PDF, Word, Excel, PowerPoint och många fler.
### Finns det en testversion tillgänglig för GroupDocs.Watermark?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Kan jag anpassa utseendet på vattenstämpeln?
Ja, du kan anpassa olika aspekter av vattenstämpeln, såsom position, storlek, rotation, transparens, etc.
### Erbjuder GroupDocs.Watermark teknisk support?
 Ja, du kan få teknisk support från GroupDocs.Watermark-forumet[här](https://forum.groupdocs.com/c/watermark/19).