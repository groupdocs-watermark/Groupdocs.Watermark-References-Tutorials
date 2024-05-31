---
title: Voeg een watermerk toe aan alle bijlagen in PDF
linktitle: Voeg een watermerk toe aan alle bijlagen in PDF
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken aan PDF-bijlagen kunt toevoegen met GroupDocs.Watermark voor .NET. Beveilig uw documenten eenvoudig met aangepaste watermerken.
type: docs
weight: 16
url: /nl/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Invoering
Het toevoegen van watermerken aan PDF-bijlagen kan een cruciale stap zijn in documentbeheer, vooral als het gaat om het garanderen van beveiliging of branding. GroupDocs.Watermark voor .NET biedt een uitgebreide oplossing voor het naadloos insluiten van watermerken in PDF-bestanden. In deze zelfstudie begeleiden we u bij het toevoegen van een watermerk aan alle bijlagen in een PDF-document met GroupDocs.Watermark voor .NET.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1.  GroupDocs.Watermark voor .NET: Als u dat nog niet heeft gedaan, download en installeer dan GroupDocs.Watermark voor .NET vanaf de[website](https://releases.groupdocs.com/Watermark/net/).
2. Ontwikkelomgeving: Zet een geschikte ontwikkelomgeving op met Visual Studio of een andere .NET-compatibele IDE.
3. PDF-document: bereid het PDF-document voor waaraan u watermerken wilt toevoegen, samen met de bijlagen die u van een watermerk wilt voorzien.

## Naamruimten importeren
Voordat u in de code duikt, moet u ervoor zorgen dat u de benodigde naamruimten importeert om toegang te krijgen tot GroupDocs.Watermark voor .NET-functionaliteiten:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Definieer het documentpad en de uitvoermap
Definieer eerst het pad naar uw invoer-PDF-document en de map waar het document met een watermerk zal worden opgeslagen:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Stap 2: Initialiseer laadopties en watermerk
Initialiseer vervolgens de laadopties voor het PDF-document en maak een tekstwatermerk:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Stap 3: Document en bijlagen laden
Laad het PDF-document en doorloop de bijlagen:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Stap 4: Controleer de bijlageondersteuning
Controleer of het bijgevoegde bestand wordt ondersteund door GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Stap 5: voeg een watermerk toe aan bijlagen
Laad het bijgevoegde document en voeg het watermerk toe:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Stap 6: Wijzigingen opslaan
Sla ten slotte de wijzigingen in het PDF-document met watermerk op:
```csharp
    watermarker.Save(outputFileName);
}
```

## Conclusie
In deze zelfstudie hebben we onderzocht hoe u watermerken kunt toevoegen aan alle bijlagen in een PDF-document met GroupDocs.Watermark voor .NET. Door de stapsgewijze handleiding te volgen, kunt u watermerken naadloos in uw PDF-bestanden integreren, waardoor de documentbeveiliging en branding worden gegarandeerd.
## Veelgestelde vragen
### Kan ik het uiterlijk van het watermerk aanpassen?
Ja, u kunt verschillende aspecten, zoals tekst, lettertype, grootte, kleur en positie van het watermerk, aanpassen aan uw wensen.
### Ondersteunt GroupDocs.Watermark naast PDF ook andere documentformaten?
Ja, GroupDocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder Microsoft Word, Excel, PowerPoint, Visio, Outlook en Afbeeldingen.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark?
Ja, u kunt de functies van GroupDocs.Watermark verkennen door de gratis proefversie van de website te downloaden.
### Kan ik meerdere watermerken aan één document toevoegen?
Absoluut, met GroupDocs.Watermark kunt u meerdere watermerken tegelijkertijd toevoegen, inclusief tekst, afbeelding en annotaties, om de documentbeveiliging en branding te verbeteren.
### Is er technische ondersteuning beschikbaar voor GroupDocs.Watermark-gebruikers?
Ja, GroupDocs biedt uitgebreide technische ondersteuning via forums en speciale ondersteuningskanalen om gebruikers te helpen met eventuele vragen of problemen die ze tegenkomen.