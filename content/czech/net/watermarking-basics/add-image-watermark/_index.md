---
title: Přidat obrázek vodoznak
linktitle: Přidat obrázek vodoznak
second_title: GroupDocs.Watermark .NET API
description: Pomocí GroupDocs.Watermark for .NET můžete do svých dokumentů bez námahy přidávat obrázkové vodoznaky. Chraňte své duševní vlastnictví snadno.
weight: 10
url: /cs/net/watermarking-basics/add-image-watermark/
type: docs
---
# Přidat obrázek vodoznak

## Úvod
V tomto tutoriálu se ponoříme do procesu přidávání vodoznaku obrázku do vašich dokumentů pomocí GroupDocs.Watermark for .NET. Vodoznakové dokumenty jsou nezbytné pro ochranu duševního vlastnictví a značky. S GroupDocs.Watermark for .NET můžete bez problémů integrovat vodoznaky do různých formátů dokumentů, jako je Word, Excel, PowerPoint, PDF a mnoho dalších.
## Předpoklady
Než začneme, ujistěte se, že máte splněny následující předpoklady:
1.  Knihovna GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Watermark for .NET z[webová stránka](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Připravte si dokument, do kterého chcete přidat vodoznak.
3. Obrázek pro vodoznak: Připravte soubor obrázku, který chcete použít jako vodoznak.

## Importovat jmenné prostory
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Inicializujte cestu k dokumentu a výstupní adresář
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` absolutní nebo relativní cestou k vašemu dokumentu a`"Your Document Directory"` s adresářem, kam chcete uložit dokument s vodoznakem.
## Krok 2: Otevřete tok dokumentů a inicializujte vodoznak
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Proces vodoznaku bude probíhat zde
    }
}
```
 Otevřete stream dokumentů pomocí`FileStream` a inicializujte`Watermarker` objekt.
## Krok 3: Přidejte vodoznak obrázku
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Vytvořit`ImageWatermark` objekt s cestou k souboru obrázku, který chcete použít jako vodoznak. Nastavte vodorovné a svislé zarovnání vodoznaku.
## Krok 4: Uložte dokument s vodoznakem
```csharp
watermarker.Save(outputFileName);
```
Uložte dokument s vodoznakem do zadaného výstupního adresáře s požadovaným názvem souboru.

## Závěr
Na závěr, GroupDocs.Watermark for .NET poskytuje komplexní řešení pro snadné přidávání vodoznaků do různých formátů dokumentů. Podle kroků uvedených v tomto kurzu můžete efektivně přidávat obrazové vodoznaky do svých dokumentů a chránit své duševní vlastnictví.
## FAQ
### Mohu přidat textové vodoznaky pomocí GroupDocs.Watermark for .NET?
Ano, GroupDocs.Watermark for .NET podporuje přidávání obrazových i textových vodoznaků do dokumentů.
### Je GroupDocs.Watermark for .NET kompatibilní s různými formáty dokumentů?
GroupDocs.Watermark for .NET samozřejmě podporuje širokou škálu formátů dokumentů včetně Wordu, Excelu, PowerPointu, PDF a dalších.
### Poskytuje GroupDocs.Watermark for .NET možnosti přizpůsobení vodoznaků?
Ano, můžete přizpůsobit různé aspekty vodoznaku, jako je poloha, velikost, neprůhlednost a otočení.
### Mohu odstranit vodoznaky z dokumentů pomocí GroupDocs.Watermark for .NET?
Ano, GroupDocs.Watermark for .NET nabízí funkce pro detekci a odstranění vodoznaků z dokumentů.
### Je k dispozici zkušební verze pro GroupDocs.Watermark pro .NET?
 Ano, na webu můžete využít bezplatnou zkušební verzi a prozkoumat funkce před nákupem[tady](https://releases.groupdocs.com/).