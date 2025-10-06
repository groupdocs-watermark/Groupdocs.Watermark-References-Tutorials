---
title: Voeg een vergrendeld watermerk toe aan specifieke pagina's in Word-documenten
linktitle: Voeg een vergrendeld watermerk toe aan specifieke pagina's in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u een vergrendeld watermerk aan specifieke pagina's in Word-documenten kunt toevoegen met GroupDocs.Watermark voor .NET met onze eenvoudige stapsgewijze handleiding.
weight: 12
url: /nl/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# Voeg een vergrendeld watermerk toe aan specifieke pagina's in Word-documenten

## Invoering
Wilt u een watermerk toevoegen aan specifieke pagina's in uw Word-documenten, maar wilt u dat dit wordt vergrendeld zodat het niet gemakkelijk kan worden verwijderd of bewerkt? Je bent op de juiste plek! In deze zelfstudie begeleiden we u bij het toevoegen van een vergrendeld watermerk aan specifieke pagina's in Word-documenten met behulp van GroupDocs.Watermark voor .NET. Met deze krachtige bibliotheek kunt u eenvoudig watermerken op verschillende documenttypen toepassen, beheren en aanpassen. Of u nu een ontwikkelaar bent of gewoon iemand die zijn documenten moet beveiligen, deze handleiding leidt u op een eenvoudige manier door elke stap.
## Vereisten
Voordat we ingaan op de tutorial, zorgen we ervoor dat je alles hebt wat je nodig hebt:
1.  GroupDocs.Watermark voor .NET: dat kan[downloaden](https://releases.groupdocs.com/Watermark/net/) de laatste versie.
2. Ontwikkelomgeving: een IDE zoals Visual Studio.
3. Basiskennis van C#: Bekendheid met programmeren in C# kan nuttig zijn.
4. Document naar watermerk: een Word-document (.docx of .doc) waaraan u een watermerk wilt toevoegen.
## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren. Deze naamruimten bieden toegang tot de klassen en methoden die nodig zijn om met GroupDocs.Watermark te werken.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Nu we aan de vereisten hebben voldaan en de benodigde naamruimten hebben geïmporteerd, gaan we het proces stap voor stap opsplitsen.
## Stap 1: Laad het Word-document
 Om te beginnen moet u het Word-document laden waaraan u een watermerk wilt toevoegen. Dit kan gedaan worden met behulp van de`Watermarker` klas mee`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ga door naar de volgende stappen
}
```
## Stap 2: Maak het tekstwatermerk
Maak vervolgens een tekstwatermerk. U kunt de tekst, het lettertype, de kleur en andere eigenschappen aanpassen aan uw wensen.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Stap 3: Configureer watermerkopties
 Om het watermerk op specifieke pagina's toe te passen en te vergrendelen, configureert u de`WordProcessingWatermarkPagesOptions`Hier geeft u de paginanummers op waar het watermerk moet verschijnen en stelt u de vergrendelingsopties in.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Specificeer de pagina's
options.IsLocked = true; // Vergrendel het watermerk
options.LockType = WordProcessingLockType.AllowOnlyComments; // Stel het slottype in
// Te beveiligen met een wachtwoord
// opties.Wachtwoord = "7654321";
```
## Stap 4: voeg het watermerk toe aan het document
Nu uw watermerk en opties zijn geconfigureerd, kunt u het watermerk nu aan het document toevoegen.
```csharp
watermarker.Add(watermark, options);
```
## Stap 5: Sla het document op
Sla ten slotte het document op met het toegepaste watermerk. Kies een geschikt uitvoerpad en sla het bestand op.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusie
Gefeliciteerd! U hebt met succes een vergrendeld watermerk toegevoegd aan specifieke pagina's in een Word-document met GroupDocs.Watermark voor .NET. In deze zelfstudie werden alle essentiële stappen behandeld, van het laden van het document tot het opslaan van het bestand met een watermerk. Door deze stappen te volgen, kunt u ervoor zorgen dat uw documenten veilig van een watermerk zijn voorzien, zodat uw inhoud wordt beschermd tegen ongeoorloofde bewerking en gebruik.
 Voor meer informatie kunt u verwijzen naar de[GroupDocs.Watermark-documentatie](https://tutorials.groupdocs.com/Watermark/net/) . Als u vragen heeft of meer hulp nodig heeft, kunt u gerust een bezoek brengen aan de[Helpforum](https://forum.groupdocs.com/c/watermark/19).
## Veelgestelde vragen
### Wat is GroupDocs.Watermark voor .NET?
GroupDocs.Watermark voor .NET is een krachtige bibliotheek waarmee ontwikkelaars watermerken kunnen toevoegen aan verschillende soorten documenten, waaronder Word, PDF, Excel en meer.
### Kan ik watermerken op meerdere pagina's in een document toepassen?
 Ja, u kunt meerdere paginanummers opgeven in het`PageNumbers` array om watermerken op meerdere pagina's toe te passen.
### Hoe beveilig ik een watermerk met een wachtwoord?
 U kunt een watermerk met een wachtwoord beveiligen door de`Password` eigendom in de`WordProcessingWatermarkPagesOptions`.
### Is het mogelijk om het uiterlijk van het watermerk aan te passen?
Absoluut! U kunt de tekst, het lettertype, de kleur, de grootte en andere eigenschappen van het watermerk aanpassen aan uw behoeften.
### Waar kan ik een tijdelijke licentie krijgen voor GroupDocs.Watermark?
 Een tijdelijke licentie kunt u verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/).