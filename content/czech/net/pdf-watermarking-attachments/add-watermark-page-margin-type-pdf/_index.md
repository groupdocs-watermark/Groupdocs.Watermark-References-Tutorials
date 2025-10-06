---
title: Přidejte vodoznak s typem okraje stránky v PDF
linktitle: Přidejte vodoznak s typem okraje stránky v PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak přidat vodoznaky s typem okraje stránky do PDF pomocí Groupdocs Watermark for .NET. Zabezpečte své dokumenty bez námahy.
weight: 21
url: /cs/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
type: docs
---
# Přidejte vodoznak s typem okraje stránky v PDF

## Úvod
dnešní digitální době je zabezpečení dokumentů důležitější než kdy jindy. Jedním ze způsobů, jak zajistit integritu a pravost vašich dokumentů, je přidání vodoznaků. Groupdocs.Watermark for .NET je výjimečný nástroj navržený tak, aby byl tento proces snadný. V tomto tutoriálu vás provedeme kroky k přidání vodoznaku s typem okraje stránky do PDF pomocí Groupdocs.Watermark for .NET.
## Předpoklady
Než se pustíte do výukového programu, ujistěte se, že máte splněny následující předpoklady:
-  Groupdocs.Watermark for .NET: Stáhněte a nainstalujte[Nejnovější verze](https://releases.groupdocs.com/Watermark/net/) of Groupdocs.Watermark pro .NET.
- Vývojové prostředí: Vývojové prostředí .NET jako Visual Studio.
- Základní znalost C#: Znalost programovacího jazyka C#.
- Dokument PDF: Dokument PDF, do kterého chcete přidat vodoznak.
## Importovat jmenné prostory
Nejprve musíte importovat potřebné jmenné prostory do vašeho projektu C#. Tyto jmenné prostory budou poskytovat přístup k funkcím Watermark.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Nyní si tento proces rozdělíme na zvládnutelné kroky. Chcete-li do dokumentu PDF přidat vodoznak, postupujte pečlivě podle každého kroku.
## Krok 1: Nastavte cestu k dokumentu a výstupní adresář
Nejprve budete muset zadat cestu k dokumentu a výstupní adresář, kam se uloží PDF s vodoznakem.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Načtěte dokument PDF
 Dále načtete svůj dokument PDF pomocí`PdfLoadOptions` třída. Tato třída vám umožňuje zadat jakékoli možnosti potřebné pro načtení vašeho PDF.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 3: Vytvořte textový vodoznak
Nyní je čas vytvořit vodoznak. V tomto příkladu vytvoříme textový vodoznak se specifickými vlastnostmi, jako je font, velikost a zarovnání.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Krok 4: Nastavte typ okraje stránky
 Chcete-li vodoznak správně umístit, budete muset nastavit typ okraje stránky. Zde nastavíme typ okraje stránky na`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## Krok 5: Přidejte a uložte vodoznak
Nakonec přidejte vodoznak do dokumentu a uložte upravené PDF do určeného výstupního adresáře.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## Závěr
tady to máte! Pomocí těchto kroků můžete snadno přidat vodoznak s určitým typem okraje stránky do dokumentů PDF pomocí Groupdocs.Watermark for .NET. To nejen pomáhá chránit vaše dokumenty, ale také zajišťuje jejich pravost. Ať už pracujete s důvěrnými zprávami, právními dokumenty nebo kreativními díly, vodoznak je jednoduchý, ale účinný způsob, jak chránit váš obsah.
## FAQ
### Co je Groupdocs.Watermark pro .NET?
Groupdocs.Watermark for .NET je výkonná knihovna pro programové přidávání vodoznaků do různých formátů dokumentů. Podporuje obrázky, text a další, což umožňuje rozsáhlé přizpůsobení.
### Mohu tuto metodu použít k vodoznaku jiných typů dokumentů?
Ano, Groupdocs.Watermark for .NET podporuje širokou škálu formátů dokumentů, včetně Wordu, Excelu, PowerPointu a obrázků. Proces je podobný, ale může zahrnovat různé možnosti a třídy.
### Jak mohu získat bezplatnou zkušební verzi Groupdocs.Watermark pro .NET?
 Můžeš[Stáhněte si bezplatnou zkušební verzi](https://releases.groupdocs.com/) z webu Groupdocs a prozkoumat vlastnosti a funkce knihovny.
### Je možné upravit vzhled vodoznaku?
Absolutně! Písmo, velikost, barvu, neprůhlednost, zarovnání a další vlastnosti vodoznaku můžete přizpůsobit svým potřebám.
### Kde mohu získat podporu pro Groupdocs.Watermark pro .NET?
 Pro podporu můžete navštívit[Fórum podpory vodoznaků Groupdocs](https://forum.groupdocs.com/c/watermark/19) kde můžete klást otázky a získat pomoc od komunity a týmu Groupdocs.