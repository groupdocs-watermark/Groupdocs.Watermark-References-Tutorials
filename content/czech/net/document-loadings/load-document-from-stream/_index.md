---
title: Načíst dokument ze streamu
linktitle: Načíst dokument ze streamu
second_title: GroupDocs.Watermark .NET API
description: V této příručce se dozvíte, jak přidat vodoznaky do dokumentů pomocí GroupDocs.Watermark for .NET. Ideální pro vývojáře, kteří chtějí zlepšit zabezpečení dokumentů.
weight: 11
url: /cs/net/document-loadings/load-document-from-stream/
---
## Úvod
Přejete si přidat vodoznaky do svých dokumentů hladce pomocí .NET? Už nehledejte! GroupDocs.Watermark for .NET je výkonná a snadno použitelná knihovna, která umožňuje spravovat vodoznaky v různých formátech dokumentů. Ať už pracujete s PDF, dokumenty Wordu nebo obrázky, tento nástroj vám pomůže. V tomto tutoriálu vás krok za krokem provedeme procesem načítání dokumentu ze streamu a přidáním vodoznaku. Takže, pojďme se rovnou ponořit!
## Předpoklady
Než začneme, ujistěte se, že máte následující nastavení:
1. Visual Studio: Jakákoli nejnovější verze sady Visual Studio bude fungovat dobře.
2. .NET Framework: Ujistěte se, že máte nainstalované rozhraní .NET Framework 4.0 nebo vyšší.
3.  GroupDocs.Watermark for .NET: Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).
4. Základní znalost C#: Užitečná bude znalost C# a objektově orientovaného programování.

## Importovat jmenné prostory
Chcete-li ve svém projektu použít GroupDocs.Watermark, budete muset importovat potřebné jmenné prostory. To vám umožní bez problémů přistupovat k funkcím knihovny.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Nastavení vašeho projektu
Nejprve musíte projekt nastavit ve Visual Studiu. Postup je následující:
1. Vytvoření nového projektu: Otevřete Visual Studio a vytvořte nový projekt C# Console Application.
2.  Instalace GroupDocs.Watermark: Nainstalujte knihovnu GroupDocs.Watermark prostřednictvím NuGet Package Manager. Jednoduše vyhledejte`GroupDocs.Watermark` a nainstalujte jej.
## Krok 2: Definujte cesty dokumentu
Dále musíte definovat cesty pro váš dokument a výstupní soubor, kam se uloží dokument s vodoznakem.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` se skutečnou cestou dokumentu, který chcete vodoznakem, a`"Your Document Directory"` s adresářem, kam chcete uložit dokument s vodoznakem.
## Krok 3: Načtěte dokument ze streamu
Nyní načteme dokument ze streamu. To zahrnuje otevření dokumentu jako stream a následné použití`Watermarker` třídy z knihovny GroupDocs.Watermark, abyste jej mohli spravovat.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Sem bude umístěn váš kód pro správu vodoznaků
}
```
 Tento fragment kódu zajišťuje, že dokument bude otevřen jako stream a soubor`Watermarker` třída je inicializována tímto streamem. The`using` Prohlášení zajišťuje, že zdroje jsou po použití správně zlikvidovány.
## Krok 4: Vytvořte a přidejte vodoznak
Vytvoření vodoznaku je s GroupDocs.Watermark jednoduché. V tomto příkladu vytvoříme jednoduchý textový vodoznak.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Zde vytvoříme a`TextWatermark` objekt s textem "Test vodoznak" a zadejte podrobnosti o písmu. Poté přidáme tento vodoznak do dokumentu pomocí`Add` metoda`Watermarker` třída.
## Krok 5: Uložte dokument s vodoznakem
Nakonec uložte dokument s vodoznakem do zadané výstupní cesty.
```csharp
watermarker.Save(outputFileName);
```
 Tento kód uloží dokument s nově přidaným vodoznakem`outputFileName` cesta, kterou jste definovali dříve.

## Závěr
Gratulujeme! Úspěšně jste do dokumentu přidali vodoznak pomocí GroupDocs.Watermark for .NET. Tato knihovna neuvěřitelně usnadňuje správu vodoznaků v různých formátech dokumentů. Ať už potřebujete přidat text, obrázky nebo jiné typy vodoznaků, GroupDocs.Watermark má nástroje, které potřebujete. Nezapomeňte se podívat na[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) pro pokročilejší funkce a možnosti přizpůsobení.
## FAQ
### Jaké typy vodoznaků mohu přidat pomocí GroupDocs.Watermark for .NET?
Můžete přidat textové vodoznaky, obrázkové vodoznaky a dokonce i složité tvary a loga. Knihovna podporuje širokou škálu možností přizpůsobení.
### Mohu odstranit vodoznaky z dokumentů pomocí GroupDocs.Watermark?
Ano, GroupDocs.Watermark umožňuje odstranit i existující vodoznaky z dokumentů.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Watermark?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Jak si koupím licenci pro GroupDocs.Watermark?
Licenci si můžete zakoupit přímo od[Web GroupDocs](https://purchase.groupdocs.com/buy).
### Kde mohu získat podporu, pokud narazím na problémy?
 Pro podporu můžete navštívit[Fórum podpory GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).