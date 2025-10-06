---
title: Voeg watermerk toe aan afbeeldingen in PDF
linktitle: Voeg watermerk toe aan afbeeldingen in PDF
second_title: GroupDocs.Watermark .NET API
description: Leer watermerken toevoegen aan afbeeldingen in PDF-documenten met GroupDocs.Watermark voor .NET met onze gedetailleerde, stapsgewijze zelfstudie. Beveilig uw PDF's eenvoudig.
weight: 19
url: /nl/net/pdf-watermarking-attachments/add-watermark-images-pdf/
type: docs
---
# Voeg watermerk toe aan afbeeldingen in PDF

## Invoering
Het toevoegen van watermerken aan afbeeldingen in een PDF-document kan essentieel zijn voor het beschermen van uw intellectuele eigendom of het garanderen van de authenticiteit van uw documenten. Met GroupDocs.Watermark voor .NET kan deze taak efficiënt en gemakkelijk worden uitgevoerd. Deze tutorial begeleidt u bij elke stap van het proces, van het instellen van uw omgeving tot het toevoegen van watermerken en het opslaan van het definitieve document. Laten we erin duiken!
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1. Visual Studio: Installeer Visual Studio, de Integrated Development Environment (IDE) voor .NET-applicaties.
2.  GroupDocs.Watermark voor .NET: Download en installeer de GroupDocs.Watermark voor .NET-bibliotheek vanaf de[pagina vrijgeven](https://releases.groupdocs.com/Watermark/net/).
3. Een PDF-document: Zorg ervoor dat u een PDF-document met afbeeldingen gereed heeft om de watermerkfunctionaliteit te testen.
4.  Tijdelijke licentie: verkrijg een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) als u het product evalueert.
## Naamruimten importeren
Zorg er eerst voor dat de benodigde naamruimten in uw project zijn geïmporteerd. Dit omvat de kernnaamruimten die nodig zijn om met PDF-documenten en watermerken te werken.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Stel het documentpad en de uitvoermap in
Definieer om te beginnen de paden voor het invoerdocument en de uitvoermap waar het document met een watermerk zal worden opgeslagen. Deze stap is cruciaal om ervoor te zorgen dat uw programma weet waar het het brondocument kan vinden en waar het verwerkte bestand moet worden opgeslagen.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Stap 2: Laad het PDF-document
 Vervolgens moet u het PDF-document laden met behulp van`PdfLoadOptions`. Met deze klasse kunt u opties opgeven voor het laden van de PDF, zoals wachtwoordbeveiliging indien nodig.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Uw code voor watermerken komt hier terecht
}
```
## Stap 3: Maak het watermerk
Initialiseer nu het watermerk. In dit voorbeeld maken we een tekstwatermerk met de tekst 'Beveiligde afbeelding'. Pas het lettertype, de uitlijning, de rotatie en de schaling aan uw behoeften aan.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Stap 4: Toegang tot PDF-inhoud
Haal de inhoud van het PDF-document op. Concreet hebben we toegang nodig tot de afbeeldingen in de PDF. Hier concentreren we ons op de eerste pagina, maar u kunt dit indien nodig uitbreiden naar andere pagina's.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Haal alle afbeeldingen van de eerste pagina op
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Stap 5: Pas het watermerk toe op afbeeldingen
Loop door elke afbeelding op de eerste pagina en pas het watermerk toe. Dit zorgt ervoor dat op alle afbeeldingen op de opgegeven pagina het watermerk wordt toegepast.
```csharp
// Voeg een watermerk toe aan alle gevonden afbeeldingen
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Stap 6: Bewaar het document met watermerk
Sla ten slotte de PDF met watermerk op in de opgegeven uitvoermap. Met deze stap wordt het proces afgerond door de wijzigingen naar een nieuw bestand te schrijven.
```csharp
watermarker.Save(outputFileName);
```
## Conclusie
En daar heb je het! Het toevoegen van een watermerk aan afbeeldingen in een PDF met behulp van GroupDocs voor .NET is een eenvoudig proces dat de veiligheid en authenticiteit van uw documenten aanzienlijk kan verbeteren. Door deze stappen te volgen, kunt u ervoor zorgen dat uw intellectuele eigendom wordt beschermd en dat uw documenten veilig zijn.
## Veelgestelde vragen
### Wat is GroupDocs.Watermark voor .NET?
GroupDocs.Watermark voor .NET is een uitgebreide bibliotheek waarmee ontwikkelaars watermerken in verschillende documentformaten, waaronder PDF's, kunnen toevoegen, zoeken en verwijderen.
### Kan ik zowel tekst- als afbeeldingswatermerken toevoegen met GroupDocs.Watermark?
Ja, GroupDocs.Watermark ondersteunt zowel tekst- als afbeeldingswatermerken, waardoor flexibiliteit wordt geboden voor verschillende soorten watermerkbehoeften.
### Is het mogelijk om meerdere pagina's in een PDF van een watermerk te voorzien?
Absoluut! U kunt door elke pagina in de PDF bladeren en watermerken op afbeeldingen op elke pagina toepassen.
### Heb ik een licentie nodig om GroupDocs.Watermark voor .NET te gebruiken?
 Ja, een licentie is vereist. U kunt een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) voor evaluatiedoeleinden.
### Waar kan ik meer documentatie vinden over GroupDocs.Watermark voor .NET?
 Uitgebreide documentatie vindt u op de website[GroupDocs.Watermark documentatiepagina](https://tutorials.groupdocs.com/Watermark/net/).