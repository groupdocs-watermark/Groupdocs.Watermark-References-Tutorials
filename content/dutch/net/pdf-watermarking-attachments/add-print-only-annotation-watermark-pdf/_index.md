---
title: Voeg alleen print-annotatiewatermerk toe aan PDF
linktitle: Voeg alleen print-annotatiewatermerk toe aan PDF
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u alleen-afdrukbare annotatiewatermerken aan PDF's kunt toevoegen met GroupDocs.Watermark voor .NET. Verbeter moeiteloos documentbeveiliging en branding.
weight: 13
url: /nl/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Voeg alleen print-annotatiewatermerk toe aan PDF

## Invoering
In deze zelfstudie gaan we dieper in op het proces van het toevoegen van een alleen-afdrukbaar annotatiewatermerk aan een PDF met behulp van GroupDocs.Watermark voor .NET. Het watermerken van documenten is een cruciaal aspect van documentbeveiliging en branding, en GroupDocs.Watermark biedt een naadloze oplossing voor .NET-ontwikkelaars om dit te bereiken.
## Vereisten
Voordat we aan de slag gaan, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
- Basiskennis van de programmeertaal C#.
- Visual Studio is op uw computer geïnstalleerd.
- GroupDocs.Watermark voor .NET-bibliotheek geïnstalleerd in uw project.

## Naamruimten importeren
Zorg er om te beginnen voor dat u de benodigde naamruimten importeert:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad het document
 Eerst moet u het PDF-document laden dat u van een watermerk wilt voorzien. Vervangen`"Your Document Path"` met het pad naar uw PDF-bestand en`"Your Document Directory"` met de map waarin u het uitvoerbestand wilt opslaan.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Hier wordt de watermerkcode toegevoegd
}
```
## Stap 2: voeg een watermerk toe
Maak vervolgens een tekstwatermerkobject met de gewenste tekst en lettertype. Set`isPrintOnly` naar`true` om ervoor te zorgen dat het watermerk alleen zichtbaar is wanneer het document wordt afgedrukt, en niet in de weergavemodus.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Stap 3: Configureer watermerkopties
Definieer opties voor het watermerk, zoals de pagina-index waar het watermerk moet worden toegevoegd en geef dit op als annotatie die alleen kan worden afgedrukt.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Stap 4: Watermerk toepassen
Voeg het watermerk toe aan het document met behulp van de opgegeven opties en sla het uitvoerbestand op.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u een alleen-afdrukbaar annotatiewatermerk aan een PDF-document kunt toevoegen met GroupDocs.Watermark voor .NET. Hierdoor kunnen ontwikkelaars de documentbeveiliging en branding eenvoudig verbeteren.
## Veelgestelde vragen
### Is GroupDocs.Watermark compatibel met andere documentformaten dan PDF?
Ja, GroupDocs Watermark ondersteunt verschillende documentformaten zoals Word, Excel, PowerPoint en afbeeldingen.
### Kan ik het uiterlijk van het watermerk aanpassen?
Zeker, GroupDocs.Watermark biedt uitgebreide opties om watermerktekst, lettertype, kleur, grootte en positionering aan te passen.
### Biedt GroupDocs.Watermark mogelijkheden voor batchverwerking?
Absoluut, ontwikkelaars kunnen meerdere documenten tegelijkertijd van een watermerk voorzien met behulp van batchverwerkingsfuncties.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark?
Ja, u kunt via de meegeleverde link toegang krijgen tot een gratis proefversie van GroupDocs.Watermark.
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Watermark?
U kunt technische hulp zoeken op het GroupDocs.Watermark-forum dat beschikbaar is via de meegeleverde ondersteuningslink.