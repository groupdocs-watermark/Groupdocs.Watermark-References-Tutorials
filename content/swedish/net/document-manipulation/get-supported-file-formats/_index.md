---
title: Skaffa filformat som stöds
linktitle: Skaffa filformat som stöds
second_title: GroupDocs.Watermark .NET API
description: Lägg enkelt till vattenstämplar i dina dokument med GroupDocs.Watermark för .NET. Följ vår omfattande, steg-för-steg-guide för att skydda dina digitala tillgångar.
weight: 13
url: /sv/net/document-manipulation/get-supported-file-formats/
---
## Introduktion
Att vattenmärka dina dokument är ett avgörande steg för att skydda dina digitala tillgångar. Oavsett om det är för att skydda immateriella rättigheter, säkerställa konfidentialitet eller helt enkelt varumärke, spelar vattenstämplar en viktig roll. Om du är en .NET-utvecklare som vill integrera vattenmärkningsfunktioner i dina applikationer, är GroupDocs.Watermark for .NET ett kraftfullt och mångsidigt verktyg som du bör överväga. Denna handledning guidar dig genom det väsentliga med att använda GroupDocs.Watermark, från installation till att applicera din första vattenstämpel, och dela upp varje steg för att säkerställa att du enkelt kan följa med.
## Förutsättningar
Innan vi dyker in i detaljerna, låt oss se till att du har allt du behöver för att komma igång:
1.  Visual Studio: Se till att du har Visual Studio installerat på din dator. Du kan ladda ner den från[Visual Studio hemsida](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark stöder olika versioner av .NET Framework. Se till att ditt projekt är inriktat på en kompatibel version.
3. GroupDocs.Watermark för .NET: Du kan ladda ner den senaste versionen från[släpp sida](https://releases.groupdocs.com/Watermark/net/).
4. Grundläggande kunskaper om C#: Denna handledning förutsätter att du har en grundläggande förståelse för C#- och .NET-utveckling.
## Importera namnområden
Låt oss först importera de nödvändiga namnrymden i ditt projekt. Öppna din C#-fil och lägg till följande med hjälp av direktiv högst upp:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Med dessa namnrymder importerade är du redo att börja lägga till vattenstämplar i dina dokument.

## Steg 1: Initiera Watermarking Engine
 Det första steget är att initiera vattenmärkningsmotorn. Detta innebär att skapa en instans av`Watermarker` klass med dokumentet du vill vattenstämpla.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Detta kodavsnitt ställer in`Watermarker` objekt, som du använder för att applicera vattenstämplar på ditt dokument.
## Steg 2: Lägg till en textvattenstämpel
Låt oss nu lägga till en enkel textvattenstämpel till ditt dokument. Textvattenstämplar är bra för att lägga till etiketter som "Konfidentiellt" eller "Utkast".
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Här har vi skapat en`TextWatermark`objekt med texten "Konfidentiellt", ställ in dess teckensnitt och färg och justerade det till mitten av dokumentet.
## Steg 3: Lägg till en bildvattenstämpel
Om du föredrar att använda en bild som vattenstämpel, gör GroupDocs.Watermark det enkelt att göra det.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 I det här exemplet skapar vi en`ImageWatermark` objekt, ställ in dess dimensioner och justera det till det övre högra hörnet av dokumentet.
## Steg 4: Spara dokumentet
Efter att ha lagt till önskade vattenstämplar är det sista steget att spara det ändrade dokumentet.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Detta kommer att spara det vattenmärkta dokumentet till den angivna sökvägen och frigöra alla resurser som används av det`Watermarker` exempel.
## Steg 5: Skaffa filformat som stöds
För att se vilka filformat som stöds av GroupDocs.Watermark kan du använda följande kodavsnitt:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Detta kommer att skriva ut alla filtyper som GroupDocs.Watermark kan hantera, vilket ger dig en heltäckande bild av dess kapacitet.
## Slutsats
Vattenmärka dina dokument med GroupDocs Watermark för .NET är enkelt och effektivt. Genom att följa den här handledningen har du lärt dig hur du initierar vattenmärkningsmotorn, lägger till text- och bildvattenstämplar, sparar dina vattenstämplade dokument och listar filformat som stöds. Med dessa verktyg kan du skydda dina dokument med tillförsikt.
 Om du har några frågor eller behöver ytterligare hjälp, tveka inte att besöka[Supportforum för GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## FAQ's
### Hur installerar jag GroupDocs.Watermark för .NET?
 Du kan ladda ner den från[släpp sida](https://releases.groupdocs.com/Watermark/net/) och lägg till DLL till ditt projekt.
### Kan jag prova GroupDocs.Watermark gratis?
 Ja, du kan begära en[gratis provperiod](https://releases.groupdocs.com/) att utvärdera programvaran innan du köper den.
### Vilka filformat stöds av GroupDocs.Watermark?
Du kan använda det medföljande kodavsnittet för att lista alla filformat som stöds.
### Hur kan jag köpa en licens för GroupDocs.Watermark?
 Licenser kan köpas direkt från[köpsidan](https://purchase.groupdocs.com/buy).
### Finns det någon dokumentation tillgänglig för GroupDocs.Watermark?
 Ja, omfattande dokumentation finns tillgänglig[här](https://tutorials.groupdocs.com/Watermark/net/).