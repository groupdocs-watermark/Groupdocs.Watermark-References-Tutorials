---
title: Voeg watermerk toe aan XObjects in PDF
linktitle: Voeg watermerk toe aan XObjects in PDF
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken aan XObjects in PDF kunt toevoegen met Groupdocs.Watermark voor .NET. Volg onze stapsgewijze handleiding voor een eenvoudige implementatie.
type: docs
weight: 20
url: /nl/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Invoering
Het watermerken van PDF's is een cruciale stap om ervoor te zorgen dat uw documenten worden beschermd tegen ongeoorloofd gebruik. Met Groupdocs.Watermark voor .NET is het toevoegen van watermerken aan XObjects in uw PDF's nog nooit zo eenvoudig geweest. In deze zelfstudie leiden we u stap voor stap door het proces, zodat u vol vertrouwen watermerken op uw PDF-documenten kunt toepassen. Laten we beginnen!
## Vereisten
Voordat we in de tutorial duiken, zorgen we ervoor dat je alles hebt wat je nodig hebt om naadloos te kunnen volgen:
-  Groupdocs.Watermark voor .NET: Download en installeer de nieuwste versie van[hier](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Zorg ervoor dat .NET Framework op uw ontwikkelmachine is geïnstalleerd.
- Ontwikkelomgeving: Gebruik Visual Studio of een andere IDE die .NET-ontwikkeling ondersteunt.
-  Tijdelijke licentie: verkrijg een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) als u het product evalueert.
Zodra u aan deze vereisten voldoet, bent u klaar om uw PDF's van een watermerk te voorzien.
## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw project importeren. Open uw C#-project en voeg het volgende toe met behulp van richtlijnen:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Stel uw documentpaden in
De eerste stap omvat het instellen van de paden voor uw document. Definieer het pad waar uw PDF zich bevindt en waar u de PDF met watermerk wilt opslaan.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Path"` En`"Your Document Directory"` met de daadwerkelijke paden op uw machine.
## Stap 2: Initialiseer de PDF-laadopties
Vervolgens moet u de laadopties voor de PDF initialiseren. Dit is cruciaal voor het correct laden van de PDF-inhoud.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Stap 3: Laad het PDF-document
Gebruik de laadopties om het PDF-document te laden met de`Watermarker` klas.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Stap 4: Maak het watermerk
Nu moet u het watermerk maken dat aan de PDF wordt toegevoegd. Voor deze zelfstudie maken we een tekstwatermerk.
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
## Stap 5: voeg een watermerk toe aan XObjects
Blader door elke pagina en elk XObject in de PDF om het watermerk toe te passen.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Voeg een watermerk toe aan de afbeelding
            xObject.Image.Add(watermark);
        }
    }
}
```
## Stap 6: Sla de PDF met watermerk op
Sla ten slotte de PDF met watermerk op in het opgegeven uitvoerbestand.
```csharp
    watermarker.Save(outputFileName);
}
```
En daar heb je het! Uw PDF bevat nu watermerken op al zijn XObjects.
## Conclusie
 Het toevoegen van watermerken aan uw PDF-documenten met behulp van Groupdocs voor .NET is een eenvoudig proces dat een extra beveiligingslaag biedt. Door de stappen in deze zelfstudie te volgen, kunt u ervoor zorgen dat uw documenten worden beschermd tegen ongeoorloofd gebruik. Vergeet niet dat u altijd kunt verwijzen naar de[documentatie](https://reference.groupdocs.com/Watermark/net/) voor meer gedetailleerde informatie en geavanceerde functies.
## Veelgestelde vragen
### Kan ik een afbeelding als watermerk gebruiken in plaats van tekst?
Ja, Groupdocs.Watermark voor .NET ondersteunt zowel tekst- als afbeeldingswatermerken.
### Hoe kan ik Groupdocs.Watermark testen zonder het te kopen?
 U kunt gebruik maken van een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) om het product te beoordelen.
### Is het mogelijk om het uiterlijk van het watermerk aan te passen?
Absoluut! U kunt het lettertype, de grootte, de rotatiehoek en meer aanpassen.
### Ondersteunt Groupdocs.Watermark andere documentformaten?
Ja, het ondersteunt verschillende formaten, waaronder Word, Excel en PowerPoint.
### Waar kan ik ondersteuning krijgen als ik problemen tegenkom?
 U kunt ondersteuning krijgen van de[Groupdocs-forum](https://forum.groupdocs.com/c/watermark/19).