---
title: Rastrovat stránku PDF
linktitle: Rastrovat stránku PDF
second_title: GroupDocs.Watermark .NET API
description: Vylepšete zabezpečení dokumentů pomocí GroupDocs pro .NET. Bezproblémově přidejte vodoznaky do PDF a dalších formátů.
weight: 28
url: /cs/net/pdf-watermarking-attachments/rasterize-pdf-page/
type: docs
---
# Rastrovat stránku PDF

## Úvod
GroupDocs.Watermark for .NET je výkonné rozhraní API, které umožňuje vývojářům bezproblémově přidávat vodoznaky do různých formátů dokumentů, včetně PDF, Wordu, Excelu, PowerPointu a dalších. Se svým intuitivním rozhraním a rozsáhlými funkcemi zjednodušuje GroupDocs.Watermark proces přidávání textových nebo obrazových vodoznaků do dokumentů a umožňuje uživatelům bez námahy chránit jejich duševní vlastnictví a zvýšit zabezpečení dokumentů.
## Předpoklady
Než se pustíte do používání GroupDocs.Watermark pro .NET, ujistěte se, že máte splněny následující předpoklady:
1. Instalace: Stáhněte a nainstalujte GroupDocs.Watermark for .NET z[stránka ke stažení](https://releases.groupdocs.com/Watermark/net/).
2.  Licence: Získejte licenci pro GroupDocs.Watermark pro .NET. Dočasnou licenci pro zkušební účely můžete získat od[tady](https://purchase.groupdocs.com/temporary-license/) nebo si zakupte plnou licenci od[nákupní stránku](https://purchase.groupdocs.com/buy).
3. .NET Framework: Ujistěte se, že máte na svém vývojovém počítači nainstalováno rozhraní .NET Framework.
4. Dokument: Připravte dokument, do kterého chcete přidat vodoznak.

## Importovat jmenné prostory
Chcete-li začít používat GroupDocs.Watermark pro .NET, importujte do svého projektu potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Váš kód je zde
}
```
## Krok 2: Inicializujte vodoznak
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Krok 3: Přidejte vodoznak
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Krok 4: Rastrujte stránku
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Krok 5: Uložte dokument
```csharp
watermarker.Save(outputFileName);
```

## Závěr
Na závěr, GroupDocs.Watermark for .NET nabízí bezproblémové řešení pro přidávání vodoznaků do PDF a dalších formátů dokumentů. Podle výše uvedeného podrobného průvodce mohou vývojáři efektivně rastrovat stránky PDF a snadno zvýšit zabezpečení dokumentů.
## FAQ
### Je GroupDocs.Watermark kompatibilní s jinými formáty dokumentů kromě PDF?
Ano, GroupDocs.Watermark podporuje širokou škálu formátů dokumentů, včetně Wordu, Excelu, PowerPointu, Visia a dalších.
### Mohu upravit vzhled vodoznaku přidaného do dokumentu?
Absolutně! GroupDocs.Watermark poskytuje rozsáhlé možnosti přizpůsobení textových a obrazových vodoznaků a umožňuje uživatelům upravit písmo, velikost, barvu, krytí a umístění podle jejich preferencí.
### Je GroupDocs.Watermark vhodný pro osobní i komerční použití?
Ano, GroupDocs.Watermark nabízí flexibilní možnosti licencování, které uspokojí individuální i podnikové potřeby, takže je vhodný pro osobní projekty i rozsáhlé komerční aplikace.
### Nabízí GroupDocs.Watermark technickou podporu pro vývojáře?
Ano, vývojáři mají přístup ke komplexní technické podpoře prostřednictvím fóra GroupDocs.Watermark, kde mohou hledat pomoc, sdílet zkušenosti a spolupracovat s ostatními vývojáři.
### Mohu GroupDocs.Watermark před nákupem vyzkoušet?
Rozhodně! Můžete využít bezplatnou zkušební verzi GroupDocs.Watermark z[stránka vydání](https://releases.groupdocs.com/), což vám umožní prozkoumat jeho vlastnosti a funkce, než se zavážete k nákupu.