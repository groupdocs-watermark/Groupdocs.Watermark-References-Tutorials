---
title: Nahraďte text tvaru formátovaným textem v dokumentech aplikace Word
linktitle: Nahraďte text tvaru formátovaným textem v dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak nahradit text tvaru formátovaným textem v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Vaše možnosti úpravy dokumentů bez námahy.
type: docs
weight: 34
url: /cs/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Úvod
tomto tutoriálu vás provedeme procesem nahrazení textu tvaru formátovaným textem v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Tato knihovna poskytuje výkonné funkce pro práci s vodoznaky, včetně nahrazování textu v rámci tvarů.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Watermark pro .NET: Ujistěte se, že jste nainstalovali a nastavili GroupDocs.Watermark pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Cesta k dokumentu: Měli byste mít cestu k dokumentu aplikace Word, kde chcete nahradit text.

## Importovat jmenné prostory
Před napsáním kódu importujte potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
 Načtěte dokument aplikace Word pomocí`Watermarker` třída:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Váš kód pokračuje zde...
}
```
## Krok 2: Získejte obsah a nahraďte text
Po načtení dokumentu získejte obsah a nahraďte text ve tvarech:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Krok 3: Uložte dokument
Po nahrazení textu uložte upravený dokument:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Závěr
Nahrazení textu tvaru formátovaným textem v dokumentech aplikace Word je s aplikací GroupDocs pro .NET snadné. Podle kroků uvedených v tomto kurzu můžete efektivně spravovat a manipulovat s textem v dokumentech.

## FAQ
### Mohu nahradit text v jiných typech dokumentů pomocí GroupDocs.Watermark for .NET?
Ano, GroupDocs podporuje různé formáty dokumentů, jako je PDF, Excel, PowerPoint a další.
### Je GroupDocs.Watermark kompatibilní s .NET Core?
Ano, GroupDocs.Watermark podporuje .NET Framework i .NET Core.
### Poskytuje GroupDocs.Watermark podporu pro přidávání obrázků jako vodoznaků?
Rozhodně vám GroupDocs.Watermark umožňuje přidávat do dokumentů textové i obrázkové vodoznaky.
### Mohu upravit vzhled vodoznaků přidaných pomocí GroupDocs.Watermark?
Ano, máte plnou kontrolu nad vzhledem, pozicí a dalšími vlastnostmi vodoznaků.
### Je k dispozici zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).