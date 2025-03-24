---
title: Ondersteunde bestandsformaten verkrijgen
linktitle: Ondersteunde bestandsformaten verkrijgen
second_title: GroupDocs.Watermark .NET API
description: Voeg moeiteloos watermerken toe aan uw documenten met GroupDocs.Watermark voor .NET. Volg onze uitgebreide, stapsgewijze handleiding om uw digitale activa te beschermen.
weight: 13
url: /nl/net/document-manipulation/get-supported-file-formats/
---
## Invoering
Het watermerken van uw documenten is een cruciale stap bij het beschermen van uw digitale activa. Of het nu gaat om het beschermen van intellectueel eigendom, het garanderen van vertrouwelijkheid of gewoon om branding, watermerken spelen een cruciale rol. Als u een .NET-ontwikkelaar bent en watermerkmogelijkheden in uw toepassingen wilt integreren, is GroupDocs.Watermark voor .NET een krachtige en veelzijdige tool die u zou moeten overwegen. Deze tutorial leidt u door de essentie van het gebruik van GroupDocs.Watermark, van de installatie tot het aanbrengen van uw eerste watermerk, waarbij elke stap wordt opgesplitst zodat u deze gemakkelijk kunt volgen.
## Vereisten
Voordat we ingaan op de details, zorgen we ervoor dat u alles heeft wat u nodig heeft om aan de slag te gaan:
1.  Visual Studio: Zorg ervoor dat Visual Studio op uw computer is geïnstalleerd. Je kunt het downloaden van de[Visual Studio-website](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark ondersteunt verschillende versies van .NET Framework. Zorg ervoor dat uw project een compatibele versie target.
3. GroupDocs.Watermark voor .NET: u kunt de nieuwste versie downloaden van de[pagina vrijgeven](https://releases.groupdocs.com/Watermark/net/).
4. Basiskennis van C#: Deze tutorial gaat ervan uit dat je een fundamenteel begrip hebt van C# en .NET-ontwikkeling.
## Naamruimten importeren
Laten we eerst de benodigde naamruimten in uw project importeren. Open uw C#-bestand en voeg bovenaan het volgende toe met behulp van richtlijnen:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Nu deze naamruimten zijn geïmporteerd, bent u klaar om watermerken aan uw documenten toe te voegen.

## Stap 1: Initialiseer de watermerkengine
 De eerste stap is het initialiseren van de watermerkengine. Dit omvat het maken van een exemplaar van de`Watermarker` klasse met het document dat u van een watermerk wilt voorzien.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Met dit codefragment wordt de`Watermarker` object, dat u gaat gebruiken om watermerken op uw document toe te passen.
## Stap 2: voeg een tekstwatermerk toe
Laten we nu een eenvoudig tekstwatermerk aan uw document toevoegen. Tekstwatermerken zijn ideaal voor het toevoegen van labels als 'Vertrouwelijk' of 'Concept'.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Hier hebben we een`TextWatermark`object met de tekst 'Vertrouwelijk', stel het lettertype en de kleur in en lijn het uit met het midden van het document.
## Stap 3: Voeg een afbeeldingswatermerk toe
Als u liever een afbeelding als watermerk gebruikt, maakt GroupDocs.Watermark dat gemakkelijk.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 In dit voorbeeld maken we een`ImageWatermark` object, stel de afmetingen in en lijn het uit met de rechterbovenhoek van het document.
## Stap 4: Sla het document op
Na het toevoegen van de gewenste watermerken is de laatste stap het opslaan van het gewijzigde document.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Hierdoor wordt het document met een watermerk opgeslagen in het opgegeven pad en worden alle bronnen die erdoor worden gebruikt, vrijgegeven`Watermarker` voorbeeld.
## Stap 5: Ondersteunde bestandsformaten verkrijgen
Om te zien welke bestandsformaten worden ondersteund door GroupDocs.Watermark, kunt u het volgende codefragment gebruiken:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Hiermee worden alle bestandstypen afgedrukt die GroupDocs.Watermark aankan, waardoor u een uitgebreid beeld krijgt van de mogelijkheden ervan.
## Conclusie
Uw documenten van een watermerk voorzien met GroupDocs Watermark voor .NET is eenvoudig en efficiënt. Door deze zelfstudie te volgen, heeft u geleerd hoe u de watermerkengine kunt initialiseren, watermerken voor tekst en afbeeldingen kunt toevoegen, uw documenten met een watermerk kunt opslaan en ondersteunde bestandsindelingen kunt weergeven. Met deze tools kunt u uw documenten met vertrouwen beschermen.
 Als u vragen heeft of verdere hulp nodig heeft, aarzel dan niet om een bezoek te brengen aan de[GroupDocs.Watermark-ondersteuningsforum](https://forum.groupdocs.com/c/watermark/19).
## Veelgestelde vragen
### Hoe installeer ik GroupDocs.Watermark voor .NET?
 Je kunt het downloaden van de[pagina vrijgeven](https://releases.groupdocs.com/Watermark/net/) en voeg de DLL toe aan uw project.
### Kan ik GroupDocs.Watermark gratis uitproberen?
 Ja, u kunt een aanvraag indienen[gratis proefperiode](https://releases.groupdocs.com/) om de software te evalueren alvorens deze aan te schaffen.
### Welke bestandsformaten worden ondersteund door GroupDocs.Watermark?
U kunt het meegeleverde codefragment gebruiken om alle ondersteunde bestandsindelingen weer te geven.
### Hoe kan ik een licentie kopen voor GroupDocs.Watermark?
 Licenties kunnen rechtstreeks bij de[aankooppagina](https://purchase.groupdocs.com/buy).
### Is er documentatie beschikbaar voor GroupDocs.Watermark?
 Ja, er is uitgebreide documentatie beschikbaar[hier](https://tutorials.groupdocs.com/Watermark/net/).