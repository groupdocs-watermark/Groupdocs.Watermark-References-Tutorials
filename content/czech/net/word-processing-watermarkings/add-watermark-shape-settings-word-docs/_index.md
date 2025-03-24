---
title: Přidejte vodoznak s nastavením tvaru ve Word Docs
linktitle: Přidejte vodoznak s nastavením tvaru ve Word Docs
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky s nastavením tvaru do dokumentů aplikace Word pomocí GroupDocs pro .NET. Chraňte své dokumenty efektivně.
weight: 20
url: /cs/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Úvod
V tomto tutoriálu si projdeme proces přidávání vodoznaku s nastavením tvaru do dokumentů aplikace Word pomocí GroupDocs.Watermark for .NET.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1.  GroupDocs.Watermark for .NET nainstalován. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Základní znalost programování v C#.
3. Pochopení zpracování dokumentů ve Wordu.

## Importovat jmenné prostory
Nejprve musíte importovat potřebné jmenné prostory pro přístup k požadovaným třídám a metodám.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
Vložte dokument aplikace Word do místa, kam chcete přidat vodoznak.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Zde je kód přidání vodoznaku
}
```
## Krok 2: Přidejte vodoznak
 Instantovat a`TextWatermark` objekt a zadejte text, který chcete použít jako vodoznak.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Krok 3: Upravte nastavení vodoznaku
Nastavte různá nastavení vodoznaku, jako je zarovnání, úhel otočení, barva a krytí.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Krok 4: Definujte možnosti sekce vodoznaku
Definujte možnosti pro sekci vodoznaku, jako je název tvaru a alternativní text.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Krok 5: Přidejte do dokumentu vodoznak
Přidejte vodoznak do dokumentu se zadanými možnostmi.
```csharp
watermarker.Add(watermark, options);
```
## Krok 6: Uložte dokument
Uložte dokument s přidaným vodoznakem.
```csharp
watermarker.Save(outputFileName);
```

## Závěr
Přidávání vodoznaků s nastavením tvaru do dokumentů aplikace Word pomocí GroupDocs pro .NET je jednoduchý proces. Podle kroků uvedených v tomto kurzu můžete účinně chránit své dokumenty pomocí přizpůsobených vodoznaků.
## FAQ
### Mohu do stejného dokumentu přidat více vodoznaků?
Ano, do stejného dokumentu můžete přidat více vodoznaků s různým nastavením.
### Podporuje GroupDocs.Watermark jiné formáty dokumentů kromě Wordu?
Ano, GroupDocs.Watermark podporuje různé formáty dokumentů, včetně Excelu, PowerPointu, PDF a dalších.
### Mohu si vzhled vodoznaku dále přizpůsobit?
Samozřejmě můžete upravit různé parametry, jako je velikost písma, styl, barva a poloha, aby vyhovovaly vašim potřebám.
### Je k dispozici zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi od[tady](https://releases.groupdocs.com/).
### Kde najdu podporu pro GroupDocs.Watermark?
 Podporu a dotazy můžete najít na fóru GroupDocs[tady](https://forum.groupdocs.com/c/watermark/19).