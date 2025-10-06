---
title: Spara dokument till angiven plats
linktitle: Spara dokument till angiven plats
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du enkelt lägger till vattenstämplar i dina dokument med GroupDocs.Watermark for .NET med denna steg-för-steg-guide. Förbättra dokumentsäkerheten.
weight: 11
url: /sv/net/document-savings/save-document-specified-location/
type: docs
---
# Spara dokument till angiven plats

## Introduktion
I den digitala tidsåldern har säkra dokument blivit mer avgörande än någonsin. Vattenmärkning är ett effektivt sätt att skydda dina dokument från obehörig användning. GroupDocs.Watermark för .NET erbjuder en robust lösning för att lägga till vattenstämplar i dina dokument. Oavsett om du är en utvecklare som vill integrera vattenmärkning i din applikation eller någon som är intresserad av att skydda dina dokument, kommer den här handledningen att guida dig genom processen steg-för-steg.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:
- .NET-utvecklingsmiljö: Se till att du har Visual Studio eller någon annan .NET-utvecklingsmiljö installerad.
-  GroupDocs.Watermark for .NET Library: Ladda ner och referera till biblioteket i ditt projekt.[Ladda ner GroupDocs.Watermark för .NET](https://releases.groupdocs.com/Watermark/net/)
- Grundläggande kunskaper om C#-programmering: Att förstå grundläggande C#-programmeringskoncept kommer att vara till hjälp.
- Dokument till vattenstämpel: Ha ett exempeldokument redo som du vill applicera vattenstämpeln på.
## Importera namnområden
Innan vi börjar med exemplet måste du importera de nödvändiga namnrymden. Lägg till följande med hjälp av satser överst i din kodfil:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Låt oss dela upp processen att lägga till en vattenstämpel i ett dokument med GroupDocs.Watermark för .NET i hanterbara steg. Följ dessa steg för att framgångsrikt använda en vattenstämpel och spara ditt dokument på en angiven plats.
## Steg 1: Konfigurera ditt projekt
Börja med att skapa ett nytt .NET-projekt i Visual Studio. Du kan välja en konsolapp för enkelhetens skull.
1. Öppna Visual Studio.
2.  Välj`File` >`New` >`Project`.
3.  Välja`Console App (.NET Core)` eller`Console App (.NET Framework)`.
4.  Namnge ditt projekt och klicka`Create`.

## Steg 2: Förbered ditt dokument och vattenstämpeltext
### Ange dokumentsökväg
Definiera sökvägen för dokumentet du vill vattenstämpla. För det här exemplet, låt oss använda en platshållarbana.
```csharp
string documentPath = "Your Document Path";
```
### Definiera utdataväg
Ställ in utmatningsbanan där du vill att det vattenmärkta dokumentet ska sparas.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Steg 3: Ladda dokumentet
 Använd`Watermarker` klass för att ladda ditt dokument. Den här klassen tillhandahåller metoder för att lägga till, ta bort och redigera vattenstämplar.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Lägg till vattenmärkningslogik här
}
```
## Steg 4: Skapa och lägg till en vattenstämpel

### Skapa textvattenstämpel
 Instantiera en`TextWatermark` objekt med önskad text och teckensnittsegenskaper.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Lägg till vattenstämpel i dokumentet
 Lägg till den skapade vattenstämpeln i ditt dokument med hjälp av`Add` metod för`Watermarker` klass.
```csharp
watermarker.Add(watermark);
```
## Steg 5: Spara dokumentet
Slutligen sparar du dokumentet med vattenstämpeln på den angivna platsen.
```csharp
watermarker.Save(outputFileName);
```
## Slutsats
Vattenmärka dina dokument med GroupDocs Watermark för .NET är en enkel process som avsevärt kan förbättra din dokumentsäkerhet. Genom att följa denna steg-för-steg-guide kan du enkelt lägga till vattenstämplar i dina dokument och spara dem på önskad plats. Oavsett om du skyddar immateriella rättigheter, säkerställer dokumentets äkthet eller bara lägger till en professionell touch, tillhandahåller GroupDocs.Watermark för .NET de verktyg du behöver.
## FAQ's
### Kan jag använda bilder som vattenstämplar med GroupDocs.Watermark for .NET?
Ja, du kan använda både text- och bildvattenstämplar med GroupDocs Watermark för .NET. Biblioteket stöder olika typer av vattenstämplar för att passa dina behov.
### Finns det en gratis testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan ladda ner en gratis testversion från[hemsida](https://releases.groupdocs.com/).
### Hur kan jag köpa en licens för GroupDocs.Watermark för .NET?
 Du kan köpa en licens från[köpsidan](https://purchase.groupdocs.com/buy).
### Stöder GroupDocs.Watermark for .NET batch-vattenmärkning?
Ja, du kan vattenmärka flera dokument i en batchprocess genom att iterera genom en lista med dokument och använda vattenstämplar.
### Var kan jag få support för GroupDocs.Watermark för .NET?
 Support finns tillgänglig på[GroupDocs forum](https://forum.groupdocs.com/c/watermark/19).