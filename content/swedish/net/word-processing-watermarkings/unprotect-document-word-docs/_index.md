---
title: Ta bort skyddet av dokument i Word Docs
linktitle: Ta bort skyddet av dokument i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du enkelt tar bort skyddet av Word-dokument med GroupDocs.Watermark för .NET. Följ vår steg-för-steg-guide.
type: docs
weight: 38
url: /sv/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## Introduktion
GroupDocs.Watermark for .NET är ett kraftfullt API som låter utvecklare arbeta med vattenstämplar i olika dokumentformat, inklusive Word-dokument. I den här självstudien guidar vi dig genom processen att avskydda ett Word-dokument med GroupDocs.Watermark för .NET. Oavsett om du är en erfaren utvecklare eller precis har börjat med .NET-utveckling, hjälper den här steg-för-steg-guiden dig att utföra uppgiften effektivt.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
1.  GroupDocs.Watermark for .NET: Du måste ha GroupDocs.Watermark for .NET API installerat i din utvecklingsmiljö. Du kan ladda ner den från[här](https://releases.groupdocs.com/Watermark/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö inställd för .NET-utveckling, inklusive Visual Studio eller någon annan kompatibel IDE.
3. Word-dokument: Ha ett Word-dokument som du vill ta bort skyddet redo i ditt filsystem.

## Importera namnområden
Innan du dyker in i koden måste du importera de nödvändiga namnrymden till ditt .NET-projekt. Detta ger dig tillgång till funktionerna som tillhandahålls av GroupDocs.Watermark för .NET sömlöst.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Steg 1: Ange dokumentsökväg
Definiera sökvägen till ditt Word-dokument som du vill ta bort skyddet.
```csharp
string documentPath = "Your Document Path";
```
 Byta ut`"Your Document Path"` med den faktiska sökvägen till ditt Word-dokument.
## Steg 2: Ställ in utdatafilnamn
Ange katalogen där du vill spara det oskyddade dokumentet och ange ett namn för utdatafilen.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Byta ut`"Your Document Directory"` med katalogsökvägen där du vill spara utdatafilen.
## Steg 3: Ladda dokument med alternativ
 Skapa en instans av`WordProcessingLoadOptions` för att ladda Word-dokumentet med specifika alternativ.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Steg 4: Ta bort skyddet av dokumentet
 Instantiera`Watermarker` klass med dokumentsökväg och laddningsalternativ. Hämta sedan innehållet i dokumentet som WordProcessingContent och avskydda det.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## Slutsats
Genom att följa dessa steg kan du enkelt ta bort skyddet av ett Word-dokument med GroupDocs.Watermark for .NET. Detta API ger ett enkelt sätt att manipulera vattenstämplar och skydda dina dokument effektivt.
## FAQ's
### Är GroupDocs.Watermark for .NET kompatibelt med alla versioner av .NET?
Ja, GroupDocs.Watermark för .NET är kompatibelt med .NET Framework 2.0 och senare versioner, inklusive .NET Core och .NET Standard.
### Kan jag använda vattenstämplar på dokument i andra format än Word?
Absolut! GroupDocs.Watermark for .NET stöder ett brett utbud av dokumentformat, inklusive PDF, Excel, PowerPoint och mer.
### Finns det en testversion tillgänglig för GroupDocs.Watermark för .NET?
 Ja, du kan få en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur kan jag få teknisk support för GroupDocs.Watermark for .NET?
 Du kan besöka[GroupDocs.Watermark forum](https://forum.groupdocs.com/c/watermark/19) för tekniskt stöd och samhällsstöd.
### Kan jag köpa en tillfällig licens för GroupDocs.Watermark för .NET?
 Ja, du kan köpa en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).