---
title: Odebrat vodoznak z PDF
linktitle: Odebrat vodoznak z PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak odstranit vodoznaky ze souborů PDF pomocí GroupDocs.Watermark for .NET. Snadné kroky pro profesionální úpravy dokumentů.
weight: 34
url: /cs/net/pdf-watermarking-attachments/remove-watermark-pdf/
---
## Úvod
V dnešní digitální době je ochrana citlivých dokumentů vodoznakem běžnou praxí. Existují však případy, kdy možná budete muset z různých důvodů odstranit vodoznaky ze souborů PDF. Ať už upravujete dokument nebo prostě potřebujete čistou verzi pro prezentaci, GroupDocs.Watermark for .NET poskytuje bezproblémové řešení pro odstraňování vodoznaků ze souborů PDF.
## Předpoklady
Než se pustíme do odstraňování vodoznaků ze souborů PDF pomocí GroupDocs.Watermark for .NET, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Watermark for .NET Library: Stáhněte a nainstalujte knihovnu z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Vývojové prostředí: Mějte na svém systému nainstalované Visual Studio nebo jakékoli kompatibilní IDE.
3. Dokument s vodoznakem: Připravte dokument PDF obsahující vodoznak, který chcete odstranit.

## Import jmenných prostorů
Ve svém projektu C# začněte importováním potřebných jmenných prostorů:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Krok 1: Načtěte dokument PDF
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
V tomto kroku zadejte cestu k vašemu PDF dokumentu a adresář, kam chcete uložit výstupní soubor.
## Krok 2: Inicializujte vodoznak a kritéria vyhledávání
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
Inicializujte objekt Watermarker s cestou a možnostmi načtení dokumentu PDF. Poté definujte kritéria vyhledávání pro vodoznak, který chcete odstranit. Vodoznaky můžete vyhledávat na základě obrázků nebo textu.
## Krok 3: Vyhledejte a odstraňte vodoznaky
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // Odstraňte všechny nalezené vodoznaky
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
Vyhledejte možné vodoznaky na první stránce dokumentu PDF na základě definovaných kritérií vyhledávání. Poté projděte sbírku možných vodoznaků a jeden po druhém je odstraňte. Nakonec uložte upravený dokument PDF bez vodoznaku.

## Závěr
Odstranění vodoznaků ze souborů PDF je zásadním úkolem v různých scénářích, od úpravy dokumentu až po přípravu prezentace. S GroupDocs.Watermark for .NET můžete bez námahy odstranit vodoznaky ze souborů PDF pomocí jednoduchého kódu C#, čímž zajistíte, že vaše dokumenty budou čisté a profesionální.
## FAQ
### Je GroupDocs.Watermark for .NET kompatibilní se všemi verzemi sady Visual Studio?
Ano, GroupDocs.Watermark for .NET je kompatibilní se všemi verzemi sady Visual Studio, včetně sady Visual Studio 2019 a Visual Studio 2022.
### Mohu odstranit více vodoznaků z jednoho dokumentu PDF pomocí GroupDocs.Watermark for .NET?
Ano, zadáním vhodných kritérií vyhledávání můžete vyhledat a odstranit více vodoznaků z jednoho dokumentu PDF.
### Podporuje GroupDocs.Watermark for .NET jiné formáty dokumentů kromě PDF?
Ano, GroupDocs.Watermark for .NET podporuje širokou škálu formátů dokumentů, včetně dokumentů Word, tabulek Excel, prezentací PowerPoint a dalších.
### Je k dispozici zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi GroupDocs.Watermark for .NET z[tady](https://releases.groupdocs.com/).
### Kde najdu další podporu a pomoc pro GroupDocs.Watermark for .NET?
 Pro další podporu můžete navštívit fórum GroupDocs.Watermark[tady](https://forum.groupdocs.com/c/watermark/19).