---
title: Voeg een watermerk toe aan sectieafbeeldingen in Word-documenten
linktitle: Voeg een watermerk toe aan sectieafbeeldingen in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken aan afbeeldingen in Word-documenten kunt toevoegen met behulp van Groupdocs. Volg onze gids voor veilige en professionele documentbescherming.
weight: 16
url: /nl/net/word-processing-watermarkings/add-watermark-section-images-word-docs/
---

# Voeg een watermerk toe aan sectieafbeeldingen in Word-documenten

## Invoering
In de digitale wereld van vandaag is het beschermen van uw documenten essentieel. Het toevoegen van watermerken aan uw Word-documenten is een eenvoudige maar effectieve manier om uw inhoud te beveiligen. Deze tutorial leidt u door het proces van het toevoegen van watermerken aan sectieafbeeldingen in Word-documenten met behulp van Groupdocs.Watermark voor .NET. Of u nu een ontwikkelaar bent en deze functie in uw toepassing wilt integreren of gewoon uw documenten wilt beschermen, deze handleiding is voor u.
## Vereisten
Voordat we ingaan op de details, zorg ervoor dat u over het volgende beschikt:
1.  Groupdocs.Watermark voor .NET: Download het[hier](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
3. Een Word-document: Zorg ervoor dat u een Word-document bij de hand heeft waaraan u watermerken wilt toevoegen.
4. Ontwikkelomgeving: Visual Studio of een andere .NET-compatibele IDE.
5.  Tijdelijke licentie: verkrijg een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) voor Groupdocs.Watermark.
## Naamruimten importeren
Importeer om te beginnen de benodigde naamruimten in uw project. Dit is een cruciale stap om ervoor te zorgen dat alle functionaliteiten van Groupdocs.Watermark beschikbaar zijn.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Laten we het proces nu opsplitsen in beheersbare stappen.
## Stap 1: Uw project opzetten
Stel eerst uw project in de IDE van uw voorkeur in. Maak een nieuw .NET-project en installeer de Groupdocs.Watermark-bibliotheek.
```bash
dotnet add package GroupDocs.Watermark
```
## Stap 2: Laad het Word-document
Laad het Word-document waarvan u een watermerk wilt maken. Zorg ervoor dat het pad naar uw document correct is.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Uw code komt hier terecht
}
```
## Stap 3: Maak het watermerk
Maak een tekstwatermerk dat u op de afbeeldingen in het Word-document toepast. Pas de tekst, het lettertype, de grootte en de uitlijning aan uw behoeften aan.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Stap 4: haal afbeeldingen op uit het eerste gedeelte
Krijg toegang tot de inhoud van het Word-document en vind alle afbeeldingen in het eerste gedeelte. Deze stap is cruciaal omdat hiermee de afbeeldingen worden geïdentificeerd waarop het watermerk wordt toegepast.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WatermarkableImageCollection images = content.Sections[0].FindImages();
```
## Stap 5: Pas watermerk toe op afbeeldingen
Loop door elke afbeelding in het eerste gedeelte en pas het gemaakte watermerk toe. Dit zorgt ervoor dat alle afbeeldingen in de sectie beveiligd zijn.
```csharp
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Stap 6: Bewaar het document
Sla ten slotte het document met een watermerk op in het opgegeven pad. Hiermee is het proces van het toevoegen van een watermerk aan sectieafbeeldingen in een Word-document voltooid.
```csharp
watermarker.Save(outputFileName);
```
## Conclusie
Het toevoegen van watermerken aan afbeeldingen in uw Word-documenten is een krachtige manier om uw inhoud te beschermen. Met Groupdocs.Watermark voor .NET is dit proces eenvoudig en efficiënt. Volg de stappen in deze zelfstudie om ervoor te zorgen dat uw documenten veilig en goed beschermd zijn.
 Voor meer gedetailleerde documentatie, bezoek de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) . Als u vragen heeft of meer hulp nodig heeft, kijk dan op de[Helpforum](https://forum.groupdocs.com/c/watermark/19).
## Veelgestelde vragen
### Kan ik de watermerktekst aanpassen?
Ja, u kunt de watermerktekst, het lettertype, de grootte, de uitlijning en de rotatie aanpassen aan uw behoeften.
### Is het mogelijk om watermerken aan meerdere secties toe te voegen?
Ja, u kunt elke sectie doorlopen en het watermerk op afbeeldingen in alle secties toepassen.
### Kan ik deze methode gebruiken voor andere documentformaten?
 Groupdocs Watermark ondersteunt verschillende documentformaten. Controleer de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) voor meer details.
### Hoe kan ik een tijdelijke licentie verkrijgen?
 U kunt een tijdelijke licentie verkrijgen[hier](https://purchase.groupdocs.com/temporary-license/).
### Wat moet ik doen als ik problemen ondervind tijdens het gebruik van Groupdocs.Watermark?
 Bezoek de[Helpforum](https://forum.groupdocs.com/c/watermark/19)voor hulp bij eventuele problemen die u tegen kunt komen.