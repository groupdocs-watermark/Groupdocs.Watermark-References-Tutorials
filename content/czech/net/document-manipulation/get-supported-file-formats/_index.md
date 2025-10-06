---
title: Získejte podporované formáty souborů
linktitle: Získejte podporované formáty souborů
second_title: GroupDocs.Watermark .NET API
description: Bez námahy přidejte vodoznaky do svých dokumentů pomocí GroupDocs.Watermark pro .NET. Postupujte podle našeho komplexního průvodce krok za krokem k ochraně svých digitálních aktiv.
weight: 13
url: /cs/net/document-manipulation/get-supported-file-formats/
type: docs
---
# Získejte podporované formáty souborů

## Úvod
Vodoznak vašich dokumentů je zásadním krokem k ochraně vašich digitálních aktiv. Vodoznaky hrají zásadní roli, ať už jde o ochranu duševního vlastnictví, zajištění důvěrnosti nebo jednoduše o branding. Pokud jste vývojář .NET a chcete do svých aplikací integrovat možnosti vodoznaku, GroupDocs.Watermark for .NET je výkonný a všestranný nástroj, který byste měli zvážit. Tento tutoriál vás provede základy používání GroupDocs.Watermark, od instalace až po použití prvního vodoznaku, přičemž rozepíše každý krok, abyste se ujistili, že jej budete moci snadno sledovat.
## Předpoklady
Než se ponoříme do podrobností, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:
1.  Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Můžete si jej stáhnout z[Webové stránky Visual Studia](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark podporuje různé verze rozhraní .NET Framework. Ujistěte se, že váš projekt cílí na kompatibilní verzi.
3. GroupDocs.Watermark for .NET: Nejnovější verzi si můžete stáhnout z webu[stránka vydání](https://releases.groupdocs.com/Watermark/net/).
4. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti o vývoji C# a .NET.
## Importovat jmenné prostory
Nejprve importujme potřebné jmenné prostory do vašeho projektu. Otevřete svůj soubor C# a pomocí direktiv v horní části přidejte následující:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Po importu těchto jmenných prostorů jste připraveni začít přidávat vodoznaky do svých dokumentů.

## Krok 1: Inicializujte modul Watermarking Engine
 Prvním krokem je inicializace stroje pro vytváření vodoznaků. To zahrnuje vytvoření instance souboru`Watermarker` třídy s dokumentem, který chcete vodoznakem.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Tento fragment kódu nastavuje`Watermarker` objekt, který použijete k použití vodoznaků na váš dokument.
## Krok 2: Přidejte textový vodoznak
Nyní do dokumentu přidáme jednoduchý textový vodoznak. Textové vodoznaky jsou skvělé pro přidávání štítků jako „Důvěrné“ nebo „Koncept“.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Zde jsme vytvořili a`TextWatermark`objekt s textem "Důvěrné", nastavte jeho písmo a barvu a zarovnejte jej na střed dokumentu.
## Krok 3: Přidejte vodoznak obrázku
Pokud dáváte přednost použití obrázku jako vodoznaku, GroupDocs.Watermark to usnadňuje.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 V tomto příkladu vytvoříme`ImageWatermark` objekt, nastavte jeho rozměry a zarovnejte jej do pravého horního rohu dokumentu.
## Krok 4: Uložte dokument
Po přidání požadovaných vodoznaků je posledním krokem uložení upraveného dokumentu.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Tím se dokument s vodoznakem uloží do zadané cesty a uvolní se všechny zdroje, které používá`Watermarker` instance.
## Krok 5: Získejte podporované formáty souborů
Chcete-li zjistit, které formáty souborů jsou podporovány GroupDocs.Watermark, můžete použít následující fragment kódu:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Tím se vytisknou všechny typy souborů, které GroupDocs.Watermark zvládne, a získáte tak komplexní přehled o jeho možnostech.
## Závěr
Vodoznak vašich dokumentů pomocí GroupDocs Watermark for .NET je přímočarý a efektivní. Podle tohoto návodu jste se naučili, jak inicializovat stroj pro vytváření vodoznaků, přidávat textové a obrázkové vodoznaky, ukládat dokumenty s vodoznakem a vypisovat podporované formáty souborů. Pomocí těchto nástrojů můžete své dokumenty spolehlivě chránit.
 Pokud máte nějaké dotazy nebo potřebujete další pomoc, neváhejte a navštivte[Fórum podpory GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Jak nainstaluji GroupDocs.Watermark for .NET?
 Můžete si jej stáhnout z[stránka vydání](https://releases.groupdocs.com/Watermark/net/) a přidejte DLL do projektu.
### Mohu vyzkoušet GroupDocs.Watermark zdarma?
 Ano, můžete požádat o a[zkušební verze zdarma](https://releases.groupdocs.com/) vyhodnotit software před nákupem.
### Jaké formáty souborů podporuje GroupDocs.Watermark?
Pomocí poskytnutého fragmentu kódu můžete zobrazit seznam všech podporovaných formátů souborů.
### Jak si mohu zakoupit licenci pro GroupDocs.Watermark?
 Licence lze zakoupit přímo od[nákupní stránku](https://purchase.groupdocs.com/buy).
### Je k dispozici nějaká dokumentace pro GroupDocs.Watermark?
 Ano, k dispozici je komplexní dokumentace[tady](https://tutorials.groupdocs.com/Watermark/net/).