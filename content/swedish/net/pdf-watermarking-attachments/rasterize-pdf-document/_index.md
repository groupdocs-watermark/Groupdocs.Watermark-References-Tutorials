---
title: Rasterisera PDF-dokument
linktitle: Rasterisera PDF-dokument
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du rastrerar PDF-dokument med GroupDocs.Watermark för .NET. Förbättra dokumentsäkerheten och visuellt tilltalande utan ansträngning.
weight: 27
url: /sv/net/pdf-watermarking-attachments/rasterize-pdf-document/
---

# Rasterisera PDF-dokument

## Introduktion
När det gäller dokumenthantering och manipulation står GroupDocs.Watermark för .NET högt som ett kraftfullt verktyg, som erbjuder robusta möjligheter att lägga till, ta bort och söka efter vattenstämplar i olika dokumentformat. Oavsett om det gäller att skydda dina dokument med upphovsrättsmeddelanden, lägga till företagslogotyper för varumärkesbyggande eller helt enkelt kommentera dokument med stämplar, förenklar GroupDocs.Watermark processen med sitt intuitiva API och omfattande funktionsuppsättning.
## Förutsättningar
Innan du dyker in i en värld av vattenmärkning med GroupDocs.Watermark för .NET, se till att du har följande förutsättningar:
### 1. Installera .NET Framework
Se till att du har .NET Framework installerat på din utvecklingsmaskin. Du kan ladda ner den från Microsofts webbplats eller använda din föredragna pakethanterare.
#### Steg 1: Ladda ner .NET Framework
Besök nedladdningssidan för Microsoft .NET Framework.
#### Steg 2: Installera .NET Framework
Följ installationsinstruktionerna på nedladdningssidan för att installera .NET Framework på ditt system.
### 2. Skaffa GroupDocs.Watermark-licens
För att använda alla funktioner i GroupDocs.Watermark behöver du en giltig licens. Du kan antingen köpa en licens eller skaffa en tillfällig licens för utvärderingsändamål.
#### Steg 1: Skaffa en licens
Besök GroupDocs.Watermark köpsidan.
#### Steg 2: Köp eller skaffa en tillfällig licens
Välj lämpligt licensalternativ baserat på dina behov – köp en licens för fortsatt användning eller skaffa en tillfällig licens för utvärderingssyften.

## Importera namnområden
Innan du börjar vattenmärka dina dokument, se till att importera de nödvändiga namnområdena för att få åtkomst till GroupDocs vattenmärkes funktionalitet.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Nu när du har allt inställt, låt oss dyka in i att rastrera ett PDF-dokument med GroupDocs.Watermark för .NET. Rasterisering konverterar varje sida i PDF-dokumentet till ett rasterbildsformat, till exempel PNG.
## Steg 1: Initiera variabler
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Se till att du ersätter "Din dokumentsökväg" och "Din dokumentkatalog" med den faktiska sökvägen till ditt PDF-dokument respektive den önskade utdatakatalogen.
## Steg 2: Ladda dokument och lägg till vattenstämpel
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Initiera bild eller text vattenstämpel
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Lägg till vattenstämpel av vilken typ som helst först
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasterisera alla sidor
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Innehållet på alla sidor ersätts med rasterbilder
    watermarker.Save(outputFileName);
}
```
I det här steget laddar vi PDF-dokumentet och initierar en textvattenstämpel med specificerade egenskaper som text, teckensnitt, justering, rotationsvinkel, storlekstyp, skalfaktor och opacitet. Sedan lägger vi till vattenstämpeln i dokumentet. Därefter hämtar vi innehållet i PDF-dokumentet och rastrerar alla sidor till PNG-format med en upplösning på 100 DPI. Slutligen sparar vi det ändrade dokumentet med rastrerat innehåll.

## Slutsats
GroupDocs.Watermark för .NET erbjuder en heltäckande lösning för att enkelt lägga till vattenstämplar i olika dokumentformat. Genom att följa stegen som beskrivs i den här handledningen kan du effektivt rastrera PDF-dokument och förbättra deras säkerhet och visuella tilltalande.
## FAQ's
### Är GroupDocs.Watermark kompatibel med andra dokumentformat förutom PDF?
Ja, GroupDocs.Watermark stöder ett brett utbud av dokumentformat, inklusive Microsoft Word, Excel, PowerPoint, Visio, Outlook och många fler.
### Kan jag anpassa utseendet på vattenstämplar som lagts till med GroupDocs.Watermark?
Absolut! GroupDocs.Watermark ger omfattande alternativ för att anpassa vattenstämpelegenskaper som text, teckensnitt, färg, storlek, opacitet, rotation och position.
### Erbjuder GroupDocs.Watermark stöd för batchbearbetning?
Ja, du kan enkelt bearbeta flera dokument i batchläge med hjälp av GroupDocs Watermark, vilket sparar tid och ansträngning vid vattenmärkning av stora uppsättningar filer.
### Finns det en testversion tillgänglig för GroupDocs.Watermark?
Ja, du kan ladda ner en gratis testversion av GroupDocs.Watermark från webbplatsen för att utvärdera dess funktioner innan du gör ett köp.
### Hur kan jag få hjälp om jag stöter på några problem eller har frågor om GroupDocs.Watermark?
Du kan besöka GroupDocs.Watermark-forumet för att söka stöd från communityn eller kontakta GroupDocs supportteam för hjälp.