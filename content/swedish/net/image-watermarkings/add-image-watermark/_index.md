---
title: Lägg till bildvattenstämpel
linktitle: Lägg till bildvattenstämpel
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till bildvattenstämplar i dina dokument med hjälp av GroupDocs.Watermark for .NET med vår detaljerade, steg-för-steg handledning.
weight: 11
url: /sv/net/image-watermarkings/add-image-watermark/
---

# Lägg till bildvattenstämpel

## Introduktion
Välkommen till den här omfattande guiden för att lägga till bildvattenstämplar med GroupDocs.Watermark för .NET! Vattenmärkning är ett kraftfullt sätt att skydda dina dokument och bilder från obehörig användning, vilket säkerställer att din immateriella egendom förblir säker. I den här handledningen går vi igenom hela processen, från att ställa in din miljö till att applicera en vattenstämpel på dina dokument. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer du att tycka att den här guiden är användbar och lätt att följa.
## Förutsättningar
Innan vi dyker in i handledningen, låt oss se till att du har allt du behöver:
- Utvecklingsmiljö: Visual Studio eller någon .NET-kompatibel IDE
- .NET Framework: .NET Framework 4.0 eller senare
-  GroupDocs.Watermark för .NET: Du kan ladda ner det från[GroupDocs webbplats](https://releases.groupdocs.com/Watermark/net/)
-  Bildfil: En bildfil att använda som vattenstämpel (t.ex.`watermark.jpg`)
- Dokumentfil: Ett dokument till vilket du vill lägga till vattenstämpeln (t.ex.`presentation.pptx`)
## Importera namnområden
För att komma igång måste du importera de nödvändiga namnrymden till ditt projekt. Detta är viktigt för att få tillgång till GroupDocs Watermark-funktioner.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
I det här avsnittet kommer vi att dela upp processen att lägga till en bildvattenstämpel i tydliga, hanterbara steg. Följ varje steg noggrant för att framgångsrikt vattenmärka ditt dokument.
## Steg 1: Ställ in din miljö
 Se först till att din utvecklingsmiljö är korrekt inställd. Installera GroupDocs.Watermark-biblioteket genom att ladda ner det från[GroupDocs webbplats](https://releases.groupdocs.com/Watermark/net/).
1. Öppna ditt projekt i Visual Studio.
2. Högerklicka på ditt projekt i Solution Explorer.
3. Välj "Hantera NuGet-paket..."
4.  Söka efter`GroupDocs.Watermark` och installera den.
## Steg 2: Definiera filsökvägar
Därefter måste du definiera sökvägarna för ditt inmatningsdokument och utdatakatalogen. Detta hjälper programmet att hitta de filer det behöver arbeta med.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` och`"Your Document Directory"` med de faktiska sökvägarna till ditt dokument och önskad utdatakatalog.
## Steg 3: Initiera Watermarker
Initiera nu`Watermarker` klass med sökvägen till ditt dokument. Denna klass ansvarar för att hantera vattenmärkningsprocessen.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Fortsätt till nästa steg inom detta block
}
```
## Steg 4: Skapa bildvattenstämpel
 Inom`Watermarker` blockera, skapa en instans av`ImageWatermark` klass med hjälp av sökvägen till din vattenstämpelbild. Den här klassen representerar bilden du vill använda som vattenstämpel.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Fortsätt till nästa steg inom detta block
}
```
## Steg 5: Lägg till vattenstämpel i dokumentet
 Med`ImageWatermark` instans redo, lägg till den i ditt dokument med hjälp av`Add` metod för`Watermarker` klass.
```csharp
watermarker.Add(watermark);
```
## Steg 6: Spara dokumentet
Spara slutligen det vattenmärkta dokumentet i den angivna utdatakatalogen. Detta steg säkerställer att dina ändringar skrivs till en ny fil.
```csharp
watermarker.Save(outputFileName);
```
## Slutsats
Grattis! Du har framgångsrikt lagt till en bildvattenstämpel till ditt dokument med GroupDocs.Watermark for .NET. Genom att följa denna steg-för-steg-guide kan du enkelt skydda dina dokument med anpassade vattenstämplar. Kom ihåg att vattenmärkning är ett avgörande steg för att skydda dina digitala tillgångar från obehörig användning.

## FAQ's
### Vilka filformat stöds av GroupDocs.Watermark?
GroupDocs.Watermark stöder ett brett utbud av filformat, inklusive PDF, DOCX, PPTX, XLSX och bildfiler som JPEG och PNG.
### Kan jag använda GroupDocs.Watermark med .NET Core?
Ja, GroupDocs.Watermark är kompatibel med både .NET Framework och .NET Core.
### Hur kan jag få en tillfällig licens för GroupDocs.Watermark?
 Du kan få en tillfällig licens från[GroupDocs webbplats](https://purchase.groupdocs.com/temporary-license/).
### Är det möjligt att lägga till flera vattenstämplar i ett enda dokument?
 Absolut! Du kan lägga till flera vattenstämplar genom att anropa`Add` metod flera gånger med olika vattenstämpelinstanser.
### Var kan jag hitta fler exempel och dokumentation?
 För fler exempel och detaljerad dokumentation, besök[GroupDocs.Watermark dokumentation](https://tutorials.groupdocs.com/Watermark/net/).