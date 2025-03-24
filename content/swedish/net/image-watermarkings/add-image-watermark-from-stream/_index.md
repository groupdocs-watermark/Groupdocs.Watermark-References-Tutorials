---
title: Lägg till bildvattenstämpel från Stream
linktitle: Lägg till bildvattenstämpel från Stream
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till bildvattenstämplar i dokument med GroupDocs.Watermark for .NET. Följ vår steg-för-steg-guide för sömlös vattenstämpelintegrering.
weight: 12
url: /sv/net/image-watermarkings/add-image-watermark-from-stream/
---

# Lägg till bildvattenstämpel från Stream

## Introduktion
När det gäller dokumenthantering och säkerhet är det av största vikt att införliva vattenstämplar i filer. Oavsett om det handlar om varumärke, upphovsrättsskydd eller att bibehålla dokumentintegritet, spelar vattenstämplar en avgörande roll. Lyckligtvis tillhandahåller GroupDocs.Watermark för .NET en robust lösning för att lägga till, ta bort och söka efter vattenstämplar i olika dokumentformat.
## Förutsättningar
Innan du dyker in i implementeringen av vattenstämplar med GroupDocs.Watermark för .NET, se till att följande förutsättningar är uppfyllda:
1.  Installera GroupDocs.Watermark for .NET: Ladda ner och installera GroupDocs.Watermark for .NET-biblioteket från[nedladdningslänk](https://releases.groupdocs.com/Watermark/net/).
2. Åtkomst till dokument: Ha åtkomst till dokumentet som du vill lägga till eller ta bort vattenstämplar på.
3. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# är nödvändigt för att förstå och implementera de medföljande kodavsnitten.

## Importera namnområden
Innan du fortsätter med att lägga till bildvattenstämplar från en ström, importera nödvändiga namnområden:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Steg 1: Definiera dokumentsökväg och utdatakatalog
Ange först sökvägen till dokumentet där du vill lägga till vattenstämpeln och ange utdatakatalogen för det bearbetade dokumentet.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Steg 2: Öppna Watermark Stream
 Öppna vattenstämpelns bildfil som en ström med hjälp av`File.OpenRead` metod.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // Bearbetningslogik för vattenstämpel kommer hit
}
```
## Steg 3: Lägg till vattenstämpel i dokumentet
 Initiera a`Watermarker` objekt med dokumentsökvägen, skapa sedan en`ImageWatermark` objekt med vattenstämpelströmmen som erhölls i steg 2. Lägg till vattenstämpeln i dokumentet med hjälp av`Add` metod för`Watermarker` objekt.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Lägg till vattenstämpel i dokumentet
        watermarker.Add(watermark);
        // Spara dokumentet med vattenstämpel
        watermarker.Save(outputFileName);
    }
}
```

## Slutsats
GroupDocs.Watermark för .NET tillhandahåller en sömlös lösning för att lägga till vattenstämplar i dokument, säkerställa varumärkesidentitet, upphovsrättsskydd och dokumentintegritet. Genom att följa de skisserade stegen och använda de medföljande kodavsnitten kan användare enkelt införliva vattenstämplar i sina dokument.
## FAQ's
### Är GroupDocs.Watermark kompatibel med olika dokumentformat?
Ja, GroupDocs.Watermark stöder ett brett utbud av dokumentformat inklusive Word-dokument, Excel-kalkylblad, PowerPoint-presentationer, PDF-filer och mer.
### Kan jag anpassa utseendet och placeringen av vattenstämplar?
Absolut, GroupDocs.Watermark erbjuder omfattande alternativ för att anpassa vattenstämpelns utseende, position, transparens, rotation och mer för att passa specifika krav.
### Tillhandahåller GroupDocs.Watermark API:er för att ta bort befintliga vattenstämplar?
Ja, GroupDocs.Watermark tillåter användare att inte bara lägga till vattenstämplar utan också ta bort befintliga vattenstämplar från dokument med lätthet.
### Finns teknisk support tillgänglig för GroupDocs.Watermark-användare?
 Ja, användare kan få teknisk support och hjälp via dedikerade[GroupDocs.Watermark forum](https://forum.groupdocs.com/c/watermark/19).
### Kan jag utvärdera GroupDocs.Watermark innan jag köper?
Visst kan användare välja en gratis provversion av GroupDocs.Watermark för att utforska dess funktioner och funktioner innan de fattar ett köpbeslut.