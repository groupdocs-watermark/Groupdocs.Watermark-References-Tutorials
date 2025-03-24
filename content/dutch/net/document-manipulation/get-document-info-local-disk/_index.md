---
title: Documentinformatie ophalen van lokale schijf
linktitle: Documentinformatie ophalen van lokale schijf
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u watermerken in documenten kunt toevoegen, verwijderen en extraheren met behulp van GroupDocs voor .NET met deze uitgebreide stapsgewijze handleiding.
weight: 11
url: /nl/net/document-manipulation/get-document-info-local-disk/
---
## Invoering
Welkom bij de ultieme handleiding voor het gebruik van GroupDocs.Watermark voor .NET! Of u nu een doorgewinterde ontwikkelaar bent of net begint, dit artikel begeleidt u bij de basisprincipes van het watermerken van uw documenten met deze krachtige tool. Uiteindelijk zult u een professional zijn in het insluiten van watermerken in uw documenten, zodat u er zeker van kunt zijn dat ze worden beschermd en van uw merk worden voorzien volgens uw specificaties.
## Vereisten
Voordat u in de stapsgewijze handleiding duikt, zijn er een aantal vereisten waaraan u moet voldoen:
1.  .NET Framework: Zorg ervoor dat .NET Framework op uw systeem is geïnstalleerd. GroupDocs.Watermark voor .NET is compatibel met verschillende versies van .NET Framework, dus controleer de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) voor compatibiliteitsdetails.
2.  GroupDocs.Watermark voor .NET Library: Download en installeer de nieuwste versie van de[downloadpagina](https://releases.groupdocs.com/Watermark/net/).
3. Ontwikkelomgeving: U moet een ontwikkelomgeving hebben opgezet. Visual Studio is een populaire keuze voor .NET-ontwikkeling.
4. Basiskennis van C#: Als u de basisprincipes van C#-programmeren begrijpt, kunt u de voorbeelden volgen.
## Naamruimten importeren
Voordat u GroupDocs.Watermark voor .NET kunt gebruiken, moet u de benodigde naamruimten in uw project importeren. Dit is een eenvoudig proces en essentieel voor toegang tot de functies van de bibliotheek.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Laten we het proces van het watermerken van een document opsplitsen in duidelijke, beheersbare stappen. Elke stap is bedoeld om u te helpen de functionaliteit gemakkelijk te begrijpen en te implementeren.
## Stap 1: Laad uw document
 De eerste stap is het laden van het document dat u van een watermerk wilt voorzien. Dit gebeurt met behulp van de`Watermarker` class, waarmee u uw document kunt openen en manipuleren.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Het document is nu geladen en klaar voor watermerken
}
```
 In deze stap vervangt u`"Your Document Path"` met het daadwerkelijke pad naar uw document. Hiermee initialiseert u de`Watermarker`object, waardoor u toegang krijgt tot verschillende watermerkfunctionaliteiten.
## Stap 2: Documentinformatie ophalen
Voordat u een watermerk toevoegt, wilt u wellicht wat informatie over het document verzamelen. Dit kan handig zijn voor het aanpassen van uw watermerk op basis van documenteigenschappen.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 In deze stap wordt de`GetDocumentInfo` methode haalt details op zoals bestandstype, aantal pagina's en documentgrootte. Deze informatie wordt op de console afgedrukt, maar u kunt deze indien nodig in uw toepassing gebruiken.
## Stap 3: voeg een tekstwatermerk toe
Nu u uw document hebt geladen en de informatie bij de hand heeft, is het tijd om een watermerk toe te voegen. We beginnen met een eenvoudig tekstwatermerk.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Hier maak je een`TextWatermark` object met uw gewenste tekst, lettertype en stijl. Pas eigenschappen zoals kleur, dekking en rotatiehoek aan uw behoeften aan. Ten slotte wordt het watermerk aan het document toegevoegd en op een opgegeven pad opgeslagen.
## Stap 4: Voeg een afbeeldingswatermerk toe
Tekstwatermerken zijn geweldig, maar wat als u een logo of een andere afbeelding wilt toevoegen? In deze stap wordt beschreven hoe u een afbeeldingswatermerk toevoegt.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Vervangen`"Path to Your Image"` met het pad naar uw watermerkafbeelding. Stel eigenschappen zoals dekking en rotatiehoek in om het uiterlijk van uw afbeeldingswatermerk aan te passen. Het proces voor het toevoegen en opslaan van het watermerk is vergelijkbaar met dat van een tekstwatermerk.
## Stap 5: verwijder bestaande watermerken
 Soms moet u bestaande watermerken uit een document verwijderen. Dit kan gedaan worden met behulp van de`Remove` methode aangeboden door de`Watermarker` klas.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Hier de`Remove` methode wordt gebruikt om tekstwatermerken uit het document te verwijderen. U kunt verschillende soorten watermerken opgeven die u wilt verwijderen, zoals afbeeldingen of tekst, afhankelijk van uw behoeften. Sla het document op in een nieuw pad om de wijzigingen te zien.
## Stap 6: Extraheer watermerken
Als u watermerken uit een document moet extraheren en inspecteren, maakt GroupDocs.Watermark voor .NET dit eenvoudig mogelijk.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Aanvullende eigenschappen en logica voor elk watermerk
    }
}
```
 Deze stap omvat het gebruik van de`GetWatermarks`methode om alle watermerken in een document op te halen. Vervolgens kunt u de lijst met watermerken doorlopen en hun eigenschappen inspecteren of indien nodig aanvullende acties uitvoeren.
## Conclusie
 Gefeliciteerd! U hebt nu geleerd hoe u GroupDocs.Watermark voor .NET kunt gebruiken om watermerken aan uw documenten toe te voegen, te verwijderen en te extraheren. Met deze vaardigheden kunt u uw documenten effectief beschermen en van een merk voorzien. Herinner de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) is er altijd als u meer gedetailleerde informatie of geavanceerde functionaliteit nodig heeft.
## Veelgestelde vragen
### Kan ik GroupDocs.Watermark voor .NET gebruiken met elke .NET-versie?
 Ja, GroupDocs.Watermark voor .NET is compatibel met verschillende .NET Framework-versies. Controleer de[documentatie](https://tutorials.groupdocs.com/Watermark/net/) voor bijzonderheden.
### Waar kan ik GroupDocs.Watermark voor .NET downloaden?
 U kunt de nieuwste versie downloaden van de[downloadpagina](https://releases.groupdocs.com/Watermark/net/).
### Hoe krijg ik een tijdelijke licentie?
 Een tijdelijke licentie kunt u verkrijgen bij de[tijdelijke licentiepagina](https://purchase.groupdocs.com/temporary-license/).
### Is er een gratis proefversie beschikbaar?
 Ja, u kunt een gratis proefperiode starten door naar de website te gaan[gratis proefpagina](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning krijgen als ik problemen tegenkom?
 Ondersteuning is beschikbaar op de[GroupDocs Watermerk-forum](https://forum.groupdocs.com/c/watermark/19).