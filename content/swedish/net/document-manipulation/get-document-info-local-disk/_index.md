---
title: Få dokumentinformation från lokal disk
linktitle: Få dokumentinformation från lokal disk
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till, tar bort och extraherar vattenstämplar i dokument med hjälp av GroupDocs Watermark for .NET med den här omfattande steg-för-steg-guiden.
weight: 11
url: /sv/net/document-manipulation/get-document-info-local-disk/
---
## Introduktion
Välkommen till den ultimata guiden om hur du använder GroupDocs.Watermark för .NET! Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här artikeln att gå igenom det väsentliga för att vattenmärka dina dokument med detta kraftfulla verktyg. I slutet kommer du att vara proffs på att bädda in vattenstämplar i dina dokument, och se till att de är skyddade och märkta enligt dina specifikationer.
## Förutsättningar
Innan du dyker in i steg-för-steg-guiden finns det några förutsättningar som du måste uppfylla:
1.  .NET Framework: Se till att du har .NET Framework installerat på ditt system. GroupDocs.Watermark for .NET är kompatibel med olika versioner av .NET Framework, så kontrollera[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) för kompatibilitetsinformation.
2.  GroupDocs.Watermark for .NET Library: Ladda ner och installera den senaste versionen från[nedladdningssida](https://releases.groupdocs.com/Watermark/net/).
3. Utvecklingsmiljö: Du bör ha en utvecklingsmiljö inrättad. Visual Studio är ett populärt val för .NET-utveckling.
4. Grundläggande C#-kunskap: Att förstå grunderna i C#-programmering hjälper dig att följa exemplen.
## Importera namnområden
Innan du kan använda GroupDocs.Watermark för .NET måste du importera de nödvändiga namnrymden till ditt projekt. Detta är en enkel process och väsentlig för att komma åt bibliotekets funktioner.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Låt oss dela upp processen att vattenmärka ett dokument i tydliga, hanterbara steg. Varje steg är utformat för att hjälpa dig att förstå och implementera funktionaliteten med lätthet.
## Steg 1: Ladda ditt dokument
 Det första steget är att ladda dokumentet du vill vattenstämpla. Detta görs med hjälp av`Watermarker` klass, som låter dig komma åt och manipulera ditt dokument.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Dokumentet är nu laddat och redo för vattenmärkning
}
```
 I detta steg, byt ut`"Your Document Path"` med den faktiska sökvägen till ditt dokument. Detta initierar`Watermarker`objekt, vilket ger dig tillgång till olika vattenmärkningsfunktioner.
## Steg 2: Få dokumentinformation
Innan du lägger till en vattenstämpel kanske du vill samla in lite information om dokumentet. Detta kan vara användbart för att anpassa din vattenstämpel baserat på dokumentegenskaper.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 I det här steget`GetDocumentInfo` metoden hämtar detaljer som filtyp, sidantal och dokumentstorlek. Denna information skrivs ut på konsolen, men du kan använda den i din applikation efter behov.
## Steg 3: Lägg till en textvattenstämpel
Nu när du har ditt dokument laddat och dess information till hands är det dags att lägga till en vattenstämpel. Vi börjar med en enkel textvattenstämpel.

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
 Här skapar du en`TextWatermark` objekt med önskad text, typsnitt och stil. Justera egenskaper som färg, opacitet och rotationsvinkel för att passa dina behov. Slutligen läggs vattenstämpeln till i dokumentet och sparas på en angiven sökväg.
## Steg 4: Lägg till en bildvattenstämpel
Textvattenstämplar är bra, men vad händer om du vill lägga till en logotyp eller en annan bild? Det här steget beskriver hur du lägger till en bildvattenstämpel.

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
 Byta ut`"Path to Your Image"` med sökvägen till din vattenstämpelbild. Ställ in egenskaper som opacitet och rotationsvinkel för att anpassa utseendet på din bildvattenstämpel. Processen att lägga till och spara vattenstämpeln liknar den för en textvattenstämpel.
## Steg 5: Ta bort befintliga vattenstämplar
 Ibland kan du behöva ta bort befintliga vattenstämplar från ett dokument. Detta kan göras med hjälp av`Remove` metod som tillhandahålls av`Watermarker` klass.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Här, den`Remove` metod används för att ta bort textvattenstämplar från dokumentet. Du kan ange olika typer av vattenstämplar som ska tas bort, till exempel bild eller text, beroende på dina behov. Spara dokumentet på en ny sökväg för att se ändringarna.
## Steg 6: Extrahera vattenstämplar
Om du behöver extrahera och inspektera vattenstämplar från ett dokument, gör GroupDocs.Watermark för .NET detta möjligt med lätthet.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Ytterligare egenskaper och logik för varje vattenstämpel
    }
}
```
 Detta steg innebär att använda`GetWatermarks`metod för att hämta alla vattenstämplar i ett dokument. Du kan sedan iterera genom listan med vattenstämplar och inspektera deras egenskaper eller utföra ytterligare åtgärder efter behov.
## Slutsats
 Grattis! Du har nu lärt dig hur du använder GroupDocs.Watermark för .NET för att lägga till, ta bort och extrahera vattenstämplar från dina dokument. Med dessa färdigheter kan du skydda och varumärkesmärka dina dokument effektivt. Kom ihåg att[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) finns alltid där om du behöver mer detaljerad information eller avancerad funktionalitet.
## FAQ's
### Kan jag använda GroupDocs.Watermark för .NET med någon .NET-version?
 Ja, GroupDocs.Watermark för .NET är kompatibelt med olika .NET Framework-versioner. Kolla[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) för detaljer.
### Var kan jag ladda ner GroupDocs.Watermark för .NET?
 Du kan ladda ner den senaste versionen från[nedladdningssida](https://releases.groupdocs.com/Watermark/net/).
### Hur får jag en tillfällig licens?
 Du kan få en tillfällig licens från[sida för tillfällig licens](https://purchase.groupdocs.com/temporary-license/).
### Finns det en gratis provperiod?
 Ja, du kan starta en gratis provperiod genom att besöka[gratis provsida](https://releases.groupdocs.com/).
### Var kan jag få support om jag stöter på problem?
 Support finns tillgänglig på[GroupDocs Watermark forum](https://forum.groupdocs.com/c/watermark/19).