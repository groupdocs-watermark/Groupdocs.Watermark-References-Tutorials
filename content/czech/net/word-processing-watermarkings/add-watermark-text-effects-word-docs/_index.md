---
title: Přidejte vodoznak s textovými efekty v Dokumentech aplikace Word
linktitle: Přidejte vodoznak s textovými efekty v Dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vlastní vodoznaky s textovými efekty do dokumentů aplikace Word pomocí GroupDocs.Watermark for .NET. Zabezpečení dokumentů a vizuální přitažlivost bez námahy.
weight: 21
url: /cs/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
type: docs
---
# Přidejte vodoznak s textovými efekty v Dokumentech aplikace Word

## Úvod
V tomto tutoriálu prozkoumáme, jak přidat vodoznak s textovými efekty do dokumentů aplikace Word pomocí GroupDocs.Watermark for .NET. Podle těchto podrobných pokynů budete moci vylepšit své dokumenty pomocí přizpůsobených vodoznaků, které obsahují různé textové efekty.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
1.  GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu z[webová stránka](https://releases.groupdocs.com/Watermark/net/).
2. Cesta k dokumentu: Znáte cestu k dokumentu aplikace Word, do kterého chcete přidat vodoznak.
3. Výstupní adresář: Mějte adresář, kam chcete uložit upravený dokument.

## Importovat jmenné prostory
Ujistěte se, že jste importovali potřebné jmenné prostory pro přístup k požadovaným třídám a metodám:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
Vložte dokument aplikace Word, do kterého chcete přidat vodoznak.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kód pro přidání vodoznaku je zde
}
```
## Krok 2: Přidejte vodoznak s textovými efekty
Vytvořte textový vodoznak s požadovaným textem a písmem a poté definujte textové efekty, jako je formát čáry.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## Krok 3: Přizpůsobte možnosti vodoznaku
Definujte možnosti sekce vodoznaku, jako jsou textové efekty, a přiřaďte je k vodoznaku.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Krok 4: Uložte dokument
Uložte upravený dokument s přidaným vodoznakem.
```csharp
watermarker.Save(outputFileName);
```

## Závěr
Přidání vodoznaků s textovými efekty do dokumentů aplikace Word může výrazně zlepšit jejich vizuální přitažlivost a ochranu. S GroupDocs.Watermark for .NET se tento proces zjednoduší a přizpůsobí, což vám umožní efektivně vytvářet profesionálně vypadající dokumenty.
## FAQ
### Mohu přizpůsobit písmo a velikost textu vodoznaku?
Ano, při vytváření objektu TextWatermark můžete určit písmo a velikost.
### Je možné přidat více vodoznaků do jednoho dokumentu?
GroupDocs.Watermark for .NET rozhodně podporuje přidávání více vodoznaků s různým nastavením do jednoho dokumentu.
### Podporuje GroupDocs.Watermark jiné formáty dokumentů kromě Wordu?
Ano, podporuje širokou škálu formátů dokumentů včetně PDF, Excel, PowerPoint a dalších.
### Mohu odstranit vodoznak, jakmile je přidán do dokumentu?
Ano, knihovna poskytuje metody pro snadné odstranění vodoznaků z dokumentů.
### Je k dispozici zkušební verze pro účely testování?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).