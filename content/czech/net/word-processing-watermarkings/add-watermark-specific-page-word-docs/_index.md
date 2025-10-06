---
title: Přidat vodoznak na konkrétní stránku ve Word Docs
linktitle: Přidat vodoznak na konkrétní stránku ve Word Docs
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky na konkrétní stránky v dokumentech aplikace Word pomocí GroupDocs pro .NET. Chraňte svůj obsah bez námahy.
weight: 14
url: /cs/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
type: docs
---
# Přidat vodoznak na konkrétní stránku ve Word Docs

## Úvod
Vodoznakové dokumenty jsou klíčovým aspektem zabezpečení dokumentů a brandingu. V tomto tutoriálu prozkoumáme, jak přidat vodoznak na konkrétní stránku v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
- Základní znalost programování v C#.
- Nainstalované Visual Studio IDE.
- GroupDocs.Watermark for .NET nainstalovaný ve vašem projektu.

## Import jmenných prostorů
Než se ponoříte do kódu, ujistěte se, že importujete potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Váš kód půjde sem
}
```
## Krok 2: Přidejte vodoznak
```csharp
// Definujte text a styl vodoznaku
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Přidejte vodoznak na poslední stránku
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Krok 3: Uložte dokument
```csharp
// Uložte dokument s vodoznakem
watermarker.Save(outputFileName);
```

## Závěr
tomto tutoriálu jsme se naučili, jak přidat vodoznak na konkrétní stránku v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Dodržováním těchto kroků můžete účinně chránit své dokumenty a podle potřeby přidávat prvky značky.
## FAQ
### Mohu upravit text a styl vodoznaku?
Ano, text, písmo, velikost, barvu a umístění vodoznaku si můžete přizpůsobit podle svých požadavků.
### Je GroupDocs.Watermark for .NET kompatibilní s jinými formáty dokumentů?
Ano, GroupDocs.Watermark podporuje různé formáty dokumentů, včetně Wordu, Excelu, PowerPointu, PDF a dalších.
### Mohu přidat více vodoznaků do jednoho dokumentu?
Do stejného dokumentu můžete samozřejmě přidat více vodoznaků s různým obsahem a styly.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, funkce GroupDocs.Watermark můžete prozkoumat pomocí bezplatné zkušební verze. Chcete-li začít, stačí navštívit poskytnutý odkaz[tady](https://releases.groupdocs.com/).
### Kde mohu získat technickou podporu pro GroupDocs.Watermark?
 Můžete najít užitečné zdroje a získat technickou podporu[tady](https://forum.groupdocs.com/c/watermark/19)na fóru GroupDocs.Watermark. Chcete-li se připojit ke komunitě, přejděte na uvedený odkaz.