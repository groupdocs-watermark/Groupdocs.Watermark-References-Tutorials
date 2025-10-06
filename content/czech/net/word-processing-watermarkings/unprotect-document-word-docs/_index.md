---
title: Odemkněte dokument v Dokumentech aplikace Word
linktitle: Odemkněte dokument v Dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak snadno zrušit ochranu dokumentů aplikace Word pomocí GroupDocs.Watermark for .NET. Postupujte podle našeho podrobného průvodce.
weight: 38
url: /cs/net/word-processing-watermarkings/unprotect-document-word-docs/
type: docs
---
# Odemkněte dokument v Dokumentech aplikace Word

## Úvod
GroupDocs.Watermark for .NET je výkonné API, které umožňuje vývojářům pracovat s vodoznaky v různých formátech dokumentů, včetně dokumentů Word. V tomto tutoriálu vás provedeme procesem zrušení ochrany dokumentu aplikace Word pomocí GroupDocs.Watermark for .NET. Ať už jste zkušený vývojář nebo s vývojem .NET teprve začínáte, tento podrobný průvodce vám pomůže splnit tento úkol efektivně.
## Předpoklady
Než začneme, ujistěte se, že máte splněny následující předpoklady:
1.  GroupDocs.Watermark for .NET: Ve vývojovém prostředí musíte mít nainstalované rozhraní GroupDocs.Watermark for .NET API. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Vývojové prostředí: Ujistěte se, že máte vhodné vývojové prostředí nastavené pro vývoj .NET, včetně sady Visual Studio nebo jakéhokoli jiného kompatibilního IDE.
3. Dokument aplikace Word: Připravte si ve svém systému souborů dokument aplikace Word, u kterého chcete zrušit ochranu.

## Importovat jmenné prostory
Než se ponoříte do kódu, musíte do svého .NET projektu importovat potřebné jmenné prostory. To vám umožní bezproblémový přístup k funkcím, které poskytuje GroupDocs.Watermark for .NET.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Krok 1: Zadejte cestu dokumentu
Definujte cestu k dokumentu aplikace Word, který chcete zrušit.
```csharp
string documentPath = "Your Document Path";
```
 Nahradit`"Your Document Path"` se skutečnou cestou k dokumentu aplikace Word.
## Krok 2: Nastavte název výstupního souboru
Zadejte adresář, kam chcete uložit nechráněný dokument, a zadejte název výstupního souboru.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Directory"` s cestou k adresáři, kam chcete uložit výstupní soubor.
## Krok 3: Načtěte dokument s možnostmi
 Vytvořte instanci`WordProcessingLoadOptions` k načtení dokumentu aplikace Word se specifickými možnostmi.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Krok 4: Zrušte ochranu dokumentu
 Vytvořte instanci`Watermarker` třídy s možností cesty dokumentu a načtení. Poté získejte obsah dokumentu jako WordProcessingContent a zrušte jeho ochranu.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## Závěr
Pomocí následujících kroků můžete snadno zrušit ochranu dokumentu aplikace Word pomocí GroupDocs.Watermark for .NET. Toto rozhraní API poskytuje přímý způsob, jak manipulovat s vodoznaky a efektivně chránit vaše dokumenty.
## FAQ
### Je GroupDocs.Watermark for .NET kompatibilní se všemi verzemi .NET?
Ano, GroupDocs.Watermark for .NET je kompatibilní s .NET Framework 2.0 a novějšími verzemi, včetně .NET Core a .NET Standard.
### Mohu použít vodoznak na dokumenty v jiných formátech než Word?
Absolutně! GroupDocs.Watermark for .NET podporuje širokou škálu formátů dokumentů, včetně PDF, Excel, PowerPoint a dalších.
### Je k dispozici zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi od[tady](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Watermark pro .NET?
 Můžete navštívit[Fórum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) za technickou pomoc a podporu komunity.
### Mohu si zakoupit dočasnou licenci pro GroupDocs.Watermark for .NET?
 Ano, můžete si zakoupit dočasnou licenci od[tady](https://purchase.groupdocs.com/temporary-license/).