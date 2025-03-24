---
title: Lägg till låst vattenstämpel på alla sidor i Word Docs
linktitle: Lägg till låst vattenstämpel på alla sidor i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Säkra dina dokument genom att lägga till låsta vattenstämplar med Groupdocs.Watermark for .NET. Följ vår steg-för-steg-guide för enkel implementering.
weight: 11
url: /sv/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

# Lägg till låst vattenstämpel på alla sidor i Word Docs

## Introduktion
Att lägga till vattenstämplar i dina dokument är ett viktigt steg för att säkra och skapa varumärke för ditt innehåll. Oavsett om du förhindrar obehörig användning eller bara lägger till en professionell touch, kan vattenstämplar tjäna flera syften. I den här handledningen går vi igenom processen att lägga till en låst vattenstämpel på alla sidor i ett Word-dokument med hjälp av Groupdocs.Watermark for .NET.
## Förutsättningar
Innan vi dyker in i steg-för-steg-guiden, låt oss se till att du har allt du behöver:
1. Groupdocs.Watermark for .NET: Ladda ner den senaste versionen från[här](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Se till att du har .NET Framework installerat på din dator.
3. Utvecklingsmiljö: En utvecklingsmiljö som Visual Studio.
4.  Licens: Du kan välja en[gratis provperiod](https://releases.groupdocs.com/) eller köp en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/).
## Importera namnområden
Först och främst måste du importera de nödvändiga namnrymden i ditt projekt. Dessa är viktiga för att komma åt klasserna och metoderna som tillhandahålls av Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Konfigurera ditt projekt

Öppna din utvecklingsmiljö och skapa ett nytt .NET-projekt. Detta kan vara en konsolapplikation eller någon annan typ som passar dina behov.

Du måste lägga till Groupdocs.Watermark-paketet till ditt projekt. Detta kan göras via NuGet Package Manager. Kör följande kommando i NuGet Package Manager Console:
```sh
Install-Package GroupDocs.Watermark
```
## Steg 2: Ladda Word-dokumentet
### Definiera dokumentsökvägen
Ange sökvägen till ditt Word-dokument. Detta kommer att vara dokumentet där du vill lägga till vattenstämpeln.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Ställ in laddningsalternativ
 Skapa en instans av`WordProcessingLoadOptions` för att ladda ditt Word-dokument med specifika alternativ.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Steg 3: Skapa vattenstämpeln
### Initiera Watermarker
 Använda`Watermarker`klass, ladda dokumentet med de angivna laddningsalternativen.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ytterligare steg kommer att finnas i detta block
}
```
### Definiera egenskaper för vattenstämpel
 Skapa en`TextWatermark` instans med önskad text, typsnitt och färg.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Steg 4: Använd vattenstämpel på alla sidor
### Ställ in vattenstämpelalternativ
 Definiera`WordProcessingWatermarkPagesOptions` och ställ in`IsLocked` egenskapen till sann för att låsa vattenstämpeln. Detta säkerställer att vattenstämpeln inte kan tas bort lätt.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Valfritt: Lägg till lösenordsskydd
Om du vill lägga till ett extra lager av säkerhet kan du ställa in ett lösenord för vattenstämpeln.
```csharp
// För att skydda med lösenord
// options.Password = "7654321";
```
### Lägg till vattenstämpeln
 Använd`Add` metod för`Watermarker` klass för att lägga till vattenstämpeln i dokumentet med de angivna alternativen.
```csharp
watermarker.Add(watermark, options);
```
## Steg 5: Spara dokumentet
Spara slutligen det ändrade dokumentet till den angivna utdatafilen.
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
Genom att följa dessa steg kan du enkelt lägga till en låst vattenstämpel på alla sidor i dina Word-dokument med Groupdocs.Watermark for .NET. Detta hjälper inte bara till att skydda dina dokument från obehörig användning utan ger också en professionell touch till ditt innehåll. Groupdocs.Watermark erbjuder en heltäckande lösning för behov av vattenmärkning, vilket säkerställer att dina dokument förblir säkra och märkta.
## FAQ's
### Kan jag använda en bild som vattenstämpel istället för text?
 Ja, Groupdocs Watermark stöder både text- och bildvattenstämplar. Du kan byta ut`TextWatermark` med`ImageWatermark` och ange din bild.
### Är det möjligt att anpassa placeringen av vattenstämpeln?
 Absolut! Du kan ställa in vattenstämpelns position med hjälp av egenskaper som`HorizontalAlignment` och`VerticalAlignment`.
### Kan jag använda olika vattenstämplar på olika sidor i dokumentet?
 Ja, du kan anpassa vattenstämplar för specifika sidor med hjälp av`PageIndex` egendom i`WordProcessingWatermarkPagesOptions`.
### Stöder Groupdocs.Watermark andra dokumentformat än Word?
Ja, Groupdocs Watermark stöder olika format inklusive PDF, Excel, PowerPoint och mer.
### Vilka är systemkraven för att använda Groupdocs.Watermark?
Du behöver ett system med .NET Framework installerat och en utvecklingsmiljö som Visual Studio.