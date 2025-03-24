---
title: Lägg till vattenstämpel till alla bilagor i PDF
linktitle: Lägg till vattenstämpel till alla bilagor i PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du lägger till vattenstämplar i PDF-bilagor med GroupDocs.Watermark for .NET. Säkra dina dokument enkelt med anpassade vattenstämplar.
weight: 16
url: /sv/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---

# Lägg till vattenstämpel till alla bilagor i PDF

## Introduktion
Att lägga till vattenstämplar i PDF-bilagor kan vara ett avgörande steg i dokumenthanteringen, särskilt när man säkerställer säkerhet eller varumärke. GroupDocs.Watermark för .NET erbjuder en omfattande lösning för att sömlöst bädda in vattenstämplar i PDF-filer. I den här handledningen guidar vi dig genom processen att lägga till en vattenstämpel till alla bilagor i ett PDF-dokument med GroupDocs.Watermark för .NET.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1.  GroupDocs.Watermark for .NET: Om du inte redan har gjort det, ladda ner och installera GroupDocs.Watermark for .NET från[hemsida](https://releases.groupdocs.com/Watermark/net/).
2. Utvecklingsmiljö: Sätt upp en lämplig utvecklingsmiljö med Visual Studio eller någon annan .NET-kompatibel IDE.
3. PDF-dokument: Förbered PDF-dokumentet som du vill lägga till vattenstämplar i, tillsammans med de bilagor du vill vattenstämpla.

## Importera namnområden
Innan du dyker in i koden, se till att importera de nödvändiga namnområdena för att komma åt GroupDocs.Watermark for .NET-funktioner:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Steg 1: Definiera dokumentsökväg och utdatakatalog
Definiera först sökvägen till ditt inmatade PDF-dokument och katalogen där det vattenmärkta dokumentet ska sparas:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Steg 2: Initiera laddningsalternativ och vattenstämpel
Initiera sedan laddningsalternativen för PDF-dokumentet och skapa en textvattenstämpel:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Steg 3: Ladda dokument och bilagor
Ladda PDF-dokumentet och gå igenom dess bilagor:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Steg 4: Kontrollera stöd för bilagor
Kontrollera om den bifogade filen stöds av GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Steg 5: Lägg till vattenstämpel till bilagor
Ladda det bifogade dokumentet och lägg till vattenstämpeln:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Steg 6: Spara ändringar
Slutligen, spara ändringarna i det vattenmärkta PDF-dokumentet:
```csharp
    watermarker.Save(outputFileName);
}
```

## Slutsats
I den här handledningen har vi utforskat hur man lägger till vattenstämplar till alla bilagor i ett PDF-dokument med GroupDocs.Watermark for .NET. Genom att följa den steg-för-steg-guiden kan du sömlöst integrera vattenstämplar i dina PDF-filer, vilket säkerställer dokumentsäkerhet och varumärke.
## FAQ's
### Kan jag anpassa utseendet på vattenstämpeln?
Ja, du kan anpassa olika aspekter som text, teckensnitt, storlek, färg och placering av vattenstämpeln enligt dina krav.
### Stöder GroupDocs.Watermark andra dokumentformat än PDF?
Ja, GroupDocs.Watermark stöder ett brett utbud av dokumentformat inklusive Microsoft Word, Excel, PowerPoint, Visio, Outlook och Bilder.
### Finns det en testversion tillgänglig för GroupDocs.Watermark?
Ja, du kan utforska funktionerna i GroupDocs.Watermark genom att ladda ner den kostnadsfria testversionen från webbplatsen.
### Kan jag lägga till flera vattenstämplar i ett enda dokument?
Absolut, GroupDocs.Watermark låter dig lägga till flera vattenstämplar inklusive text, bild och anteckningar samtidigt för att förbättra dokumentsäkerheten och varumärket.
### Finns teknisk support tillgänglig för GroupDocs.Watermark-användare?
Ja, GroupDocs tillhandahåller omfattande teknisk support genom forum och dedikerade supportkanaler för att hjälpa användare med alla frågor eller problem de kan stöta på.