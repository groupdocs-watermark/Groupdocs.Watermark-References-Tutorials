---
title: Lägg till bildvattenstämpel i alla rubriker i Word Docs
linktitle: Lägg till bildvattenstämpel i alla rubriker i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lägg enkelt till bildvattenstämplar i alla rubriker i Word-dokument med GroupDocs.Watermark för .NET. Följ vår steg-för-steg-guide med detaljerade kodexempel.
weight: 10
url: /sv/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---

# Lägg till bildvattenstämpel i alla rubriker i Word Docs

## Introduktion
Vattenstämplar kan vara en viktig del av dokumenthanteringen, vilket ger ett sätt att bädda in information som ägande, konfidentialitet eller varumärke i dokument. I den här handledningen går vi igenom stegen för att lägga till en bildvattenstämpel till alla rubriker i Word-dokument med GroupDocs.Watermark för .NET. Oavsett om du är ny på programmering eller en erfaren utvecklare, kommer den här guiden att hjälpa dig att nå dina vattenmärkningsmål med lätthet.
## Förutsättningar
Innan vi dyker in i koden, låt oss se till att vi har allt vi behöver. Här är en checklista för att komma igång:
1.  GroupDocs.Watermark för .NET: Ladda ner den senaste versionen från[här](https://releases.groupdocs.com/Watermark/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan .NET-kompatibel IDE.
3. .NET Framework: Se till att du har .NET Framework installerat.
4. Exempel på Word-dokument: Ett Word-dokument där du vill lägga till vattenstämpeln.
5. Bild för vattenstämpel: En bildfil som du vill använda som vattenstämpel.
När du har dessa redo kan vi börja sätta upp vårt projekt.
## Importera namnområden
Låt oss först importera de nödvändiga namnrymden. Dessa namnrymder innehåller klasser och metoder som hjälper oss att arbeta med vattenstämplar i våra dokument.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Konfigurera ditt projekt
För att komma igång, skapa en ny konsolapplikation i Visual Studio. Lägg till referenser till GroupDocs.Watermark DLL i ditt projekt. Detta kan göras genom att installera GroupDocs.Watermark NuGet-paketet.
```bash
Install-Package GroupDocs.Watermark
```
## Steg 2: Ladda ditt dokument
 Det första steget för att lägga till en vattenstämpel är att ladda dokumentet där vattenstämpeln ska läggas till. Här kommer vi att använda`WordProcessingLoadOptions` för att ladda ett Word-dokument.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Koden för att lägga till vattenstämpel kommer hit
}
```
## Steg 3: Skapa bildvattenstämpeln
Därefter skapar vi en bildvattenstämpel. Detta innebär att du anger vilken bildfil du vill använda som vattenstämpel.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Koden för att applicera vattenstämpeln kommer hit
}
```
## Steg 4: Lägg till vattenstämpel i rubrikerna för första avsnittet
 Vi måste lägga till vattenstämpeln i alla rubriker i den första delen av Word-dokumentet. För detta använder vi`WordProcessingWatermarkSectionOptions` och ange avsnittsindex.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Steg 5: Länka sidhuvuden och sidfötter
För att säkerställa att vattenstämpeln visas i sidhuvuden i alla avsnitt länkar vi alla andra sidhuvuden och sidfötter till sidhuvuden och sidfötter i det första avsnittet.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Steg 6: Spara dokumentet
Slutligen sparar vi det vattenmärkta dokumentet till en angiven sökväg. Detta steg säkerställer att dina ändringar skrivs till en ny fil, vilket bevarar originaldokumentet.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Slutsats
Och där har du det! Du har framgångsrikt lagt till en bildvattenstämpel till alla rubriker i ett Word-dokument med hjälp av GroupDocs.Watermark för .NET. Detta kraftfulla bibliotek gör det enkelt att hantera och applicera vattenstämplar på olika dokumenttyper, vilket säkerställer att ditt innehåll är skyddat och professionellt varumärke.
## FAQ's
### Kan jag använda andra typer av vattenstämplar förutom bilder?
Ja, GroupDocs Watermark stöder text, bild och till och med sammansatta vattenstämplar.
### Är det möjligt att vattenmärka andra delar av dokumentet förutom rubriker?
Absolut! Du kan vattenstämpla sidfötter, brödtext och till och med specifika sidor eller avsnitt.
### Stöder GroupDocs.Watermark andra dokumentformat?
Ja, den stöder ett brett utbud av format inklusive PDF-filer, Excel, PowerPoint och mer.
### Kan jag anpassa placeringen och utseendet på vattenstämpeln?
Ja, du kan anpassa storleken, positionen, opaciteten och många andra egenskaper för vattenstämpeln.
### Finns det en gratis testversion tillgänglig för GroupDocs.Watermark?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).