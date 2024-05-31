---
title: Načíst dokument chráněný heslem
linktitle: Načíst dokument chráněný heslem
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky do dokumentů chráněných heslem pomocí Groupdocs Watermark for .NET pomocí našeho podrobného průvodce. Zabezpečte a označte své soubory snadno.
type: docs
weight: 13
url: /cs/net/document-loadings/load-password-protected-document/
---
## Úvod
Chcete chránit své dokumenty přidáním vodoznaků, i když jsou chráněny heslem? Groupdocs.Watermark for .NET je výkonný nástroj, který vám to umožní. V tomto tutoriálu vás provedeme procesem načtení dokumentu chráněného heslem a přidání vodoznaku do něj pomocí Groupdocs.Watermark for .NET. Pojďme se ponořit!
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1. Visual Studio: Jakákoli verze sady Visual Studio nainstalovaná na vašem počítači.
2. .NET Framework: Ujistěte se, že máte rozhraní .NET Framework 4.6.1 nebo novější.
3. Groupdocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu Groupdocs.Watermark for .NET z[odkaz ke stažení](https://releases.groupdocs.com/Watermark/net/).
## Importovat jmenné prostory
Nejprve musíme do našeho projektu importovat potřebné jmenné prostory. To zajišťuje, že máme přístup ke všem metodám a vlastnostem, které poskytuje Groupdocs.Watermark pro .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Nyní si tento proces rozdělíme do jednoduchých, snadno pochopitelných kroků.
## Krok 1: Nastavte svůj projekt
Začněte vytvořením nové konzolové aplikace C# v sadě Visual Studio. Jakmile je váš projekt nastaven, nainstalujte si knihovnu Groupdocs.Watermark for .NET prostřednictvím NuGet Package Manager.
1. Otevřete Visual Studio a vytvořte novou konzolovou aplikaci (.NET Framework).
2.  Jít do`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Hledat`GroupDocs.Watermark` a nainstalujte balíček.
## Krok 2: Definujte cesty dokumentu
Dále budete muset definovat cestu k vašemu dokumentu chráněnému heslem a cestu k výstupnímu souboru, kam bude dokument s vodoznakem uložen.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` a`"Your Document Directory"` se skutečnými cestami na vašem počítači.
## Krok 3: Nastavte možnosti načtení pomocí hesla
Chcete-li otevřít dokument chráněný heslem, musíte zadat heslo v možnostech načtení.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Nahradit`"P@$w0rd"` se skutečným heslem vašeho dokumentu.
## Krok 4: Vložte dokument
 Nyní načteme dokument pomocí`Watermarker` třída.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Sem bude umístěn váš kód pro přidání vodoznaku
}
```
## Krok 5: Vytvořte vodoznak
Vytvoříme textový vodoznak, který můžeme přidat do dokumentu. Podle potřeby můžete upravit text, písmo, velikost a další vlastnosti.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Neváhejte se změnit`"Test watermark"`, `"Arial"` , a`12` na vámi preferovaný text, písmo a velikost.
## Krok 6: Přidejte vodoznak
 Přidejte vodoznak do dokumentu pomocí`Add` metoda`Watermarker` třída.
```csharp
watermarker.Add(watermark);
```
## Krok 7: Uložte dokument s vodoznakem
Nakonec uložte dokument s vodoznakem do zadané cesty k výstupnímu souboru.
```csharp
watermarker.Save(outputFileName);
```
## Závěr
Přidávání vodoznaků do dokumentů chráněných heslem je s Groupdocs pro .NET jednoduchý proces. Dodržováním těchto jednoduchých kroků můžete zajistit, že vaše dokumenty budou chráněny a označeny podle vašich požadavků. Ať už jde o zabezpečení, branding nebo shodu, vodoznak vašich dokumentů nebyl nikdy jednodušší.
## FAQ
### Mohu přidat obrázkové vodoznaky pomocí Groupdocs.Watermark for .NET?
 Ano, můžete přidat textové i obrázkové vodoznaky. Jednoduše použijte`ImageWatermark` třída místo toho`TextWatermark`.
### Je možné odstranit vodoznak z dokumentu?
Ano, Groupdocs.Watermark for .NET poskytuje metody pro vyhledávání a odstraňování vodoznaků.
### Podporuje Groupdocs.Watermark for .NET jiné formáty dokumentů kromě PDF?
Ano, podporuje širokou škálu formátů včetně Wordu, Excelu, PowerPointu a dalších.
### Mohu upravit vzhled vodoznaku?
Absolutně! Můžete si přizpůsobit písmo, velikost, barvu, neprůhlednost a další.
### Kde mohu získat podporu, pokud narazím na problémy?
 Můžete navštívit[Fórum podpory Groupdocs](https://forum.groupdocs.com/c/watermark/19) za pomoc a vedení.