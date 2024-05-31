---
title: Přidejte vodoznak k obrázkům anotací v PDF
linktitle: Přidejte vodoznak k obrázkům anotací v PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se chránit své dokumenty PDF přidáním vodoznaků do obrázků anotací pomocí Groupdocs.Watermark for .NET.
type: docs
weight: 17
url: /cs/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak přidat vodoznaky do obrázků anotací v dokumentech PDF pomocí Groupdocs.Watermark for .NET. Vodoznak je zásadní pro ochranu vašich dokumentů před neoprávněným použitím nebo distribucí. Podle tohoto podrobného průvodce se naučíte, jak efektivně aplikovat textové vodoznaky na obrázky anotací v souborech PDF.
## Předpoklady
Než budete pokračovat, ujistěte se, že máte následující:
1. Základní znalost programovacího jazyka C#.
2. Nainstalovaná knihovna Groupdocs.Watermark pro .NET.
3. Přístup k vývojovému prostředí, jako je Visual Studio.
4. Dokument PDF s obrázky anotací k vodoznaku.

## Import jmenných prostorů
Nejprve musíte do kódu C# importovat potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Načtěte dokument PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 2: Získejte obsah PDF a inicializujte vodoznak
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Inicializujte vodoznak obrázku nebo textu
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Krok 3: Iterujte stránky PDF a obrázky s poznámkami
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Přidejte do obrázku vodoznak
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Krok 4: Uložte dokument s vodoznakem
```csharp
    watermarker.Save(outputFileName);
}
```
Po provedení těchto kroků bude mít váš dokument PDF k obrázkům anotací přidán zadaný vodoznak.

## Závěr
Přidání vodoznaků k obrázkům anotací v souborech PDF je nezbytné pro ochranu integrity vašich dokumentů a zajištění toho, aby nebyly zneužity. S Groupdocs.Watermark for .NET se tento proces stává jednoduchým a efektivním, což vám umožní efektivně chránit vaše soubory PDF.
## FAQ
### Mohu do stejného dokumentu PDF přidat více vodoznaků?
Ano, do stejného dokumentu PDF můžete přidat více vodoznaků pomocí Groupdocs.Watermark for .NET.
### Podporuje Groupdocs.Watermark jiné formáty dokumentů kromě PDF?
Ano, Groupdocs podporuje různé formáty dokumentů, včetně Wordu, Excelu, PowerPointu a dalších.
### Je možné upravit vzhled vodoznaku?
Text, písmo, barvu, velikost a polohu vodoznaku můžete samozřejmě přizpůsobit podle svých preferencí.
### Mohu odstranit vodoznaky z dokumentů PDF pomocí Groupdocs.Watermark?
Ano, Groupdocs.Watermark poskytuje funkce pro snadné odstranění vodoznaků z dokumentů PDF.
### Je k dispozici nějaká bezplatná zkušební verze pro Groupdocs.Watermark pro .NET?
Ano, můžete využít bezplatnou zkušební verzi Groupdocs.Watermark for .NET z webu.