---
title: Document uit stroom laden
linktitle: Document uit stroom laden
second_title: GroupDocs.Watermark .NET API
description: Leer in deze handleiding hoe u watermerken aan documenten kunt toevoegen met GroupDocs.Watermark voor .NET. Perfect voor ontwikkelaars die de documentbeveiliging willen verbeteren.
weight: 11
url: /nl/net/document-loadings/load-document-from-stream/
---
## Invoering
Wilt u naadloos watermerken aan uw documenten toevoegen met behulp van .NET? Zoek niet verder! GroupDocs.Watermark voor .NET is een krachtige en gebruiksvriendelijke bibliotheek waarmee u watermerken in verschillende documentformaten kunt beheren. Of u nu met PDF's, Word-documenten of afbeeldingen werkt, met deze tool zit u goed. In deze zelfstudie leiden we u stap voor stap door het proces van het laden van een document uit een stream en het toevoegen van een watermerk. Dus laten we er meteen in duiken!
## Vereisten
Voordat we beginnen, zorg ervoor dat u het volgende heeft ingesteld:
1. Visual Studio: Elke recente versie van Visual Studio werkt prima.
2. .NET Framework: Zorg ervoor dat .NET Framework 4.0 of hoger is geïnstalleerd.
3.  GroupDocs.Watermark voor .NET: u kunt het downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).
4. Basiskennis van C#: Bekendheid met C# en objectgeoriënteerde programmeerconcepten zal nuttig zijn.

## Naamruimten importeren
Om GroupDocs.Watermark in uw project te gebruiken, moet u de benodigde naamruimten importeren. Hierdoor heeft u zonder problemen toegang tot de functies van de bibliotheek.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Stap 1: Uw project opzetten
Allereerst moet u uw project in Visual Studio instellen. Zo doe je het:
1. Maak een nieuw project: Open Visual Studio en maak een nieuw C# Console Application-project.
2.  Installeer GroupDocs.Watermark: Installeer de GroupDocs.Watermark-bibliotheek via NuGet Package Manager. Zoek eenvoudigweg naar`GroupDocs.Watermark` en installeer het.
## Stap 2: Documentpaden definiëren
Vervolgens moet u de paden voor uw document en het uitvoerbestand definiëren waar het document met een watermerk zal worden opgeslagen.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Path"` met het daadwerkelijke pad van het document dat u van een watermerk wilt voorzien`"Your Document Directory"` met de map waarin u het document met een watermerk wilt opslaan.
## Stap 3: Laad het document uit een stream
Laten we nu het document vanuit een stream laden. Dit houdt in dat u het document als een stream opent en vervolgens de`Watermarker` klasse uit de GroupDocs.Watermark-bibliotheek om deze te beheren.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Uw code om watermerken te beheren komt hier terecht
}
```
 Dit codefragment zorgt ervoor dat het document als stream wordt geopend en de`Watermarker` klasse wordt geïnitialiseerd met deze stream. De`using` Verklaringen zorgen ervoor dat middelen na gebruik op de juiste manier worden afgevoerd.
## Stap 4: Maak een watermerk en voeg het toe
Het maken van een watermerk is eenvoudig met GroupDocs.Watermark. In dit voorbeeld maken we een eenvoudig tekstwatermerk.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Hier creëren we een`TextWatermark` object met de tekst "Testwatermerk" en geef de lettertypedetails op. Vervolgens voegen we dit watermerk aan het document toe met behulp van de`Add` werkwijze van de`Watermarker` klas.
## Stap 5: Bewaar het document met watermerk
Sla ten slotte het document met een watermerk op in het opgegeven uitvoerpad.
```csharp
watermarker.Save(outputFileName);
```
 Met deze code wordt het document opgeslagen met het nieuw toegevoegde watermerk`outputFileName` pad dat u eerder hebt gedefinieerd.

## Conclusie
Gefeliciteerd! U hebt met succes een watermerk aan uw document toegevoegd met GroupDocs.Watermark voor .NET. Deze bibliotheek maakt het ongelooflijk eenvoudig om watermerken in verschillende documentformaten te beheren. Of u nu tekst, afbeeldingen of andere soorten watermerken moet toevoegen, GroupDocs.Watermark heeft de tools die u nodig heeft. Vergeet niet een kijkje te nemen op de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) voor meer geavanceerde functies en aanpassingsmogelijkheden.
## Veelgestelde vragen
### Welke soorten watermerken kan ik toevoegen met GroupDocs.Watermark voor .NET?
U kunt tekstwatermerken, afbeeldingswatermerken en zelfs complexe vormen en logo's toevoegen. De bibliotheek ondersteunt een breed scala aan aanpassingsopties.
### Kan ik watermerken uit documenten verwijderen met GroupDocs.Watermark?
Ja, met GroupDocs.Watermark kunt u ook bestaande watermerken uit documenten verwijderen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Watermark?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Hoe koop ik een licentie voor GroupDocs.Watermark?
 kunt een licentie rechtstreeks bij de[GroupDocs-website](https://purchase.groupdocs.com/buy).
### Waar kan ik ondersteuning krijgen als ik problemen tegenkom?
 Voor ondersteuning kunt u terecht op de[GroupDocs.Watermark-ondersteuningsforum](https://forum.groupdocs.com/c/watermark/19).