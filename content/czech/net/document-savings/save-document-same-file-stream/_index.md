---
title: Uložit dokument do stejného souboru nebo streamu
linktitle: Uložit dokument do stejného souboru nebo streamu
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky do dokumentů pomocí Groupdocs.Watermark for .NET. Tato příručka obsahuje pokyny k zajištění ochrany a integrity dokumentů.
type: docs
weight: 10
url: /cs/net/document-savings/save-document-same-file-stream/
---
## Úvod
V dnešním digitálním věku se přidávání vodoznaků do dokumentů stalo nezbytným pro ochranu duševního vlastnictví a zajištění integrity značky. Groupdocs.Watermark for .NET nabízí robustní řešení pro vývojáře, kteří chtějí bezproblémově vkládat vodoznaky do dokumentů. Tento komplexní průvodce vás provede kroky uložení dokumentu s vodoznakem do stejného souboru nebo streamu pomocí Groupdocs.Watermark for .NET.
## Předpoklady
Než se pustíte do výukového programu, ujistěte se, že máte následující:
1. Vývojové prostředí: Visual Studio nainstalované na vašem počítači.
2. .NET Framework: Ujistěte se, že máte .NET Framework 4.0 nebo novější.
3.  Groupdocs.Watermark for .NET: Stáhněte a nainstalujte nejnovější verzi z[místo](https://releases.groupdocs.com/Watermark/net/).
4.  Licence: Získejte dočasnou nebo trvalou licenci od[tady](https://purchase.groupdocs.com/temporary-license/).
## Importovat jmenné prostory
Chcete-li začít používat Groupdocs.Watermark ve svém projektu .NET, musíte importovat potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Nastavte svůj projekt
Než přidáme vodoznaky do našich dokumentů, musíme nastavit náš .NET projekt. Zde je postup:
1. Vytvoření nového projektu: Otevřete Visual Studio a vytvořte novou konzolovou aplikaci.
2. Přidat Groupdocs.Watermark Reference: Klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení, vyberte „Spravovat balíčky NuGet“ a nainstalujte balíček Groupdocs.Watermark.
## Krok 2: Zkopírujte dokument do nového umístění
Chcete-li se vyhnout přímým změnám původního dokumentu, je vhodné jej nejprve zkopírovat do nového umístění. Postup:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Krok 3: Inicializujte vodoznak
Nyní, když máme dokument zkopírovaný, můžeme inicializovat třídu Watermarker a přidat náš vodoznak:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Vodoznak je zde
}
```
## Krok 4: Vytvořte a přidejte textový vodoznak
Dále vytvoříme textový vodoznak a přidáme jej do našeho dokumentu:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Krok 5: Uložte dokument
Nakonec uložte dokument s vodoznakem:
```csharp
watermarker.Save();
```
## Závěr
Přidávání vodoznaků do dokumentů pomocí Groupdocs je jednoduché a efektivní. Dodržováním výše uvedených kroků můžete bez námahy chránit své dokumenty a udržovat jejich integritu. Pro více podrobností se můžete podívat na[dokumentace](https://reference.groupdocs.com/Watermark/net/).
## FAQ
### Mohu použít obrázek jako vodoznak místo textu?
Ano, Groupdocs.Watermark vám umožňuje používat obrázky, tvary a text jako vodoznaky.
### Jak odstraním vodoznak z dokumentu?
 Vodoznak můžete odstranit otevřením kolekce vodoznaků v dokumentu a použitím`Remove` metoda.
### Je možné upravit vzhled vodoznaku?
Absolutně. Můžete přizpůsobit písmo, velikost, barvu a umístění vodoznaku.
### Mohu použít více vodoznaků na jeden dokument?
 Ano, můžete přidat více vodoznaků zavoláním na`Add` metoda několikrát s různými objekty vodoznaku.
### Je Groupdocs.Watermark kompatibilní se všemi formáty dokumentů?
Groupdocs.Watermark podporuje širokou škálu formátů dokumentů včetně PDF, DOCX, PPTX a mnoha dalších.