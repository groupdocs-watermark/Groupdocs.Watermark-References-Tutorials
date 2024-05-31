---
title: Uložit dokument do určeného umístění
linktitle: Uložit dokument do určeného umístění
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak snadno přidávat vodoznaky do dokumentů pomocí GroupDocs.Watermark for .NET, pomocí tohoto podrobného průvodce. Zvyšte zabezpečení dokumentů.
type: docs
weight: 11
url: /cs/net/document-savings/save-document-specified-location/
---
## Úvod
V digitálním věku se zabezpečení dokumentů stalo důležitější než kdy jindy. Vodoznak je účinný způsob, jak chránit vaše dokumenty před neoprávněným použitím. GroupDocs.Watermark for .NET nabízí robustní řešení pro přidávání vodoznaků do vašich dokumentů. Ať už jste vývojář, který chce integrovat vodoznak do své aplikace, nebo někdo, kdo má zájem o zabezpečení vašich dokumentů, tento tutoriál vás provede procesem krok za krokem.
## Předpoklady
Než se pustíte do výukového programu, ujistěte se, že máte splněny následující předpoklady:
- Vývojové prostředí .NET: Ujistěte se, že máte nainstalované Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
-  Knihovna GroupDocs.Watermark for .NET: Stáhněte si knihovnu a odkazujte na ni ve svém projektu.[Stáhněte si GroupDocs.Watermark pro .NET](https://releases.groupdocs.com/Watermark/net/)
- Základní znalost programování v C#: Bude užitečné porozumět základním konceptům programování v C#.
- Dokument k vodoznaku: Připravte si vzorový dokument, na který chcete vodoznak použít.
## Importovat jmenné prostory
Než začneme s příkladem, musíte importovat potřebné jmenné prostory. Přidejte následující příkazy pomocí příkazů v horní části souboru kódu:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Pojďme si rozdělit proces přidávání vodoznaku do dokumentu pomocí GroupDocs.Watermark for .NET do zvládnutelných kroků. Chcete-li úspěšně použít vodoznak a uložit dokument do určeného umístění, postupujte podle těchto kroků.
## Krok 1: Nastavte svůj projekt
Začněte vytvořením nového projektu .NET v sadě Visual Studio. Pro jednoduchost si můžete vybrat konzolovou aplikaci.
1. Otevřete Visual Studio.
2.  Vybrat`File` >`New` >`Project`.
3.  Vybrat`Console App (.NET Core)` nebo`Console App (.NET Framework)`.
4.  Pojmenujte svůj projekt a klikněte`Create`.

## Krok 2: Připravte si dokument a text vodoznaku
### Zadejte cestu dokumentu
Definujte cestu k dokumentu, který chcete označit vodoznakem. Pro tento příklad použijeme zástupnou cestu.
```csharp
string documentPath = "Your Document Path";
```
### Definujte výstupní cestu
Nastavte výstupní cestu, kam chcete uložit dokument s vodoznakem.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Krok 3: Vložte dokument
 Použijte`Watermarker` třídy k načtení dokumentu. Tato třída poskytuje metody pro přidávání, odstraňování a úpravu vodoznaků.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Zde přidejte logiku vodoznaku
}
```
## Krok 4: Vytvořte a přidejte vodoznak

### Vytvořit textový vodoznak
 Instantovat a`TextWatermark` objekt s požadovanými vlastnostmi textu a písma.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Přidat vodoznak do dokumentu
 Přidejte vytvořený vodoznak do dokumentu pomocí`Add` metoda`Watermarker` třída.
```csharp
watermarker.Add(watermark);
```
## Krok 5: Uložte dokument
Nakonec uložte dokument s vodoznakem na určené místo.
```csharp
watermarker.Save(outputFileName);
```
## Závěr
Vodoznak vašich dokumentů pomocí GroupDocs Watermark for .NET je přímočarý proces, který může výrazně zlepšit zabezpečení vašich dokumentů. Podle tohoto podrobného průvodce můžete snadno přidat vodoznaky do dokumentů a uložit je na požadované místo. Ať už chráníte duševní vlastnictví, zajišťujete pravost dokumentů nebo jednoduše přidáváte profesionální dotek, GroupDocs.Watermark for .NET poskytuje nástroje, které potřebujete.
## FAQ
### Mohu použít obrázky jako vodoznaky s GroupDocs.Watermark pro .NET?
Ano, s GroupDocs můžete používat vodoznaky pro text i obrázky. Knihovna podporuje různé typy vodoznaků, aby vyhovovaly vašim potřebám.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[webová stránka](https://releases.groupdocs.com/).
### Jak si mohu zakoupit licenci pro GroupDocs.Watermark for .NET?
 Licenci si můžete zakoupit od[nákupní stránku](https://purchase.groupdocs.com/buy).
### Podporuje GroupDocs.Watermark for .NET dávkové vodoznaky?
Ano, můžete vodoznakem více dokumentů v dávkovém procesu opakováním seznamu dokumentů a použitím vodoznaků.
### Kde mohu získat podporu pro GroupDocs.Watermark pro .NET?
 Podpora je k dispozici na[Fórum GroupDocs](https://forum.groupdocs.com/c/watermark/19).