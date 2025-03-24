---
title: Extrahera anteckningsinformation från PDF
linktitle: Extrahera anteckningsinformation från PDF
second_title: GroupDocs.Watermark .NET API
description: Lär dig hur du extraherar anteckningsinformation från PDF-dokument med GroupDocs.Watermark for .NET i den här detaljerade steg-för-steg-guiden.
weight: 23
url: /sv/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# Extrahera anteckningsinformation från PDF

## Introduktion
Upplever du ofta att du behöver extrahera detaljerad anteckningsinformation från dina PDF-dokument? Oavsett om du är en utvecklare som arbetar med dokumenthanteringssystem eller en affärsprofessionell som hanterar många PDF-filer, kan det vara avgörande att effektivt extrahera och bearbeta kommentarer. Med GroupDocs.Watermark för .NET har du en kraftfull verktygslåda till ditt förfogande för att göra denna uppgift enkel och effektiv.
## Förutsättningar
Innan vi dyker in i koden, låt oss se till att du har allt du behöver för att komma igång:
1. Visual Studio: Se till att du har Visual Studio installerat. Detta kommer att vara vår IDE för att skriva och köra koden.
2.  GroupDocs.Watermark for .NET: Du måste ha GroupDocs.Watermark for .NET-biblioteket. Du kan[ladda ner den här](https://releases.groupdocs.com/Watermark/net/).
3. Grundläggande kunskaper i C#: Förtrogenhet med C#-programmering är nödvändig för att följa exemplen.
## Importera namnområden
Till att börja med måste du importera de nödvändiga namnrymden till ditt projekt. Dessa namnområden innehåller de klasser och metoder som krävs för att arbeta med PDF-filer och extrahera kommentarer.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Steg 1: Konfigurera ditt projekt
Låt oss först ställa in vårt projekt i Visual Studio. Skapa ett nytt Console App-projekt (.NET Core). När ditt projekt har skapats måste du lägga till en referens till GroupDocs.Watermark for .NET-biblioteket.
1. Öppna NuGet Package Manager.
2.  Söka efter`GroupDocs.Watermark`.
3.  Installera`GroupDocs.Watermark` paket.
## Steg 2: Definiera dokumentsökvägar
Därefter måste du ange sökvägarna för ditt inmatade PDF-dokument och utdatakatalogen där den extraherade informationen kommer att sparas. Detta säkerställer att din applikation vet var PDF-filen kan hittas och var resultaten ska lagras.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Steg 3: Ladda PDF-dokumentet
 För att arbeta med PDF-dokumentet måste vi ladda det med hjälp av`PdfLoadOptions`. Den här klassen ger alternativ för att konfigurera laddningsprocessen.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Koden för att extrahera kommentarer kommer hit
}
```
## Steg 4: Få åtkomst till PDF-innehåll
När dokumentet har laddats kan vi komma åt dess innehåll. Specifikt vill vi få PDF-innehållet så att vi kan iterera genom sidorna och kommentarerna.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Steg 5: Iterera genom sidor och anteckningar
Med PDF-innehållet i handen kan vi gå igenom varje sida och sedan genom varje anteckning på dessa sidor. Detta gör att vi kan extrahera den information vi behöver.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Extrahera anteckningsdetaljer här
    }
}
```
## Steg 6: Extrahera anteckningsdetaljer
Inom de kapslade slingorna extraherar vi olika detaljer om varje anteckning. Detta inkluderar typen av anteckning, eventuella associerade bilder, text och positionsdata.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Steg 7: Spara eller bearbeta extraherade data
Bestäm slutligen vad du vill göra med den extraherade anteckningsinformationen. Du kan skriva ut den till konsolen, spara den i en fil eller till och med lagra den i en databas, beroende på dina behov.
```csharp
// Exempel på att spara extraherade data till en fil
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Slutsats
Att extrahera anteckningsinformation från PDF-dokument med GroupDocs.Watermark för .NET är en enkel process som kan spara mycket tid och ansträngning. Genom att följa stegen som beskrivs i den här guiden kan du enkelt integrera den här funktionen i dina projekt och automatisera extraheringen av värdefull anteckningsdata.
 Oavsett om du hanterar stora volymer PDF-filer eller helt enkelt behöver extrahera specifik information, erbjuder GroupDocs.Watermark för .NET en pålitlig och effektiv lösning. Glöm inte att kolla in[dokumentation](https://tutorials.groupdocs.com/Watermark/net/) för mer avancerade funktioner och anpassningsalternativ.
## FAQ's
### Vad är GroupDocs.Watermark för .NET?
GroupDocs.Watermark for .NET är ett omfattande bibliotek som låter utvecklare lägga till, söka och ta bort vattenstämplar från olika dokumentformat, inklusive PDF-filer, Word-dokument och bilder.
### Kan jag prova GroupDocs.Watermark gratis?
 Ja, du kan få en[gratis provperiod](https://releases.groupdocs.com/) för att testa bibliotekets funktioner innan du gör ett köp.
### Hur får jag support om jag stöter på problem?
 Du kan få support från GroupDocs-teamet genom att besöka dem[supportforum](https://forum.groupdocs.com/c/watermark/19).
### Är det möjligt att få en tillfällig licens för att testa?
 Ja, du kan begära en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/)för teständamål.
### Var kan jag köpa den fullständiga versionen av GroupDocs.Watermark för .NET?
 Du kan köpa den fullständiga versionen från[GroupDocs webbplats](https://purchase.groupdocs.com/buy).