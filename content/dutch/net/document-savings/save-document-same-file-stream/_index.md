---
title: Document opslaan in hetzelfde bestand of dezelfde stream
linktitle: Document opslaan in hetzelfde bestand of dezelfde stream
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken aan documenten kunt toevoegen met Groupdocs.Watermark voor .NET. Deze handleiding bevat instructies om de bescherming en integriteit van documenten te garanderen.
type: docs
weight: 10
url: /nl/net/document-savings/save-document-same-file-stream/
---
## Invoering
In het huidige digitale tijdperk is het toevoegen van watermerken aan documenten essentieel geworden voor het beschermen van intellectueel eigendom en het waarborgen van merkintegriteit. Groupdocs.Watermark voor .NET biedt een robuuste oplossing voor ontwikkelaars die watermerken naadloos in documenten willen insluiten. Deze uitgebreide handleiding leidt u door de stappen voor het opslaan van een document met een watermerk in hetzelfde bestand of dezelfde stream met Groupdocs.Watermark voor .NET.
## Vereisten
Voordat u in de zelfstudie duikt, moet u ervoor zorgen dat u over het volgende beschikt:
1. Ontwikkelomgeving: Visual Studio geïnstalleerd op uw machine.
2. .NET Framework: Zorg ervoor dat u .NET Framework 4.0 of hoger hebt.
3.  Groupdocs.Watermark voor .NET: Download en installeer de nieuwste versie van de[plaats](https://releases.groupdocs.com/Watermark/net/).
4.  Licentie: Verkrijg een tijdelijke of permanente licentie van[hier](https://purchase.groupdocs.com/temporary-license/).
## Naamruimten importeren
Om Groupdocs.Watermark in uw .NET-project te gaan gebruiken, moet u de benodigde naamruimten importeren:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Stap 1: Stel uw project in
Voordat we watermerken aan onze documenten toevoegen, moeten we ons .NET-project opzetten. Hier is hoe:
1. Maak een nieuw project: Open Visual Studio en maak een nieuwe consoletoepassing.
2. Groupdocs.Watermark-referentie toevoegen: Klik met de rechtermuisknop op het project in Solution Explorer, kies "NuGet-pakketten beheren" en installeer het Groupdocs.Watermark-pakket.
## Stap 2: Kopieer het document naar een nieuwe locatie
Om te voorkomen dat u het originele document rechtstreeks wijzigt, is het een goede gewoonte om het eerst naar een nieuwe locatie te kopiëren. Zo doe je het:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Stap 3: Initialiseer de watermerker
Nu we ons document hebben gekopieerd, kunnen we de klasse Watermarker initialiseren om ons watermerk toe te voegen:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Watermerken hoort hier
}
```
## Stap 4: Maak een tekstwatermerk en voeg het toe
Vervolgens maken we een tekstwatermerk en voegen dit toe aan ons document:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Stap 5: Sla het document op
Sla ten slotte het document op met het toegepaste watermerk:
```csharp
watermarker.Save();
```
## Conclusie
Het toevoegen van watermerken aan uw documenten met Groupdocs voor .NET is eenvoudig en efficiënt. Door de hierboven beschreven stappen te volgen, kunt u uw documenten beschermen en hun integriteit moeiteloos behouden. Voor meer details kunt u verwijzen naar de[documentatie](https://reference.groupdocs.com/Watermark/net/).
## Veelgestelde vragen
### Kan ik een afbeelding als watermerk gebruiken in plaats van tekst?
Ja, met Groupdocs.Watermark kunt u afbeeldingen, vormen en tekst als watermerken gebruiken.
### Hoe verwijder ik een watermerk uit een document?
 U kunt een watermerk verwijderen door naar de watermerkverzameling in het document te gaan en de knop te gebruiken`Remove` methode.
### Is het mogelijk om het uiterlijk van het watermerk aan te passen?
Absoluut. U kunt het lettertype, de grootte, de kleur en de positie van het watermerk aanpassen.
### Kan ik meerdere watermerken op één document toepassen?
 Ja, u kunt meerdere watermerken toevoegen door te bellen naar de`Add` methode meerdere keren met verschillende watermerkobjecten.
### Is Groupdocs.Watermark compatibel met alle documentformaten?
Groupdocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, PPTX en vele andere.