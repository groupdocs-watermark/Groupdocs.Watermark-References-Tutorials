---
title: Artefactwatermerk toevoegen aan PDF
linktitle: Artefactwatermerk toevoegen aan PDF
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u moeiteloos artefactwatermerken aan PDF-bestanden kunt toevoegen met Groupdocs.Watermark voor .NET. Bescherm uw documenten met gemak.
type: docs
weight: 11
url: /nl/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Invoering
Het toevoegen van watermerken aan PDF-bestanden is een cruciaal aspect van documentbeheer, vooral als het gaat om de bescherming van intellectueel eigendom of branding van documenten. Groupdocs.Watermark voor .NET biedt een robuuste oplossing voor het moeiteloos toevoegen van watermerken aan PDF-bestanden. In deze zelfstudie doorlopen we stap voor stap het proces van het toevoegen van een artefactwatermerk aan PDF-bestanden.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  Groupdocs.Watermark voor .NET: Download en installeer Groupdocs.Watermark voor .NET van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Ontwikkelomgeving: zorg dat u een .NET-ontwikkelomgeving hebt opgezet.
3. PDF-document: bereid het PDF-document voor waaraan u het watermerk wilt toevoegen.
4. Uitvoermap: maak een map om het PDF-bestand met watermerk op te slaan.

## Naamruimten importeren
Importeer om te beginnen de benodigde naamruimten in uw C#-project:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het PDF-document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Stap 2: Definieer watermerkopties
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Stap 3: tekstwatermerk toevoegen
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Stap 4: Voeg een afbeeldingswatermerk toe
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Stap 5: Sla de PDF met watermerk op
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u artefactwatermerken aan PDF-bestanden kunt toevoegen met Groupdocs.Watermark voor .NET. Door deze stappen te volgen, kunt u de watermerkfunctionaliteit naadloos integreren in uw .NET-toepassingen, waardoor de veiligheid en integriteit van uw documenten wordt gewaarborgd.
## Veelgestelde vragen
### Kan ik het uiterlijk van het tekstwatermerk aanpassen?
Ja, u kunt verschillende aspecten, zoals lettertype, grootte, kleur en uitlijning van het tekstwatermerk, aanpassen aan uw voorkeuren.
### Ondersteunt Groupdocs.Watermark het toevoegen van watermerken aan andere documentformaten?
Ja, Groupdocs.Watermark ondersteunt het toevoegen van watermerken aan een breed scala aan documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is er een proefversie beschikbaar voor Groupdocs.Watermark voor .NET?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor eventuele problemen of vragen met betrekking tot Groupdocs.Watermark?
 U kunt ondersteuning krijgen van het Groupdocs-communityforum[hier](https://forum.groupdocs.com/c/watermark/19).
### Kan ik Groupdocs.Watermark gebruiken voor commerciële doeleinden?
Ja, u kunt een licentie voor commercieel gebruik aanschaffen bij[hier](https://purchase.groupdocs.com/buy).