---
title: Zoek watermerk in koptekst/voettekst in Word-documenten
linktitle: Zoek watermerk in koptekst/voettekst in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u efficiënt watermerken uit Word-documenten kunt vinden en verwijderen met behulp van GroupDocs voor .NET, waardoor documentintegriteit en professionaliteit wordt gegarandeerd.
weight: 22
url: /nl/net/word-processing-watermarkings/find-watermark-header-footer-word-docs/
type: docs
---
# Zoek watermerk in koptekst/voettekst in Word-documenten

## Invoering
In de wereld van documentbeheer en -bescherming speelt watermerken een cruciale rol. Of het nu gaat om merkdoeleinden, auteursrechtbescherming of het volgen van documenten, het toevoegen van watermerken aan uw documenten is essentieel. Het efficiënt vinden en verwijderen van watermerken kan echter, vooral in grote documentensets, een hele klus zijn. Dit is waar GroupDocs.Watermark voor .NET in het spel komt. In deze zelfstudie gaan we dieper in op het vinden van watermerken in kop- en voetteksten van Word-documenten met behulp van GroupDocs.Watermark voor .NET, waarbij we elke stap opsplitsen om een uitgebreid begrip te garanderen.
## Vereisten
Voordat u in de zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. GroupDocs.Watermark voor .NET: Zorg ervoor dat de GroupDocs.Watermark voor .NET-bibliotheek in uw ontwikkelomgeving is geïnstalleerd en geconfigureerd. U kunt de bibliotheek downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Toegang tot Word-documenten: Krijg toegang tot de Word-documenten met watermerken die u wilt manipuleren.
3. Basiskennis van C#: Maak uzelf vertrouwd met de basisprincipes van de programmeertaal C#, aangezien deze tutorial C#-codefragmenten zal bevatten.
## Naamruimten importeren
Voordat u aan de slag gaat met de code, importeert u de benodigde naamruimten:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Stap 1: Definieer het documentpad en de naam van het uitvoerbestand
Definieer eerst het pad van het document dat het watermerk bevat en de naam van het uitvoerbestand waar het gewijzigde document zal worden opgeslagen.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Stap 2: Initialiseer watermerker
 Initialiseer de`Watermarker` object met het documentpad en de laadopties.
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Code voor watermerkmanipulatie komt hier te staan
}
```
## Stap 3: Definieer zoekcriteria
Definieer de zoekcriteria om het watermerk te vinden. Dit kan op basis van afbeelding of tekst.
```csharp
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
## Stap 4: Zoek naar watermerken
Zoek naar watermerken in de primaire koptekst van het document met behulp van de gedefinieerde zoekcriteria.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
PossibleWatermarkCollection possibleWatermarks = content.Sections[0]
                                                        .HeadersFooters[OfficeHeaderFooterType.HeaderPrimary]
                                                        .Search(textSearchCriteria.Or(imageSearchCriteria));
```
## Stap 5: verwijder watermerken
Verwijder alle gevonden watermerken uit het document.
```csharp
for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
{
    possibleWatermarks.RemoveAt(i);
}
```
## Stap 6: Document opslaan
Sla het gewijzigde document op met verwijderde watermerken.
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
GroupDocs.Watermark voor .NET biedt een robuuste oplossing voor het vinden en verwijderen van watermerken uit Word-documenten. Door de stappen in deze zelfstudie te volgen, kunt u op efficiënte wijze watermerken uit kop- en voetteksten lokaliseren en verwijderen, waardoor de integriteit en professionaliteit van uw documenten wordt gewaarborgd.
## Veelgestelde vragen
### Is GroupDocs.Watermark compatibel met andere documentformaten?
Ja, GroupDocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder Word, Excel, PowerPoint, PDF en meer.
### Kan ik de zoekcriteria voor watermerken aanpassen?
Absoluut, GroupDocs.Watermark biedt flexibele zoekcriteria, waardoor u naar watermerken kunt zoeken op basis van verschillende parameters, zoals tekst-, afbeelding-, vorm- of objecteigenschappen.
### Behoudt GroupDocs.Watermark de originele opmaak van documenten?
Ja, GroupDocs.Watermark zorgt ervoor dat de oorspronkelijke opmaak van documenten intact blijft terwijl watermerken worden verwijderd, waardoor de esthetiek en lay-out van het document behouden blijven.
### Is GroupDocs.Watermark geschikt voor batchverwerking van documenten?
Zeker, GroupDocs.Watermark biedt API's voor batchverwerking, waardoor u met gemak meerdere documenten tegelijk kunt verwerken.
### Waar kan ik hulp of ondersteuning zoeken voor GroupDocs.Watermark?
 Voor vragen of hulp met betrekking tot GroupDocs.Watermark kunt u terecht op de[GroupDocs.Watermark-forum](https://forum.groupdocs.com/c/watermark/19) of neem contact op met het ondersteuningsteam.