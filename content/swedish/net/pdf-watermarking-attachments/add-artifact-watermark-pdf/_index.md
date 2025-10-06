---
title: Lägg till Artifact Watermark till PDF
linktitle: Lägg till Artifact Watermark till PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till artefaktvattenstämplar till PDF-filer utan ansträngning med Groupdocs.Watermark for .NET. Skydda dina dokument med lätthet.
weight: 11
url: /sv/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
type: docs
---
# Lägg till Artifact Watermark till PDF

## Introduktion
Att lägga till vattenstämplar i PDF-filer är en avgörande aspekt av dokumenthantering, särskilt när det gäller att skydda immateriella rättigheter eller varumärkesdokument. Groupdocs.Watermark för .NET ger en robust lösning för att lägga till vattenstämplar till PDF-filer utan ansträngning. I den här handledningen går vi igenom processen att lägga till en artefaktvattenstämpel till PDF-filer steg för steg.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1.  Groupdocs.Watermark for .NET: Ladda ner och installera Groupdocs.Watermark for .NET från[här](https://releases.groupdocs.com/Watermark/net/).
2. Utvecklingsmiljö: Ha en .NET-utvecklingsmiljö inrättad.
3. PDF-dokument: Förbered PDF-dokumentet som du vill lägga till vattenstämpeln till.
4. Utdatakatalog: Skapa en katalog för att spara den vattenmärkta PDF-filen.

## Importera namnområden
Till att börja med, importera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using GroupDocs.Watermark.Common;
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
## Steg 2: Definiera vattenstämpelalternativ
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Steg 3: Lägg till textvattenstämpel
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Steg 4: Lägg till bildvattenstämpel
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Steg 5: Spara den vattenmärkta PDF-filen
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till artefaktvattenstämplar till PDF-filer med Groupdocs.Watermark for .NET. Genom att följa dessa steg kan du sömlöst integrera vattenmärkningsfunktioner i dina .NET-applikationer, vilket säkerställer säkerheten och integriteten för dina dokument.
## FAQ's
### Kan jag anpassa utseendet på textens vattenstämpel?
Ja, du kan anpassa olika aspekter som teckensnitt, storlek, färg och justering av textvattenstämpeln enligt dina preferenser.
### Stöder Groupdocs.Watermark att lägga till vattenstämplar i andra dokumentformat?
Ja, Groupdocs.Watermark stöder att lägga till vattenstämplar i ett brett utbud av dokumentformat inklusive Word, Excel, PowerPoint och mer.
### Finns det en testversion tillgänglig för Groupdocs.Watermark för .NET?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur kan jag få support för eventuella problem eller frågor relaterade till Groupdocs.Watermark?
 Du kan få support från Groupdocs communityforum[här](https://forum.groupdocs.com/c/watermark/19).
### Kan jag använda Groupdocs.Watermark för kommersiella ändamål?
Ja, du kan köpa en licens för kommersiellt bruk från[här](https://purchase.groupdocs.com/buy).