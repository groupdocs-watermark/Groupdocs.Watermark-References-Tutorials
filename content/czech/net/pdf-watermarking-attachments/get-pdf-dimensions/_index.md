---
title: Získejte rozměry PDF
linktitle: Získejte rozměry PDF
second_title: GroupDocs.Watermark .NET API
description: Chraňte své dokumenty snadno pomocí Groupdocs.Watermark pro .NET. Přidejte vodoznaky, razítka a poznámky bez námahy.
weight: 26
url: /cs/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# Získejte rozměry PDF

## Úvod
dnešní digitální době je ochrana vašich dokumentů prvořadá. Ať už jste obchodní profesionál, právní expert nebo kreativní umělec, ochrana vašeho duševního vlastnictví je zásadní. Groupdocs.Watermark for .NET nabízí robustní řešení pro přidávání vodoznaků, razítek a poznámek k vašim dokumentům, což zajišťuje jejich bezpečnost a pravost.
## Předpoklady
Než se ponoříte do světa Groupdocs.Watermark for .NET, ujistěte se, že máte splněny následující předpoklady:
1.  Instalace Groupdocs.Watermark for .NET: Stáhněte a nainstalujte Groupdocs.Watermark for .NET z[odkaz ke stažení](https://releases.groupdocs.com/Watermark/net/).
2.  Licenční klíč (Volitelně): Zatímco Groupdocs.Watermark for .NET nabízí bezplatnou zkušební verzi, můžete se rozhodnout pro dočasnou licenci nebo zakoupit plnou licenci od[tady](https://purchase.groupdocs.com/buy) pro rozšířenou funkčnost.
3. Znalost C#: Pro pochopení a implementaci uvedených příkladů se doporučuje základní znalost programovacího jazyka C#.
4. Dokument k ochraně: Připravte si vzorový dokument (např. PDF, Word, Excel) na místním počítači, se kterým můžete experimentovat.

## Importovat jmenné prostory
Chcete-li začít pracovat s Groupdocs.Watermark for .NET, musíte do svého projektu C# importovat potřebné jmenné prostory.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Krok 1: Deklarujte proměnné
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Krok 2: Vložte dokument
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Krok 3: Získejte obsah PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Krok 4: Načtení rozměrů
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Závěr
Na závěr, Groupdocs.Watermark for .NET nabízí komplexní řešení pro ochranu vašich dokumentů před neoprávněným použitím a distribucí. Dodržením výše uvedených kroků a využitím výkonu Groupdocs.Watermark pro .NET můžete zajistit bezpečnost a integritu svých cenných digitálních aktiv.
## FAQ
### Mohu používat Groupdocs.Watermark pro .NET zdarma?
Ano, Groupdocs.Watermark for .NET nabízí bezplatnou zkušební verzi pro účely vyhodnocení. Pro rozšířenou funkčnost však můžete zvážit zakoupení plné licence.
### Podporuje Groupdocs.Watermark více formátů dokumentů?
Ano, Groupdocs podporuje širokou škálu formátů dokumentů včetně PDF, Word, Excel, PowerPoint a dalších.
### Mohu upravit vodoznaky a razítka pomocí Groupdocs.Watermark?
Absolutně! Groupdocs.Watermark poskytuje rozsáhlé možnosti přizpůsobení vodoznaků, razítek a poznámek tak, aby vyhovovaly vašim specifickým požadavkům.
### Je pro uživatele Groupdocs.Watermark k dispozici technická podpora?
 Ano, můžete získat technickou pomoc a zapojit se do komunity Groupdocs prostřednictvím[Fórum podpory](https://forum.groupdocs.com/c/watermark/19).
### Jak mohu získat dočasnou licenci pro Groupdocs.Watermark?
 Dočasnou licenci pro Groupdocs.Watermark můžete získat od[tady](https://purchase.groupdocs.com/temporary-license/).