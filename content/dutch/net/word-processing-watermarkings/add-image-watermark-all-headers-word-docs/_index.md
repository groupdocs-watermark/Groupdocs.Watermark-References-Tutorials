---
title: Voeg een afbeeldingswatermerk toe aan alle kopteksten in Word-documenten
linktitle: Voeg een afbeeldingswatermerk toe aan alle kopteksten in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Voeg eenvoudig afbeeldingswatermerken toe aan alle kopteksten in Word-documenten met GroupDocs.Watermark voor .NET. Volg onze stapsgewijze handleiding met gedetailleerde codevoorbeelden.
weight: 10
url: /nl/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---

# Voeg een afbeeldingswatermerk toe aan alle kopteksten in Word-documenten

## Invoering
Watermerken kunnen een essentieel onderdeel zijn van documentbeheer en bieden een manier om informatie zoals eigendom, vertrouwelijkheid of branding in documenten in te bedden. In deze zelfstudie doorlopen we de stappen om een afbeeldingswatermerk toe te voegen aan alle kopteksten in Word-documenten met behulp van GroupDocs.Watermark voor .NET. Of u nu nieuw bent bij het programmeren of een ervaren ontwikkelaar bent, deze gids helpt u uw watermerkdoelen met gemak te bereiken.
## Vereisten
Voordat we in de code duiken, zorgen we ervoor dat we alles hebben wat we nodig hebben. Hier is een checklist om u op weg te helpen:
1.  GroupDocs.Watermark voor .NET: Download de nieuwste versie van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Ontwikkelomgeving: Visual Studio of een andere .NET-compatibele IDE.
3. .NET Framework: Zorg ervoor dat het .NET-framework is geïnstalleerd.
4. Voorbeeld van een Word-document: een Word-document waaraan u het watermerk wilt toevoegen.
5. Afbeelding voor watermerk: een afbeeldingsbestand dat u als watermerk wilt gebruiken.
Zodra u deze gereed heeft, kunnen wij beginnen met het opzetten van ons project.
## Naamruimten importeren
Laten we eerst de benodigde naamruimten importeren. Deze naamruimten bevatten klassen en methoden die ons helpen bij het werken met watermerken in onze documenten.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Uw project opzetten
Maak om te beginnen een nieuwe consoletoepassing in Visual Studio. Voeg verwijzingen toe naar de GroupDocs.Watermark DLL in uw project. Dit kunt u doen door het GroupDocs.Watermark NuGet-pakket te installeren.
```bash
Install-Package GroupDocs.Watermark
```
## Stap 2: Laad uw document
 De eerste stap bij het toevoegen van een watermerk is het laden van het document waar het watermerk zal worden toegevoegd. Hier gebruiken we de`WordProcessingLoadOptions` om een Word-document te laden.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Code om watermerk toe te voegen komt hier terecht
}
```
## Stap 3: Maak het afbeeldingswatermerk
Vervolgens maken we een afbeeldingswatermerk. Hierbij moet u het afbeeldingsbestand opgeven dat u als watermerk wilt gebruiken.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Code om het watermerk toe te passen komt hier terecht
}
```
## Stap 4: voeg een watermerk toe aan de kopteksten van de eerste sectie
 We moeten het watermerk toevoegen aan alle kopteksten in het eerste gedeelte van het Word-document. Hiervoor gebruiken wij`WordProcessingWatermarkSectionOptions` en specificeer de sectie-index.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Stap 5: Koppel kop- en voetteksten
Om ervoor te zorgen dat het watermerk in de kop- en voetteksten van alle secties verschijnt, koppelen we alle andere kop- en voetteksten aan de kop- en voetteksten van de eerste sectie.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Stap 6: Bewaar het document
Ten slotte slaan we het document met een watermerk op een opgegeven pad op. Deze stap zorgt ervoor dat uw wijzigingen naar een nieuw bestand worden geschreven, waarbij het originele document behouden blijft.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusie
En daar heb je het! U hebt met succes een afbeeldingswatermerk toegevoegd aan alle kopteksten in een Word-document met GroupDocs.Watermark voor .NET. Deze krachtige bibliotheek maakt het eenvoudig om watermerken te beheren en toe te passen op verschillende documenttypen, zodat uw inhoud wordt beschermd en professioneel wordt gebrandmerkt.
## Veelgestelde vragen
### Kan ik naast afbeeldingen ook andere soorten watermerken gebruiken?
Ja, GroupDocs Watermark ondersteunt tekst-, afbeelding- en zelfs samengestelde watermerken.
### Is het mogelijk om naast de kopteksten ook andere delen van het document van een watermerk te voorzien?
Absoluut! U kunt voetteksten, hoofdtekst en zelfs specifieke pagina's of secties van een watermerk voorzien.
### Ondersteunt GroupDocs.Watermark andere documentformaten?
Ja, het ondersteunt een breed scala aan indelingen, waaronder PDF's, Excel, PowerPoint en meer.
### Kan ik de positie en het uiterlijk van het watermerk aanpassen?
Ja, u kunt de grootte, positie, dekking en vele andere eigenschappen van het watermerk aanpassen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Watermark?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).