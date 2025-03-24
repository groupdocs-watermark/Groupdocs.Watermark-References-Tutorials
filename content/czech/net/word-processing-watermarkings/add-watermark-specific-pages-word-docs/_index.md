---
title: Přidejte vodoznak na konkrétní stránky v Dokumentech aplikace Word
linktitle: Přidejte vodoznak na konkrétní stránky v Dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky na konkrétní stránky v dokumentech aplikace Word bez námahy pomocí Groupdocs pro .NET. Vylepšete zabezpečení dokumentů a branding.
weight: 18
url: /cs/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---
## Úvod
V tomto tutoriálu si projdeme proces přidávání vodoznaků na konkrétní stránky v dokumentech aplikace Word pomocí Groupdocs.Watermark for .NET. Vodoznak je klíčovým aspektem správy dokumentů, poskytuje zabezpečení a branding vašich dokumentů. S Groupdocs.Watermark for .NET můžete snadno a přesně přidávat textové nebo obrázkové vodoznaky do dokumentů aplikace Word.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  Groupdocs.Watermark for .NET: Stáhněte a nainstalujte Groupdocs.Watermark for .NET z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Připravte si dokument Word, který chcete vodoznakem.
3. Vývojové prostředí: Nastavte své vývojové prostředí pomocí sady Visual Studio nebo jakéhokoli jiného vývojového nástroje .NET.

## Importovat jmenné prostory
Než se ponoříme do kódu, importujme potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Vložte dokument
Nejprve musíme načíst dokument aplikace Word do objektu vodoznaku.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Přidání vodoznakového kódu bude zde
}
```
## Krok 2: Přidejte vodoznak
Nyní přidáme textový vodoznak na konkrétní stránky dokumentu.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Zadejte stránky, na které chcete vodoznak přidat
};
watermarker.Add(textWatermark);
```
## Krok 3: Uložte dokument
Nakonec uložte dokument s vodoznakem na požadované místo.
```csharp
watermarker.Save(outputFileName);
```

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat vodoznaky na konkrétní stránky v dokumentech aplikace Word pomocí Groupdocs.Watermark for .NET. Pomocí několika řádků kódu můžete bez námahy zvýšit zabezpečení a branding svých dokumentů.
## FAQ
### Mohu přidat více vodoznaků do jednoho dokumentu?
Ano, můžete přidat více vodoznaků opakováním procesu přidávání vodoznaku pro každý vodoznak.
### Podporuje Groupdocs.Watermark jiné formáty dokumentů kromě Wordu?
Ano, Groupdocs podporuje širokou škálu formátů dokumentů včetně PDF, Excel, PowerPoint a dalších.
### Je k dispozici zkušební verze?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Mohu upravit vzhled vodoznaku?
Rozhodně si můžete přizpůsobit různé aspekty vodoznaku, jako je písmo, velikost, barva a neprůhlednost.
### Je k dispozici technická podpora?
 Ano, technickou podporu a zdroje najdete na fóru Groupdocs[tady](https://forum.groupdocs.com/c/watermark/19).