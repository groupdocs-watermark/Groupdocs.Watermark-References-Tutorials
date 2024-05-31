---
title: Document laden vanaf lokale schijf
linktitle: Document laden vanaf lokale schijf
second_title: GroupDocs.Watermark .NET API
description: Bescherm en beheer uw documenten met Groupdocs voor .NET. Volg onze gedetailleerde gids om naadloos watermerken toe te voegen.
type: docs
weight: 10
url: /nl/net/document-loadings/load-document-from-local-disk/
---
## Invoering
Het watermerken van documenten is essentieel in het huidige digitale tijdperk om de bescherming van de inhoud, de eigendomsbevestiging en de vertrouwelijkheid te garanderen. Groupdocs.Watermark voor .NET is een krachtige bibliotheek waarmee ontwikkelaars watermerken in verschillende documentformaten kunnen toevoegen, zoeken en beheren. In deze zelfstudie doorlopen we het proces van het gebruik van Groupdocs.Watermark voor .NET om watermerken aan uw documenten toe te voegen met gedetailleerde stapsgewijze instructies.
## Vereisten
Voordat u in de implementatie duikt, moet u ervoor zorgen dat u over het volgende beschikt:
1. Visual Studio geïnstalleerd: u hebt Visual Studio of een andere compatibele .NET IDE nodig.
2.  Groupdocs.Watermark voor .NET: Download de bibliotheek van de[download link](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Zorg ervoor dat .NET Framework 4.6.1 of hoger is geïnstalleerd.
4. Een voorbeelddocument: bereid een voorbeelddocument voor om het watermerkproces te testen.
## Naamruimten importeren
Om aan de slag te gaan, moet u de benodigde naamruimten in uw project importeren. Deze zijn essentieel voor toegang tot de klassen en methoden die nodig zijn voor watermerken.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Document laden vanaf lokale schijf
Eerst moet u het document vanaf uw lokale schijf laden. Dit document is het document waaraan u een watermerk gaat toevoegen.
Definieer het pad van het document dat u van een watermerk wilt voorzien.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Stap 2: Initialiseer laadopties
 Initialiseer vervolgens de laadopties. Als u bijvoorbeeld met een Word-document werkt, gebruikt u`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Stap 3: Watermarker maken en configureren
 Nu gaat u een exemplaar maken van de`Watermarker` klas. Deze instantie wordt gebruikt om watermerken te beheren en op uw document toe te passen.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dit blok bevat verdere stappen om het watermerk toe te voegen en op te slaan
}
```
## Stap 4: Maak een watermerk
Maak een tekstwatermerk. Dit watermerk kan elke gewenste tekst bevatten. Hier zullen we "Testwatermerk" gebruiken.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Stap 5: voeg een watermerk toe aan het document
Voeg het gemaakte watermerk toe aan het document met behulp van de`Add` werkwijze van de`Watermarker` klas.
```csharp
watermarker.Add(watermark);
```
## Stap 6: Bewaar het document met watermerk
Sla ten slotte het document met een watermerk op in het opgegeven pad.
```csharp
watermarker.Save(outputFileName);
```

## Conclusie
Het toevoegen van watermerken aan uw documenten met Groupdocs voor .NET is eenvoudig en efficiënt. Deze handleiding heeft u door het hele proces geleid, van het instellen van uw omgeving tot het opslaan van een document met een watermerk. Met deze krachtige tool kunt u ervoor zorgen dat uw documenten worden beschermd en dat uw intellectuele eigendom veilig is. 
 Voor meer details, kijk op de[documentatie](https://reference.groupdocs.com/Watermark/net/) , en als u problemen ondervindt, kunt u de[Helpforum](https://forum.groupdocs.com/c/watermark/19) is een uitstekende plek voor hulp. 
## Veelgestelde vragen
### Kan ik aangepaste lettertypen voor watermerken gebruiken?
Ja, Groupdocs ondersteunt aangepaste lettertypen. U kunt elk lettertype opgeven dat op uw systeem is geïnstalleerd.
### Welke soorten documenten worden ondersteund?
Groupdocs.Watermark ondersteunt een breed scala aan documentformaten, waaronder Word, Excel, PDF, PowerPoint en meer.
### Hoe kan ik een watermerk uit een document verwijderen?
 U kunt gebruik maken van de`Remove` methode aangeboden door de`Watermarker` klasse om watermerken te verwijderen.
### Is het mogelijk om afbeeldingswatermerken toe te voegen?
 Ja, u kunt afbeeldingswatermerken toevoegen met behulp van de`ImageWatermark` klas.
### Kan ik Groupdocs.Watermark gratis uitproberen?
 Absoluut, je kunt een[gratis proefperiode](https://releases.groupdocs.com/) om de bibliotheek te evalueren voordat u deze aanschaft.