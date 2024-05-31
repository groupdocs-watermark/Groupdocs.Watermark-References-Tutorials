---
title: PDF-pagina rasteren
linktitle: PDF-pagina rasteren
second_title: GroupDocs.Watermark .NET API
description: Verbeter de documentbeveiliging met GroupDocs voor .NET. Voeg naadloos watermerken toe aan PDF en andere formaten.
type: docs
weight: 28
url: /nl/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## Invoering
GroupDocs.Watermark voor .NET is een krachtige API waarmee ontwikkelaars naadloos watermerken kunnen toevoegen aan verschillende documentformaten, waaronder PDF, Word, Excel, PowerPoint en meer. Met zijn intuïtieve interface en uitgebreide functies vereenvoudigt GroupDocs.Watermark het proces van het toevoegen van tekst- of afbeeldingswatermerken aan documenten, waardoor gebruikers hun intellectuele eigendom kunnen beschermen en de documentbeveiliging moeiteloos kunnen verbeteren.
## Vereisten
Voordat u GroupDocs.Watermark voor .NET gaat gebruiken, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Installatie: Download en installeer GroupDocs.Watermark voor .NET vanaf de[downloadpagina](https://releases.groupdocs.com/Watermark/net/).
2.  Licentie: verkrijg een licentie voor GroupDocs.Watermark voor .NET. U kunt een tijdelijke licentie voor evaluatiedoeleinden verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/) , of koop een volledige licentie van de[aankooppagina](https://purchase.groupdocs.com/buy).
3. .NET Framework: Zorg ervoor dat .NET Framework op uw ontwikkelmachine is geïnstalleerd.
4. Document: bereid het document voor waaraan u watermerken wilt toevoegen.

## Naamruimten importeren
Om GroupDocs.Watermark voor .NET te gaan gebruiken, importeert u de benodigde naamruimten in uw project:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Je code komt hier
}
```
## Stap 2: Initialiseer het watermerk
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Stap 3: voeg een watermerk toe
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Stap 4: De pagina rasteren
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Stap 5: Sla het document op
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
Concluderend biedt GroupDocs.Watermark voor .NET een naadloze oplossing voor het toevoegen van watermerken aan PDF en andere documentformaten. Door de hierboven beschreven stapsgewijze handleiding te volgen, kunnen ontwikkelaars PDF-pagina's efficiënt rasteren en de documentbeveiliging eenvoudig verbeteren.
## Veelgestelde vragen
### Is GroupDocs.Watermark compatibel met andere documentformaten dan PDF?
Ja, GroupDocs.Watermark ondersteunt een breed scala aan documentindelingen, waaronder Word, Excel, PowerPoint, Visio en meer.
### Kan ik het uiterlijk van het watermerk dat aan het document wordt toegevoegd, aanpassen?
Absoluut! GroupDocs.Watermark biedt uitgebreide aanpassingsopties voor tekst- en afbeeldingswatermerken, waardoor gebruikers het lettertype, de grootte, de kleur, de dekking en de positionering kunnen aanpassen aan hun voorkeuren.
### Is GroupDocs.Watermark geschikt voor zowel persoonlijk als commercieel gebruik?
Ja, GroupDocs.Watermark biedt flexibele licentieopties om tegemoet te komen aan zowel individuele als zakelijke behoeften, waardoor het geschikt is voor zowel persoonlijke projecten als grootschalige commerciële toepassingen.
### Biedt GroupDocs.Watermark technische ondersteuning voor ontwikkelaars?
Ja, ontwikkelaars hebben toegang tot uitgebreide technische ondersteuning via het GroupDocs.Watermark-forum, waar ze hulp kunnen zoeken, ervaringen kunnen delen en met collega-ontwikkelaars kunnen communiceren.
### Kan ik GroupDocs.Watermark uitproberen voordat ik een aankoop doe?
Zeker! U kunt gebruikmaken van een gratis proefversie van GroupDocs.Watermark van de[releases pagina](https://releases.groupdocs.com/), zodat u de kenmerken en functionaliteiten ervan kunt verkennen voordat u een aankoop doet.