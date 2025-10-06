---
title: Lägg till vattenstämplar till PDF
linktitle: Lägg till vattenstämplar till PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till text- och bildvattenstämplar i dina PDF-filer med hjälp av GroupDocs.Watermark for .NET med vår omfattande steg-för-steg-guide.
weight: 14
url: /sv/net/pdf-watermarking-attachments/add-watermarks-pdf/
type: docs
---
# Lägg till vattenstämplar till PDF

## Introduktion
Vill du lägga till vattenstämplar i dina PDF-filer för att skydda dina dokument eller märka dem med din logotyp? Kolla inte vidare! I den här handledningen kommer vi att dyka ner i processen att använda GroupDocs.Watermark för .NET för att lägga till både text- och bildvattenstämplar till dina PDF-filer. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här guiden att leda dig genom varje steg, vilket säkerställer att du kan applicera vattenstämplar med lätthet och precision.
## Förutsättningar
Innan vi börjar, låt oss se till att du har allt du behöver följa tillsammans med den här handledningen:
-  GroupDocs.Watermark för .NET: Se till att du har den senaste versionen installerad. Du kan[ladda ner den här](https://releases.groupdocs.com/Watermark/net/).
- .NET-utvecklingsmiljö: Visual Studio eller någon annan IDE som stöder .NET.
- Grundläggande kunskaper om C#: Att förstå grunderna i C#-programmering hjälper dig att följa stegen med lätthet.
- PDF-dokument: Ha ett exempel på PDF-dokument redo för vattenmärkning.
- Bild för vattenstämpel: Om du lägger till en bildvattenstämpel, ha din bildfil redo.
## Importera namnområden
Först måste du importera de nödvändiga namnrymden i ditt C#-projekt. Detta ger dig tillgång till GroupDocs.Watermark-funktionen.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Låt oss nu dela upp processen i hanterbara steg.
## Steg 1: Ladda ditt PDF-dokument
Det första steget är att ladda ditt PDF-dokument i vattenmärket. Så här kan du göra det:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ytterligare steg kommer att läggas till här
}
```
## Steg 2: Lägg till en textvattenstämpel på första sidan
Därefter lägger vi till en textvattenstämpel på första sidan i din PDF. Följ dessa instruktioner:
```csharp
// Lägg till textvattenstämpel på första sidan
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Att lägga till en textvattenstämpel kan hjälpa till att skydda ditt dokument från obehörig användning eller helt enkelt märka det. Föreställ dig att stämpla ditt dokument med ett osynligt äkthetsstämpel.
## Steg 3: Lägg till en bildvattenstämpel på den andra sidan
Låt oss nu lägga till en bildvattenstämpel på den andra sidan. Detta är särskilt användbart för logotyper eller andra grafiska vattenstämplar.
```csharp
// Lägg till bildvattenstämpel på den andra sidan
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Bildvattenstämplar kan få dina dokument att se professionella ut och se till att ditt varumärke alltid är synligt. Det är som att lägga till din signatur på varje sida.
## Steg 4: Spara den vattenmärkta PDF-filen
När du har lagt till vattenstämplarna är det sista steget att spara den vattenstämplade PDF-filen på önskad plats.
```csharp
watermarker.Save(outputFileName);
```
Genom att spara dokumentet slutförs alla ändringar du gjort. Detta är ögonblicket dina ansträngningar stelnas till ett påtagligt resultat, redo för användning eller distribution.
## Slutsats
Grattis! Du har framgångsrikt lagt till både text- och bildvattenstämplar till din PDF med hjälp av GroupDocs.Watermark för .NET. Denna process är inte bara enkel utan också mycket anpassningsbar för att passa dina specifika behov. Oavsett om du skyddar dina dokument eller märker dem är vattenstämplar ett kraftfullt verktyg till ditt förfogande.
## FAQ's
### Kan jag lägga till flera vattenstämplar på samma sida?
 Ja, du kan lägga till flera vattenstämplar på samma sida genom att anropa`Add` metod flera gånger med olika vattenstämpelobjekt.
### Hur kan jag anpassa utseendet på textens vattenstämpel?
 Du kan anpassa textens vattenstämpel genom att justera egenskaper som teckensnitt, storlek, färg och opacitet med hjälp av`TextWatermark` objekt.
### Är det möjligt att endast vattenmärka specifika sidor i en PDF?
 Ja, du kan ange vilka sidor som ska vattenstämplas genom att ställa in`PageIndex` egendom i`PdfArtifactWatermarkOptions`.
### Kan jag ta bort vattenstämplar från en PDF?
Ja, GroupDocs.Watermark tillhandahåller funktionalitet för att söka efter och ta bort vattenstämplar från PDF-dokument.
### Hur får jag en tillfällig licens för GroupDocs.Watermark?
Du kan få en tillfällig licens genom att besöka[sida för tillfällig licens](https://purchase.groupdocs.com/temporary-license/).