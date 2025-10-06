---
title: Ladda lösenordsskyddat dokument
linktitle: Ladda lösenordsskyddat dokument
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar i lösenordsskyddade dokument med hjälp av Groupdocs Watermark for .NET med vår steg-för-steg-guide. Säkra och märk dina filer enkelt.
weight: 13
url: /sv/net/document-loadings/load-password-protected-document/
type: docs
---
# Ladda lösenordsskyddat dokument

## Introduktion
Vill du skydda dina dokument genom att lägga till vattenstämplar, även om de är lösenordsskyddade? Groupdocs.Watermark för .NET är ett kraftfullt verktyg som låter dig göra just det. I den här handledningen guidar vi dig genom processen att ladda ett lösenordsskyddat dokument och lägga till en vattenstämpel till det med Groupdocs.Watermark for .NET. Låt oss dyka in!
## Förutsättningar
Innan vi börjar, se till att du har följande:
1. Visual Studio: Alla versioner av Visual Studio installerade på din dator.
2. .NET Framework: Se till att du har .NET Framework 4.6.1 eller senare.
3. Groupdocs.Watermark for .NET: Ladda ner och installera Groupdocs.Watermark for .NET-biblioteket från[nedladdningslänk](https://releases.groupdocs.com/Watermark/net/).
## Importera namnområden
Först måste vi importera de nödvändiga namnrymden till vårt projekt. Detta säkerställer att vi kan komma åt alla metoder och egenskaper som tillhandahålls av Groupdocs.Watermark for .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Låt oss nu dela upp processen i enkla steg som är lätta att följa.
## Steg 1: Konfigurera ditt projekt
Börja med att skapa en ny C# Console Application i Visual Studio. När ditt projekt är konfigurerat installerar du Groupdocs.Watermark for .NET-biblioteket via NuGet Package Manager.
1. Öppna Visual Studio och skapa en ny konsolapp (.NET Framework).
2.  Gå till`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Söka efter`GroupDocs.Watermark` och installera paketet.
## Steg 2: Definiera dokumentsökvägar
Därefter måste du definiera sökvägen till ditt lösenordsskyddade dokument och utdatafilens sökväg där det vattenmärkta dokumentet ska sparas.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` och`"Your Document Directory"` med de faktiska sökvägarna på din maskin.
## Steg 3: Ställ in laddningsalternativ med lösenord
För att öppna ett lösenordsskyddat dokument måste du ange lösenordet i laddningsalternativen.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Byta ut`"P@$w0rd"` med det faktiska lösenordet för ditt dokument.
## Steg 4: Ladda dokumentet
 Låt oss nu ladda dokumentet med hjälp av`Watermarker` klass.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din kod för att lägga till vattenstämpel kommer hit
}
```
## Steg 5: Skapa en vattenstämpel
Vi kommer att skapa en textvattenstämpel som vi kan lägga till i dokumentet. Du kan anpassa text, teckensnitt, storlek och andra egenskaper efter behov.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Byt gärna`"Test watermark"`, `"Arial"` , och`12` till önskad text, typsnitt och storlek.
## Steg 6: Lägg till vattenstämpeln
 Lägg till vattenstämpeln i dokumentet med hjälp av`Add` metod för`Watermarker` klass.
```csharp
watermarker.Add(watermark);
```
## Steg 7: Spara det vattenmärkta dokumentet
Spara slutligen det vattenmärkta dokumentet till den angivna sökvägen för utdatafilen.
```csharp
watermarker.Save(outputFileName);
```
## Slutsats
Att lägga till vattenstämplar i dina lösenordsskyddade dokument är en enkel process med Groupdocs Watermark for .NET. Genom att följa dessa enkla steg kan du se till att dina dokument är skyddade och märkta enligt dina krav. Oavsett om det är för säkerhet, varumärke eller efterlevnad, har det aldrig varit enklare att vattenmärka dina dokument.
## FAQ's
### Kan jag lägga till bildvattenstämplar med Groupdocs.Watermark for .NET?
 Ja, du kan lägga till både text- och bildvattenstämplar. Använd helt enkelt`ImageWatermark` klass istället för`TextWatermark`.
### Är det möjligt att ta bort vattenstämplar från ett dokument?
Ja, Groupdocs.Watermark for .NET tillhandahåller metoder för att söka efter och ta bort vattenstämplar.
### Stöder Groupdocs.Watermark for .NET andra dokumentformat förutom PDF-filer?
Ja, den stöder ett brett utbud av format inklusive Word, Excel, PowerPoint och mer.
### Kan jag anpassa utseendet på vattenstämpeln?
Absolut! Du kan anpassa teckensnitt, storlek, färg, opacitet och mer.
### Var kan jag få support om jag stöter på problem?
 Du kan besöka[Groupdocs supportforum](https://forum.groupdocs.com/c/watermark/19) för hjälp och vägledning.