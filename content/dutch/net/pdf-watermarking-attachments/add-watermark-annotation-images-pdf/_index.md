---
title: Voeg een watermerk toe aan annotatieafbeeldingen in PDF
linktitle: Voeg een watermerk toe aan annotatieafbeeldingen in PDF
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u uw PDF-documenten kunt beveiligen door watermerken aan annotatieafbeeldingen toe te voegen met Groupdocs.Watermark voor .NET.
weight: 17
url: /nl/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u watermerken kunt toevoegen aan annotatieafbeeldingen in PDF-documenten met Groupdocs.Watermark voor .NET. Watermerken zijn van cruciaal belang om uw documenten te beschermen tegen ongeoorloofd gebruik of verspreiding. Door deze stapsgewijze handleiding te volgen, leert u hoe u tekstwatermerken effectief kunt toepassen op annotatieafbeeldingen in PDF's.
## Vereisten
Zorg ervoor dat u over het volgende beschikt voordat u doorgaat:
1. Basiskennis van de programmeertaal C#.
2. Groupdocs.Watermark voor .NET-bibliotheek geïnstalleerd.
3. Toegang tot een ontwikkelomgeving zoals Visual Studio.
4. Een PDF-document met annotatieafbeeldingen als watermerk.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-code importeren:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## Stap 2: PDF-inhoud ophalen en watermerk initialiseren
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Initialiseer een afbeeldings- of tekstwatermerk
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Stap 3: Blader door PDF-pagina's en annotatieafbeeldingen
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Voeg een watermerk toe aan de afbeelding
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Stap 4: Bewaar het document met watermerk
```csharp
    watermarker.Save(outputFileName);
}
```
Nadat u deze stappen heeft uitgevoerd, wordt aan uw PDF-document het opgegeven watermerk toegevoegd aan annotatieafbeeldingen.

## Conclusie
Het toevoegen van watermerken aan annotatieafbeeldingen in PDF's is essentieel om de integriteit van uw documenten te beschermen en ervoor te zorgen dat ze niet worden misbruikt. Met Groupdocs.Watermark voor .NET wordt dit proces eenvoudig en efficiënt, waardoor u uw PDF-bestanden effectief kunt beveiligen.
## Veelgestelde vragen
### Kan ik meerdere watermerken aan hetzelfde PDF-document toevoegen?
Ja, u kunt meerdere watermerken aan hetzelfde PDF-document toevoegen met Groupdocs.Watermark voor .NET.
### Ondersteunt Groupdocs.Watermark naast PDF ook andere documentformaten?
Ja, Groupdocs ondersteunt verschillende documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is het mogelijk om het uiterlijk van het watermerk aan te passen?
Absoluut, u kunt de tekst, het lettertype, de kleur, de grootte en de positie van het watermerk aanpassen aan uw voorkeuren.
### Kan ik watermerken uit PDF-documenten verwijderen met Groupdocs.Watermark?
Ja, Groupdocs.Watermark biedt functionaliteit om moeiteloos watermerken uit PDF-documenten te verwijderen.
### Is er een gratis proefversie beschikbaar voor Groupdocs.Watermark voor .NET?
Ja, u kunt via de website profiteren van een gratis proefversie van Groupdocs.Watermark voor .NET.