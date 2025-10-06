---
title: Přidat zamčený vodoznak na všechny stránky v Dokumentech aplikace Word
linktitle: Přidat zamčený vodoznak na všechny stránky v Dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Zabezpečte své dokumenty přidáním zamčených vodoznaků pomocí Groupdocs.Watermark pro .NET. Pro snadnou implementaci postupujte podle našeho podrobného průvodce.
weight: 11
url: /cs/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Přidat zamčený vodoznak na všechny stránky v Dokumentech aplikace Word

## Úvod
Přidání vodoznaků do vašich dokumentů je zásadním krokem v zabezpečení a brandingu vašeho obsahu. Ať už bráníte neoprávněnému použití nebo jednoduše přidáváte profesionální nádech, vodoznaky mohou sloužit mnoha účelům. V tomto tutoriálu vás provedeme procesem přidání zamčeného vodoznaku na všechny stránky dokumentu aplikace Word pomocí Groupdocs.Watermark for .NET.
## Předpoklady
Než se ponoříme do podrobného průvodce, ujistěte se, že máte vše, co potřebujete:
1. Groupdocs.Watermark for .NET: Stáhněte si nejnovější verzi z[tady](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
3. Vývojové prostředí: Vývojové prostředí jako Visual Studio.
4.  Licence: Můžete se rozhodnout pro a[zkušební verze zdarma](https://releases.groupdocs.com/) nebo koupit a[dočasná licence](https://purchase.groupdocs.com/temporary-license/).
## Importovat jmenné prostory
Nejprve musíte do projektu importovat potřebné jmenné prostory. Ty jsou nezbytné pro přístup ke třídám a metodám poskytovaným Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Nastavte svůj projekt

Otevřete své vývojové prostředí a vytvořte nový projekt .NET. Může to být konzolová aplikace nebo jakýkoli jiný typ, který vyhovuje vašim potřebám.

Do svého projektu musíte přidat balíček Groupdocs.Watermark. To lze provést pomocí Správce balíčků NuGet. Spusťte následující příkaz v konzole NuGet Package Manager Console:
```sh
Install-Package GroupDocs.Watermark
```
## Krok 2: Načtěte dokument aplikace Word
### Definujte cestu dokumentu
Zadejte cestu k dokumentu aplikace Word. Toto bude dokument, do kterého chcete přidat vodoznak.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Nastavte možnosti načítání
 Vytvořte instanci`WordProcessingLoadOptions` k načtení dokumentu aplikace Word se specifickými možnostmi.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Krok 3: Vytvořte vodoznak
### Inicializujte vodoznak
 Za použití`Watermarker`třídy, načtěte dokument se zadanými možnostmi načtení.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Další kroky budou uvnitř tohoto pomocí bloku
}
```
### Definujte vlastnosti vodoznaku
 Vytvořit`TextWatermark` instance s požadovaným textem, písmem a barvou.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Krok 4: Použijte vodoznak na všechny stránky
### Nastavte možnosti vodoznaku
 Definovat`WordProcessingWatermarkPagesOptions` a nastavte`IsLocked` vlastnost na true pro zamknutí vodoznaku. Tím je zajištěno, že vodoznak nelze snadno odstranit.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Volitelné: Přidejte ochranu heslem
Pokud chcete přidat další vrstvu zabezpečení, můžete pro vodoznak nastavit heslo.
```csharp
// Pro ochranu heslem
// options.Password = "7654321";
```
### Přidejte vodoznak
 Použijte`Add` metoda`Watermarker` třídy přidat vodoznak do dokumentu se zadanými možnostmi.
```csharp
watermarker.Add(watermark, options);
```
## Krok 5: Uložte dokument
Nakonec upravený dokument uložte do zadaného výstupního souboru.
```csharp
watermarker.Save(outputFileName);
```

## Závěr
Pomocí následujících kroků můžete snadno přidat zamčený vodoznak na všechny stránky dokumentů aplikace Word pomocí Groupdocs.Watermark for .NET. To nejen pomáhá chránit vaše dokumenty před neoprávněným použitím, ale také dodává vašemu obsahu profesionální vzhled. Groupdocs.Watermark nabízí komplexní řešení pro potřeby vodoznaků, které zajistí, že vaše dokumenty zůstanou bezpečné a označené značkou.
## FAQ
### Mohu použít obrázek jako vodoznak místo textu?
 Ano, Groupdocs podporuje textové i obrázkové vodoznaky. Můžete vyměnit`TextWatermark` s`ImageWatermark` a zadejte svůj obrázek.
### Je možné upravit polohu vodoznaku?
 Absolutně! Polohu vodoznaku můžete nastavit pomocí vlastností jako`HorizontalAlignment` a`VerticalAlignment`.
### Mohu použít různé vodoznaky na různé stránky dokumentu?
 Ano, můžete upravit vodoznaky pro konkrétní stránky pomocí`PageIndex` nemovitost v`WordProcessingWatermarkPagesOptions`.
### Podporuje Groupdocs.Watermark jiné formáty dokumentů kromě Wordu?
Ano, Groupdocs podporuje různé formáty včetně PDF, Excel, PowerPoint a dalších.
### Jaké jsou systémové požadavky pro používání Groupdocs.Watermark?
Potřebujete systém s nainstalovaným .NET Framework a vývojové prostředí jako Visual Studio.