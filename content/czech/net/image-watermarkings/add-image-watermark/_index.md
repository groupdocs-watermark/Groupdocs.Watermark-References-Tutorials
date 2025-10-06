---
title: Přidat obrázek vodoznak
linktitle: Přidat obrázek vodoznak
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak přidat obrázkové vodoznaky do dokumentů pomocí GroupDocs.Watermark for .NET s naším podrobným, podrobným návodem.
weight: 11
url: /cs/net/image-watermarkings/add-image-watermark/
type: docs
---
# Přidat obrázek vodoznak

## Úvod
Vítejte v tomto komplexním průvodci přidáváním vodoznaků do obrázků pomocí GroupDocs.Watermark pro .NET! Vodoznak je účinný způsob, jak chránit vaše dokumenty a obrázky před neoprávněným použitím a zajistit, že vaše duševní vlastnictví zůstane v bezpečí. V tomto tutoriálu vás provedeme celým procesem, od nastavení prostředí až po použití vodoznaku na vaše dokumenty. Ať už jste zkušený vývojář nebo teprve začínáte, tato příručka vám bude užitečná a snadno se budete řídit.
## Předpoklady
Než se vrhneme na tutoriál, ujistěte se, že máte vše, co potřebujete:
- Vývojové prostředí: Visual Studio nebo jakékoli IDE kompatibilní s .NET
- .NET Framework: .NET Framework 4.0 nebo vyšší
-  GroupDocs.Watermark for .NET: Můžete si jej stáhnout z[Web GroupDocs](https://releases.groupdocs.com/Watermark/net/)
-  Soubor obrázku: Soubor obrázku, který se má použít jako vodoznak (např.`watermark.jpg`)
- Soubor dokumentu: Dokument, do kterého chcete přidat vodoznak (např.`presentation.pptx`)
## Importovat jmenné prostory
Chcete-li začít, budete muset do projektu importovat potřebné jmenné prostory. To je nezbytné pro přístup k funkcím GroupDocs.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
V této části rozdělíme proces přidávání vodoznaku obrázku do jasných a zvládnutelných kroků. Pečlivě dodržujte každý krok k úspěšnému vodoznaku dokumentu.
## Krok 1: Nastavte své prostředí
 Nejprve se ujistěte, že je vaše vývojové prostředí správně nastaveno. Nainstalujte knihovnu GroupDocs.Watermark jejím stažením z[Web GroupDocs](https://releases.groupdocs.com/Watermark/net/).
1. Otevřete projekt v sadě Visual Studio.
2. Klepněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
3. Vyberte „Spravovat balíčky NuGet...“
4.  Hledat`GroupDocs.Watermark` a nainstalujte jej.
## Krok 2: Definujte cesty k souboru
Dále budete muset definovat cesty pro váš vstupní dokument a výstupní adresář. To pomáhá programu najít soubory, se kterými potřebuje pracovat.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` a`"Your Document Directory"` se skutečnými cestami k vašemu dokumentu a požadovaným výstupním adresářem.
## Krok 3: Inicializujte vodoznak
Nyní inicializujte`Watermarker` třídy s cestou k vašemu dokumentu. Tato třída je zodpovědná za řízení procesu vodoznaku.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Pokračujte dalšími kroky v rámci tohoto bloku pomocí
}
```
## Krok 4: Vytvořte vodoznak obrázku
 V rámci`Watermarker` bloku, vytvořte instanci souboru`ImageWatermark` třídy pomocí cesty k obrázku vodoznaku. Tato třída představuje obrázek, který chcete použít jako vodoznak.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Pokračujte dalším krokem v rámci tohoto bloku pomocí
}
```
## Krok 5: Přidejte do dokumentu vodoznak
 s`ImageWatermark` instance připravena, přidejte ji do dokumentu pomocí`Add` metoda`Watermarker` třída.
```csharp
watermarker.Add(watermark);
```
## Krok 6: Uložte dokument
Nakonec uložte dokument s vodoznakem do určeného výstupního adresáře. Tento krok zajistí, že vaše změny budou zapsány do nového souboru.
```csharp
watermarker.Save(outputFileName);
```
## Závěr
Gratulujeme! Úspěšně jste do dokumentu přidali vodoznak obrázku pomocí GroupDocs.Watermark for .NET. Podle tohoto podrobného průvodce můžete snadno chránit své dokumenty pomocí vlastních vodoznaků. Pamatujte, že vodoznak je zásadním krokem k ochraně vašich digitálních aktiv před neoprávněným použitím.

## FAQ
### Jaké formáty souborů podporuje GroupDocs.Watermark?
GroupDocs.Watermark podporuje širokou škálu formátů souborů, včetně PDF, DOCX, PPTX, XLSX a obrazových souborů, jako jsou JPEG a PNG.
### Mohu používat GroupDocs.Watermark s .NET Core?
Ano, GroupDocs.Watermark je kompatibilní s .NET Framework i .NET Core.
### Jak mohu získat dočasnou licenci pro GroupDocs.Watermark?
 Dočasnou licenci můžete získat od[Web GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Je možné přidat více vodoznaků do jednoho dokumentu?
 Absolutně! Můžete přidat více vodoznaků zavoláním na`Add` metoda vícekrát s různými instancemi vodoznaku.
### Kde najdu další příklady a dokumentaci?
 Další příklady a podrobnou dokumentaci naleznete na adrese[Dokumentace GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).