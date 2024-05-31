---
title: Lägg till vattenstämpel till bilder i PDF
linktitle: Lägg till vattenstämpel till bilder i PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig att lägga till vattenstämplar till bilder i PDF-dokument med hjälp av GroupDocs.Watermark for .NET med vår detaljerade, steg-för-steg handledning. Säkra dina PDF-filer enkelt.
type: docs
weight: 19
url: /sv/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Introduktion
Att lägga till vattenstämplar till bilder i ett PDF-dokument kan vara avgörande för att skydda din immateriella egendom eller för att säkerställa äktheten hos dina dokument. Genom att använda GroupDocs.Watermark för .NET kan denna uppgift utföras effektivt och enkelt. Denna handledning guidar dig genom varje steg i processen, från att ställa in din miljö till att lägga till vattenstämplar till att spara det slutliga dokumentet. Låt oss dyka in!
## Förutsättningar
Innan vi börjar, se till att du har följande:
1. Visual Studio: Installera Visual Studio, den integrerade utvecklingsmiljön (IDE) för .NET-applikationer.
2.  GroupDocs.Watermark for .NET: Ladda ner och installera GroupDocs.Watermark for .NET-biblioteket från[släpp sida](https://releases.groupdocs.com/Watermark/net/).
3. Ett PDF-dokument: Ha ett PDF-dokument med bilder redo för att testa vattenmärkningsfunktionen.
4.  Tillfällig licens: Skaffa en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/) om du utvärderar produkten.
## Importera namnområden
Se först till att du har de nödvändiga namnrymden importerade i ditt projekt. Detta kommer att inkludera de centrala namnutrymmen som krävs för att arbeta med PDF-dokument och vattenstämplar.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ställ in dokumentsökväg och utdatakatalog
För att börja, definiera sökvägarna för inmatningsdokumentet och utdatakatalogen där det vattenmärkta dokumentet ska sparas. Det här steget är avgörande för att säkerställa att ditt program vet var man hittar källdokumentet och var den bearbetade filen ska lagras.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Steg 2: Ladda PDF-dokumentet
 Därefter måste du ladda PDF-dokumentet med`PdfLoadOptions`. Den här klassen låter dig ange alternativ för att ladda PDF-filen, till exempel lösenordsskydd vid behov.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din kod för vattenmärkning kommer hit
}
```
## Steg 3: Skapa vattenstämpeln
Initiera nu vattenstämpeln. I det här exemplet skapar vi en textvattenstämpel som läser "Skyddad bild". Anpassa teckensnitt, justering, rotation och skalning efter dina behov.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Steg 4: Få åtkomst till PDF-innehåll
Hämta innehållet i PDF-dokumentet. Specifikt måste vi komma åt bilderna i PDF:en. Här fokuserar vi på den första sidan, men du kan utöka den till andra sidor efter behov.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Få alla bilder från första sidan
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Steg 5: Applicera vattenstämpeln på bilder
Gå igenom varje bild som finns på första sidan och applicera vattenstämpeln. Detta säkerställer att alla bilder på den angivna sidan kommer att ha vattenstämpeln applicerad.
```csharp
// Lägg till vattenstämpel till alla hittade bilder
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Steg 6: Spara det vattenmärkta dokumentet
Slutligen, spara den vattenmärkta PDF-filen i den angivna utdatakatalogen. Detta steg avslutar processen genom att skriva ändringarna till en ny fil.
```csharp
watermarker.Save(outputFileName);
```
## Slutsats
Och där har du det! Att lägga till en vattenstämpel till bilder i en PDF med hjälp av GroupDocs Watermark för .NET är en enkel process som avsevärt kan förbättra säkerheten och äktheten för dina dokument. Genom att följa dessa steg kan du säkerställa att din immateriella egendom är skyddad och att dina dokument är säkra.
## FAQ's
### Vad är GroupDocs.Watermark för .NET?
GroupDocs.Watermark for .NET är ett omfattande bibliotek som låter utvecklare lägga till, söka och ta bort vattenstämplar i olika dokumentformat, inklusive PDF-filer.
### Kan jag lägga till både text- och bildvattenstämplar med GroupDocs.Watermark?
Ja, GroupDocs.Watermark stöder både text- och bildvattenstämplar, vilket ger flexibilitet för olika typer av vattenmärkningsbehov.
### Är det möjligt att vattenmärka flera sidor i en PDF?
Absolut! Du kan gå igenom varje sida i PDF:en och använda vattenstämplar på bilder på varje sida.
### Behöver jag en licens för att använda GroupDocs.Watermark för .NET?
 Ja, en licens krävs. Du kan få en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/) i utvärderingssyfte.
### Var kan jag hitta mer dokumentation om GroupDocs.Watermark for .NET?
 Du kan hitta omfattande dokumentation på[GroupDocs.Watermark dokumentationssida](https://reference.groupdocs.com/Watermark/net/).