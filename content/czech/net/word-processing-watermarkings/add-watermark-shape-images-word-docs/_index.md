---
title: Přidejte vodoznak k obrázkům tvaru v dokumentech Word
linktitle: Přidejte vodoznak k obrázkům tvaru v dokumentech Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky do tvarů obrázků v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Vylepšete zabezpečení dokumentů pomocí tohoto kurzu.
weight: 17
url: /cs/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---

# Přidejte vodoznak k obrázkům tvaru v dokumentech Word

## Úvod
V tomto tutoriálu prozkoumáme, jak přidat vodoznak do tvaru obrázků v dokumentech Word pomocí GroupDocs.Watermark for .NET. Vodoznak je zásadním aspektem ochrany dokumentů, zejména při práci s citlivými nebo důvěrnými informacemi. Přidáním vodoznaků do tvarových obrázků můžete zajistit integritu a bezpečnost svých dokumentů.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1.  GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Watermark z[stránka ke stažení](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Připravte dokument aplikace Word, kam chcete přidat vodoznak.
3. Vývojové prostředí: Nastavte si preferované vývojové prostředí .NET.
## Importovat jmenné prostory
Před napsáním kódu se ujistěte, že jste importovali potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
Nejprve definujte cestu k dokumentu a zadejte název výstupního souboru:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Krok 2: Inicializujte vodoznak
 Instantovat a`Watermarker` objekt poskytnutím cesty dokumentu a volitelných možností načtení:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Zde přidejte logiku vodoznaku
}
```
## Krok 3: Vytvořte textový vodoznak
Definujte textový vodoznak s požadovanými vlastnostmi, jako je text, písmo, zarovnání, otočení, velikost atd.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Krok 4: Použijte vodoznak na obrázky tvaru
Procházejte sekcemi a tvary dokumentu, abyste identifikovali obrázky tvarů a přidali vodoznak:
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
## Krok 5: Uložte dokument
Uložte dokument s přidaným vodoznakem do zadaného výstupního souboru:
```csharp
watermarker.Save(outputFileName);
```

## Závěr
tomto tutoriálu jsme se naučili, jak pomocí GroupDocs.Watermark for .NET přidávat vodoznaky k tvarování obrázků v dokumentech aplikace Word. Dodržováním tohoto podrobného průvodce a využitím výkonných funkcí GroupDocs.Watermark můžete efektivně zvýšit zabezpečení a ochranu svých dokumentů.
## FAQ
### Mohu upravit vzhled textu vodoznaku?
Ano, můžete upravit různé vlastnosti, jako je písmo, velikost, barva, úhel otočení a zarovnání, a upravit tak vodoznak podle svých preferencí.
### Podporuje GroupDocs.Watermark jiné formáty dokumentů kromě Wordu?
Ano, GroupDocs.Watermark poskytuje podporu pro širokou škálu formátů dokumentů včetně PDF, Excel, PowerPoint a dalších.
### Je možné přidat více vodoznaků do jednoho dokumentu?
V rámci jednoho dokumentu můžete samozřejmě přidat více vodoznaků s různým obsahem, styly a pozicemi.
### Mohu odstranit vodoznaky z dokumentů pomocí GroupDocs.Watermark?
Ano, GroupDocs.Watermark nabízí funkce pro efektivní detekci a odstranění vodoznaků z dokumentů.
### Poskytuje GroupDocs.Watermark kompatibilitu napříč platformami?
Ano, GroupDocs.Watermark je kompatibilní s .NET Framework, .NET Core a .NET Standard, což zajišťuje bezproblémovou integraci napříč různými platformami.