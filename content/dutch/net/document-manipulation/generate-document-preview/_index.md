---
title: Documentvoorbeeld genereren
linktitle: Documentvoorbeeld genereren
second_title: GroupDocs.Watermark .NET API
description: Leer in deze handleiding hoe u documentvoorbeelden kunt genereren met GroupDocs.Watermark voor .NET. Verbeter moeiteloos uw documentbeveiliging en -beheer.
weight: 10
url: /nl/net/document-manipulation/generate-document-preview/
---

# Documentvoorbeeld genereren

## Invoering
In de wereld van digitaal documentbeheer speelt watermerken een cruciale rol bij het waarborgen van de veiligheid en authenticiteit van documenten. GroupDocs.Watermark voor .NET is een krachtige tool waarmee ontwikkelaars moeiteloos watermerken aan documenten kunnen toevoegen. In deze zelfstudie begeleiden we u bij het genereren van documentvoorbeelden met GroupDocs.Watermark voor .NET. Of u nu een doorgewinterde ontwikkelaar bent of net begint, deze handleiding biedt u een uitgebreid stapsgewijs proces om uw doel te bereiken.
## Vereisten
Voordat we ingaan op de implementatie, moeten we ervoor zorgen dat u alles heeft wat u nodig heeft om aan de slag te gaan:
- Een basiskennis van C# en .NET framework.
- Visual Studio is op uw computer geïnstalleerd.
- GroupDocs.Watermark voor .NET-bibliotheek. Jij kan[download het hier](https://releases.groupdocs.com/Watermark/net/).
-  Een geldige licentie voor GroupDocs.Watermark. Je kunt het kopen[hier](https://purchase.groupdocs.com/buy) of verkrijgen van een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) voor evaluatiedoeleinden.
## Naamruimten importeren
Om GroupDocs.Watermark in uw project te gaan gebruiken, moet u de benodigde naamruimten importeren. Dit kunt u doen door de volgende gebruiksinstructies aan uw code toe te voegen:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Deze naamruimten bieden toegang tot de klassen en methoden die nodig zijn voor het watermerken en het genereren van documentvoorbeelden.

Laten we het proces van het genereren van een documentvoorbeeld opsplitsen in eenvoudige, gemakkelijk te volgen stappen.
## Stap 1: Stel uw project in
Stel eerst uw .NET-project in Visual Studio in. Als u nog geen project heeft, kunt u een nieuw project maken door deze stappen te volgen:
1. Open Visuele Studio.
2. Klik op 'Een nieuw project maken'.
3. Selecteer 'Console-app (.NET Core)' en klik op 'Volgende'.
4. Geef uw project een naam, kies een locatie om het op te slaan en klik vervolgens op 'Maken'.
## Stap 2: Installeer GroupDocs.Watermark voor .NET
Om GroupDocs.Watermark in uw project te gebruiken, moet u de bibliotheek installeren. Dit kan gedaan worden met behulp van NuGet Package Manager:
1. Klik met de rechtermuisknop op uw project in de Solution Explorer.
2. Selecteer 'NuGet-pakketten beheren'.
3. Zoek naar "GroupDocs.Watermark" op het tabblad Bladeren.
4. Klik op "Installeren" om de bibliotheek aan uw project toe te voegen.
Als alternatief kunt u het installeren via de Package Manager Console:
```powershell
Install-Package GroupDocs.Watermark
```
## Stap 3: Definieer het documentpad en de uitvoermap
Voordat u het voorbeeld genereert, moet u het pad opgeven van het document waarvan u een voorbeeld wilt bekijken en de map waar de voorbeeldafbeeldingen worden opgeslagen:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Vervang "Uw documentpad" door het pad naar uw document en "Uw documentenmap" door de map waarin u de voorbeeldafbeeldingen wilt opslaan.
## Stap 4: Initialiseer het watermerkobject
Maak een exemplaar van de`Watermarker` klasse door het documentpad door te geven aan de constructor ervan. Dit object wordt gebruikt om alle watermerkbewerkingen uit te voeren:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Jouw code hier
}
```
## Stap 5: Maak gedelegeerde methoden voor streamafhandeling
Om de preview te genereren, moet u gedelegeerde methoden definiëren voor het maken en vrijgeven van streams. Deze methoden zorgen voor het maken en vrijgeven van streams voor elke pagina van het document:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 De`createPageStreamDelegate` methode creëert een stream voor elke pagina van het document, terwijl de`releasePageStreamDelegate` methode sluit de stream nadat het voorbeeld is gegenereerd.
## Stap 6: Configureer voorbeeldopties
 Configureer vervolgens de voorbeeldopties door een exemplaar van het`PreviewOptions` klas. Geef de gedelegeerde methoden op en stel het voorbeeldformaat in op PNG. U kunt ook opgeven welke pagina's u in het voorbeeld wilt opnemen:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
In dit voorbeeld genereren we voorbeelden voor de eerste twee pagina's van het document.
## Stap 7: Genereer het documentvoorbeeld
 Bel ten slotte de`GeneratePreview` methode op de`Watermarker`object, waarbij het geconfigureerde wordt doorgegeven`PreviewOptions`. Hiermee worden de voorbeeldafbeeldingen gegenereerd en opgeslagen in de opgegeven map:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Conclusie
Het genereren van documentvoorbeelden met GroupDocs.Watermark voor .NET is een eenvoudig proces dat met slechts een paar regels code kan worden uitgevoerd. Door de stappen in deze handleiding te volgen, kunt u eenvoudig uw project instellen, de benodigde opties configureren en voorbeelden voor uw documenten genereren. Deze krachtige bibliotheek vereenvoudigt niet alleen het watermerkproces, maar biedt ook robuuste functies voor het beheren en manipuleren van watermerken.
 Als u vragen heeft of verdere hulp nodig heeft, aarzel dan niet om een bezoek te brengen aan de[GroupDocs.Watermark-ondersteuningsforum](https://forum.groupdocs.com/c/watermark/19) of raadpleeg de[documentatie](https://tutorials.groupdocs.com/Watermark/net/).
## Veelgestelde vragen
### Welke bestandsformaten worden ondersteund door GroupDocs.Watermark voor .NET?
 GroupDocs.Watermark voor .NET ondersteunt een breed scala aan bestandsindelingen, waaronder PDF, DOCX, PPTX, XLSX en nog veel meer. Voor een volledige lijst met ondersteunde formaten raadpleegt u de[documentatie](https://tutorials.groupdocs.com/Watermark/net/).
### Kan ik het uiterlijk van watermerken aanpassen?
Ja, met GroupDocs.Watermark kunt u het uiterlijk van watermerken volledig aanpassen, inclusief tekst-, afbeeldings- en vormwatermerken. U kunt eigenschappen zoals lettertype, kleur, grootte en transparantie aanpassen.
### Is er een proefversie beschikbaar?
 Ja, u kunt een[gratis proefperiode](https://releases.groupdocs.com/) van GroupDocs.Watermark voor .NET om de functies ervan te evalueren voordat u een aankoop doet.
### Hoe kan ik een licentie kopen voor GroupDocs.Watermark?
 U kunt een licentie kopen voor GroupDocs.Watermark[hier](https://purchase.groupdocs.com/buy). Er zijn verschillende licentieopties beschikbaar om aan verschillende behoeften te voldoen.
### Kan ik GroupDocs.Watermark gebruiken in een commercieel project?
 Ja, met een geldige licentie kunt u GroupDocs.Watermark gebruiken in commerciële projecten. Zorg ervoor dat u de licentievoorwaarden op de website leest[aankooppagina](https://purchase.groupdocs.com/buy).