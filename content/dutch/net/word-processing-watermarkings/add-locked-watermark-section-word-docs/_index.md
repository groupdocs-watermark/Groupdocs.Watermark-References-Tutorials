---
title: Voeg een vergrendeld watermerk toe aan sectie in Word-documenten
linktitle: Voeg een vergrendeld watermerk toe aan sectie in Word-documenten
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u een vergrendeld watermerk aan een specifieke sectie in Word-documenten kunt toevoegen met behulp van Groupdocs voor .NET met deze uitgebreide stapsgewijze handleiding.
weight: 13
url: /nl/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
type: docs
---
# Voeg een vergrendeld watermerk toe aan sectie in Word-documenten

## Invoering
Bent u op zoek naar een efficiënte manier om een vergrendeld watermerk toe te voegen aan een sectie in uw Word-documenten? Zoek niet verder! Met Groupdocs.Watermark voor .NET kunt u naadloos watermerken in Word-documenten invoegen, terwijl u ervoor zorgt dat ze vergrendeld en fraudebestendig blijven. Deze krachtige tool biedt een verscheidenheid aan functies om aan uw watermerkbehoeften te voldoen, of het nu gaat om branding, vertrouwelijkheid of beveiligingsdoeleinden. In deze stapsgewijze zelfstudie laten we u zien hoe u een vergrendeld watermerk kunt toevoegen aan een specifiek gedeelte van een Word-document met Groupdocs.Watermark voor .NET. Laten we erin duiken!
## Vereisten
Voordat we aan de slag gaan, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1.  Groupdocs.Watermark voor .NET: Zorg ervoor dat de Groupdocs.Watermark-bibliotheek is geïnstalleerd. Je kunt het downloaden[hier](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Zorg ervoor dat u het .NET-framework hebt ingesteld in uw ontwikkelomgeving.
3. IDE: Gebruik een Integrated Development Environment (IDE) zoals Visual Studio.
4. Document: Een Word-document (.docx) om het watermerk toe te passen.
## Naamruimten importeren
Om te beginnen moet u de benodigde naamruimten in uw project importeren. Hier leest u hoe u het moet doen:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Stap 1: Laad uw document
 Eerst moet u het document laden waaraan u het watermerk wilt toevoegen. Deze stap omvat het opgeven van het pad van uw document en het laden ervan met behulp van de`Watermarker` klas.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Uw watermerkcode komt hier terecht.
}
```
## Stap 2: Maak het watermerk
Maak vervolgens het watermerk dat u aan uw document wilt toevoegen. In dit voorbeeld maken we een tekstwatermerk met specifieke lettertype-instellingen en kleur.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Stap 3: Configureer watermerkopties
Configureer nu de watermerkopties om de sectie-index en vergrendelingsinstellingen op te geven. Dit zorgt ervoor dat het watermerk aan de juiste sectie wordt toegevoegd en wordt vergrendeld.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // Voeg toe aan het eerste gedeelte
options.IsLocked = true; // Vergrendel het watermerk
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Type slot
```
## Stap 4: voeg het watermerk toe aan het document
 Nu uw watermerk en opties zijn geconfigureerd, is het tijd om het watermerk aan het document toe te voegen met behulp van de`Add` werkwijze van de`Watermarker` klas.
```csharp
watermarker.Add(watermark, options);
```
## Stap 5: Sla het gewijzigde document op
Sla ten slotte het document met het toegevoegde watermerk op de gewenste uitvoerlocatie op.
```csharp
watermarker.Save(outputFileName);
```
## Conclusie
Het toevoegen van een vergrendeld watermerk aan een specifieke sectie in een Word-document met behulp van Groupdocs voor .NET is een eenvoudig proces. Door deze stappen te volgen, kunt u de veiligheid en integriteit van uw documenten verbeteren en ervoor zorgen dat belangrijke informatie wordt beschermd. Of u nu gevoelige gegevens beveiligt of een professioneel tintje aan uw documenten toevoegt, Groupdocs.Watermark voor .NET biedt de tools die u nodig hebt om uw doelen effectief te bereiken.
## Veelgestelde vragen
### Wat is Groupdocs.Watermark voor .NET?
Groupdocs.Watermark voor .NET is een krachtige bibliotheek waarmee ontwikkelaars watermerken kunnen toevoegen aan verschillende documenttypen, waaronder Word, PDF en afbeeldingen, met geavanceerde aanpassings- en beveiligingsfuncties.
### Kan ik een watermerk vergrendelen met een wachtwoord?
 Ja, u kunt het watermerk beveiligen met een wachtwoord door het in te stellen`options.Password` eigendom in de`WordProcessingWatermarkSectionOptions` klas.
### Is het mogelijk om verschillende watermerken op verschillende secties van een document toe te passen?
 Absoluut! Door anders in te stellen`SectionIndex` waarden in de`WordProcessingWatermarkSectionOptions`kunt u unieke watermerken op verschillende delen van het document toepassen.
### Welke soorten watermerken kan ik toevoegen met Groupdocs.Watermark?
Groupdocs.Watermark ondersteunt verschillende soorten watermerken, waaronder tekst-, afbeeldings- en vormwatermerken, en biedt uitgebreide aanpassingsopties voor elk type.
### Waar kan ik meer informatie vinden over Groupdocs.Watermark voor .NET?
 Voor meer informatie kunt u terecht op de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) En[Helpforum](https://forum.groupdocs.com/c/watermark/19).