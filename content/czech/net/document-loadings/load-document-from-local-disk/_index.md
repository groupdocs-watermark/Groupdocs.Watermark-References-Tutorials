---
title: Načíst dokument z místního disku
linktitle: Načíst dokument z místního disku
second_title: GroupDocs.Watermark .NET API
description: Chraňte a spravujte své dokumenty pomocí Groupdocs pro .NET. Postupujte podle našeho podrobného průvodce a přidejte vodoznaky hladce.
weight: 10
url: /cs/net/document-loadings/load-document-from-local-disk/
---
## Úvod
Vodoznakové dokumenty jsou v dnešním digitálním věku zásadní pro zajištění ochrany obsahu, tvrzení o vlastnictví a důvěrnosti. Groupdocs.Watermark for .NET je výkonná knihovna, která umožňuje vývojářům přidávat, vyhledávat a spravovat vodoznaky v různých formátech dokumentů. V tomto tutoriálu projdeme procesem používání Groupdocs.Watermark for .NET k přidávání vodoznaků do vašich dokumentů s podrobnými pokyny krok za krokem.
## Předpoklady
Než se pustíte do implementace, ujistěte se, že máte následující:
1. Visual Studio nainstalované: Budete potřebovat Visual Studio nebo jiné kompatibilní .NET IDE.
2.  Groupdocs.Watermark for .NET: Stáhněte si knihovnu z[odkaz ke stažení](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Ujistěte se, že máte nainstalované rozhraní .NET Framework 4.6.1 nebo vyšší.
4. Vzorový dokument: Připravte vzorový dokument pro testování procesu vodoznaku.
## Importovat jmenné prostory
Chcete-li začít, budete muset do projektu importovat potřebné jmenné prostory. Ty jsou nezbytné pro přístup k třídám a metodám požadovaným pro vodoznak.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Načtěte dokument z místního disku
Nejprve musíte načíst dokument z místního disku. Tento dokument bude ten, ke kterému přidáte vodoznak.
Definujte cestu k dokumentu, který chcete označit vodoznakem.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Krok 2: Inicializujte možnosti načítání
 Dále inicializujte možnosti načítání. Pokud například pracujete s dokumentem aplikace Word, použijete`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Krok 3: Vytvořte a nakonfigurujte vodoznak
 Nyní vytvoříte instanci`Watermarker` třída. Tato instance bude použita ke správě a aplikování vodoznaků na váš dokument.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tento blok bude obsahovat další kroky k přidání a uložení vodoznaku
}
```
## Krok 4: Vytvořte vodoznak
Vytvořte textový vodoznak. Tento vodoznak může obsahovat libovolný text, který si zvolíte. Zde použijeme "Testovací vodoznak".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Krok 5: Přidejte do dokumentu vodoznak
Přidejte vytvořený vodoznak do dokumentu pomocí`Add` metoda`Watermarker` třída.
```csharp
watermarker.Add(watermark);
```
## Krok 6: Uložte dokument s vodoznakem
Nakonec uložte dokument s vodoznakem do zadané cesty.
```csharp
watermarker.Save(outputFileName);
```

## Závěr
Přidávání vodoznaků do dokumentů pomocí Groupdocs je jednoduché a efektivní. Tato příručka vás provede celým procesem od nastavení prostředí až po uložení dokumentu s vodoznakem. Pomocí tohoto výkonného nástroje můžete zajistit ochranu vašich dokumentů a zabezpečení vašeho duševního vlastnictví. 
 Pro další podrobnosti zkontrolujte[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) a pokud narazíte na nějaké problémy,[Fórum podpory](https://forum.groupdocs.com/c/watermark/19) je skvělým místem pro pomoc. 
## FAQ
### Mohu pro vodoznaky použít vlastní písma?
Ano, Groupdocs podporuje vlastní písma. Můžete zadat libovolné písmo nainstalované ve vašem systému.
### Jaké typy dokumentů jsou podporovány?
Groupdocs.Watermark podporuje širokou škálu formátů dokumentů včetně Wordu, Excelu, PDF, PowerPointu a dalších.
### Jak mohu odstranit vodoznak z dokumentu?
 Můžete použít`Remove` metoda poskytovaná společností`Watermarker` třídy k odstranění vodoznaků.
### Je možné přidat vodoznak do obrázku?
 Ano, můžete přidat vodoznaky obrázku pomocí`ImageWatermark` třída.
### Mohu vyzkoušet Groupdocs.Watermark zdarma?
 Rozhodně si můžete stáhnout a[zkušební verze zdarma](https://releases.groupdocs.com/) zhodnotit knihovnu před nákupem.