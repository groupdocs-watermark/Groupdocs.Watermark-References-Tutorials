---
title: Rasterisera PDF-sida
linktitle: Rasterisera PDF-sida
second_title: GroupDocs.Watermark .NET API
description: Förbättra dokumentsäkerheten med GroupDocs Watermark för .NET. Lägg till vattenstämplar till PDF och andra format utan problem.
weight: 28
url: /sv/net/pdf-watermarking-attachments/rasterize-pdf-page/
---

# Rasterisera PDF-sida

## Introduktion
GroupDocs.Watermark for .NET är ett kraftfullt API som gör det möjligt för utvecklare att sömlöst lägga till vattenstämplar i olika dokumentformat, inklusive PDF, Word, Excel, PowerPoint och mer. Med sitt intuitiva gränssnitt och omfattande funktioner förenklar GroupDocs.Watermark processen att lägga till text- eller bildvattenstämplar i dokument, vilket gör det möjligt för användare att skydda sina immateriella rättigheter och förbättra dokumentsäkerheten utan ansträngning.
## Förutsättningar
Innan du börjar använda GroupDocs.Watermark för .NET, se till att du har följande förutsättningar:
1. Installation: Ladda ner och installera GroupDocs.Watermark för .NET från[nedladdningssida](https://releases.groupdocs.com/Watermark/net/).
2.  Licens: Skaffa en licens för GroupDocs.Watermark för .NET. Du kan få en tillfällig licens för utvärderingsändamål från[här](https://purchase.groupdocs.com/temporary-license/) , eller köp en fullständig licens från[köpsidan](https://purchase.groupdocs.com/buy).
3. .NET Framework: Se till att du har .NET Framework installerat på din utvecklingsmaskin.
4. Dokument: Förbered dokumentet som du vill lägga till vattenstämplar till.

## Importera namnområden
För att börja använda GroupDocs.Watermark för .NET, importera de nödvändiga namnrymden till ditt projekt:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din kod kommer hit
}
```
## Steg 2: Initiera vattenstämpel
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Steg 3: Lägg till vattenstämpel
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Steg 4: Rasterisera sidan
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Steg 5: Spara dokumentet
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
Sammanfattningsvis erbjuder GroupDocs.Watermark för .NET en sömlös lösning för att lägga till vattenstämplar till PDF och andra dokumentformat. Genom att följa den steg-för-steg-guide som beskrivs ovan kan utvecklare effektivt rastrera PDF-sidor och förbättra dokumentsäkerheten med lätthet.
## FAQ's
### Är GroupDocs.Watermark kompatibel med andra dokumentformat förutom PDF?
Ja, GroupDocs.Watermark stöder ett brett utbud av dokumentformat, inklusive Word, Excel, PowerPoint, Visio och mer.
### Kan jag anpassa utseendet på vattenstämpeln som lagts till i dokumentet?
Absolut! GroupDocs.Watermark tillhandahåller omfattande anpassningsalternativ för text- och bildvattenstämplar, vilket gör att användarna kan justera teckensnitt, storlek, färg, opacitet och placering enligt deras preferenser.
### Är GroupDocs.Watermark lämplig för både personlig och kommersiell användning?
Ja, GroupDocs.Watermark erbjuder flexibla licensalternativ för att tillgodose både individuella och företags behov, vilket gör den lämplig för såväl personliga projekt som storskaliga kommersiella tillämpningar.
### Erbjuder GroupDocs.Watermark teknisk support för utvecklare?
Ja, utvecklare kan få tillgång till omfattande teknisk support via forumet GroupDocs.Watermark, där de kan söka hjälp, dela erfarenheter och engagera sig med andra utvecklare.
### Kan jag prova GroupDocs.Watermark innan jag köper?
Säkert! Du kan använda en gratis testversion av GroupDocs.Watermark från[släpper sida](https://releases.groupdocs.com/), så att du kan utforska dess funktioner och funktioner innan du förbinder dig till ett köp.