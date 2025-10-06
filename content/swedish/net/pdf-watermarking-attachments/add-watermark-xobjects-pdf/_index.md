---
title: Lägg till vattenstämpel till XObjects i PDF
linktitle: Lägg till vattenstämpel till XObjects i PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar till XObjects i PDF med Groupdocs.Watermark for .NET. Följ vår steg-för-steg-guide för enkel implementering.
weight: 20
url: /sv/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# Lägg till vattenstämpel till XObjects i PDF

## Introduktion
Vattenmärka PDF-filer är ett avgörande steg för att säkerställa att dina dokument skyddas från obehörig användning. Med Groupdocs.Watermark för .NET har det aldrig varit enklare att lägga till vattenstämplar till XObjects i dina PDF-filer. I den här handledningen går vi igenom processen steg-för-steg, och säkerställer att du med säkerhet kan applicera vattenstämplar på dina PDF-dokument. Låt oss börja!
## Förutsättningar
Innan vi dyker in i handledningen, låt oss se till att du har allt du behöver för att följa med sömlöst:
-  Groupdocs.Watermark for .NET: Ladda ner och installera den senaste versionen från[här](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Se till att du har .NET Framework installerat på din utvecklingsmaskin.
- Utvecklingsmiljö: Använd Visual Studio eller någon annan IDE som stöder .NET-utveckling.
-  Tillfällig licens: Skaffa en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/) om du utvärderar produkten.
När du har dessa förutsättningar på plats är du redo att börja vattenmärka dina PDF-filer.
## Importera namnområden
Först måste du importera de nödvändiga namnrymden i ditt projekt. Öppna ditt C#-projekt och lägg till följande med hjälp av direktiv:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ställ in dina dokumentsökvägar
Det första steget innebär att ställa in sökvägarna för ditt dokument. Definiera sökvägen där din PDF-fil finns och var du vill spara den vattenmärkta PDF-filen.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` och`"Your Document Directory"` med de faktiska sökvägarna på din maskin.
## Steg 2: Initiera PDF-laddningsalternativ
Därefter måste du initiera PDF-laddningsalternativen. Detta är avgörande för att ladda PDF-innehållet korrekt.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Steg 3: Ladda PDF-dokumentet
Använd laddningsalternativen för att ladda PDF-dokumentet med`Watermarker` klass.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Steg 4: Skapa vattenstämpeln
Nu måste du skapa vattenstämpeln som kommer att läggas till i PDF:en. För den här handledningen skapar vi en textvattenstämpel.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Steg 5: Lägg till vattenstämpel till XObjects
Iterera genom varje sida och varje XObject i PDF-filen för att applicera vattenstämpeln.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Lägg till vattenstämpel på bilden
            xObject.Image.Add(watermark);
        }
    }
}
```
## Steg 6: Spara den vattenmärkta PDF-filen
Slutligen, spara den vattenmärkta PDF-filen till den angivna utdatafilen.
```csharp
    watermarker.Save(outputFileName);
}
```
Och där har du det! Din PDF innehåller nu vattenstämplar på alla dess XObjects.
## Slutsats
 Att lägga till vattenstämplar i dina PDF-dokument med Groupdocs Watermark för .NET är en enkel process som ger ett extra lager av säkerhet. Genom att följa stegen som beskrivs i den här handledningen kan du säkerställa att dina dokument skyddas från obehörig användning. Kom ihåg att du alltid kan hänvisa till[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) för mer detaljerad information och avancerade funktioner.
## FAQ's
### Kan jag använda en bild som vattenstämpel istället för text?
Ja, Groupdocs.Watermark för .NET stöder både text- och bildvattenstämplar.
### Hur kan jag testa Groupdocs.Watermark utan att köpa det?
 Du kan använda en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/) att utvärdera produkten.
### Är det möjligt att anpassa vattenstämpelns utseende?
Absolut! Du kan anpassa teckensnitt, storlek, rotationsvinkel och mer.
### Stöder Groupdocs.Watermark andra dokumentformat?
Ja, det stöder olika format, inklusive Word, Excel och PowerPoint.
### Var kan jag få support om jag stöter på problem?
 Du kan få stöd från[Groupdocs forum](https://forum.groupdocs.com/c/watermark/19).