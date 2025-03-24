---
title: Přidejte zamčený vodoznak na konkrétní stránky v Dokumentech aplikace Word
linktitle: Přidejte zamčený vodoznak na konkrétní stránky v Dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak přidat zamčený vodoznak na konkrétní stránky v dokumentech Word pomocí GroupDocs.Watermark for .NET s naším jednoduchým průvodcem krok za krokem.
weight: 12
url: /cs/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## Úvod
Chcete přidat vodoznak na konkrétní stránky v dokumentech aplikace Word, ale chcete, aby byl uzamčen, aby jej nebylo možné snadno odstranit nebo upravit? Jste na správném místě! V tomto tutoriálu vás provedeme procesem přidání zamčeného vodoznaku na konkrétní stránky v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Tato výkonná knihovna usnadňuje použití, správu a přizpůsobení vodoznaků na různé typy dokumentů. Ať už jste vývojář nebo jen někdo, kdo potřebuje zabezpečit své dokumenty, tento průvodce vás jednoduchým způsobem provede každým krokem.
## Předpoklady
Než se ponoříme do tutoriálu, ujistěte se, že máte vše, co potřebujete:
1.  GroupDocs.Watermark pro .NET: Můžete[stažení](https://releases.groupdocs.com/Watermark/net/) poslední verze.
2. Vývojové prostředí: IDE jako Visual Studio.
3. Základní znalost C#: Užitečná bude znalost programování v C#.
4. Dokument k vodoznaku: Dokument aplikace Word (.docx nebo .doc), do kterého chcete přidat vodoznak.
## Importovat jmenné prostory
Nejprve musíte importovat potřebné jmenné prostory do vašeho projektu C#. Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným pro práci s GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Nyní, když máme pokryty předpoklady a importujeme potřebné jmenné prostory, pojďme si proces rozebrat krok za krokem.
## Krok 1: Načtěte dokument aplikace Word
 Nejprve musíte načíst dokument aplikace Word, do kterého chcete přidat vodoznak. To lze provést pomocí`Watermarker` třída spolu s`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Pokračujte dalšími kroky
}
```
## Krok 2: Vytvořte textový vodoznak
Dále vytvořte textový vodoznak. Text, písmo, barvu a další vlastnosti si můžete přizpůsobit podle svých požadavků.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Krok 3: Nakonfigurujte možnosti vodoznaku
 Chcete-li vodoznak použít na konkrétní stránky a uzamknout jej, nakonfigurujte`WordProcessingWatermarkPagesOptions`Zde určíte čísla stránek, kde se má vodoznak objevit, a nastavíte možnosti zamykání.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Určete stránky
options.IsLocked = true; // Zamkněte vodoznak
options.LockType = WordProcessingLockType.AllowOnlyComments; // Nastavte typ zámku
// Pro ochranu heslem
// options.Password = "7654321";
```
## Krok 4: Přidejte do dokumentu vodoznak
S nakonfigurovaným vodoznakem a možnostmi můžete nyní vodoznak přidat do dokumentu.
```csharp
watermarker.Add(watermark, options);
```
## Krok 5: Uložte dokument
Nakonec uložte dokument s aplikovaným vodoznakem. Vyberte vhodnou výstupní cestu a soubor uložte.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Závěr
Gratulujeme! Úspěšně jste přidali zamčený vodoznak na konkrétní stránky v dokumentu aplikace Word pomocí GroupDocs.Watermark for .NET. Tento tutoriál pokryl všechny základní kroky od načtení dokumentu po uložení souboru s vodoznakem. Dodržováním těchto kroků můžete zajistit, že vaše dokumenty budou bezpečně opatřeny vodoznakem, čímž bude váš obsah chráněn před neoprávněnými úpravami a použitím.
 Pro více informací se můžete podívat na[Dokumentace GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . Pokud máte nějaké dotazy nebo potřebujete další pomoc, neváhejte navštívit[Fórum podpory](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Co je GroupDocs.Watermark pro .NET?
GroupDocs.Watermark for .NET je výkonná knihovna, která umožňuje vývojářům přidávat vodoznaky do různých typů dokumentů, včetně Wordu, PDF, Excelu a dalších.
### Mohu použít vodoznak na více stránek v dokumentu?
 Ano, v souboru můžete zadat více čísel stránek`PageNumbers` pole pro použití vodoznaků na více stránek.
### Jak ochráním vodoznak heslem?
 Vodoznak můžete chránit heslem nastavením`Password` nemovitost v`WordProcessingWatermarkPagesOptions`.
### Je možné upravit vzhled vodoznaku?
Absolutně! Text, písmo, barvu, velikost a další vlastnosti vodoznaku můžete přizpůsobit svým potřebám.
### Kde mohu získat dočasnou licenci pro GroupDocs.Watermark?
 Dočasnou licenci můžete získat od[tady](https://purchase.groupdocs.com/temporary-license/).