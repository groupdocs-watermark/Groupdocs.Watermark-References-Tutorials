---
title: Lägg till vattenstämpel till bildartefakter i PDF
linktitle: Lägg till vattenstämpel till bildartefakter i PDF
second_title: GroupDocs.Watermark .NET API
description: Skydda dina PDF-filer med personliga vattenstämplar med GroupDocs.Watermark för .NET. Lägg enkelt till text- eller bildvattenstämplar till bildartefakter i PDF-dokument.
weight: 18
url: /sv/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Introduktion
den här självstudien guidar vi dig genom processen att lägga till en vattenstämpel till bildartefakter i ett PDF-dokument med hjälp av GroupDocs.Watermark för .NET. Genom att följa dessa steg kan du effektivt skydda dina PDF-filer med personliga vattenstämplar.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1.  GroupDocs.Watermark for .NET: Ladda ner och installera GroupDocs.Watermark for .NET-biblioteket från[här](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentsökväg: Har sökvägen till PDF-dokumentet där du vill lägga till vattenstämpeln.
3. Utdatakatalog: Skapa en katalog där det vattenmärkta dokumentet kommer att sparas.

## Importera namnområden
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet och initiera vattenmärke
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Steg 2: Hämta PDF-innehåll och lägg till vattenstämpel
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Initiera bild eller text vattenstämpel
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Lägg till vattenstämpel på bilden
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Steg 3: Spara det vattenmärkta dokumentet
```csharp
	watermarker.Save(outputFileName);
}
```

## Slutsats
Med GroupDocs.Watermark för .NET blir det en sömlös process att lägga till vattenstämplar till bildartefakter i PDF-dokument. Genom att följa denna handledning kan du effektivt skydda dina PDF-filer med anpassade vattenstämplar, vilket säkerställer deras säkerhet och autenticitet.
## FAQ's
### Kan jag lägga till både bild- och textvattenstämplar i mitt PDF-dokument?
Ja, GroupDocs.Watermark för .NET stöder att lägga till både bild- och textvattenstämplar samtidigt.
### Finns det någon begränsning på antalet vattenstämplar jag kan lägga till i ett dokument?
Nej, du kan lägga till flera vattenstämplar i ett dokument utan några begränsningar.
### Kan jag anpassa utseendet och placeringen av vattenstämpeln?
Absolut, du har full kontroll över vattenstämpelns utseende, position och egenskaper.
### Stöder GroupDocs.Watermark for .NET andra dokumentformat än PDF?
Ja, det stöder olika dokumentformat inklusive Word, Excel, PowerPoint och mer.
### Finns det något sätt att ta bort vattenstämplar från ett dokument?
Ja, GroupDocs.Watermark för .NET tillhandahåller metoder för att ta bort vattenstämplar från dokument om det behövs.