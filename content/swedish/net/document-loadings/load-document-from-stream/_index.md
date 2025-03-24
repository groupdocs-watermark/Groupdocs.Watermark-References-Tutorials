---
title: Ladda dokument från Stream
linktitle: Ladda dokument från Stream
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar i dokument med GroupDocs.Watermark for .NET med den här guiden. Perfekt för utvecklare som vill förbättra dokumentsäkerheten.
weight: 11
url: /sv/net/document-loadings/load-document-from-stream/
---
## Introduktion
Vill du lägga till vattenstämplar till dina dokument sömlöst med .NET? Kolla inte vidare! GroupDocs.Watermark for .NET är ett kraftfullt och lättanvänt bibliotek som låter dig hantera vattenstämplar i olika dokumentformat. Oavsett om du arbetar med PDF-filer, Word-dokument eller bilder, har det här verktyget dig täckt. I den här handledningen går vi igenom processen att ladda ett dokument från en ström och lägga till en vattenstämpel steg för steg. Så, låt oss dyka direkt in!
## Förutsättningar
Innan vi börjar, se till att du har följande inställning:
1. Visual Studio: Alla nyare versioner av Visual Studio fungerar bra.
2. .NET Framework: Se till att du har .NET Framework 4.0 eller senare installerat.
3.  GroupDocs.Watermark för .NET: Du kan ladda ner det från[här](https://releases.groupdocs.com/Watermark/net/).
4. Grundläggande kunskaper i C#: Bekantskap med C# och objektorienterade programmeringskoncept kommer att vara till hjälp.

## Importera namnområden
För att använda GroupDocs.Watermark i ditt projekt måste du importera de nödvändiga namnrymden. Detta gör att du kan komma åt bibliotekets funktioner utan problem.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Steg 1: Konfigurera ditt projekt
Först och främst måste du ställa in ditt projekt i Visual Studio. Så här gör du:
1. Skapa ett nytt projekt: Öppna Visual Studio och skapa ett nytt C# Console Application-projekt.
2.  Installera GroupDocs.Watermark: Installera GroupDocs.Watermark-biblioteket via NuGet Package Manager. Sök helt enkelt efter`GroupDocs.Watermark` och installera den.
## Steg 2: Definiera dokumentsökvägar
Därefter måste du definiera sökvägarna för ditt dokument och utdatafilen där det vattenmärkta dokumentet ska sparas.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` med den faktiska sökvägen till dokumentet du vill vattenstämpla och`"Your Document Directory"` med katalogen där du vill spara det vattenmärkta dokumentet.
## Steg 3: Ladda dokumentet från en ström
Låt oss nu ladda dokumentet från en ström. Detta innebär att dokumentet öppnas som en ström och sedan använda`Watermarker` klass från GroupDocs.Watermark-biblioteket för att hantera det.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Din kod för att hantera vattenstämplar kommer hit
}
```
 Detta kodavsnitt säkerställer att dokumentet öppnas som en ström och`Watermarker` klass initieras med denna ström. De`using` Uttalanden säkerställer att resurser kasseras på rätt sätt efter användning.
## Steg 4: Skapa och lägg till en vattenstämpel
Att skapa ett vattenmärke är enkelt med GroupDocs.Watermark. I det här exemplet skapar vi en enkel textvattenstämpel.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Här skapar vi en`TextWatermark` objekt med texten "Testa vattenstämpel" och ange teckensnittsdetaljerna. Sedan lägger vi till denna vattenstämpel i dokumentet med hjälp av`Add` metod för`Watermarker` klass.
## Steg 5: Spara det vattenmärkta dokumentet
Spara slutligen det vattenmärkta dokumentet till den angivna utmatningsvägen.
```csharp
watermarker.Save(outputFileName);
```
 Denna kod sparar dokumentet med den nyligen tillagda vattenstämpeln`outputFileName` sökväg du definierade tidigare.

## Slutsats
Grattis! Du har framgångsrikt lagt till en vattenstämpel i ditt dokument med GroupDocs.Watermark for .NET. Detta bibliotek gör det otroligt enkelt att hantera vattenstämplar i en mängd olika dokumentformat. Oavsett om du behöver lägga till text, bilder eller andra typer av vattenstämplar har GroupDocs.Watermark de verktyg du behöver. Glöm inte att kolla in[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) för mer avancerade funktioner och anpassningsalternativ.
## FAQ's
### Vilka typer av vattenstämplar kan jag lägga till med GroupDocs.Watermark for .NET?
Du kan lägga till textvattenstämplar, bildvattenstämplar och till och med komplexa former och logotyper. Biblioteket stöder ett brett utbud av anpassningsalternativ.
### Kan jag ta bort vattenstämplar från dokument med GroupDocs.Watermark?
Ja, GroupDocs.Watermark låter dig ta bort befintliga vattenstämplar från dokument också.
### Finns det en gratis testversion tillgänglig för GroupDocs.Watermark?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur köper jag en licens för GroupDocs.Watermark?
Du kan köpa en licens direkt från[GroupDocs webbplats](https://purchase.groupdocs.com/buy).
### Var kan jag få support om jag stöter på problem?
 För support kan du besöka[Supportforum för GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).