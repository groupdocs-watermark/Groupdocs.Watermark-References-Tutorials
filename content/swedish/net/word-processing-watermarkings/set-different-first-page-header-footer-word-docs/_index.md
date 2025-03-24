---
title: Ställ in annan sidhuvud/sidfot på första sidan i Word Docs
linktitle: Ställ in annan sidhuvud/sidfot på första sidan i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du ställer in olika sidhuvuden och sidfötter på första sidan i Word-dokument med hjälp av GroupDocs.Watermark för .NET.
weight: 36
url: /sv/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---

# Ställ in annan sidhuvud/sidfot på första sidan i Word Docs

## Introduktion
När det gäller dokumenthantering och manipulation framstår GroupDocs.Watermark för .NET som ett kraftfullt verktyg som erbjuder sömlös integration och robusta funktioner för vattenmärkning av dokument. Ett av de vanligaste kraven vid dokumentbehandling är att sätta olika sidhuvuden och sidfötter på första sidan i Word-dokument. Denna handledning kommer att belysa processen för att uppnå denna uppgift med GroupDocs.Watermark för .NET, och dela upp varje steg i lättbegripliga segment.
## Förutsättningar
Innan du går in i implementeringen, se till att följande förutsättningar är uppfyllda:
1.  Installation av GroupDocs.Watermark for .NET: Ladda ner och installera GroupDocs.Watermark for .NET från[nedladdningslänk](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentförberedelse: Ha ett Word-dokument redo som kräver inställning av olika sidhuvuden och sidfötter på sin första sida.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden som krävs för att använda GroupDocs.Watermark for .NET-funktioner:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 det här steget definierar vi sökvägen till dokumentet som behöver bearbetas och anger utdatafilens namn och katalog. Dessutom initierar vi en`Watermarker` objekt med dokumentets sökväg och laddningsalternativ.
## Steg 2: Få åtkomst till dokumentinnehåll
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Här hämtar vi innehållet i Word-dokumentet med hjälp av`GetContent<T>()` metod för`Watermarker` objekt, som anger typen av innehåll som`WordProcessingContent`.
## Steg 3: Konfigurera sidinställningar
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
I det här steget konfigurerar vi sidinställningarna för att aktivera olika sidhuvuden och sidfötter för den första sidan (`DifferentFirstPageHeaderFooter`) samt för udda och jämna sidor (`OddAndEvenPagesHeaderFooter`).
## Steg 4: Spara ändringar
```csharp
watermarker.Save(outputFileName);
```
 Slutligen sparar vi ändringarna som gjorts i dokumentet genom att anropa`Save()` metod för`Watermarker` objekt och skickar utdatafilens namn.

## Slutsats
GroupDocs.Watermark för .NET ger en enkel lösning för att ställa in olika sidhuvuden och sidfötter på första sidan i Word-dokument. Genom att följa stegen som beskrivs i denna handledning kan användare enkelt manipulera dokumentinnehåll enligt deras krav.
## FAQ's
### Kan GroupDocs.Watermark för .NET hantera andra dokumentformat än Word?
Ja, GroupDocs.Watermark för .NET stöder ett brett utbud av dokumentformat inklusive PDF, Excel, PowerPoint och mer.
### Finns det en testversion tillgänglig för teständamål?
Ja, användare kan använda en gratis provversion av GroupDocs.Watermark för .NET från[släpper sida](https://releases.groupdocs.com/).
### Erbjuder GroupDocs.Watermark för .NET teknisk support?
 Ja, teknisk support för GroupDocs för .NET är tillgänglig via[supportforum](https://forum.groupdocs.com/c/watermark/19).
### Kan jag köpa en tillfällig licens för kortvarig användning?
 Ja, tillfälliga licenser för GroupDocs Watermark för .NET kan erhållas från[Sida för tillfällig licensköp](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag hitta omfattande dokumentation för GroupDocs.Watermark for .NET?
 Detaljerad dokumentation för GroupDocs.Watermark för .NET finns tillgänglig på[Referenssida](https://tutorials.groupdocs.com/Watermark/net/).