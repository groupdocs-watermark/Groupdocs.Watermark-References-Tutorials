---
title: Ladda dokument från lokal disk
linktitle: Ladda dokument från lokal disk
second_title: GroupDocs.Watermark .NET API
description: Skydda och hantera dina dokument med Groupdocs Watermark for .NET. Följ vår detaljerade guide för att lägga till vattenstämplar sömlöst.
weight: 10
url: /sv/net/document-loadings/load-document-from-local-disk/
type: docs
---
# Ladda dokument från lokal disk

## Introduktion
Vattenmärkning av dokument är viktigt i dagens digitala tidsålder för att säkerställa innehållsskydd, äganderätt och konfidentialitet. Groupdocs.Watermark for .NET är ett kraftfullt bibliotek som låter utvecklare lägga till, söka och hantera vattenstämplar i olika dokumentformat. I den här handledningen går vi igenom processen att använda Groupdocs.Watermark för .NET för att lägga till vattenstämplar i dina dokument med detaljerade steg-för-steg-instruktioner.
## Förutsättningar
Innan du går in i implementeringen, se till att du har följande:
1. Visual Studio installerad: Du behöver Visual Studio eller en annan kompatibel .NET IDE.
2.  Groupdocs.Watermark for .NET: Ladda ner biblioteket från[nedladdningslänk](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Se till att du har .NET Framework 4.6.1 eller senare installerat.
4. Ett provdokument: Förbered ett provdokument för att testa vattenmärkningsprocessen.
## Importera namnområden
För att komma igång måste du importera de nödvändiga namnrymden i ditt projekt. Dessa är viktiga för att komma åt de klasser och metoder som krävs för vattenmärkning.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokument från lokal disk
Först måste du ladda dokumentet från din lokala disk. Detta dokument kommer att vara det som du kommer att lägga till en vattenstämpel till.
Definiera sökvägen för dokumentet du vill vattenstämpla.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Steg 2: Initiera laddningsalternativ
 Initiera sedan laddningsalternativen. Om du till exempel arbetar med ett Word-dokument kommer du att använda`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Steg 3: Skapa och konfigurera Watermarker
 Nu ska du skapa en instans av`Watermarker` klass. Denna instans kommer att användas för att hantera och tillämpa vattenstämplar på ditt dokument.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Detta block kommer att innehålla ytterligare steg för att lägga till och spara vattenstämpeln
}
```
## Steg 4: Skapa en vattenstämpel
Skapa en textvattenstämpel. Denna vattenstämpel kan innehålla vilken text du väljer. Här kommer vi att använda "Testa vattenstämpel".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Steg 5: Lägg till vattenstämpel i dokumentet
Lägg till den skapade vattenstämpeln i dokumentet med hjälp av`Add` metod för`Watermarker` klass.
```csharp
watermarker.Add(watermark);
```
## Steg 6: Spara det vattenmärkta dokumentet
Spara slutligen det vattenmärkta dokumentet till den angivna sökvägen.
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
Att lägga till vattenstämplar i dina dokument med Groupdocs Watermark för .NET är enkelt och effektivt. Den här guiden har gått igenom hela processen från att ställa in din miljö till att spara ett vattenmärkt dokument. Med detta kraftfulla verktyg kan du säkerställa att dina dokument är skyddade och att din immateriella egendom är säker. 
 För ytterligare information, kolla[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) , och om du stöter på några problem,[supportforum](https://forum.groupdocs.com/c/watermark/19) är en utmärkt plats för hjälp. 
## FAQ's
### Kan jag använda anpassade teckensnitt för vattenstämplar?
Ja, Groupdocs stöder anpassade teckensnitt. Du kan ange vilket typsnitt som helst som är installerat på ditt system.
### Vilka typer av dokument stöds?
Groupdocs.Watermark stöder ett brett utbud av dokumentformat inklusive Word, Excel, PDF, PowerPoint och mer.
### Hur tar jag bort en vattenstämpel från ett dokument?
 Du kan använda`Remove` metod som tillhandahålls av`Watermarker` klass för att ta bort vattenstämplar.
### Är det möjligt att lägga till bildvattenstämplar?
 Ja, du kan lägga till bildvattenstämplar med hjälp av`ImageWatermark` klass.
### Kan jag prova Groupdocs.Watermark gratis?
 Absolut, du kan ladda ner en[gratis provperiod](https://releases.groupdocs.com/) att utvärdera biblioteket innan köp.