---
title: Nahraďte text za konkrétní tvar v dokumentech Word
linktitle: Nahraďte text za konkrétní tvar v dokumentech Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak nahradit text pro konkrétní tvary v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Postupujte podle našeho podrobného návodu.
type: docs
weight: 35
url: /cs/net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
---
## Úvod
V tomto tutoriálu prozkoumáme, jak použít GroupDocs.Watermark pro .NET k nahrazení textu za konkrétní tvar v dokumentech aplikace Word. GroupDocs.Watermark for .NET je výkonná knihovna, která poskytuje širokou škálu funkcí pro práci s vodoznaky v různých formátech dokumentů, včetně dokumentů Word.
## Předpoklady
Než začneme, ujistěte se, že máte splněny následující předpoklady:
1.  GroupDocs.Watermark for .NET: Ujistěte se, že jste si stáhli a nainstalovali GroupDocs.Watermark for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Připravte dokument aplikace Word, ve kterém chcete nahradit text za konkrétní tvar.
3. Vývojové prostředí: Nastavte si vývojové prostředí s nezbytnými nástroji a závislostmi.

## Importovat jmenné prostory
Nejprve importujme požadované jmenné prostory pro práci s GroupDocs.Watermark for .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Váš kód je zde
}
```
 V tomto kroku určíme cestu k dokumentu aplikace Word a vytvoříme instanci`WordProcessingLoadOptions` k načtení dokumentu.
## Krok 2: Získejte obsah dokumentu
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Zde načteme obsah dokumentu aplikace Word pomocí`GetContent<T>()` metoda`Watermarker`třídy s uvedením typu jako`WordProcessingContent`.
## Krok 3: Nahraďte text za konkrétní tvar
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
V tomto kroku iterujeme každý tvar v dokumentu. Pokud tvar obsahuje zadaný text (v tomto příkladu "Nějaký text"), nahradíme jej požadovaným textem ("Další text").
## Krok 4: Uložte dokument
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
Nakonec upravený dokument uložíme do zadaného adresáře.

## Závěr
GroupDocs.Watermark for .NET nabízí pohodlný a efektivní způsob manipulace s vodoznaky v dokumentech aplikace Word. Podle kroků uvedených v tomto kurzu můžete snadno nahradit text konkrétními tvary, což poskytuje flexibilitu a možnosti přizpůsobení pro vaše potřeby zpracování dokumentů.
## FAQ
### Mohu nahradit text tvary v jiných formátech dokumentů kromě Wordu?
GroupDocs.Watermark for .NET podporuje různé formáty dokumentů, včetně PDF, Excel, PowerPoint a dalších. Pomocí podobných metod můžete nahradit text tvary v různých formátech.
### Je k dispozici zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Watermark pro .NET?
Technickou podporu můžete získat na fóru GroupDocs[tady](https://forum.groupdocs.com/c/watermark/19).
### Potřebuji dočasnou licenci k používání GroupDocs.Watermark pro .NET?
 Pokud požadujete další funkce nebo rozšířené používání, můžete získat dočasnou licenci od[tady](https://purchase.groupdocs.com/temporary-license/).
### Kde si mohu zakoupit plnou licenci pro GroupDocs.Watermark for .NET?
 Plnou licenci si můžete zakoupit na webu GroupDocs[tady](https://purchase.groupdocs.com/buy).