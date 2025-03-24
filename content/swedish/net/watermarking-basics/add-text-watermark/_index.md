---
title: Lägg till textvattenstämpel
linktitle: Lägg till textvattenstämpel
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till textvattenstämplar i dina dokument med hjälp av Groupdocs Watermark for .NET med denna steg-för-steg-guide.
weight: 11
url: /sv/net/watermarking-basics/add-text-watermark/
---

# Lägg till textvattenstämpel

## Introduktion
GroupDocs.Watermark for .NET är ett kraftfullt bibliotek som låter utvecklare lägga till, söka och ta bort vattenstämplar från olika dokumentformat i .NET-applikationer. I den här handledningen kommer vi att fokusera på att lägga till en textvattenstämpel i ett dokument med GroupDocs.Watermark.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1. Grundläggande kunskaper i programmeringsspråket C#.
2. Visual Studio installerat på ditt system.
3.  GroupDocs.Watermark för .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/Watermark/net/).

## Importera namnområden
Först måste du importera de nödvändiga namnrymden till ditt C#-projekt.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Steg 1: Definiera dokumentsökväg och utdatakatalog
Definiera sökvägen till ditt inmatningsdokument och utdatakatalogen där det vattenmärkta dokumentet ska sparas.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` med den absoluta eller relativa sökvägen till ditt inmatningsdokument, till exempel:`@"C:\Docs\document.pdf"`. Ange också katalogen där du vill spara det vattenmärkta dokumentet.
## Steg 2: Lägg till textvattenstämpel
 Instantiera`Watermarker` klass med indatadokumentets sökväg. Skapa sedan en`TextWatermark` objekt med önskad text och teckensnittsinställningar.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till en textvattenstämpel i ett dokument med hjälp av GroupDocs.Watermark för .NET. Med dess intuitiva API kan utvecklare enkelt manipulera vattenstämplar i olika dokumentformat.
## FAQ's
### Är GroupDocs.Watermark for .NET kompatibelt med alla dokumentformat?
GroupDocs.Watermark stöder ett brett utbud av dokumentformat inklusive PDF, Microsoft Word, Excel, PowerPoint och många fler.
### Kan jag anpassa utseendet på textens vattenstämpel?
Ja, du kan anpassa olika egenskaper som teckensnitt, färg, justering och opacitet för textens vattenstämpel.
### Ger GroupDocs.Watermark stöd för att ta bort vattenstämplar från dokument?
Ja, GroupDocs.Watermark erbjuder funktionalitet för att söka efter och ta bort vattenstämplar från dokument.
### Kan jag prova GroupDocs.Watermark för .NET innan jag köper?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur kan jag få teknisk support för GroupDocs.Watermark?
 Du kan få teknisk support genom att besöka[GroupDocs.Watermark forum](https://forum.groupdocs.com/c/watermark/19).