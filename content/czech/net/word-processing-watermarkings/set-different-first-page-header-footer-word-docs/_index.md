---
title: Nastavit jiné záhlaví/zápatí první stránky v Dokumentech aplikace Word
linktitle: Nastavit jiné záhlaví/zápatí první stránky v Dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak nastavit různá záhlaví a zápatí na první stránce dokumentů Word pomocí GroupDocs.Watermark for .NET.
weight: 36
url: /cs/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
type: docs
---
# Nastavit jiné záhlaví/zápatí první stránky v Dokumentech aplikace Word

## Úvod
oblasti správy a manipulace s dokumenty se GroupDocs.Watermark for .NET ukazuje jako výkonný nástroj, který nabízí bezproblémovou integraci a robustní funkce pro vodoznaky dokumentů. Jedním z běžných požadavků při zpracování dokumentů je nastavení různých záhlaví a zápatí na první stránce dokumentů aplikace Word. Tento tutoriál objasní proces dosažení tohoto úkolu pomocí GroupDocs.Watermark for .NET, přičemž každý krok rozdělí do snadno srozumitelných segmentů.
## Předpoklady
Než se pustíte do implementace, ujistěte se, že jsou splněny následující předpoklady:
1.  Instalace GroupDocs.Watermark for .NET: Stáhněte a nainstalujte GroupDocs.Watermark for .NET z[odkaz ke stažení](https://releases.groupdocs.com/Watermark/net/).
2. Příprava dokumentu: Připravte si dokument aplikace Word, který vyžaduje nastavení různých záhlaví a zápatí na první stránce.

## Importovat jmenné prostory
Chcete-li začít, importujte potřebné obory názvů potřebné pro využití funkcí GroupDocs.Watermark for .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 tomto kroku definujeme cestu k dokumentu, který je potřeba zpracovat a určíme název výstupního souboru a adresář. Navíc inicializujeme a`Watermarker` objekt s možností cesty dokumentu a načtení.
## Krok 2: Přístup k obsahu dokumentu
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Zde načteme obsah dokumentu aplikace Word pomocí`GetContent<T>()` metoda`Watermarker` objekt s uvedením typu obsahu jako`WordProcessingContent`.
## Krok 3: Nakonfigurujte nastavení stránky
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
V tomto kroku nakonfigurujeme možnosti nastavení stránky, abychom povolili různá záhlaví a zápatí pro první stránku (`DifferentFirstPageHeaderFooter`) a také pro liché a sudé stránky (`OddAndEvenPagesHeaderFooter`).
## Krok 4: Uložte změny
```csharp
watermarker.Save(outputFileName);
```
 Nakonec změny provedené v dokumentu uložíme voláním`Save()` metoda`Watermarker` objekt, předání názvu výstupního souboru.

## Závěr
GroupDocs.Watermark for .NET poskytuje jednoduché řešení pro nastavení různých záhlaví a zápatí na první stránce dokumentů aplikace Word. Podle kroků uvedených v tomto kurzu mohou uživatelé bez námahy manipulovat s obsahem dokumentu podle svých požadavků.
## FAQ
### Dokáže GroupDocs.Watermark for .NET zpracovat jiné formáty dokumentů kromě Wordu?
Ano, GroupDocs.Watermark for .NET podporuje širokou škálu formátů dokumentů včetně PDF, Excel, PowerPoint a dalších.
### Je k dispozici zkušební verze pro účely testování?
Ano, uživatelé mohou využít bezplatnou zkušební verzi GroupDocs.Watermark for .NET z webu[stránka vydání](https://releases.groupdocs.com/).
### Nabízí GroupDocs.Watermark for .NET technickou podporu?
 Ano, technická podpora pro GroupDocs pro .NET je k dispozici prostřednictvím[Fórum podpory](https://forum.groupdocs.com/c/watermark/19).
### Mohu si zakoupit dočasnou licenci pro krátkodobé použití?
 Ano, dočasné licence pro GroupDocs pro .NET lze získat z[Stránka pro dočasný nákup licence](https://purchase.groupdocs.com/temporary-license/).
### Kde najdu komplexní dokumentaci k GroupDocs.Watermark for .NET?
 Podrobná dokumentace k GroupDocs.Watermark for .NET je k dispozici na[Referenční stránka](https://tutorials.groupdocs.com/Watermark/net/).