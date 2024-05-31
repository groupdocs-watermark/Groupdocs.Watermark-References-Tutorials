---
title: Použití typu tvaru v dokumentech Word
linktitle: Použití typu tvaru v dokumentech Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se manipulovat s tvary v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Tento kurz poskytuje návod pro efektivní zpracování dokumentů.
type: docs
weight: 37
url: /cs/net/word-processing-watermarkings/shape-type-usage-word-docs/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak používat typy tvarů v dokumentech aplikace Word pomocí GroupDocs.Watermark pro .NET. Tvary v dokumentech aplikace Word se mohou lišit a pochopení toho, jak s nimi manipulovat, může být klíčové pro různé úlohy zpracování dokumentů.
## Předpoklady
Než začneme, ujistěte se, že máte splněny následující předpoklady:
1.  Knihovna GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Watermark for .NET z[odkaz ke stažení](https://releases.groupdocs.com/Watermark/net/).
2. Cesta dokumentu: Připravte dokument Wordu ke zpracování.
3. Vývojové prostředí: Nastavte vhodné vývojové prostředí s podporou .NET frameworku.

## Importovat jmenné prostory
Chcete-li začít, musíte do projektu importovat potřebné jmenné prostory. Tyto jmenné prostory budou poskytovat přístup k požadovaným třídám a metodám pro práci s dokumenty aplikace Word.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Krok 1: Vložte dokument
Začněte načtením dokumentu aplikace Word do objektu Watermarker. Ujistěte se, že jste během procesu načítání specifikovali cestu dokumentu a všechny další požadované možnosti.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Zde je kód pro zpracování dokumentu
}
```
## Krok 2: Přístup k obsahu dokumentu
 Přístup k obsahu načteného dokumentu aplikace Word pomocí`GetContent<WordProcessingContent>()` metoda. To poskytne přístup k oddílům, odstavcům a tvarům přítomným v dokumentu.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Krok 3: Iterujte sekcemi a tvary
Procházejte každou sekci a tvar v dokumentu, abyste si je mohli prohlédnout a podle potřeby s nimi manipulovat.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Zde je kód manipulace s tvarem
    }
}
```
## Krok 4: Zkontrolujte typy tvarů
 rámci smyčky zkontrolujte konkrétní typy tvarů pomocí`ShapeType` vlastnictví. Tento příklad ukazuje identifikaci a manipulaci Diagonální rohy Zaoblené tvary.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Zde je manipulační kód specifický pro tvar
}
```
## Krok 5: Manipulujte s tvary
Proveďte akce, jako je přidání textu, úprava formátování nebo použití vizuálních změn na identifikované tvary.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Krok 6: Uložte dokument
Po provedení všech nezbytných úprav uložte dokument s použitými změnami do určeného výstupního souboru.
```csharp
watermarker.Save(outputFileName);
```

## Závěr
Manipulace s tvary v dokumentech aplikace Word může být nezbytná pro různé úlohy zpracování dokumentů. S GroupDocs.Watermark for .NET můžete snadno identifikovat, upravovat a manipulovat s tvary tak, aby efektivně vyhovovaly vašim požadavkům.
## FAQ
### Dokáže GroupDocs.Watermark for .NET zpracovat jiné formáty dokumentů kromě Wordu?
Ano, GroupDocs.Watermark for .NET podporuje širokou škálu formátů dokumentů, včetně PDF, Excel, PowerPoint a dalších.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, máte přístup k bezplatné zkušební verzi z[stránka vydání](https://releases.groupdocs.com/).
### Poskytuje GroupDocs.Watermark for .NET technickou podporu?
 Ano, můžete vyhledat pomoc a zapojit se do komunity prostřednictvím[Fórum podpory](https://forum.groupdocs.com/c/watermark/19).
### Mohu přizpůsobit proces vodoznaku pro konkrétní požadavky na dokument?
Rozhodně, GroupDocs.Watermark for .NET nabízí rozsáhlé možnosti přizpůsobení pro přizpůsobení procesu vodoznaku podle vašich potřeb.
### Jak mohu získat dočasnou licenci pro GroupDocs.Watermark for .NET?
 Dočasnou licenci můžete získat od[Stránka pro dočasný nákup licence](https://purchase.groupdocs.com/temporary-license/) pro účely testování a hodnocení.