---
title: Lägg till låst vattenstämpel till avsnitt i Word Docs
linktitle: Lägg till låst vattenstämpel till avsnitt i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till en låst vattenstämpel i ett specifikt avsnitt i Word-dokument med hjälp av Groupdocs Watermark for .NET med den här omfattande steg-för-steg-guiden.
type: docs
weight: 13
url: /sv/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---
## Introduktion
Letar du efter ett effektivt sätt att lägga till en låst vattenstämpel till ett avsnitt i dina Word-dokument? Kolla inte vidare! Med Groupdocs.Watermark for .NET kan du sömlöst infoga vattenstämplar i Word-dokument samtidigt som du säkerställer att de förblir låsta och manipuleringssäkra. Detta kraftfulla verktyg erbjuder en mängd olika funktioner för att tillgodose dina behov av vattenmärkning, oavsett om det är för varumärkes-, konfidentialitets- eller säkerhetsändamål. I denna steg-för-steg handledning går vi igenom hur du lägger till en låst vattenstämpel till en specifik del av ett Word-dokument med hjälp av Groupdocs.Watermark for .NET. Låt oss dyka in!
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
1.  Groupdocs.Watermark för .NET: Se till att du har Groupdocs.Watermark-biblioteket installerat. Du kan ladda ner den[här](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Se till att du har .NET Framework installerat i din utvecklingsmiljö.
3. IDE: Använd en integrerad utvecklingsmiljö (IDE) som Visual Studio.
4. Dokument: Ett Word-dokument (.docx) för att applicera vattenstämpeln.
## Importera namnområden
Till att börja med måste du importera de nödvändiga namnrymden i ditt projekt. Så här gör du:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda ditt dokument
 Först måste du ladda dokumentet som du vill lägga till vattenstämpeln till. Detta steg innebär att ange sökvägen till ditt dokument och ladda det med hjälp av`Watermarker` klass.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Din vattenmärkningskod kommer hit.
}
```
## Steg 2: Skapa vattenstämpeln
Skapa sedan vattenstämpeln du vill lägga till i ditt dokument. I det här exemplet skapar vi en textvattenstämpel med specifika teckensnittsinställningar och färg.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Steg 3: Konfigurera vattenstämpelalternativ
Konfigurera nu vattenstämpelalternativen för att ange avsnittsindex och låsinställningar. Detta säkerställer att vattenstämpeln läggs till i rätt sektion och är låst.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // Lägg till i det första avsnittet
options.IsLocked = true; // Lås vattenstämpeln
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Låstyp
```
## Steg 4: Lägg till vattenstämpeln i dokumentet
 Med din vattenstämpel och dina alternativ konfigurerade är det dags att lägga till vattenstämpeln i dokumentet med hjälp av`Add` metod för`Watermarker` klass.
```csharp
watermarker.Add(watermark, options);
```
## Steg 5: Spara det ändrade dokumentet
Slutligen sparar du dokumentet med den tillagda vattenstämpeln till önskad utmatningsplats.
```csharp
watermarker.Save(outputFileName);
```
## Slutsats
Att lägga till en låst vattenstämpel i ett specifikt avsnitt i ett Word-dokument med hjälp av Groupdocs Watermark för .NET är en enkel process. Genom att följa dessa steg kan du förbättra säkerheten och integriteten för dina dokument och säkerställa att viktig information skyddas. Oavsett om du skyddar känsliga data eller lägger till en professionell touch till dina dokument, tillhandahåller Groupdocs.Watermark för .NET de verktyg du behöver för att uppnå dina mål effektivt.
## FAQ's
### Vad är Groupdocs.Watermark för .NET?
Groupdocs.Watermark for .NET är ett kraftfullt bibliotek som låter utvecklare lägga till vattenstämplar till olika dokumenttyper, inklusive Word, PDF och bilder, med avancerade anpassnings- och säkerhetsfunktioner.
### Kan jag låsa en vattenstämpel med ett lösenord?
 Ja, du kan skydda vattenstämpeln med ett lösenord genom att ställa in`options.Password` egendom i`WordProcessingWatermarkSectionOptions` klass.
### Är det möjligt att använda olika vattenstämplar på olika delar av ett dokument?
 Absolut! Genom att ställa olika`SectionIndex` värden i`WordProcessingWatermarkSectionOptions`, kan du använda unika vattenstämplar på olika delar av dokumentet.
### Vilka typer av vattenstämplar kan jag lägga till med Groupdocs.Watermark?
Groupdocs.Watermark stöder olika typer av vattenstämplar, inklusive text-, bild- och formvattenstämplar, och erbjuder omfattande anpassningsalternativ för varje typ.
### Var kan jag hitta mer information om Groupdocs.Watermark for .NET?
 För mer information kan du besöka[dokumentation](https://reference.groupdocs.com/Watermark/net/) och[supportforum](https://forum.groupdocs.com/c/watermark/19).