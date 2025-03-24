---
title: Voeg watermerken toe aan PDF
linktitle: Voeg watermerken toe aan PDF
second_title: GroupDocs.Watermark .NET API
description: Leer hoe u tekst- en afbeeldingswatermerken aan uw PDF's kunt toevoegen met GroupDocs.Watermark voor .NET met onze uitgebreide stapsgewijze handleiding.
weight: 14
url: /nl/net/pdf-watermarking-attachments/add-watermarks-pdf/
---

# Voeg watermerken toe aan PDF

## Invoering
Wilt u watermerken aan uw PDF's toevoegen om uw documenten te beschermen of ze van uw logo te voorzien? Zoek niet verder! In deze zelfstudie duiken we in het proces van het gebruik van GroupDocs.Watermark voor .NET om zowel tekst- als afbeeldingswatermerken aan uw PDF-bestanden toe te voegen. Of u nu een doorgewinterde ontwikkelaar bent of net begint, deze gids begeleidt u bij elke stap, zodat u gemakkelijk en nauwkeurig watermerken kunt aanbrengen.
## Vereisten
Voordat we aan de slag gaan, zorgen we ervoor dat u alles heeft wat u nodig heeft om deze tutorial te volgen:
-  GroupDocs.Watermark voor .NET: Zorg ervoor dat de nieuwste versie is geïnstalleerd. Jij kan[download het hier](https://releases.groupdocs.com/Watermark/net/).
- .NET-ontwikkelomgeving: Visual Studio of een andere IDE die .NET ondersteunt.
- Basiskennis van C#: Als u de basisprincipes van programmeren in C# begrijpt, kunt u de stappen gemakkelijk volgen.
- PDF-document: Zorg ervoor dat u een voorbeeld-PDF-document gereed heeft voor watermerken.
- Afbeelding voor watermerk: Als u een afbeeldingswatermerk toevoegt, zorg er dan voor dat u uw afbeeldingsbestand gereed heeft.
## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren. Hierdoor krijgt u toegang tot de GroupDocs.Watermark-functionaliteit.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Laten we het proces nu opsplitsen in beheersbare stappen.
## Stap 1: Laad uw PDF-document
De eerste stap is het laden van uw PDF-document in de watermarker. Hier ziet u hoe u het kunt doen:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Hier zullen verdere stappen worden toegevoegd
}
```
## Stap 2: voeg een tekstwatermerk toe aan de eerste pagina
Vervolgens voegen we een tekstwatermerk toe aan de eerste pagina van uw PDF. Volg deze instructies:
```csharp
// Voeg een tekstwatermerk toe aan de eerste pagina
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Door een tekstwatermerk toe te voegen, kunt u uw document beschermen tegen ongeoorloofd gebruik of er eenvoudigweg een merk aan toevoegen. Stel je voor dat je je document van een onzichtbaar zegel van echtheid voorziet.
## Stap 3: Voeg een afbeeldingswatermerk toe aan de tweede pagina
Laten we nu een afbeeldingswatermerk toevoegen aan de tweede pagina. Dit is met name handig voor logo's of grafische watermerken.
```csharp
// Voeg een afbeeldingswatermerk toe aan de tweede pagina
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Met afbeeldingswatermerken kunnen uw documenten er professioneel uitzien en ervoor zorgen dat uw merk altijd zichtbaar is. Het is alsof u uw handtekening aan elke pagina toevoegt.
## Stap 4: Sla de PDF met watermerk op
Nadat u de watermerken hebt toegevoegd, is de laatste stap het opslaan van de PDF met watermerk op de gewenste locatie.
```csharp
watermarker.Save(outputFileName);
```
Door het document op te slaan, worden alle aangebrachte wijzigingen definitief gemaakt. Dit is het moment waarop uw inspanningen worden omgezet in een tastbaar resultaat, klaar voor gebruik of distributie.
## Conclusie
Gefeliciteerd! U hebt met succes zowel tekst- als afbeeldingswatermerken aan uw PDF toegevoegd met GroupDocs.Watermark voor .NET. Dit proces is niet alleen eenvoudig, maar ook zeer aanpasbaar aan uw specifieke behoeften. Of u uw documenten nu beschermt of van een branding voorziet, watermerken zijn een krachtig hulpmiddel dat u tot uw beschikking heeft.
## Veelgestelde vragen
### Kan ik meerdere watermerken aan dezelfde pagina toevoegen?
 Ja, u kunt meerdere watermerken aan dezelfde pagina toevoegen door de`Add` methode meerdere keren met verschillende watermerkobjecten.
### Hoe kan ik het uiterlijk van het tekstwatermerk aanpassen?
 U kunt het tekstwatermerk aanpassen door eigenschappen zoals lettertype, grootte, kleur en dekking aan te passen met behulp van de`TextWatermark` voorwerp.
### Is het mogelijk om alleen specifieke pagina's van een PDF van een watermerk te voorzien?
 Ja, u kunt opgeven welke pagina's u van een watermerk wilt voorzien door de`PageIndex` eigendom in de`PdfArtifactWatermarkOptions`.
### Kan ik watermerken uit een PDF verwijderen?
Ja, GroupDocs.Watermark biedt functionaliteit voor het zoeken naar en verwijderen van watermerken uit PDF-documenten.
### Hoe krijg ik een tijdelijke licentie voor GroupDocs.Watermark?
 kunt een tijdelijke licentie verkrijgen door naar de website te gaan[tijdelijke licentiepagina](https://purchase.groupdocs.com/temporary-license/).