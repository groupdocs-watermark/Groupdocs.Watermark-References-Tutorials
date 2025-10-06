---
title: Document opslaan op opgegeven locatie
linktitle: Document opslaan op opgegeven locatie
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u eenvoudig watermerken aan uw documenten kunt toevoegen met GroupDocs.Watermark voor .NET met deze stapsgewijze handleiding. Verbeter de documentbeveiliging.
weight: 11
url: /nl/net/document-savings/save-document-specified-location/
type: docs
---
# Document opslaan op opgegeven locatie

## Invoering
In het digitale tijdperk is het beveiligen van documenten belangrijker dan ooit geworden. Watermerken zijn een effectieve manier om uw documenten te beschermen tegen ongeoorloofd gebruik. GroupDocs.Watermark voor .NET biedt een robuuste oplossing voor het toevoegen van watermerken aan uw documenten. Of u nu een ontwikkelaar bent die watermerken in uw toepassing wil integreren of iemand die geïnteresseerd is in het beveiligen van uw documenten: deze tutorial begeleidt u stap voor stap door het proces.
## Vereisten
Voordat u in de zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
- .NET-ontwikkelomgeving: Zorg ervoor dat Visual Studio of een andere .NET-ontwikkelomgeving is geïnstalleerd.
-  GroupDocs.Watermark voor .NET Library: Download en verwijs naar de bibliotheek in uw project.[Download GroupDocs.Watermark voor .NET](https://releases.groupdocs.com/Watermark/net/)
- Basiskennis van C#-programmeren: Het begrijpen van de basisconcepten van C#-programmeren zal nuttig zijn.
- Document naar watermerk: Houd een voorbeelddocument bij de hand waarop u het watermerk wilt toepassen.
## Naamruimten importeren
Voordat we met het voorbeeld beginnen, moet u de benodigde naamruimten importeren. Voeg de volgende gebruiksinstructies toe bovenaan uw codebestand:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Laten we het proces van het toevoegen van een watermerk aan een document met GroupDocs.Watermark voor .NET opsplitsen in beheersbare stappen. Volg deze stappen om met succes een watermerk toe te passen en uw document op een opgegeven locatie op te slaan.
## Stap 1: Stel uw project in
Begin met het maken van een nieuw .NET-project in Visual Studio. Voor de eenvoud kunt u een console-app kiezen.
1. Open Visuele Studio.
2.  Selecteer`File` >`New` >`Project`.
3.  Kiezen`Console App (.NET Core)` of`Console App (.NET Framework)`.
4.  Geef uw project een naam en klik`Create`.

## Stap 2: bereid uw document en watermerktekst voor
### Geef het documentpad op
Definieer het pad van het document dat u van een watermerk wilt voorzien. Laten we voor dit voorbeeld een plaatsaanduidingspad gebruiken.
```csharp
string documentPath = "Your Document Path";
```
### Definieer het uitvoerpad
Stel het uitvoerpad in waar u het document met een watermerk wilt opslaan.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Stap 3: Laad het document
 Gebruik de`Watermarker` klasse om uw document te laden. Deze klasse biedt methoden voor het toevoegen, verwijderen en bewerken van watermerken.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Voeg hier watermerklogica toe
}
```
## Stap 4: Maak een watermerk en voeg het toe

### Maak een tekstwatermerk
 Instantieer een`TextWatermark` object met de gewenste tekst- en lettertype-eigenschappen.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Voeg watermerk toe aan document
 Voeg het gemaakte watermerk toe aan uw document met behulp van de`Add` werkwijze van de`Watermarker` klas.
```csharp
watermarker.Add(watermark);
```
## Stap 5: Sla het document op
Sla ten slotte het document met het watermerk op de opgegeven locatie op.
```csharp
watermarker.Save(outputFileName);
```
## Conclusie
Het van een watermerk voorzien van uw documenten met GroupDocs Watermark voor .NET is een eenvoudig proces dat uw documentbeveiliging aanzienlijk kan verbeteren. Door deze stapsgewijze handleiding te volgen, kunt u eenvoudig watermerken aan uw documenten toevoegen en deze op de gewenste locatie opslaan. Of u nu intellectueel eigendom beschermt, de authenticiteit van documenten waarborgt of eenvoudigweg een professioneel tintje toevoegt, GroupDocs.Watermark voor .NET biedt de tools die u nodig heeft.
## Veelgestelde vragen
### Kan ik afbeeldingen als watermerken gebruiken met GroupDocs.Watermark voor .NET?
Ja, u kunt zowel tekst- als afbeeldingswatermerken gebruiken met GroupDocs Watermark voor .NET. De bibliotheek ondersteunt verschillende soorten watermerken om aan uw behoeften te voldoen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Watermark voor .NET?
 Ja, u kunt een gratis proefversie downloaden van de[website](https://releases.groupdocs.com/).
### Hoe kan ik een licentie kopen voor GroupDocs.Watermark voor .NET?
 U kunt een licentie aanschaffen bij de[aankooppagina](https://purchase.groupdocs.com/buy).
### Ondersteunt GroupDocs.Watermark voor .NET batchwatermerken?
Ja, u kunt meerdere documenten in een batchproces van een watermerk voorzien door een lijst met documenten te doorlopen en watermerken toe te passen.
### Waar kan ik ondersteuning krijgen voor GroupDocs.Watermark voor .NET?
 Ondersteuning is beschikbaar op de[GroupDocs-forum](https://forum.groupdocs.com/c/watermark/19).