---
title: Voeg een vergrendeld watermerk toe aan alle pagina's in Word-documenten
linktitle: Voeg een vergrendeld watermerk toe aan alle pagina's in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Beveilig uw documenten door vergrendelde watermerken toe te voegen met Groupdocs.Watermark voor .NET. Volg onze stapsgewijze handleiding voor een eenvoudige implementatie.
weight: 11
url: /nl/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Voeg een vergrendeld watermerk toe aan alle pagina's in Word-documenten

## Invoering
Het toevoegen van watermerken aan uw documenten is een essentiële stap bij het beveiligen en brandmerken van uw inhoud. Of u nu ongeoorloofd gebruik voorkomt of gewoon een professioneel tintje toevoegt, watermerken kunnen meerdere doeleinden dienen. In deze zelfstudie leiden we u door het proces van het toevoegen van een vergrendeld watermerk aan alle pagina's van een Word-document met Groupdocs.Watermark voor .NET.
## Vereisten
Voordat we in de stapsgewijze handleiding duiken, zorgen we ervoor dat u alles heeft wat u nodig heeft:
1. Groupdocs.Watermark voor .NET: Download de nieuwste versie van[hier](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
3. Ontwikkelomgeving: Een ontwikkelomgeving zoals Visual Studio.
4.  Licentie: U kunt kiezen voor een[gratis proefperiode](https://releases.groupdocs.com/) of koop een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/).
## Naamruimten importeren
Allereerst moet u de benodigde naamruimten in uw project importeren. Deze zijn essentieel voor toegang tot de klassen en methoden van Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Stel uw project in

Open uw ontwikkelomgeving en maak een nieuw .NET-project. Dit kan een consoletoepassing zijn of een ander type dat aan uw behoeften voldoet.

U moet het Groupdocs.Watermark-pakket aan uw project toevoegen. Dit kan gedaan worden via NuGet Package Manager. Voer de volgende opdracht uit in de NuGet Package Manager-console:
```sh
Install-Package GroupDocs.Watermark
```
## Stap 2: Laad het Word-document
### Definieer het documentpad
Geef het pad naar uw Word-document op. Dit is het document waaraan u het watermerk wilt toevoegen.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Laadopties instellen
 Maak een exemplaar van`WordProcessingLoadOptions` om uw Word-document met specifieke opties te laden.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Stap 3: Maak het watermerk
### Initialiseer watermerk
 De ... gebruiken`Watermarker`klasse, laadt u het document met de opgegeven laadopties.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Verdere stappen zullen binnen dit gebruiksblok plaatsvinden
}
```
### Definieer watermerkeigenschappen
 Maak een`TextWatermark` bijvoorbeeld met uw gewenste tekst, lettertype en kleur.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Stap 4: Pas een watermerk toe op alle pagina's
### Watermerkopties instellen
 Definiëren`WordProcessingWatermarkPagesOptions` en stel de`IsLocked` eigenschap op true om het watermerk te vergrendelen. Dit zorgt ervoor dat het watermerk niet gemakkelijk kan worden verwijderd.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Optioneel: voeg wachtwoordbeveiliging toe
Als u een extra beveiligingslaag wilt toevoegen, kunt u een wachtwoord voor het watermerk instellen.
```csharp
// Te beveiligen met een wachtwoord
// opties.Wachtwoord = "7654321";
```
### Voeg het watermerk toe
 Gebruik de`Add` werkwijze van de`Watermarker` class om het watermerk aan het document toe te voegen met de opgegeven opties.
```csharp
watermarker.Add(watermark, options);
```
## Stap 5: Sla het document op
Sla ten slotte het gewijzigde document op in het opgegeven uitvoerbestand.
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
Door deze stappen te volgen, kunt u eenvoudig een vergrendeld watermerk toevoegen aan alle pagina's van uw Word-documenten met Groupdocs.Watermark voor .NET. Dit helpt niet alleen bij het beschermen van uw documenten tegen ongeoorloofd gebruik, maar voegt ook een professioneel tintje toe aan uw inhoud. Groupdocs.Watermark biedt een uitgebreide oplossing voor watermerkbehoeften, zodat uw documenten veilig en gemerkt blijven.
## Veelgestelde vragen
### Kan ik een afbeelding als watermerk gebruiken in plaats van tekst?
 Ja, Groupdocs Watermark ondersteunt zowel tekst- als afbeeldingswatermerken. Je kunt vervangen`TextWatermark` met`ImageWatermark` en specificeer uw afbeelding.
### Is het mogelijk om de positie van het watermerk aan te passen?
 Absoluut! U kunt de positie van het watermerk instellen met behulp van eigenschappen zoals`HorizontalAlignment` En`VerticalAlignment`.
### Kan ik verschillende watermerken op verschillende pagina's van het document toepassen?
 Ja, u kunt watermerken voor specifieke pagina's aanpassen met behulp van de`PageIndex` eigendom in de`WordProcessingWatermarkPagesOptions`.
### Ondersteunt Groupdocs.Watermark andere documentformaten dan Word?
Ja, Groupdocs ondersteunt verschillende formaten, waaronder PDF, Excel, PowerPoint en meer.
### Wat zijn de systeemvereisten voor het gebruik van Groupdocs.Watermark?
U hebt een systeem nodig waarop .NET Framework is geïnstalleerd en een ontwikkelomgeving zoals Visual Studio.