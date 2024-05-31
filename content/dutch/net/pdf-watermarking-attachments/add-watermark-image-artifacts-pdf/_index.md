---
title: Voeg watermerk toe aan afbeeldingsartefacten in PDF
linktitle: Voeg watermerk toe aan afbeeldingsartefacten in PDF
second_title: GroupDocs.Watermark .NET API
description: Bescherm uw PDF-bestanden met gepersonaliseerde watermerken met GroupDocs.Watermark voor .NET. Voeg eenvoudig tekst- of afbeeldingswatermerken toe aan afbeeldingsartefacten in PDF-documenten.
type: docs
weight: 18
url: /nl/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Invoering
In deze zelfstudie begeleiden we u bij het toevoegen van een watermerk aan afbeeldingsartefacten in een PDF-document met behulp van GroupDocs.Watermark voor .NET. Door deze stappen te volgen, kunt u uw PDF-bestanden efficiënt beschermen met gepersonaliseerde watermerken.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Watermark voor .NET: Download en installeer de GroupDocs.Watermark voor .NET-bibliotheek van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Documentpad: Geef het pad op naar het PDF-document waaraan u het watermerk wilt toevoegen.
3. Uitvoermap: maak een map waarin het document met een watermerk wordt opgeslagen.

## Naamruimten importeren
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het document en initialiseer de watermerker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Stap 2: ontvang PDF-inhoud en voeg een watermerk toe
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Initialiseer een afbeeldings- of tekstwatermerk
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
				// Voeg een watermerk toe aan de afbeelding
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Stap 3: Sla het document met watermerk op
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusie
Met GroupDocs.Watermark voor .NET wordt het toevoegen van watermerken aan afbeeldingsartefacten in PDF-documenten een naadloos proces. Door deze tutorial te volgen, kunt u uw PDF-bestanden efficiënt beschermen met aangepaste watermerken, waardoor de veiligheid en authenticiteit ervan wordt gegarandeerd.
## Veelgestelde vragen
### Kan ik zowel afbeeldings- als tekstwatermerken aan mijn PDF-document toevoegen?
Ja, GroupDocs.Watermark voor .NET ondersteunt het gelijktijdig toevoegen van zowel afbeeldings- als tekstwatermerken.
### Is er een beperking op het aantal watermerken dat ik aan een document kan toevoegen?
Nee, u kunt zonder enige beperking meerdere watermerken aan een document toevoegen.
### Kan ik het uiterlijk en de positie van het watermerk aanpassen?
Absoluut, u heeft volledige controle over het uiterlijk, de positie en de eigenschappen van het watermerk.
### Ondersteunt GroupDocs.Watermark voor .NET naast PDF ook andere documentformaten?
Ja, het ondersteunt verschillende documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is er een manier om watermerken uit een document te verwijderen?
Ja, GroupDocs.Watermark voor .NET biedt methoden om indien nodig watermerken uit documenten te verwijderen.