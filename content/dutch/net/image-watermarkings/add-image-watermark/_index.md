---
title: Voeg afbeeldingswatermerk toe
linktitle: Voeg afbeeldingswatermerk toe
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u afbeeldingswatermerken aan uw documenten kunt toevoegen met GroupDocs.Watermark voor .NET met onze gedetailleerde, stapsgewijze zelfstudie.
weight: 11
url: /nl/net/image-watermarkings/add-image-watermark/
---
## Invoering
Welkom bij deze uitgebreide handleiding over het toevoegen van afbeeldingswatermerken met GroupDocs.Watermark voor .NET! Watermerken zijn een krachtige manier om uw documenten en afbeeldingen te beschermen tegen ongeoorloofd gebruik, zodat uw intellectuele eigendom veilig blijft. In deze zelfstudie begeleiden we u door het hele proces, van het instellen van uw omgeving tot het aanbrengen van een watermerk op uw documenten. Of u nu een doorgewinterde ontwikkelaar bent of net begint, u zult deze handleiding nuttig en gemakkelijk te volgen vinden.
## Vereisten
Voordat we ingaan op de tutorial, zorgen we ervoor dat je alles hebt wat je nodig hebt:
- Ontwikkelomgeving: Visual Studio of een .NET-compatibele IDE
- .NET Framework: .NET Framework 4.0 of hoger
-  GroupDocs.Watermark voor .NET: u kunt het downloaden van de[GroupDocs-website](https://releases.groupdocs.com/Watermark/net/)
-  Afbeeldingsbestand: een afbeeldingsbestand dat als watermerk kan worden gebruikt (bijv.`watermark.jpg`)
- Documentbestand: een document waaraan u het watermerk wilt toevoegen (bijv.`presentation.pptx`)
## Naamruimten importeren
Om aan de slag te gaan, moet u de benodigde naamruimten in uw project importeren. Dit is essentieel voor toegang tot de GroupDocs-functionaliteiten.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
In dit gedeelte zullen we het proces van het toevoegen van een afbeeldingswatermerk opsplitsen in duidelijke, beheersbare stappen. Volg elke stap zorgvuldig om uw document succesvol van een watermerk te voorzien.
## Stap 1: Stel uw omgeving in
 Zorg er eerst voor dat uw ontwikkelomgeving correct is ingesteld. Installeer de GroupDocs.Watermark-bibliotheek door deze te downloaden van de[GroupDocs-website](https://releases.groupdocs.com/Watermark/net/).
1. Open uw project in Visual Studio.
2. Klik met de rechtermuisknop op uw project in de Solution Explorer.
3. Selecteer "NuGet-pakketten beheren..."
4.  Zoeken`GroupDocs.Watermark` en installeer het.
## Stap 2: Definieer bestandspaden
Vervolgens moet u de paden voor uw invoerdocument en de uitvoermap definiëren. Dit helpt het programma de bestanden te vinden waarmee het moet werken.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Path"` En`"Your Document Directory"` met de daadwerkelijke paden naar uw document en de gewenste uitvoermap.
## Stap 3: Initialiseer watermerker
Initialiseer nu de`Watermarker` klasse met het pad naar uw document. Deze klasse is verantwoordelijk voor het beheer van het watermerkproces.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Ga verder met de volgende stappen binnen dit gebruiksblok
}
```
## Stap 4: Maak een afbeeldingswatermerk
 Binnen de`Watermarker` blok, maak een exemplaar van het`ImageWatermark` klasse met behulp van het pad naar uw watermerkafbeelding. Deze klasse vertegenwoordigt de afbeelding die u als watermerk wilt gebruiken.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Ga verder naar de volgende stap binnen dit gebruiksblok
}
```
## Stap 5: voeg watermerk toe aan document
 Met de`ImageWatermark` exemplaar gereed, voeg het toe aan uw document met behulp van de`Add` werkwijze van de`Watermarker` klas.
```csharp
watermarker.Add(watermark);
```
## Stap 6: Bewaar het document
Sla ten slotte het document met een watermerk op in de opgegeven uitvoermap. Deze stap zorgt ervoor dat uw wijzigingen naar een nieuw bestand worden geschreven.
```csharp
watermarker.Save(outputFileName);
```
## Conclusie
Gefeliciteerd! U hebt met succes een afbeeldingswatermerk aan uw document toegevoegd met GroupDocs.Watermark voor .NET. Door deze stapsgewijze handleiding te volgen, kunt u uw documenten eenvoudig beschermen met aangepaste watermerken. Vergeet niet dat watermerken een cruciale stap zijn bij het beschermen van uw digitale activa tegen ongeoorloofd gebruik.

## Veelgestelde vragen
### Welke bestandsformaten worden ondersteund door GroupDocs.Watermark?
GroupDocs.Watermark ondersteunt een breed scala aan bestandsindelingen, waaronder PDF, DOCX, PPTX, XLSX en afbeeldingsbestanden zoals JPEG en PNG.
### Kan ik GroupDocs.Watermark gebruiken met .NET Core?
Ja, GroupDocs.Watermark is compatibel met zowel .NET Framework als .NET Core.
### Hoe kan ik een tijdelijke licentie krijgen voor GroupDocs.Watermark?
 Een tijdelijke licentie kunt u verkrijgen bij de[GroupDocs-website](https://purchase.groupdocs.com/temporary-license/).
### Is het mogelijk om meerdere watermerken aan één document toe te voegen?
 Absoluut! U kunt meerdere watermerken toevoegen door te bellen naar de`Add` methode meerdere keren met verschillende watermerkinstanties.
### Waar kan ik meer voorbeelden en documentatie vinden?
 Voor meer voorbeelden en gedetailleerde documentatie kunt u terecht op de website[GroupDocs.Watermark-documentatie](https://tutorials.groupdocs.com/Watermark/net/).