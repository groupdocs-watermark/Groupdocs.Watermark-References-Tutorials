---
title: Extrahera alla bilagor från PDF
linktitle: Extrahera alla bilagor från PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du extraherar alla bilagor från en PDF med Groupdocs.Watermark for .NET. Följ vår steg-för-steg-guide för en sömlös extraktionsprocess.
type: docs
weight: 22
url: /sv/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
---
## Introduktion
Vill du extrahera bilagor från ett PDF-dokument utan ansträngning? Tja, du är på rätt plats! I den här omfattande handledningen guidar vi dig genom processen att extrahera alla bilagor från en PDF-fil med Groupdocs.Watermark for .NET. Detta kraftfulla bibliotek låter utvecklare hantera vattenstämplar i olika dokumentformat, men det innehåller också robusta funktioner för att extrahera inbäddade filer. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer denna steg-för-steg-guide att göra processen till en lek.
## Förutsättningar
Innan vi dyker in i koden, låt oss täcka grunderna du behöver för att komma igång. Här är en snabb checklista för att säkerställa att du är redo:
1. .NET-miljö: Se till att du har en .NET-utvecklingsmiljö inställd. Du kan använda Visual Studio eller vilken annan .NET IDE som helst.
2.  Groupdocs.Watermark for .NET: Ladda ner och installera den senaste versionen av Groupdocs.Watermark for .NET från[här](https://releases.groupdocs.com/Watermark/net/).
3. Utvecklingsfärdigheter: Grundläggande förståelse för C#-programmering och förtrogenhet med .NET-bibliotek.
4. Exempel på PDF-dokument: Ha ett exempel på PDF-dokument med bilagor som du kan använda för testning.
## Importera namnområden
Innan du börjar koda måste du importera de nödvändiga namnrymden. Detta hjälper till att organisera din kod och ger dig tillgång till de klasser och metoder du kommer att använda.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Steg 1: Konfigurera ditt projekt
Först till kvarn, låt oss ställa in ditt projekt. Öppna din .NET-utvecklingsmiljö och skapa en ny konsolapplikation.
### Skapa ett nytt projekt
1. Öppna Visual Studio.
2. Välj "Skapa ett nytt projekt."
3. Välj "Console App (.NET Core)" eller ".NET Framework" beroende på vad du föredrar.
4. Namnge ditt projekt och klicka på "Skapa".
### Lägg till Groupdocs.Watermark för .NET
1. Högerklicka på ditt projekt i Solution Explorer.
2. Välj "Hantera NuGet-paket."
3. Sök efter "Groupdocs.Watermark" och installera den senaste versionen.
## Steg 2: Definiera dina vägar
Därefter måste du definiera sökvägarna för ditt dokument och utdatakatalog. Det är här din PDF och de extraherade bilagorna kommer att lagras.

 I din`Program.cs` fil, lägg till följande kod för att definiera dina sökvägar:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Path"` och`"Your Document Directory"` med de faktiska sökvägarna på ditt system.
## Steg 3: Ladda ditt PDF-dokument
 Låt oss nu ladda ditt PDF-dokument med Groupdocs.Watermark. Detta steg innebär att skapa laddningsalternativ och initiera`Watermarker` klass.
### Skapa laddningsalternativ
 Skapa först en instans av`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### Initiera Watermarker
 Använd sedan`Watermarker` klass för att ladda ditt dokument:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din kod kommer hit
}
```
## Steg 4: Extrahera bilagor
Med ditt dokument laddat är det dags att extrahera bilagorna. Du kommer att använda`PdfContent` klass för att komma åt bilagorna och sedan spara dem i din angivna utdatakatalog.
### Hämta PDF-innehåll
 Inuti`using` blockera, hämta PDF-innehållet:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Genomföra tillbehör
Gå igenom varje bilaga i PDF:en:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // Spara den bifogade filen på disken
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
Denna kod extraherar varje bilaga och sparar den i din utdatakatalog. Den skriver också ut en del grundläggande information om varje bilaga till konsolen.
## Slutsats
Och där har du det! Du har extraherat bilagor från en PDF-fil med hjälp av Groupdocs.Watermark för .NET. Denna handledning ledde dig genom att ställa in ditt projekt, ladda ditt dokument och extrahera bilagorna steg för steg. Med dessa färdigheter kan du nu enkelt hantera och manipulera PDF-bilagor i dina .NET-program.
## FAQ's
### Vad är Groupdocs.Watermark för .NET?
Groupdocs.Watermark for .NET är ett omfattande bibliotek för att lägga till, ta bort och hantera vattenstämplar i olika dokumentformat, inklusive PDF-filer. Det erbjuder också funktioner för att extrahera inbäddade filer.
### Kan jag extrahera andra typer av filer inbäddade i en PDF?
Ja, Groupdocs.Watermark för .NET låter dig extrahera alla typer av filer som är inbäddade i en PDF, inte bara bilagor.
### Finns det en gratis provperiod?
 Ja, du kan ladda ner en gratis provversion av Groupdocs.Watermark för .NET från[här](https://releases.groupdocs.com/).
### Hur kan jag få support om jag stöter på problem?
 Du kan få stöd genom att besöka[Groupdocs.Watermark supportforum](https://forum.groupdocs.com/c/watermark/19).
### Behöver jag en licens för att använda Groupdocs.Watermark för .NET?
 Ja, du behöver en licens för att använda biblioteket i produktionen. Du kan köpa en licens[här](https://purchase.groupdocs.com/buy) eller skaffa en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/).