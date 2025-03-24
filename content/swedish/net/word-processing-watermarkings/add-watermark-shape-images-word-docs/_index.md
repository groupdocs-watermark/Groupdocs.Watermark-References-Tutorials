---
title: Lägg till vattenstämpel för att forma bilder i Word Docs
linktitle: Lägg till vattenstämpel för att forma bilder i Word Docs
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar för att forma bilder i Word-dokument med GroupDocs.Watermark för .NET. Förbättra dokumentsäkerheten med denna handledning.
weight: 17
url: /sv/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---

# Lägg till vattenstämpel för att forma bilder i Word Docs

## Introduktion
I den här handledningen kommer vi att utforska hur man lägger till en vattenstämpel för att forma bilder i Word-dokument med GroupDocs.Watermark för .NET. Vattenmärkning är en avgörande aspekt av dokumentskydd, särskilt när man hanterar känslig eller konfidentiell information. Genom att lägga till vattenstämplar för att forma bilder kan du säkerställa integriteten och säkerheten för dina dokument.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1.  GroupDocs.Watermark för .NET: Ladda ner och installera GroupDocs.Watermark-biblioteket från[nedladdningssida](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Förbered Word-dokumentet där du vill lägga till vattenstämpeln.
3. Utvecklingsmiljö: Konfigurera din föredragna .NET-utvecklingsmiljö.
## Importera namnområden
Innan du skriver koden, se till att importera de nödvändiga namnrymden:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Ladda dokumentet
Definiera först sökvägen till ditt dokument och ange utdatafilens namn:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Steg 2: Initiera Watermarker
 Instantiera en`Watermarker` objekt genom att tillhandahålla dokumentsökvägen och valfria laddningsalternativ:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Lägg till vattenmärkningslogik här
}
```
## Steg 3: Skapa textvattenstämpel
Definiera textens vattenstämpel med önskade egenskaper som text, teckensnitt, justering, rotation, storlek, etc.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Steg 4: Använd vattenstämpel för att forma bilder
Iterera genom dokumentsektionerna och formerna för att identifiera formbilder och lägg till vattenstämpeln:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Steg 5: Spara dokumentet
Spara dokumentet med den tillagda vattenstämpeln till den angivna utdatafilen:
```csharp
watermarker.Save(outputFileName);
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till vattenstämplar för att forma bilder i Word-dokument med hjälp av GroupDocs.Watermark för .NET. Genom att följa den steg-för-steg-guide och utnyttja de kraftfulla funktionerna i GroupDocs.Watermark kan du förbättra säkerheten och skyddet av dina dokument effektivt.
## FAQ's
### Kan jag anpassa utseendet på vattenstämpeltexten?
Ja, du kan justera olika egenskaper som typsnitt, storlek, färg, rotationsvinkel och justering för att anpassa vattenstämpeln efter dina önskemål.
### Stöder GroupDocs.Watermark andra dokumentformat än Word?
Ja, GroupDocs.Watermark ger stöd för ett brett utbud av dokumentformat inklusive PDF, Excel, PowerPoint och mer.
### Är det möjligt att lägga till flera vattenstämplar i ett enda dokument?
Absolut, du kan lägga till flera vattenstämplar med olika innehåll, stilar och positioner inom samma dokument.
### Kan jag ta bort vattenstämplar från dokument med GroupDocs.Watermark?
Ja, GroupDocs.Watermark erbjuder funktioner för att upptäcka och ta bort vattenstämplar från dokument effektivt.
### Ger GroupDocs.Watermark plattformsoberoende kompatibilitet?
Ja, GroupDocs.Watermark är kompatibelt med .NET Framework, .NET Core och .NET Standard, vilket säkerställer sömlös integration mellan olika plattformar.