---
title: Skapa dokumentförhandsgranskning
linktitle: Skapa dokumentförhandsgranskning
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du genererar dokumentförhandsvisningar med GroupDocs.Watermark för .NET med den här guiden. Förbättra din dokumentsäkerhet och hantering utan ansträngning.
type: docs
weight: 10
url: /sv/net/document-manipulation/generate-document-preview/
---
## Introduktion
I en värld av digital dokumenthantering spelar vattenmärkning en avgörande roll för att säkerställa dokumentens säkerhet och äkthet. GroupDocs.Watermark for .NET är ett kraftfullt verktyg som låter utvecklare lägga till vattenstämplar i dokument utan ansträngning. I den här handledningen går vi igenom processen att skapa förhandsvisningar av dokument med GroupDocs.Watermark för .NET. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här guiden att ge dig en omfattande steg-för-steg-process för att uppnå ditt mål.
## Förutsättningar
Innan vi går in i implementeringen, låt oss se till att du har allt du behöver för att komma igång:
- En grundläggande förståelse för C# och .NET framework.
- Visual Studio installerat på din dator.
- GroupDocs.Watermark för .NET-bibliotek. Du kan[ladda ner den här](https://releases.groupdocs.com/Watermark/net/).
-  En giltig licens för GroupDocs.Watermark. Du kan antingen köpa den[här](https://purchase.groupdocs.com/buy) eller skaffa en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/) i utvärderingssyfte.
## Importera namnområden
För att börja använda GroupDocs.Watermark i ditt projekt måste du importera de nödvändiga namnrymden. Detta kan göras genom att lägga till följande med hjälp av direktiv till din kod:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Dessa namnrymder ger tillgång till de klasser och metoder som krävs för vattenmärkning och generering av dokumentförhandsvisningar.

Låt oss dela upp processen att skapa en förhandsgranskning av dokument i enkla steg som är lätta att följa.
## Steg 1: Konfigurera ditt projekt
Först till kvarn, ställ in ditt .NET-projekt i Visual Studio. Om du inte redan har ett projekt, skapa ett nytt genom att följa dessa steg:
1. Öppna Visual Studio.
2. Klicka på "Skapa ett nytt projekt."
3. Välj "Console App (.NET Core)" och klicka på "Nästa".
4. Namnge ditt projekt och välj en plats för att spara det och klicka sedan på "Skapa".
## Steg 2: Installera GroupDocs.Watermark för .NET
För att använda GroupDocs.Watermark i ditt projekt måste du installera biblioteket. Detta kan göras med NuGet Package Manager:
1. Högerklicka på ditt projekt i Solution Explorer.
2. Välj "Hantera NuGet-paket."
3. Sök efter "GroupDocs.Watermark" på fliken Bläddra.
4. Klicka på "Installera" för att lägga till biblioteket till ditt projekt.
Alternativt kan du installera det via Package Manager Console:
```powershell
Install-Package GroupDocs.Watermark
```
## Steg 3: Definiera dokumentsökväg och utdatakatalog
Innan du skapar förhandsgranskningen måste du ange sökvägen till dokumentet du vill förhandsgranska och katalogen där förhandsgranskningsbilderna ska sparas:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Ersätt "Din dokumentsökväg" med sökvägen till ditt dokument och "Din dokumentkatalog" med den katalog där du vill spara förhandsgranskningsbilderna.
## Steg 4: Initiera Watermarker Object
Skapa en instans av`Watermarker` klass genom att skicka dokumentsökvägen till dess konstruktor. Detta objekt kommer att användas för att utföra alla vattenmärkningsoperationer:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Din kod här
}
```
## Steg 5: Skapa delegatmetoder för strömhantering
För att generera förhandsvisningen måste du definiera ombudsmetoder för att skapa och släppa strömmar. Dessa metoder kommer att hantera skapandet och frisläppandet av strömmar för varje sida i dokumentet:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 De`createPageStreamDelegate` metoden skapar en ström för varje sida i dokumentet, medan`releasePageStreamDelegate` metoden stänger strömmen efter att förhandsgranskningen har genererats.
## Steg 6: Konfigurera förhandsgranskningsalternativ
 Konfigurera sedan förhandsgranskningsalternativen genom att skapa en instans av`PreviewOptions` klass. Ange delegeringsmetoderna och ställ in förhandsgranskningsformatet till PNG. Du kan också ange vilka sidor som ska inkluderas i förhandsgranskningen:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
I det här exemplet genererar vi förhandsvisningar för de två första sidorna i dokumentet.
## Steg 7: Skapa förhandsgranskningen av dokument
 Ring slutligen`GeneratePreview` metod på`Watermarker`objekt, som passerar i den konfigurerade`PreviewOptions`. Detta kommer att generera förhandsgranskningsbilderna och spara dem i den angivna katalogen:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Slutsats
Att skapa förhandsvisningar av dokument med GroupDocs.Watermark för .NET är en enkel process som kan utföras med bara några rader kod. Genom att följa stegen som beskrivs i den här guiden kan du enkelt ställa in ditt projekt, konfigurera nödvändiga alternativ och generera förhandsgranskningar för dina dokument. Detta kraftfulla bibliotek förenklar inte bara vattenmärkningsprocessen utan ger också robusta funktioner för att hantera och manipulera vattenstämplar.
 Om du har några frågor eller behöver ytterligare hjälp, tveka inte att besöka[Supportforum för GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) eller hänvisa till[dokumentation](https://reference.groupdocs.com/Watermark/net/).
## FAQ's
### Vilka filformat stöds av GroupDocs.Watermark för .NET?
 GroupDocs.Watermark för .NET stöder ett brett utbud av filformat, inklusive PDF, DOCX, PPTX, XLSX och många fler. För en fullständig lista över format som stöds, se[dokumentation](https://reference.groupdocs.com/Watermark/net/).
### Kan jag anpassa utseendet på vattenstämplar?
Ja, GroupDocs.Watermark låter dig anpassa utseendet på vattenstämplar, inklusive text, bild och formvattenstämplar. Du kan justera egenskaper som teckensnitt, färg, storlek och genomskinlighet.
### Finns det en testversion tillgänglig?
 Ja, du kan få en[gratis provperiod](https://releases.groupdocs.com/) av GroupDocs.Watermark för .NET för att utvärdera dess funktioner innan du gör ett köp.
### Hur kan jag köpa en licens för GroupDocs.Watermark?
 Du kan köpa en licens för GroupDocs.Watermark[här](https://purchase.groupdocs.com/buy). Det finns olika licensalternativ tillgängliga för att passa olika behov.
### Kan jag använda GroupDocs.Watermark i ett kommersiellt projekt?
 Ja, med en giltig licens kan du använda GroupDocs.Watermark i kommersiella projekt. Se till att läsa licensvillkoren på[köpsidan](https://purchase.groupdocs.com/buy).