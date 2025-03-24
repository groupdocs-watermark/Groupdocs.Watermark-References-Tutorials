---
title: Få forminformation i Word Docs
linktitle: Få forminformation i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lås upp värdefulla insikter från Word-dokument utan ansträngning med GroupDocs Watermark for .NET. Extrahera forminformation sömlöst för förbättrad dataanalys.
weight: 24
url: /sv/net/word-processing-watermarkings/get-shapes-information-word-docs/
---
## Introduktion
I det digitala landskapet där data är kung är det ytterst viktigt att extrahera meningsfulla insikter från dokument. GroupDocs.Watermark for .NET ger utvecklare möjlighet att fördjupa sig i dokumentstrukturer och extrahera värdefull information utan ansträngning. I den här handledningen kommer vi att utforska hur man kan utnyttja detta kraftfulla verktyg för att få forminformation från Word-dokument steg för steg.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:
1.  GroupDocs.Watermark för .NET: Ladda ner och installera biblioteket från[hemsida](https://releases.groupdocs.com/Watermark/net/).
2. Utvecklingsmiljö: Konfigurera en .NET-utvecklingsmiljö, inklusive Visual Studio eller valfri textredigerare.
3. Tillgång till Word-dokument: Ha tillgång till de Word-dokument som du vill extrahera forminformation från.

## Importera nödvändiga namnområden
Innan du fortsätter med koden är det viktigt att importera de nödvändiga namnrymden:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
```
## Steg 1: Ladda dokumentet
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
 Se till att byta ut`"Your Document Path"` med den faktiska sökvägen till ditt Word-dokument.
## Steg 2: Extrahera forminformation
```csharp
	WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
	foreach (WordProcessingSection section in content.Sections)
	{
		foreach (WordProcessingShape shape in section.Shapes)
		{
```
Detta utdrag hämtar innehållet i Word-dokumentet och itererar över varje avsnitt och form inom.
## Steg 3: Analysera formattribut
```csharp
			if (shape.HeaderFooter != null)
			{
				Console.WriteLine("In header/footer");
			}
			Console.WriteLine(shape.ShapeType);
			Console.WriteLine(shape.Width);
			Console.WriteLine(shape.Height);
			Console.WriteLine(shape.IsWordArt);
			Console.WriteLine(shape.RotateAngle);
			Console.WriteLine(shape.AlternativeText);
			Console.WriteLine(shape.Name);
			Console.WriteLine(shape.X);
			Console.WriteLine(shape.Y);
			Console.WriteLine(shape.Text);
			if (shape.Image != null)
			{
				Console.WriteLine(shape.Image.Width);
				Console.WriteLine(shape.Image.Height);
				Console.WriteLine(shape.Image.GetBytes().Length);
			}
			Console.WriteLine(shape.HorizontalAlignment);
			Console.WriteLine(shape.VerticalAlignment);
			Console.WriteLine(shape.RelativeHorizontalPosition);
			Console.WriteLine(shape.RelativeVerticalPosition);
		}
	}
}
```
Den här delen av kodavsnittet hämtar olika attribut för varje form, såsom dess typ, dimensioner, position, text med mera.

## Slutsats
GroupDocs.Watermark for .NET förenklar extraheringen av forminformation från Word-dokument, vilket ger utvecklare en sömlös lösning för att fördjupa sig i dokumentstrukturer utan ansträngning. Genom att följa stegen som beskrivs i den här handledningen kan du låsa upp värdefulla insikter från dina dokument, vilket förbättrar dina dataanalysmöjligheter.
## FAQ's
### Är GroupDocs.Watermark kompatibel med andra dokumentformat?
Ja, GroupDocs Watermark stöder olika dokumentformat, inklusive PDF, Excel, PowerPoint och mer.
### Kan jag använda vattenstämplar på dokument med GroupDocs.Watermark?
Absolut, GroupDocs.Watermark gör att du enkelt kan lägga till vattenstämplar till dokument programmatiskt.
### Erbjuder GroupDocs.Watermark stöd för anpassad dokumenttolkning?
Faktum är att GroupDocs.Watermark ger flexibla alternativ för anpassad dokumenttolkning för att passa olika användningsfall.
### Är GroupDocs.Watermark lämplig för dokumentbehandling på företagsnivå?
Ja, GroupDocs.Watermark är utformad för att möta behoven av dokumentbehandling på företagsnivå, och erbjuder robusta funktioner och skalbarhet.
### Kan jag integrera GroupDocs.Watermark i mina befintliga .NET-projekt?
Visst, GroupDocs.Watermark integreras sömlöst i .NET-projekt, vilket ger en heltäckande lösning för dokumentmanipulation.