---
title: Lägg till vattenstämpel till anteckningsbilder i PDF
linktitle: Lägg till vattenstämpel till anteckningsbilder i PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du skyddar dina PDF-dokument genom att lägga till vattenstämplar i anteckningsbilder med Groupdocs.Watermark for .NET.
weight: 17
url: /sv/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---

# Lägg till vattenstämpel till anteckningsbilder i PDF

## Introduktion
I den här handledningen kommer vi att undersöka hur du lägger till vattenstämplar till anteckningsbilder i PDF-dokument med Groupdocs.Watermark for .NET. Vattenmärkning är avgörande för att skydda dina dokument från obehörig användning eller distribution. Genom att följa den här steg-för-steg-guiden lär du dig hur du använder textvattenstämplar på anteckningsbilder i PDF-filer på ett effektivt sätt.
## Förutsättningar
Innan du fortsätter, se till att du har följande:
1. Grundläggande förståelse för programmeringsspråket C#.
2. Installerade Groupdocs.Watermark för .NET-biblioteket.
3. Tillgång till en utvecklingsmiljö som Visual Studio.
4. Ett PDF-dokument med anteckningsbilder till vattenstämpel.

## Importera namnområden
Först måste du importera de nödvändiga namnrymden till din C#-kod:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda PDF-dokumentet
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Steg 2: Hämta PDF-innehåll och initiera vattenstämpel
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Initiera bild eller text vattenstämpel
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Steg 3: Iterera genom PDF-sidor och anteckningsbilder
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Lägg till vattenstämpel på bilden
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Steg 4: Spara dokumentet med vattenstämpel
```csharp
    watermarker.Save(outputFileName);
}
```
När du har utfört dessa steg kommer ditt PDF-dokument att ha den angivna vattenstämpeln tillagd till anteckningsbilder.

## Slutsats
Att lägga till vattenstämplar till anteckningsbilder i PDF-filer är viktigt för att skydda dina dokuments integritet och säkerställa att de inte missbrukas. Med Groupdocs.Watermark för .NET blir denna process enkel och effektiv, vilket gör att du kan skydda dina PDF-filer effektivt.
## FAQ's
### Kan jag lägga till flera vattenstämplar i samma PDF-dokument?
Ja, du kan lägga till flera vattenstämplar i samma PDF-dokument med Groupdocs.Watermark for .NET.
### Stöder Groupdocs.Watermark andra dokumentformat än PDF?
Ja, Groupdocs Watermark stöder olika dokumentformat, inklusive Word, Excel, PowerPoint och mer.
### Är det möjligt att anpassa utseendet på vattenstämpeln?
Absolut, du kan anpassa text, teckensnitt, färg, storlek och placering av vattenstämpeln enligt dina önskemål.
### Kan jag ta bort vattenstämplar från PDF-dokument med Groupdocs.Watermark?
Ja, Groupdocs.Watermark tillhandahåller funktionalitet för att ta bort vattenstämplar från PDF-dokument utan ansträngning.
### Finns det någon gratis provversion tillgänglig för Groupdocs.Watermark för .NET?
Ja, du kan använda en gratis provversion av Groupdocs.Watermark för .NET från webbplatsen.