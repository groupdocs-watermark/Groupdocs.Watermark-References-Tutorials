---
title: Beveiliging van document in Word-documenten opheffen
linktitle: Beveiliging van document in Word-documenten opheffen
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u eenvoudig de beveiliging van Word-documenten kunt opheffen met GroupDocs.Watermark voor .NET. Volg onze stapsgewijze handleiding.
type: docs
weight: 38
url: /nl/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## Invoering
GroupDocs.Watermark voor .NET is een krachtige API waarmee ontwikkelaars met watermerken in verschillende documentformaten kunnen werken, waaronder Word-documenten. In deze zelfstudie begeleiden we u bij het proces van het opheffen van de beveiliging van een Word-document met GroupDocs.Watermark voor .NET. Of u nu een doorgewinterde ontwikkelaar bent of net begint met de ontwikkeling van .NET, deze stapsgewijze handleiding helpt u de taak efficiënt uit te voeren.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Watermark voor .NET: De GroupDocs.Watermark voor .NET API moet in uw ontwikkelomgeving zijn geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/Watermark/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u over een geschikte ontwikkelomgeving beschikt voor .NET-ontwikkeling, inclusief Visual Studio of een andere compatibele IDE.
3. Word-document: zorg ervoor dat u een Word-document waarvan u de beveiliging wilt opheffen, gereed hebt in uw bestandssysteem.

## Naamruimten importeren
Voordat u in de code duikt, moet u de benodigde naamruimten in uw .NET-project importeren. Hierdoor heeft u naadloos toegang tot de functionaliteiten van GroupDocs.Watermark voor .NET.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Stap 1: Geef het documentpad op
Definieer het pad naar uw Word-document waarvan u de beveiliging wilt opheffen.
```csharp
string documentPath = "Your Document Path";
```
 Vervangen`"Your Document Path"` met het daadwerkelijke pad naar uw Word-document.
## Stap 2: Stel de naam van het uitvoerbestand in
Geef de map op waarin u het onbeveiligde document wilt opslaan en geef een naam op voor het uitvoerbestand.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Vervangen`"Your Document Directory"` met het directorypad waar u het uitvoerbestand wilt opslaan.
## Stap 3: Document met opties laden
 Maak een exemplaar van`WordProcessingLoadOptions` om het Word-document met specifieke opties te laden.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Stap 4: Maak de beveiliging van het document ongedaan
 Instantieer de`Watermarker` klasse met het documentpad en de laadopties. Haal vervolgens de inhoud van het document op als WordProcessingContent en hef de beveiliging ervan op.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## Conclusie
Door deze stappen te volgen, kunt u eenvoudig de beveiliging van een Word-document opheffen met GroupDocs.Watermark voor .NET. Deze API biedt een eenvoudige manier om watermerken te manipuleren en uw documenten efficiënt te beschermen.
## Veelgestelde vragen
### Is GroupDocs.Watermark voor .NET compatibel met alle versies van .NET?
Ja, GroupDocs.Watermark voor .NET is compatibel met .NET Framework 2.0 en latere versies, inclusief .NET Core en .NET Standard.
### Kan ik watermerken toepassen op documenten in andere formaten dan Word?
Absoluut! GroupDocs.Watermark voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, Excel, PowerPoint en meer.
### Is er een proefversie beschikbaar voor GroupDocs.Watermark voor .NET?
 Ja, u kunt een gratis proefversie krijgen van[hier](https://releases.groupdocs.com/).
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Watermark voor .NET?
 U kunt een bezoek brengen aan de[GroupDocs.Watermark-forum](https://forum.groupdocs.com/c/watermark/19) voor technische assistentie en gemeenschapsondersteuning.
### Kan ik een tijdelijke licentie kopen voor GroupDocs.Watermark voor .NET?
 Ja, u kunt een tijdelijke licentie aanschaffen bij[hier](https://purchase.groupdocs.com/temporary-license/).