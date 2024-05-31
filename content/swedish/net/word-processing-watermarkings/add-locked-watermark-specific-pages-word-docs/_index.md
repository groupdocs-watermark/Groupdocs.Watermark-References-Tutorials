---
title: Lägg till låst vattenstämpel på specifika sidor i Word Docs
linktitle: Lägg till låst vattenstämpel på specifika sidor i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till en låst vattenstämpel på specifika sidor i Word-dokument med hjälp av GroupDocs.Watermark for .NET med vår enkla steg-för-steg-guide.
type: docs
weight: 12
url: /sv/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## Introduktion
Vill du lägga till en vattenstämpel på specifika sidor i dina Word-dokument, men vill att den ska låsas så att den inte enkelt kan tas bort eller redigeras? Du är på rätt plats! I den här självstudien guidar vi dig genom processen att lägga till en låst vattenstämpel på specifika sidor i Word-dokument med hjälp av GroupDocs.Watermark för .NET. Detta kraftfulla bibliotek gör det enkelt att applicera, hantera och anpassa vattenstämplar på en mängd olika dokumenttyper. Oavsett om du är en utvecklare eller bara någon som behöver säkra sina dokument, kommer den här guiden att gå igenom varje steg på ett enkelt sätt.
## Förutsättningar
Innan vi dyker in i handledningen, låt oss se till att du har allt du behöver:
1.  GroupDocs.Watermark för .NET: Du kan[ladda ner](https://releases.groupdocs.com/Watermark/net/) den senaste versionen.
2. Utvecklingsmiljö: En IDE som Visual Studio.
3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering kommer att vara till hjälp.
4. Dokument till vattenstämpel: Ett Word-dokument (.docx eller .doc) som du vill lägga till en vattenstämpel till.
## Importera namnområden
Först måste du importera de nödvändiga namnrymden i ditt C#-projekt. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att arbeta med GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Nu när vi har täckt förutsättningarna och de nödvändiga namnrymden importerade, låt oss bryta ner processen steg för steg.
## Steg 1: Ladda Word-dokumentet
 Till att börja med måste du ladda Word-dokumentet du vill lägga till en vattenstämpel på. Detta kan göras med hjälp av`Watermarker` klass tillsammans med`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Fortsätt till nästa steg
}
```
## Steg 2: Skapa textvattenstämpeln
Skapa sedan en textvattenstämpel. Du kan anpassa texten, teckensnittet, färgen och andra egenskaper enligt dina krav.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Steg 3: Konfigurera vattenstämpelalternativ
 För att applicera vattenstämpeln på specifika sidor och låsa den, konfigurera`WordProcessingWatermarkPagesOptions`Här anger du sidnumren där vattenstämpeln ska visas och ställer in låsalternativen.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Ange sidorna
options.IsLocked = true; // Lås vattenstämpeln
options.LockType = WordProcessingLockType.AllowOnlyComments; // Ställ in låstyp
// För att skydda med ett lösenord
// options.Password = "7654321";
```
## Steg 4: Lägg till vattenstämpeln i dokumentet
Med din vattenstämpel och dina alternativ konfigurerade kan du nu lägga till vattenstämpeln i dokumentet.
```csharp
watermarker.Add(watermark, options);
```
## Steg 5: Spara dokumentet
Slutligen sparar du dokumentet med vattenstämpeln. Välj en lämplig utdatasökväg och spara filen.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Slutsats
Grattis! Du har framgångsrikt lagt till en låst vattenstämpel på specifika sidor i ett Word-dokument med hjälp av GroupDocs.Watermark for .NET. Denna handledning täckte alla viktiga steg från att ladda dokumentet till att spara den vattenmärkta filen. Genom att följa dessa steg kan du se till att dina dokument är säkert vattenmärkta, vilket skyddar ditt innehåll från obehörig redigering och användning.
 För mer information kan du hänvisa till[GroupDocs.Watermark dokumentation](https://reference.groupdocs.com/Watermark/net/) . Om du har några frågor eller behöver ytterligare hjälp, besök gärna[supportforum](https://forum.groupdocs.com/c/watermark/19).
## FAQ's
### Vad är GroupDocs.Watermark för .NET?
GroupDocs.Watermark for .NET är ett kraftfullt bibliotek som låter utvecklare lägga till vattenstämplar i olika typer av dokument, inklusive Word, PDF, Excel och mer.
### Kan jag använda vattenstämplar på flera sidor i ett dokument?
 Ja, du kan ange flera sidnummer i`PageNumbers` array för att applicera vattenstämplar på flera sidor.
### Hur skyddar jag en vattenstämpel med ett lösenord?
 Du kan skydda en vattenstämpel med ett lösenord genom att ställa in`Password` egendom i`WordProcessingWatermarkPagesOptions`.
### Är det möjligt att anpassa utseendet på vattenstämpeln?
Absolut! Du kan anpassa text, teckensnitt, färg, storlek och andra egenskaper för vattenstämpeln för att passa dina behov.
### Var kan jag få en tillfällig licens för GroupDocs.Watermark?
 Du kan få en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).